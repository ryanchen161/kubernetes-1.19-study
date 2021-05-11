# k8s有以下几个进程

k8s最重要的2点设计：

1. resource RESTful API注册：

   apiserver注册并提供各种resource资源的RESTful API，apiserver是这些资源操作的入口。

2. list-watch机制：

   其他组件contoller-manager/scheduler/kube-proxy/kubelet通过异步通知机制list-watch进行资源实时监控。list是短链接，首次全部获得。watch是长链接，使用了http的chuck分块传输机制，会维持http的长链接。

------

下面这几个组件是以独立的进程在运行，下面目录也是各个进程的main函数入口所在位置

kube-apiserver 

​		main --> app.NewAPIServerCommand --> Run --> CreateServerChain

kube-controller-manager

kube-proxy

kube-sheduler

kubectl

kubelet

