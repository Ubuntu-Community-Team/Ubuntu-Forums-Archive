---
title: "setting up (passwordless) rsh using rsh-server and rsh-client packages"
date: 2007-05-12
forum: Server Platforms
---

### Post by MadScientistVX on 2007-05-12
I am setting up a cluster, with the master (server) running edgy desktop, and the nodes running edgy server. The programs that are going to be running on the master need to be able to connect to each of the nodes using rsh without a password. I "apt-get"-ed rsh-server on each of the nodes and rsh-client on the master, and added the IP of the master to the /root/.rhosts on the nodes and added pts/0 through pts/10 to /etc/securetty. Seems I'm still missing something because the rsh deamon isn't running on the nodes and therefore not listening for incoming connections, and when I try to rsh or rlogin from the master, I get "connection refused". It seems my first question is: how do I start the rsh daemon?
~
:wq

EDIT (2007.05.12.12.19.EDT):
I also have this in /etc/inetd.conf ```

shell           stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/in.rshd
login           stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/in.rlogind
exec            stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/in.rexecd
```
and the master's IP is listed in /etc/hosts.allow and /etc/hosts.equiv

---

### Post by craigp84 on 2007-05-12
Hi MadScientist,

Given the error, it's possible you've just forgotten to fire up inetd - sudo /etc/init.d/inetd start - on each of the nodes?

You'll probably have heard this a million times by now, but rsh really is depreciated for some fairly good reasons. SSH is a better way to go in 99%+ of cases.

It's also easier to setup IMO. Just setup pubkey authentication, and create the private keys without passwords if you're going to use the connections from cron jobs etc.

---

### Post by gonzalov on 2007-05-12
I definitely concur: ssh is quite easy to setup passwordless and is a lot safer. Sorry this doesn't directly answer the question, but I have a small setup where a Dapper server rsyncs to another Dapper via ssh, on a daily cron job, automatic, no password. Works great.

---

### Post by HiFiJive on 2007-12-28
I too have need for this rshd issue resolved. I have a few machines that are tied down to older versions of solaris that I do not have ssh installed on. They are on a private network and rsh would work just fine for me if it worked on ubuntu. 

Steps I've taken:

installed: apt-get install rsh-server, rsh-redone-server, rsh-client

edited /etc/hosts.allow /etc/hosts.equiv ~/.rhosts 
also tried to re-run inetd with code below. 
```
update-inetd --verbose --enable in.rshd
```
all the same on the remote system. I cannot get this to work.

any further help would be greatly appreciated.

---

### Post by HiFiJive on 2007-12-28
Fixed myself. I noticed netstat was not showing shell. 

make sure your /etc/inetd.conf file has the following

```
shell           stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/in.rshd
login           stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/in.rlogind

```

then I had issues reloading inetd. After I installed inetutils-inetd it all worked well.

```
sudo apt-get install inetutils-inetd

```
restart inetd to re-read /etc/inetd.conf (not sure if this is necessary if you install it after you modified the inetd.conf but just in case)
```

/etc/init.d/inetutils-inetd restart
```

---

