---
title: "Connection issue in server"
date: 2010-03-22
forum: Server Platforms
---

### Post by amuthan on 2010-03-22
Hi,

 We are using hadoop servers which is hosted in another country, 1 master & 2 slaves. When I'm trying to run some processes as soon as reboot the server, I'm getting connection timed out error & other errors in between while running the script. Can anyone tell me why this problem is occuring again & again? This also occurs whenever a cycle of java processes are completed and when we start another cycle. I have given the ouput which we got in the terminal here.

[menon@265430-vm1 ~]$ cd /cluster/clusteruser/search/nutch-1.0
[menon@265430-vm1 nutch-1.0]$ cd bin/
[menon@265430-vm1 bin]$ ps -ef | grep java
menon   3742  3586  0 04:59 pts/0    00:00:00 grep java
[menon@265430-vm1 bin]$ ./stop-clear-start-dfs.sh
CLEAR THE DFS
Stoping the DFS...
no jobtracker to stop
10.26.160.151: no tasktracker to stop
10.26.160.152: no tasktracker to stop
no namenode to stop
10.26.160.152: no datanode to stop
10.26.160.151: no datanode to stop
10.26.160.150: no secondarynamenode to stop
DFS stopped!
Removing the DFS created directories...
Removing the dfs created directories from master
master cleanup completed
Removing the dfs created directories from slave 1
slave 1 cleanup completed
Removing the dfs created directories from slave 2
slave 2 cleanup completed
The DFS created directories were removed!
Formatting the DFS...
The DFS is formatted!
Starting the DFS again...
rsync from master:10.26.160.150:/cluster/clusteruser/search/nutch-1.0
ssh: connect to host master port 22: Connection timed out
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(463) [receiver=2.6.8]
starting namenode, logging to /cluster/clusteruser/search/nutch-1.0/logs/hadoop-menon-namenode-265430-vm1.mastercrawlserver.empowerresearch.com.out
10.26.160.152: rsync from master:10.26.160.150:/cluster/clusteruser/search/nutch-1.0
10.26.160.151: rsync from master:10.26.160.150/cluster/clusteruser/search/nutch-1.0
10.26.160.151: ssh: connect to host master port 22: Connection timed out
10.26.160.151: rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
10.26.160.151: rsync error: unexplained error (code 255) at io.c(463) [receiver=2.6.8]
10.26.160.152: ssh: connect to host master port 22: Connection timed out
10.26.160.152: rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
10.26.160.152: rsync error: unexplained error (code 255) at io.c(463) [receiver=2.6.8]
10.26.160.151: starting datanode, logging to /cluster/clusteruser/search/nutch-1.0/logs/hadoop-menon-datanode-265454-vm2.slavecrawlserverA.empowerresearch.com.out
10.26.160.152: starting datanode, logging to /cluster/clusteruser/search/nutch-1.0/logs/hadoop-menon-datanode-265455-vm3.slavecrawlserverB.empowerresearch.com.out
10.26.160.150: rsync from master:10.26.160.150:/cluster/clusteruser/search/nutch-1.0
10.26.160.150: ssh: connect to host master port 22: Connection timed out
10.26.160.150: rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
10.26.160.150: rsync error: unexplained error (code 255) at io.c(463) [receiver=2.6.8]
10.26.160.150: starting secondarynamenode, logging to /cluster/clusteruser/search/nutch-1.0/logs/hadoop-menon-secondarynamenode-265430-vm1.mastercrawlserver.empowerresearch.com.out
rsync from master:10.26.160.150:/cluster/clusteruser/search/nutch-1.0
ssh: connect to host master port 22: Connection timed out
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(463) [receiver=2.6.8]
starting jobtracker, logging to /cluster/clusteruser/search/nutch-1.0/logs/hadoop-menon-jobtracker-265430-vm1.mastercrawlserver.empowerresearch.com.out
10.26.160.152: rsync from master:10.26.160.150:/cluster/clusteruser/search/nutch-1.0
10.26.160.151: rsync from master:10.26.160.150/cluster/clusteruser/search/nutch-1.0
10.26.160.152: ssh: connect to host master port 22: Connection timed out
10.26.160.152: rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
10.26.160.152: rsync error: unexplained error (code 255) at io.c(463) [receiver=2.6.8]
10.26.160.152: starting tasktracker, logging to /cluster/clusteruser/search/nutch-1.0/logs/hadoop-menon-tasktracker-265455-vm3.slavecrawlserverB.empowerresearch.com.out
10.26.160.151: ssh: connect to host master port 22: Connection timed out
10.26.160.151: rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
10.26.160.151: rsync error: unexplained error (code 255) at io.c(463) [receiver=2.6.8]
10.26.160.151: starting tasktracker, logging to /cluster/clusteruser/search/nutch-1.0/logs/hadoop-menon-tasktracker-265454-vm2.slavecrawlserverA.empowerresearch.com.out
DFS is started!

Regards,
Amuthan G.

---

