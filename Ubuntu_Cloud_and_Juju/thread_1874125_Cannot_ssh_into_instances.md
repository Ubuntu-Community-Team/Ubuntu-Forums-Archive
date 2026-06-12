---
title: "Cannot ssh into instances"
date: 2011-11-02
forum: Ubuntu Cloud and Juju
---

### Post by andpapad on 2011-11-02
My system has one server clc and walrus, another server as cc and sc and few node controllers.
All servers are running ubuntu 11.04 server.
Eucalyptus is configured in system networking mode.

I have built an image with user and password and I was able to login to the instances (ssh user@instanceip).

I am trying to run an instance which runs but I cannot access it.
I download [http://cloud-images.ubuntu.com/lucid/20111101/lucid-server-cloudimg-amd64.tar.gz](http://cloud-images.ubuntu.com/lucid/20111101/lucid-server-cloudimg-amd64.tar.gz)
After download I executed
uec-publish-tarball lucid-server-cloudimg-amd64.tar.gz lucid
which completed successfully resulting on creating a bucket named lucid and an eki and an emi.

$ euca-describe-images | grep lucid/
IMAGE emi-E9B51572 lucid/lucid-server-cloudimg-amd64.img.manifest.xml admin available public x86_64 machine eki-33971A7B instance-store
IMAGE eki-33971A7B lucid/lucid-server-cloudimg-amd64-vmlinuz-virtual.manifest.xml admin available public x86_64 kernel instance-store

I then execute:
euca-run-instances -k akey --addressing private emi-E9B51572
and after a while I get the instance running.
$ euca-describe-instances i-488B084F
RESERVATION r-47DC0818 admin default
INSTANCE i-488B084F emi-E9B51572 10.16.3.99 172.19.1.36 running akey 0 m1.small 2011-11-02T16:32:19.617Z NephelaeCC1 eki-33971A7B
The problem is when I try to ssh into the instance.
Before running ssh (I guess because get-console-output says [XX/100]: url error [[Errno 111] Connection refused]: from XX=1 to 100):
$ ssh -i akey.priv -vvv ubuntu@10.16.3.99
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 10.16.3.99 [10.16.3.99] port 22.
debug1: connect to address 10.16.3.99 port 22: Connection refused
ssh: connect to host 10.16.3.99 port 22: Connection refused
andreas@Nephelae:~$ chmod 0600 akey.priv
andreas@Nephelae:~$ ssh -i akey.priv -vvv ubuntu@10.16.3.99
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 10.16.3.99 [10.16.3.99] port 22.
debug1: connect to address 10.16.3.99 port 22: Connection refused
ssh: connect to host 10.16.3.99 port 22: Connection refused

After reaching 100/100 in console output I get this when I try to ssh:

$ ssh -i akey.priv -vvv ubuntu@10.16.3.99
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 10.16.3.99 [10.16.3.99] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "akey.priv" as a RSA1 public key
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file akey.priv type -1
debug1: identity file akey.priv-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu7
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu7 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "10.16.3.99" from file "/home/andreas/.ssh/known_hosts"
debug3: load_hostkeys: loaded 0 keys
debug3: load_hostkeys: loading entries for host "10.16.3.99" from file "/etc/ssh/ssh_known_hosts"
debug3: load_hostkeys: loaded 0 keys
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

NodeController log:
$ cat /var/log/eucalyptus/nc.log | grep i-488B084F
[Wed Nov 2 18:32:12 2011][001660][EUCAINFO ] doRunInstance() invoked (id=i-488B084F cores=1 disk=2 memory=192)
[Wed Nov 2 18:32:12 2011][001660][EUCADEBUG ] state change for instance i-488B084F: Unknown -> Staging (Pending)
[Wed Nov 2 18:32:12 2011][001660][EUCAINFO ] network started for instance i-488B084F
[Wed Nov 2 18:32:12 2011][001660][EUCAINFO ] retrieving images for instance i-488B084F (disk limit=2048MB)...
[Wed Nov 2 18:32:12 2011][001660][EUCAINFO ] vrun(): [cp -a /var/lib/eucalyptus/instances//eucalyptus/cache/eki-33971A7B/kernel /var/lib/eucalyptus/instances//admin/i-488B084F/kernel]
[Wed Nov 2 18:32:12 2011][001660][EUCAINFO ] vrun(): [cp -a /var/lib/eucalyptus/instances//eucalyptus/cache/emi-E9B51572/disk /var/lib/eucalyptus/instances//admin/i-488B084F/disk]
[Wed Nov 2 18:32:13 2011][001660][EUCAINFO ] vrun(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/partition2disk /var/lib/eucalyptus/instances//admin/i-488B084F/disk 512 91]
[Wed Nov 2 18:32:16 2011][001660][EUCAINFO ] preparing images for instance i-488B084F...
[Wed Nov 2 18:32:16 2011][001660][EUCAINFO ] adding key/tmp/sckey.5AhsfU to the root file system at /var/lib/eucalyptus/instances//admin/i-488B084F/disk using (//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/add_key.pl //usr/lib/eucalyptus/euca_mountwrap)
[Wed Nov 2 18:32:16 2011][001660][EUCAINFO ] vrun(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/add_key.pl //usr/lib/eucalyptus/euca_mountwrap 32256 /var/lib/eucalyptus/instances//admin/i-488B084F/disk /tmp/sckey.5AhsfU]
[Wed Nov 2 18:32:16 2011][001660][EUCADEBUG ] doDescribeInstances(): instanceId=i-488B084F publicIp=0.0.0.0 privateIp=172.19.1.36 mac=D0:0D:48:8B:08:4F vlan=11 networkIndex=4
[Wed Nov 2 18:32:18 2011][001660][EUCADEBUG ] system_output(): [//usr/lib/eucalyptus/euca_rootwrap //usr/share/eucalyptus/gen_kvm_libvirt_xml --ephemeral --basepath='/var/lib/eucalyptus/instances//admin/i-488B084F']
[Wed Nov 2 18:32:18 2011][001660][EUCAINFO ] currently running/booting: i-444E08FE i-488B084F
[Wed Nov 2 18:32:20 2011][001660][EUCAINFO ] booting VM instance i-488B084F
[Wed Nov 2 18:32:20 2011][001660][EUCADEBUG ] state change for instance i-488B084F: Staging -> Booting (Pending)
[Wed Nov 2 18:32:23 2011][001660][EUCADEBUG ] doDescribeInstances(): instanceId=i-488B084F publicIp=0.0.0.0 privateIp=172.19.1.36 mac=D0:0D:48:8B:08:4F vlan=11 networkIndex=4
[Wed Nov 2 18:32:25 2011][001660][EUCADEBUG ] state change for instance i-488B084F: Booting -> Running (Extant)
[Wed Nov 2 18:32:29 2011][001660][EUCADEBUG ] doDescribeInstances(): instanceId=i-488B084F publicIp=0.0.0.0 privateIp=172.19.1.36 mac=D0:0D:48:8B:08:4F vlan=11 networkIndex=4
[Wed Nov 2 18:32:30 2011][001660][EUCAINFO ] discovered public IP 10.16.3.99 for instance i-488B084F
[Wed Nov 2 18:32:36 2011][001660][EUCADEBUG ] doDescribeInstances(): instanceId=i-488B084F publicIp=10.16.3.99 privateIp=172.19.1.36 mac=D0:0D:48:8B:08:4F vlan=11 networkIndex=4

When I do euca-get-console-output I see:
waiting for metadata service at [http://169.254.169.254/2009-04-04/meta-data/instance-id](http://169.254.169.254/2009-04-04/meta-data/instance-id)
16:32:29 [ 1/100]: url error [[Errno 111] Connection refused]

Using oneiric image there was an error with add_key.pl but with the above image it looks like the keys are correctly uploaded to the instance...
Anybody who can help me to figure it out?
Thank you in advance

---

