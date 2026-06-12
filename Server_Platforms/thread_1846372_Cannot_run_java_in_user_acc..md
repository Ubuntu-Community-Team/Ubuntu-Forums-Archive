---
title: "Cannot run java in user acc."
date: 2011-09-18
forum: Server Platforms
---

### Post by kvant_doan on 2011-09-18
Hi all,

I am running CentOS server and now I am getting one problem. My friend cannot run java under his account. It also announces that java.lang.OutOfMemoryError as you can see 

```

java.lang.OutOfMemoryError: unable to create new native thread
        at java.lang.Thread.start0(Native Method)
        at java.lang.Thread.start(Thread.java:597)
        at java.util.concurrent.ThreadPoolExecutor.addIfUnderCorePoolSize(ThreadPoolExecutor.java:703)
        at java.util.concurrent.ThreadPoolExecutor.execute(ThreadPoolExecutor.java:652)
        at org.mortbay.thread.concurrent.ThreadPool.dispatch(ThreadPool.java:103)
        at org.mortbay.jetty.AbstractConnector.doStart(AbstractConnector.java:299)
        at org.mortbay.jetty.nio.SelectChannelConnector.doStart(SelectChannelConnector.java:306)
        at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:39)
        at org.mortbay.jetty.Server.doStart(Server.java:233)
        at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:39)


``` However, I can run this easily using root acc. I also do some checks such as java version, ulimit. Here are results of this account

```

$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Client VM (build 14.0-b16, mixed mode)

``````

$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
file size               (blocks, -f) unlimited
pending signals                 (-i) 1024
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
stack size              (kbytes, -s) 10240
cpu time               (seconds, -t) unlimited
max user processes              (-u) 100
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited


```Could you please give me some ways to fix this situation?

Thank you.

---

