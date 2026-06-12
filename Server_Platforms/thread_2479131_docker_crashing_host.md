---
title: "docker crashing host"
date: 2022-09-15
forum: Server Platforms
---

### Post by ericbarber2 on 2022-09-15
i have an ubuntu 20.04 server with a couple mounts and docker running on it.  Randomly it appears that my docker containers are crashing my host.  I am unable to find any logs that will tell me why my server has become unresponsive.  the only only the screen shows a "[COLOR=#24292F][FONT=ui-monospace]Memory cgroup out of memory: Kill process.....".  I did not think a docker container could crash a host?  Where can i find more information about what is happening?[/FONT][/COLOR]

---

### Post by ameinild on 2022-09-15
Here is a related topic on [Stack Exchange]("https://stackoverflow.com/questions/72937671/mongod-killed-by-oom-kill-memory-cgroup-out-of-memory-kill-process-20391-mon").

My theory is (like the SE answer) that oom-killer sets in and kills the process because of lack of memory - the thread on SE seems to have a possible solution, so you could try that.

If you expect more help here, you should probably include both some  details about which containers are affected, some logs, and some server  metrics in general (RAM usage etc.).

---

