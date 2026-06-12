---
title: "Problems ssh into OpenVZ Ubuntu VE"
date: 2007-11-19
forum: Virtualisation
---

### Post by edmnc on 2007-11-19
> 
FYI: The "ubuntu-7.10-i386-minimal.tar.gz" in Community submitted templates (size = 37 Mb) was submitted by me 


Aha! Found you :)

Now I have a problem with this template - I installed ubuntu-7.10-server, then installed openvz  2.6.18 kernel from [http://debian.systs.org/](http://debian.systs.org/) and then created VE from your ubuntu-7.10 template. Everything seems to work OK except that I can't login to VE using ssh:

```

xxxx@ubuntu:~/.ssh$ ssh 192.168.1.151
xxxx@192.168.1.151's password: 
Read from remote host 192.168.1.151: Connection reset by peer
Connection to 192.168.1.151 closed.

```

I can log into VE from the host using vzctl. Looking at the logfiles this seems to be the problem:

```

/var/log/auth.log:Nov 19 12:20:36 www1 sshd[10142]: fatal: 
ssh_selinux_getctxbyname: ssh_selinux_getctxbyname: 
security_getenforce() failed

```

Unfortunately I dont know what it means .... Any ideas? Ive searched through these forums, openvz forums and google, nothing seems to be quite relevant to this problem/setup ...

---

### Post by bodhi.zazen on 2007-11-19
I moved you post for higher visibility.

Three suggestions :

1. Did you set a root password on the VE ?

vzctl exec <VE#> passwd

2. Run ssh --v 192.168.1.151

See if a more verbose output helps.

3. You may want to post on the OpenVZ forums.

---

### Post by edmnc on 2007-11-19
Thanks for the reply and sorry for messing up your tutorial post.

About the suggestions:

1. No, but I created a new user with a password

2. I tried that, but nothing meaningfull shows up:

```

debug1: Next authentication method: password
test@192.168.1.162's password: 
debug3: packet_send2: adding 64 (len 53 padlen 11 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t3 r-1 i0/0 o0/0 fd 4/5 cfd -1)

debug3: channel 0: close_fds r 4 w 5 e 6 c -1
Read from remote host 192.168.1.162: Connection reset by peer
Connection to 192.168.1.162 closed.

```

3. I probably will do that, but the problem really seems very specific to this template/ubuntu. If I create my own template with debootsrap I get a completely different set of problems (I think they are related to upstart) but until they kick in (when pretty much nothing works anymore) ssh works fine

---

### Post by bodhi.zazen on 2007-11-19
> **edmnc said:**
> Thanks for the reply and sorry for messing up your tutorial post.

LOL, no nothing like that at all, as you can see though I am still adding sections. I penciled them in, but i doubt folks trying to offer assistance will look in my how-to thread.

> About the suggestions:

1. No, but I created a new user with a password

2. I tried that, but nothing meaningfull shows up:

```

debug1: Next authentication method: password
test@192.168.1.162's password: 
debug3: packet_send2: adding 64 (len 53 padlen 11 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t3 r-1 i0/0 o0/0 fd 4/5 cfd -1)

debug3: channel 0: close_fds r 4 w 5 e 6 c -1
Read from remote host 192.168.1.162: Connection reset by peer
Connection to 192.168.1.162 closed.

```

3. I probably will do that, but the problem really seems very specific to this template/ubuntu. If I create my own template with debootsrap I get a completely different set of problems (I think they are related to upstart) but until they kick in (when pretty much nothing works anymore) ssh works fine

OK, I have not had any problem. I did a search and found some information referring to SELinux ???

What is your primary (Host) OS ?

For your Ubuntu guest, yes upstart is a problem.

I will post on my how-to how to solve this, but it is easy

Install sysvinit```
sudo apt-get install sysvinit
```

This will remove upstart and apparmour and the system should be working better ...

Last thought for now, have you changed the default /etc/ssh/sshd_conf ? If so, try returning to the defaults.

If your machine is small, and you are willing, I would look at it if you send it to me.

FYI I have an Ubuntu server template on a Centos 5 host with no problems.

---

