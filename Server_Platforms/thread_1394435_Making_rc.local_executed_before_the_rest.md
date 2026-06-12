---
title: "Making rc.local executed before the rest?"
date: 2010-01-30
forum: Server Platforms
---

### Post by deltatux on 2010-01-30
Hey guys,

I'm trying to figure out how to launch rc.local before services like autofs is being executed during system bootup.

The reason I wanted this is because I needed for my server to pickup a DHCP address from my college's DHCP servers in order to get an IP address. Unfortunately, I couldn't get an IP address any other way and the update-rc script is really confusing to use.

May someone please point me to the right direction?

Many thanks,
deltatux

---

### Post by BkkBonanza on 2010-01-31
Usually DHCP would get started before other network dependent start-up scripts. I don't know why this doesn't work for you. Have you got a dhcp client set to startup? This type of config is very common and I haven't heard of it being a problem for others, generally.

Anyway, if you need to patch up your startup because of some oddity then you can add a new startup script in /etc/init.d/ and then link it into your runlevel with a low-numbered link so it starts before others. You can't just change rc.local to start earlier - well, not without butchering the normal startup scripts.

The startup scripts are numbered to indicate order of startup. On my system dhcp is started at 24, which is pretty early on, well before other web services.

step by step...

create and edit a new script,

/etc/init.d/mylocal

and link it in, (for runlevel 3 typical of servers)

ln -s /etc/init.d/mylocal /etc/rc3.d/S20mylocal

***Note that Ubuntu is now using Upstart. So this "patch" above is hooking into the sysv compatibility scripts. The "better" way to do it now is to create an Upstart config in /etc/init/ - eg. /etc/init/mylocal.conf but to do that you'd have to read up on Upstart configs.

Currently, Upstart handles the init sequence but it runs rcX type scripts for compatibility so either way will work. BTW update-rc.d is just a script to make it easy to manage the links made from rcX.d to init.d. You can do them manually if you like. During boot the sequence is straight forward - the scripts in /etc/rcX.d (where X is your runlevel, eg, /etc/rc3.d) are run in numeric order, prefix S is startup, K is shutdown (kill). Add your script and it will run at whatever stage you set according to script name.

---

