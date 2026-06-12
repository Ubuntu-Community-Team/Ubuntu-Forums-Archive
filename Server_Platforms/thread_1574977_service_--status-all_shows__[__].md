---
title: "service --status-all shows  [ ? ]"
date: 2010-09-15
forum: Server Platforms
---

### Post by vladoportos on 2010-09-15
Hello all

I'm kind of confused, when I use this command it
shows output like this:

root@Destro:~# service --status-all
 [ + ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ - ]  bootlogd
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  cryptdisks
 [ ? ]  cryptdisks-early
 [ ? ]  cryptdisks-enable
 [ ? ]  cryptdisks-udev
.
.
.
.

why the  [ ? ] , for example I know cron is running so why the ?

Any idea ?

Thanks,
Vlad

---

### Post by monismonther on 2010-10-19
Hi Everyone same question here what does the + - and ? mean, the man/info pages do not say anything about them.

Please explain the meaning of the + - and ?

Thanks

Monis

---

### Post by Morbius1 on 2010-10-19
There are two methods of starting and managing services in Ubuntu. The old System-V style init way and upstart.

This command will show you the status of upstart controlled services:
```
sudo initctl list
```You'll get an output that looks something like this:
> .... 
network-manager start/running, process 965
module-init-tools stop/waiting
cron start/running, process 1363
gdm start/running, process 961
.....


---

### Post by mainerror on 2010-10-19
But still where could one find the legend for the service --status-all output?

---

### Post by Morbius1 on 2010-10-19
"+" started
"-" stopped
"?"  unknown

---

### Post by monismonther on 2010-10-19
Hi Morbius,

Thanks for the great responses, I wonder if you have a link that details these options and how these commands function. for example where was this documented ( I seek details).

I am happy with the info you have and it sure does answer my question in full but only for my own knowlwdge base I would appreciate if you have some extra info to share

Thanks

Monis

---

### Post by Morbius1 on 2010-10-19
It's all in the man pages for "service" and "initctl".

[I]Actually I worked backwards because I was trying to debug a samba printing issue. While I don't know this to be an absolute fact, it certainly looks like an incomplete implementation of the "service" command. The same thing happens in the real world when you have two development sub-teams working on a software project and they don't talk to each other. 

Let's take the samba printing issue:

If you do a service --status-all you will notice that cups is started "[+] cups". That's because cups is controlled by the old method.

If you do a initctl list you will notice that cups isn't listed but samba ( smbd ) is listed. That's because upstart doesn't control cups but it does control smbd.

Funny things can happen because of all this. During the boot process samba ( smbd - and controlled by upstart ) may start before cups. If you share printers using samba then the remote user doesn't see any printers on the network because cups is supposed to start first and pass the printer list to samba. Two teams that never once had a joint design meeting. ;)


[/I]

---

### Post by monismonther on 2010-10-19
Thanks again

---

### Post by mainerror on 2010-10-19
Thanks.

---

