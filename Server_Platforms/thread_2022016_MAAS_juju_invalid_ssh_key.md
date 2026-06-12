---
title: "MAAS juju invalid ssh key"
date: 2012-07-10
forum: Server Platforms
---

### Post by Keamas on 2012-07-10
Hi I would like to setup a MAAS for OpenStack with Ubuntu 12.04

Everything workes great to this point
When i would like to bootstrap juju i get a error of a invalid ssh key
I did everything like in the ubuntu MAAS wiki documentation

> marcel@ubuntu20:~$ juju status 2012-07-09 13:00:02,559 INFO Connecting to environment... The authenticity of host 'node1 (10.110.11.71)' can't be established. ECDSA key fingerprint is 29:42:2c:7a:ef:52:d4:f8:63:51:d8:a1:1e:a9:16:0e. Are you sure you want to continue connecting (yes/no)? yes 2012-07-09 13:00:05,883 ERROR Invalid SSH key

I read some more people have this issu not sure if it is a BUG but I couldn't find a working solution... I read this Posting [http://askubuntu.com/questions/147714/invalid-ssh-key-error-in-juju-when-using-it-with-maas](http://askubuntu.com/questions/147714/invalid-ssh-key-error-in-juju-when-using-it-with-maas)

I added a Root User to this File that I can Access the Nodes: /var/lib/cobbler/kickstarts/maas.preseed:

dns time everything is correct. I can also ssh to the machine
It seems that there is no ubuntu user so i added one And created a ssh key with ssh- without passphrase
Than i copied the keys and now i can ssh with ubuntu user without a pw

> marcel@ubuntu20:~$ juju status
2012-07-09 15:43:12,130 INFO Connecting to environment...
Warning: the ECDSA host key for 'node1' differs from the key for the IP address '10.110.11.71'
Offending key for IP in /home/marcel/.ssh/known_hosts:1
Matching host key in /home/marcel/.ssh/known_hosts:8
Are you sure you want to continue connecting (yes/no)? yes
A clouser look showes me this issues:

> marcel@ubuntu20:~$ juju -v status
2012-07-09 15:36:49,458 DEBUG Initializing juju status runtime
2012-07-09 15:36:49,469 INFO Connecting to environment...
2012-07-09 15:36:49,588 DEBUG Connecting to environment using node1...
2012-07-09 15:36:49,589 DEBUG Spawning SSH process with remote_user="ubuntu" remote_host="node1" remote_port="2181" local_port="43964".
Warning: the ECDSA host key for 'node1' differs from the key for the IP address '10.110.11.71'
Offending key for IP in /home/marcel/.ssh/known_hosts:1
Matching host key in /home/marcel/.ssh/known_hosts:8
Are you sure you want to continue connecting (yes/no)? yes
2012-07-09 15:36:53,098:16474(0x7f0c16d58700):ZOO_INFO@log_env@658: Client environment:zookeeper.version=zookeeper C client 3.3.5
2012-07-09 15:36:53,098:16474(0x7f0c16d58700):ZOO_INFO@log_env@662: Client environment:host.name=ubuntu20
2012-07-09 15:36:53,098:16474(0x7f0c16d58700):ZOO_INFO@log_env@669: Client environment:os.name=Linux
2012-07-09 15:36:53,098:16474(0x7f0c16d58700):ZOO_INFO@log_env@670: Client environment:os.arch=3.2.0-23-generic
2012-07-09 15:36:53,098:16474(0x7f0c16d58700):ZOO_INFO@log_env@671: Client environment:os.version=#36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012
2012-07-09 15:36:53,099:16474(0x7f0c16d58700):ZOO_INFO@log_env@679: Client environment:user.name=marcel
2012-07-09 15:36:53,099:16474(0x7f0c16d58700):ZOO_INFO@log_env@687: Client environment:user.home=/home/marcel
2012-07-09 15:36:53,099:16474(0x7f0c16d58700):ZOO_INFO@log_env@699: Client environment:user.dir=/home/marcel
2012-07-09 15:36:53,099:16474(0x7f0c16d58700):ZOO_INFO@zookeeper_init@727: Initiating client connection, host=localhost:43964 sessionTimeout=10000 watcher=0x7f0c14b886b0 sessionId=0 sessionPasswd=<null> context=0x367e940 flags=0
2012-07-09 15:36:53,100:16474(0x7f0c118e2700):ZOO_INFO@check_events@1585: initiated connection to server [127.0.0.1:43964]
2012-07-09 15:36:53,100:16474(0x7f0c118e2700):ZOO_ERROR@handle_socket_error_msg@1603: Socket [127.0.0.1:43964] zk retcode=-4, errno=112(Host is down): failed while receiving a server response
2012-07-09 15:36:56,434:16474(0x7f0c118e2700):ZOO_ERROR@handle_socket_error_msg@1579: Socket [127.0.0.1:43964] zk retcode=-4, errno=111(Connection refused): server refused to accept the client
2012-07-09 15:36:59,770:16474(0x7f0c118e2700):ZOO_ERROR@handle_socket_error_msg@1579: Socket [127.0.0.1:43964] zk retcode=-4, errno=111(Connection refused): server refused to accept the client
2012-07-09 15:37:03,107:16474(0x7f0c118e2700):ZOO_ERROR@handle_socket_error_msg@1579: Socket [127.0.0.1:43964] zk retcode=-4, errno=111(Connection refused): server refused to accept the client
2012-07-09 15:37:06,443:16474(0x7f0c118e2700):ZOO_ERROR@handle_socket_error_msg@1579: Socket [127.0.0.1:43964] zk retcode=-4, errno=111(Connection refused): server refused to accept the client
2012-07-09 15:37:09,779:16474(0x7f0c118e2700):ZOO_ERROR@handle_socket_error_msg@1579: Socket [127.0.0.1:43964] zk retcode=-4, errno=111(Connection refused): server refused to accept the client
2012-07-09 15:37:13,116:16474(0x7f0c118e2700):ZOO_ERROR@handle_socket_error_msg@1579: Socket [127.0.0.1:43964] zk retcode=-4, errno=111(Connection refused): server refused to accept the client
2012-07-09 15:37:16,452:16474(0x7f0c118e2700):ZOO_ERROR@handle_socket_error_msg@1579: Socket [127.0.0.1:43964] zk retcode=-4, errno=111(Connection refused): server refused to accept the client
2012-07-09 15:37:19,589 DEBUG Retrying connection: Cannot connect to environment using node1 (perhaps still initializing): could not connect before timeout after 1 retries
2012-07-09 15:37:19,708 DEBUG Connecting to environment using node1...
2012-07-09 15:37:19,708 DEBUG Spawning SSH process with remote_user="ubuntu" remote_host="node1" remote_port="2181" local_port="60742".
Warning: the ECDSA host key for 'node1' differs from the key for the IP address '10.110.11.71'
Of

I think the bug is that there is no Ubuntu User in this installation but how can I fix it right ?




Edit:

Oh sorry I posted it here can anyone please move it into the Ubuntu Cloud Subforum thx !!

---

