---
title: "hosts.allow and hosts.deny questions - how to restart without rebooting?"
date: 2011-01-17
forum: Security
---

### Post by NuxIT on 2011-01-17
Hi, I'm trying to lock down my new xubuntu 10.10 load using firestarter firewall and hosts.allow and hosts.deny. I basically added sshd to be allowed from specific host systems which seems to work. Also, in order to allow xrdp do I just add xrdp to the hosts.allow as well? Still working out kinks. 

However, I have to reboot everytime I add any entries to these files before they become active. From what I recall I never had to do that with any of my other linux loads. Does this have something to do with tcpwrappers or something in ubuntu? 

Also, does anyone know how to add an execute or run command somewhere that's easy to access? The only place I've found this is after opening task mgr which seems kind of silly. Thx

---

### Post by bodhi.zazen on 2011-01-17
> **NuxIT said:**
> Hi, I'm trying to lock down my new xubuntu 10.10 load using firestarter firewall and hosts.allow and hosts.deny. I basically added sshd to be allowed from specific host systems which seems to work. Also, in order to allow xrdp do I just add xrdp to the hosts.allow as well? Still working out kinks. 

However, I have to reboot everytime I add any entries to these files before they become active. From what I recall I never had to do that with any of my other linux loads. Does this have something to do with tcpwrappers or something in ubuntu? 

Also, does anyone know how to add an execute or run command somewhere that's easy to access? The only place I've found this is after opening task mgr which seems kind of silly. Thx

It appears you are new to Xubuntu and I would suggest you almost certainly do NOT need to do anything to harden your installation.

I can not tell what you are questioning, although I have some comments / observations.

First, start by reading the security sticky.

Second, firestarter is no longer maintained and you shoud learn ufw or gufw.

Third, hosts.allow hosts.deny take effect immediately, without reboting.

---

### Post by The Cog on 2011-01-18
> Also, does anyone know how to add an execute or run command somewhere that's easy to access? The only place I've found this is after opening task mgr which seems kind of silly. ThxAlt-F2 gets you a little box to type in the command.

---

### Post by Tipo on 2011-01-18
> **NuxIT said:**
> 
However, I have to reboot everytime I add any entries to these files before they become active. From what I recall I never had to do that with any of my other linux loads. Does this have something to do with tcpwrappers or something in ubuntu? 


Have you tried just restarting the sshd service?

```
$ service sshd restart
```

---

### Post by NuxIT on 2011-01-19
> **bodhi.zazen said:**
> It appears you are new to Xubuntu and I would suggest you almost certainly do NOT need to do anything to harden your installation.

I can not tell what you are questioning, although I have some comments / observations.

First, start by reading the security sticky.

Second, firestarter is no longer maintained and you shoud learn ufw or gufw.

Third, hosts.allow hosts.deny take effect immediately, without reboting.

Thanks for the response. I'll read the security faq. I am new to x-ubuntu but I'd consider myself seasoned in linux. I used to run ubuntu on my laptop from 7.02-8.02 a few years back. I'm no veteran but I am pretty familiar with getting around. 

At first, I thought the hosts.allow changes I was making didn't become active until after a reboot. However, they seem to be active right away now so not sure what happened probably just my mistake. 

I'll look into ufw and gufw but firestarter seems to be doing what I need it to do. It's a simple and effective firewall. But if it's not maintained I guess I should check out the other ones. 

The Cog, thanks for that helpful tip. It works locally but doesn't seem to work over remote xrdp. Still tooling around but like how this runs on my pIII 600 w/ 528MB or RAM.

---

### Post by NuxIT on 2011-01-19
> **Tipo said:**
> Have you tried just restarting the sshd service?

```
$ service sshd restart
```

Hi, I didn't see your response. Yeah, I think this might of had something to do with it because sshd was not installed by default. After installing it seemed like the hosts.allow files would take affect after restarting sshd. Thanks.

Also, I was kind of surprise my load didn't have any firewall installed. It seemed like it needed some securing but that's just me.

---

