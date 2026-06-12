---
title: "Ubuntu 10.04 bullet proof server"
date: 2010-06-18
forum: Server Platforms
---

### Post by rekahsoft on 2010-06-18
Hi all, i currently run a server from home but was looking to significantly increase security. I was looking at using a Mandatory Access Control..either SELinux or AppArmor. Which would you recommend?

I am a computer science student and have no problem doing any amount of reading. I am looking for as close as i can get to military security. I also would like to use this "server" as a workstation. Also in a perfect world i would use virtualization to run my server in a contained sandbox for added security but unforchunently i have a intel core 2 quad Q8200 which does not support virtualization.

I currently have ssh restricted to only using pubilc-private key authentication an encrypted partition for sensitive data and an encrypted swap and boot partition. One question is can/should i encrypt my root partition. What encryption should i use? I was thinking 256 bit AES or maybe some other symmetric algorithm that can do > 256 bit encryption. Also how much overhead will this cause? My main concerns with security are running the server not only as a server but as a local workstation. I also am wondering how installing the nvidia proprietary driver and other proprietary software like adobe flash effects the security of my system? I also would like to setup a secure chat server (jabber or ytalk maybe) and i want to find the best way to do so; though i am looking for a VERY SECURE connection (public-private key > 2048 ). Anyways thanks for reading and your suggestions :)

*EDIT*: another question..how do i force certain specifications for passwords (require minimum length, capitols and lowercase, symbols, numbers, etc...)

---

### Post by rekahsoft on 2010-06-22
Anyone?

---

### Post by amauk on 2010-06-22
this seems like overkill, unless you're trading government secrets to foreign nations :p

MAC control systems are already in Linux
RedHat (and friends) use SELinux (as developed and open-sourced by the American National Security Agency)
SELinux is in the mainline kernel

However, SELinux is often viewed as overly complex and hard to use, so an alternative method of providing MAC control was developed, called AppArmor (meant to be much easier to use)

AppArmor isn't quite as comprehensive as SELinux, instead focussing on a subset of SELinux's functionality for the most common use-cases

Debian (and by extension, Ubuntu) uses AppArmor
and it's on by default

Most server software already have AppArmor profiles written for them (just install the "apparmor-profiles" package in the Ubuntu repos)

But some software may not come with profiles, or you may want to write profiles for custom written software, so what you need to do is read up on the various ways of locking down applications using "AppArmor Profiles"

See here for Novell's AppArmor guides
[http://www.novell.com/documentation/apparmor/?page=/documentation/apparmor/apparmor_user/data/bktitleuser.html](http://www.novell.com/documentation/apparmor/?page=/documentation/apparmor/apparmor_user/data/bktitleuser.html)

If you're interested in SELinux, take a look at RedHat (or Fedora, Centos or other RedHat'esque distro)

---

### Post by clrg on 2010-06-22
Also FYI, longer AES encryption keys do not necessarily mean better security. For example, no one would try to brute-force an SSH connection, one would try to obtain your private key and then attack your passphrase, since that is usually the weakest point.

Generally, expose only those services to your network you really need to, and make sure they're tightly controlled (AppArmor for example). As long as you don't expose voulnerable services, there's nothing to be attacked (except social engineering). For SSH, have a look at denyhosts.

Concerning HDD encryption: This only makes sense if you fear someone will physically steal your machine, otherwise you only decrease performance. If you run it as a server at a secure site (like a data center), don't bother.

---

### Post by rekahsoft on 2010-06-22
I run the server using a ddns from a dd-wrt linksys router...I know that the kind of security is not nessesarry but as a student i am interested in how it works and how to set it up. I am setting up apparmor on my netbook but on my desktop i plan on using selinux for the features that aren't provided in apparmor.

Another note: by default a lot of policies are not in enforece mode when using the default instalation of apparmor. I want a policy for EVERY SINGLE APPLICATION; i would have no quams modifying/writing the policies myself as long as i can find good documentation. The idea of having a apparmor policy for every single application on my netbook is similar to what i plan to do with my workstation/server and selinux. Though i would like to use some more of the advanced features of selinux. Regards :)

As an administrator how can i enforce passwords that meet certain specifications?

---

### Post by clrg on 2010-06-22
Have a look at /etc/pam.d/common-password

---

### Post by metalf8801 on 2010-06-22
> **rekahsoft said:**
> Hi all, i currently run a server from home but was looking to significantly increase security. I was looking at using a Mandatory Access Control..either SELinux or AppArmor. Which would you recommend?

I am a computer science student and have no problem doing any amount of reading. I am looking for as close as i can get to military security. I also would like to use this "server" as a workstation. Also in a perfect world i would use virtualization to run my server in a contained sandbox for added security but unforchunently i have a intel core 2 quad Q8200 which does not support virtualization.

I currently have ssh restricted to only using pubilc-private key authentication an encrypted partition for sensitive data and an encrypted swap and boot partition. One question is can/should i encrypt my root partition. What encryption should i use? I was thinking 256 bit AES or maybe some other symmetric algorithm that can do > 256 bit encryption. Also how much overhead will this cause? My main concerns with security are running the server not only as a server but as a local workstation. I also am wondering how installing the nvidia proprietary driver and other proprietary software like adobe flash effects the security of my system? I also would like to setup a secure chat server (jabber or ytalk maybe) and i want to find the best way to do so; though i am looking for a VERY SECURE connection (public-private key > 2048 ). Anyways thanks for reading and your suggestions :)

*EDIT*: another question..how do i force certain specifications for passwords (require minimum length, capitols and lowercase, symbols, numbers, etc...)

Sounds like a great idea please document your work and post here or better yet on the Ubuntu Wiki.  
what are you using your server for? Is it a web server, a file server, or something else? 

Have you considered running the server inside Virtualbox so the server your using doesn't have a gui and other unneeded programs? You can use Virtualbox even if you don't have hardware supported visualization. 

good luck 
Dan

---

### Post by rekahsoft on 2010-07-02
> **metalf8801 said:**
> Sounds like a great idea please document your work and post here or better yet on the Ubuntu Wiki.  
what are you using your server for? Is it a web server, a file server, or something else? 

Have you considered running the server inside Virtualbox so the server your using doesn't have a gui and other unneeded programs? You can use Virtualbox even if you don't have hardware supported visualization. 

good luck 
Dan

I am using it as a file server, an email server, dc++ hub (internal only). As for running a very stripped down linux install in virtualbox i worry about the performance issues. How much do you think service would be affected if i ran the server within virtualbox with no hardware supported virtualization?

> **clrg said:**
> Also FYI, longer AES encryption keys do not necessarily mean better security. For example, no one would try to brute-force an SSH connection, one would try to obtain your private key and then attack your passphrase, since that is usually the weakest point.

Generally, expose only those services to your network you really need to, and make sure they're tightly controlled (AppArmor for example). As long as you don't expose voulnerable services, there's nothing to be attacked (except social engineering). For SSH, have a look at denyhosts.

Concerning HDD encryption: This only makes sense if you fear someone will physically steal your machine, otherwise you only decrease performance. If you run it as a server at a secure site (like a data center), don't bother.

great advice clrg...i do intend on enforcing password restrictions. as for HDD encryption, i run the server from home so i wouldn't mind encrypting it..i do worry about loosing data due to crashes though. i only plan on encrypting data that i find needs to be protected. my home folder for starters...but i have a 2TB media RAID that i will symbolically link to that won't be encrypted (i don't care if someone takes a browse through my media lol). Anyways i will keep everyone updated..i have been reading about PAM for ensuring password security. the linuxjournal has a great article on PAM.

---

