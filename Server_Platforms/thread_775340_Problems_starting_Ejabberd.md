---
title: "Problems starting Ejabberd"
date: 2008-04-30
forum: Server Platforms
---

### Post by linuxpyro on 2008-04-30
I am trying to set up a Jabber server with Ejabberd.  The program installed fine, but I'm having trouble actually getting it to start.  When I do sudo ejabberdctl start, I get this error:

```

RPC failed on the node ejabberd@homer: nodedown

```

Where homer is my server's hostname.  I made sure to set this in the Ejabberd config, in the {hosts, ["homer"]}. line.  That hostname also resolves to my machine's IP address in the /etc/hosts file.

The last time I started it, I found this in the sasl log file in /var/log/ejabberd:

```

=PROGRESS REPORT==== 30-Apr-2008::01:13:44 ===
          supervisor: {local,kernel_safe_sup}
             started: [{pid,<0.74.0>},
                       {name,dets},
                       {mfa,{dets_server,start_link,[]}},
                       {restart_type,permanent},
                       {shutdown,2000},
                       {child_type,worker}]

```

I'm running Ejabberd 1.1.4-4, as well as Erlang 1:11.b.5dfsg-11.  The Ubuntu version is 8.04 Hardy.  I searched around and found people mentioning that there could be a problem with this version of Erlang.  Anyone have any ideas?

---

### Post by icarus75 on 2008-12-26
I've encountered similar error messages from the ejabberd deamon on an identical setup:
ejabberd 1.1.4-4
Erlang 1:11.b.5dfsg-11
Ubuntu 8.04 Hardy

Installing a more recent version of ejabberd did the trick. Just uncomment or add following repositories in /etc/apt/sources.list to allow backports from gutsy to hardy:
```
deb http://be.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://be.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
```

Then install the newest ejabberd version from the repository (currently 2.0.1-2).
```
sudo apt-get update
sudo apt-get install ejabberd

```

Here's a snippet of the output:
```
Preparing to replace ejabberd 1.1.4-4 (using .../ejabberd_2.0.1-2~hardy1_i386.deb) ...
Stopping jabber server: ejabberd already stopped.
Unpacking replacement ejabberd ...
Setting up ejabberd (2.0.1-2~hardy1) ...
Installing new version of config file /etc/default/ejabberd ...
Installing new version of config file /etc/init.d/ejabberd ...
Replacing config file /etc/ejabberd/ejabberd.cfg with new version
Starting jabber server: ejabberd.
```

Alter the cfg file to reflect your setup and restart the ejabberd server:
```
sudo vi /etc/ejabberd/ejabberd.cfg
sudo ejabberdctl restart
```

Don't forget to register the ejabberd admin account. If you still encounter the nodedown error message, try a system reset.

Cheers,
Bart.

---

