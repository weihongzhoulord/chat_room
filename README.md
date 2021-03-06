# 项目描述
+ 功能：支持注册、私聊、群聊、退出功能的网络聊天室。
+ 使用技术：Java基础、多线程、Socket编程、Maven管理、I/O处理。

# 实现思路

客户端与服务端通信过程

```
1.服务端ServerSocket监听客户端消息
2.监听到有客户端加入就实例化一个服务端处理任务并提交到线程池执行
3.客户端获取来着服务端的消息，客户端向服务端发送消息
4.服务端获取客户端的消息，服务端向客户端发送消息
```

私聊

```
1.客户端A发起私聊信息和私聊的客户端B到服务端
2.服务端从数据容器中找到客户端A的私聊的客户端B（服务端会保存所有客户端信息）
3.拿到客户端B，将客户端A发送给B的信息给客户端B

通俗理解：
客户端A：对服务端说，我给客户端B发message
服务端：从数据容器中找到客户端B，将客户端A给客户端B的message发给客户端B
```

群聊

```
1.某客户端发起信息到服务端
2.服务端从数据容器中拿到该群所有的客户端
3.将那个客户端发起的信息依次发送给该群所有客户端
```