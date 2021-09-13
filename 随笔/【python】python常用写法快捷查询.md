
# pandas



```python
# 如何输出每行的值
for index,row in df.iterrows():
    print(index)

# 如何对dataframe做多个条件的过滤，两种写法：
    # 1、普通的写法
    data[(data.a > 2)&(data.a<3)]
    # 2、query的写法（如果数据量很多、且处于介值的化比较方便）
    ## 比较pythonic
    data.query(2<a<3>)

# 对数据进行groupby 和 降序展示
df.groupby('serial_id').count().sort_values('pass',ascending=False).head(10)

# 关于解析json文件
'''
1、对json格式的数据使用json.loads;这种办法不会处理json内部的嵌套格式；
2、嵌套格式使用pd.json_normalize，返回的是一个DataFrame的格式；
3、展开后的数据列名称为：a.b.c
'''
L,F = [],[]
for data in t:
    time, elements = data.split('c.c.b.f.engine.service.OrderService - ')
    try:
        elements = json.loads(elements[1:-2])
        L.append(elements)    
    except:
        F.append(elements)
df = pd.json_normalize(L)

# 针对多列的逻辑计算
# 重点是：axis=1
data_all['lapass'] = data_all.apply(lambda x: x['islast']*x['pass'],axis=1)

```

## 参考文章
[关于如何按行输出每一行的值：](https://blog.csdn.net/sinat_29675423/article/details/87972498)

[pandas的去重方法，包括保留第一个值、保留最后一个值](https://www.yisu.com/zixun/150970.html#:~:text=pandas%E4%B8%AD%E7%9A%84%E6%95%B0%E6%8D%AE%E5%8E%BB%E9%87%8D%E5%A4%84%E7%90%86%E7%9A%84%E5%AE%9E%E7%8E%B0%E6%96%B9%E6%B3%95.%20%E6%95%B0%E6%8D%AE%E5%8E%BB%E9%87%8D%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8duplicated%20%28%29%E5%92%8Cdrop_duplicates%20%28%29%E4%B8%A4%E4%B8%AA%E6%96%B9%E6%B3%95%E3%80%82.%20DataFrame.duplicated%EF%BC%88subset%20%3D,None%EF%BC%8Ckeep%20%3D%E2%80%98first%27%20%EF%BC%89%E8%BF%94%E5%9B%9Eboolean%20Series%E8%A1%A8%E7%A4%BA%E9%87%8D%E5%A4%8D%E8%A1%8C.%20first%EF%BC%9A%E6%A0%87%E8%AE%B0%E9%87%8D%E5%A4%8D%EF%BC%8CTrue%E9%99%A4%E4%BA%86%E7%AC%AC%E4%B8%80%E6%AC%A1%E5%87%BA%E7%8E%B0%E3%80%82.%20last%EF%BC%9A%E6%A0%87%E8%AE%B0%E9%87%8D%E5%A4%8D%EF%BC%8CTrue%E9%99%A4%E4%BA%86%E6%9C%80%E5%90%8E%E4%B8%80%E6%AC%A1%E5%87%BA%E7%8E%B0%E3%80%82.)

[关于pandas的链接操作，主要注意反人类的写法](https://www.jianshu.com/p/2358d4013067)