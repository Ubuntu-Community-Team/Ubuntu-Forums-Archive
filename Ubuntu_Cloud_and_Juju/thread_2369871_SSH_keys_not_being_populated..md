---
title: "SSH keys not being populated."
date: 2017-08-28
forum: Ubuntu Cloud and Juju
---

### Post by michaelvdb2 on 2017-08-28
Hi All,
 
I’ve setup an Ubuntu vm with Juju installed.
I’ve managed to link it to a packstack openstack setup.
 
So I’ve configured MainStack to have the api to keystone on the packstack server 10.60.1.4
 
juju bootstrap MainStack --config network=38d1b49e-4ddb-47ef-92f2-23ffa5d2931f
 
so .. it proceeds to create then Xenical vm with out problems, it starts up and logs show that it gets valid routable IP.
 
Now the weird part is here.. eventually it will reach a state where it needs to ssh into the controller vm to do stuff.
So when not verify the host I did the recommended step  ‘ssh-keygen -f "/tmp/juju-known-hosts953850952" -R 10.60.1.31’ which fixed the part of the problem
But I don’t know what I missed not to have a ssh RSA key being created into the controller vm.
 
Can anyone give me pointers as to what to do ?
I think once this is done, it should be a working vm.
Oh I’m running packstack single node, because I don’t have that many hardware to play with and I need to do kvm testing. I can’t do the ubuntu single server lxd deployment.
 
Regards,
 
Michael
 
15:44:59 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: ssh: connect to host 10.60.1.31 port 22: Connection refused
15:45:04 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: ssh: connect to host 10.60.1.31 port 22: Connection refused
15:45:09 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: ssh: connect to host 10.60.1.31 port 22: Connection refused
15:45:14 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: ssh: connect to host 10.60.1.31 port 22: Connection refused
15:45:19 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: ssh: connect to host 10.60.1.31 port 22: Connection refused
15:45:24 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: ssh: connect to host 10.60.1.31 port 22: Connection refused
15:45:29 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: ssh: connect to host 10.60.1.31 port 22: Connection refused
15:45:34 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
SHA256:QPszhwseg3wKPRu9hkPILvsRVpP8FdqR5MHr9+556ac.
Please contact your system administrator.
Add correct host key in /tmp/juju-known-hosts953850952 to get rid of this message.
Offending RSA key in /tmp/juju-known-hosts953850952:1
  remove with:
  ssh-keygen -f "/tmp/juju-known-hosts953850952" -R 10.60.1.31
RSA host key for 10.60.1.31 has changed and you have requested strict checking.
Host key verification failed.
15:45:39 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
SHA256:QPszhwseg3wKPRu9hkPILvsRVpP8FdqR5MHr9+556ac.
Please contact your system administrator.
Add correct host key in /tmp/juju-known-hosts953850952 to get rid of this message.
Offending RSA key in /tmp/juju-known-hosts953850952:1
  remove with:
  ssh-keygen -f "/tmp/juju-known-hosts953850952" -R 10.60.1.31
RSA host key for 10.60.1.31 has changed and you have requested strict checking.
Host key verification failed.
15:45:44 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: No RSA host key is known for 10.60.1.31 and you have requested strict checking.
Host key verification failed.
15:45:49 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: No RSA host key is known for 10.60.1.31 and you have requested strict checking.
Host key verification failed.
15:45:54 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: No RSA host key is known for 10.60.1.31 and you have requested strict checking.
Host key verification failed.
15:45:59 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: No RSA host key is known for 10.60.1.31 and you have requested strict checking.
Host key verification failed.
15:46:04 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: No RSA host key is known for 10.60.1.31 and you have requested strict checking.
Host key verification failed.
15:46:09 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: No RSA host key is known for 10.60.1.31 and you have requested strict checking.
Host key verification failed.
15:46:14 DEBUG juju.provider.common bootstrap.go:497 connection attempt for 10.60.1.31 failed: No RSA host key is known for 10.60.1.31 and you have requested strict checking.
Host key verification failed.

---

