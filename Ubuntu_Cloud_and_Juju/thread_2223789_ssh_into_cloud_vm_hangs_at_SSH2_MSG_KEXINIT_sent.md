---
title: "ssh into cloud vm hangs at SSH2_MSG_KEXINIT sent"
date: 2014-05-12
forum: Ubuntu Cloud and Juju
---

### Post by icksa on 2014-05-12
Hello:

I have having trouble SSHing into my ubuntu 14.04 vm which I launched on my openstack ice house cloud. I've successfully launched and sshed into a 12.04 image so I fairly sure the issue is not with how the cloud is set up. I can also ping the vm. SSH hangs at the SSH2_MSG_KEXINIT step:

```

~~> ssh -vvv ubuntu@192.168.100.11
OpenSSH_6.2p2, OSSLShim 0.9.8r 8 Dec 2011
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.100.11 [192.168.100.11] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/Users/milad/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /Users/milad/.ssh/id_rsa type 1
debug1: identity file /Users/milad/.ssh/id_rsa-cert type -1
debug1: identity file /Users/milad/.ssh/id_dsa type -1
debug1: identity file /Users/milad/.ssh/id_dsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6p1 Ubuntu-2ubuntu1
debug1: match: OpenSSH_6.6p1 Ubuntu-2ubuntu1 pat OpenSSH*
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.100.11" from file "/Users/milad/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /Users/milad/.ssh/known_hosts:15
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Operation timed out

```

The time out happens about 20 seconds after the SSH2_MSG_KEXINIT is printed. I obtained the 14.04 image from [http://cloud-images.ubuntu.com/](http://cloud-images.ubuntu.com/) so I don't think there is anything unusual about the image.

Any suggestions would be greatly appreciated.

---

### Post by jason-bishop on 2014-05-16
I have exactly the same problem.  thank you for the hint that precise is working.  I found that i can ssh into the precise and then ssh to trusty using the private net address and it logged me right in.  so the image itself and the ssh config are sane.  what i also discovered is that if i run a command which generates any amount of output (dmesg, ps auxw) it hangs the connection and then times out.  it would be consistent with a mtu mismatch problem but i haven't found anything wrong yet.

hints welcome

edit: i got it now.  i was using gre tunnels and they add (i think) up to 80 bytes to the packet.  since mtu on guest os was 1500 whenever you get a packet more than 1420 bytes in length boom.  (gre does not do fragmentation it appears).  so set your guest os mtu to 1420 or lower or run big frames everywhere else.

jason

---

