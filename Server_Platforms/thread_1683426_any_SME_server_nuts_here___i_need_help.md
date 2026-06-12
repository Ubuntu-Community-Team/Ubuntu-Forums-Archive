---
title: "any SME server nuts here ???  i need help"
date: 2011-02-07
forum: Server Platforms
---

### Post by jason.b.c on 2011-02-07
wondering how to access my newly installed sme server "server manager" from ubuntu over ethernet (eth0 of ubuntu to eth1 of SME)

[http://wiki.contribs.org/SME_Server:Documentation:FAQ](http://wiki.contribs.org/SME_Server:Documentation:FAQ)

can someone help me out???

---

### Post by arrrghhh on 2011-02-07
That link isn't valid.

However, it seems that SME is based on CentOS:
> SME Server is built on CentOS using the publicly available open source Red Hat Enterprise Linux sources.

So how does Ubuntu fit in here?  Thanks.

FYI, they seem to have a [forum](http://forums.contribs.org/) as well...

---

### Post by CharlesA on 2011-02-07
Valid link: [http://wiki.contribs.org/SME_Server:Documentation](http://wiki.contribs.org/SME_Server:Documentation)

This has nothing to do with Ubuntu, but I'll leave it for now.

EDIT: We'd need more information in any case.

---

### Post by jason.b.c on 2011-02-07
> **arrrghhh said:**
> That link isn't valid.

However, it seems that SME is based on CentOS:


So how does Ubuntu fit in here?  Thanks.

FYI, they seem to have a [forum](http://forums.contribs.org/) as well...

yeah i figured they have a forum , but why join up to another one so i can ask one whole question???

what section is this ??  "server platforms"

i asked (in the title) "any SME server nuts here"

---

### Post by jason.b.c on 2011-02-07
> **CharlesA said:**
> .

EDIT: We'd need more information in any case.

like what??

the machine with sme installed has no outside internet connection , i chose that option in the install...

i'm not sure how to connect to it from my netbook eth port to it's eth port...

---

### Post by CharlesA on 2011-02-07
Use a switch?

I don't know what is installed by default, as I don't use it.

---

### Post by jason.b.c on 2011-02-07
> **CharlesA said:**
> Use a switch?

I don't know what is installed by default, as I don't use it.

a switch?????

you mean a router or something like??

---

### Post by arrrghhh on 2011-02-07
Indeed, you'll need a switch... a router... or a crossover cable.

I'm assuming if you're using SME there'll be more than just one computer connecting to it.  Do you have a LAN?

I still don't see how this applies to Ubuntu in any way shape or form.

I understand this is the server platform section - as in Ubuntu Server.  So if you have questions/issues/etc with **Ubuntu Server** they go here.  We don't really help with CentOS servers, that simply does not belong here friend.

---

### Post by jason.b.c on 2011-02-07
> **arrrghhh said:**
> Indeed, you'll need a switch... a router... or a crossover cable.

i can't just hook straight up as previously specified????? 
> 
I'm assuming if you're using SME there'll be more than just one computer connecting to it.  Do you have a LAN?

two at least.. 

A "Local area network" ??? well that is what i'm trying to do ...

> I still don't see how this applies to Ubuntu in any way shape or form.

well i guess it dosen't , then again - if U.SE came with webmin installed out of the box , i'd be here asking question to that effect.. so......

> I understand this is the server platform section - as in Ubuntu Server.  So if you have questions/issues/etc with **Ubuntu Server** they go here.  **We don't really help with CentOS servers, that simply does not belong here friend.**


why does that matter ??  , i was asking if their was anyone here that could help , as in - someone who uses it..  or something similar..

---

### Post by CharlesA on 2011-02-07
> **jason.b.c said:**
> i can't just hook straight up as previously specified????? 

You can use a crossover cable to connect two machines together without using a switch/router/whatever.

---

### Post by arrrghhh on 2011-02-07
> **jason.b.c said:**
> why does that matter ??  , i was asking if their was anyone here that could help , as in - someone who uses it..  or something similar..

Well, I guess feel free to post whatever you want - but I have a feeling if I have an issue with a particular application, or definitely a different type of Linux, it's best to post in that forum.

Especially when a specific product has a purpose-built forum.

I bet they have an FAQ as well, which answers simple questions - which if I'm not mistaken your question sounds pretty basic to their system, but you haven't really given us any details whatsoever, hence the reason we're making such great jump to conclusions.

If you would either give us more information about what you're doing and what you're not able to do, or better yet post in their forum (would that make more sense?  I know it's only "one post" you say, but you'll get a much MUCH better response there.  Plus, if you have any future questions related to SME you already have an account to ask those questions.)

I'm not trying to push you off, just trying to be logical here.  I find posts about PS3MediaServer are better responded to on their forums, as is the case with Astrisk, etc.

---

### Post by jason.b.c on 2011-02-07
ok , so if we are gonna complain that this isn't a ubuntu question in an ubuntu forum - then let me ask this then ...

if i install ubuntu server , how do i offline install webmin (as in server will have no internet) and all it's depends and connect to the server machine without internet but with ethernet cable???

---

### Post by arrrghhh on 2011-02-07
> **jason.b.c said:**
> ok , so if we are gonna complain that this isn't a ubuntu question in an ubuntu forum - then let me ask this then ...

if i install ubuntu server , how do i offline install webmin (as in server will have no internet) and all it's depends and connect to the server machine without internet but with ethernet cable???

Well webmin isn't in the repos, so this makes it easy.

Download the deb on their site.  If you do not have an installed dependency, you'll have to download the deb on another machine and move it over to the server.

It would really be much, much easier to connect it to the internet, install the package, and then disconnect it from the internet.  But, to each their own... if you like doing things the hard way :p.

---

### Post by jason.b.c on 2011-02-07
> **arrrghhh said:**
> Well webmin isn't in the repos, so this makes it easy.

Download the deb on their site.  If you do not have an installed dependency, you'll have to download the deb on another machine and move it over to the server.

It would really be much, much easier to connect it to the internet, install the package, and then disconnect it from the internet.  But, to each their own... if you like doing things the hard way :p.

well i don't like doing things the hard way , but i can't hook up the internet to the machine that would become the ubuntu server , my laptop has the usb internet gizmo that is a lot like a cell phone transceiver ..., so yeah , no dice there...

---

### Post by jason.b.c on 2011-02-08
bump

---

### Post by arrrghhh on 2011-02-08
> **jason.b.c said:**
> bump

What are you bumping?  I answered your question, are you not sure how to achieve what I described...?

---

### Post by jason.b.c on 2011-02-09
> **arrrghhh said:**
>  are you not sure how to achieve what I described...?

No....

---

### Post by spynappels on 2011-02-10
> **arrrghhh said:**
> Download the deb on their site.  If you do not have an installed dependency, you'll have to download the deb on another machine and move it over to the server.



copy the debs to a memory stick, plug said memory stick into server, copy debs to home directory, sudo dpkg -i deb files, bob's (hopefully) your uncle.

---

### Post by garfonzo on 2011-02-11
This thread was entertaining.

---

### Post by bofh80 on 2011-02-13
hey, i've just been doing this.

This is HOW THIS APPLIES TO UBUNTU.

The ubuntu server is not a 'workgroup server' the corporate ubuntu project appears to be ****** in the wind. 

SME server sets up LDAP SAMBA and a few other things so that you don't have to follow the mile long LDAP setup to begin with on ubuntu. 

So in answer to his question:

[https://servernameORipaddress/server-manager](https://servernameORipaddress/server-manager)

You should have set a static IP during the install for the server. And it's name. So you should know one or the other. And enabled the DHCP server.

If your hardware is recent enough you DO NOT NEED A CROSSOVER CABLE. It will auto detect and hook up. If that does work, you will have your eth0 on ubuntu set to DHCP and it should receieve an address from the server. Check with ifconfig.  

If you log in on the server console as admin / sameasrootpassword  you will get a nice little ncurses front end.

You will want to find the ubuntu client authentication part on the sme wiki to setup samba and domain logon from ubuntu.

So yes, this should be considered by Ubuntu desktops as the default Server instead of ubuntu, for workgroup environments. 

If you know anything else that installs and sets all this up out of the box, please share.

Hope this is helpful to anyone to who hasn't toasted this guy for nothing.:popcorn:

I'm a debian user mainly, but have just been requested to do a project with ubuntu on the desktops. But also in such a fashion that the setup can be easily replicated. Ubuntu, debian, fedora ds, do not meet this requirements. A workgroup server for n00bs, who else uses ubuntu anyway?

---

