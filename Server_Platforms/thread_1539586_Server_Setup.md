---
title: "Server Setup"
date: 2010-07-26
forum: Server Platforms
---

### Post by Thunderbolt1164 on 2010-07-26
Hello from a confused person

I work for a small Co-op that works with People With Disabilities (PWD), which has VERY limited income.
Right  now they are using a Windows Home Network setup that is crashing all  the time, and is not that secure for the Accounting Office.

Since  I have been asked to look after the network (I work for a E-Waste and  Repair shop for the Co-op), I have found it to be inadequate and a  hassle.

I have talked to the Administration team and mentioned Linux to them. They have asked me to look into it.

I have looked into both Fedora and Ubuntu. Though Fedora seems (a little) easier to setup, I found I like Ubuntu better.

Problem 1 is:
I have to setup a network and learn it without shutting down the windows network that is in use

I have been doing some research and trying to setup a network at the shop.

Problem 2 is:
It is behind a D-Link router which is in use by other people. (see attachment)
(I can not shut off router's DHCP without wrecking whole network)




I do have access to a newer DELL Computer (2.9 GHz CPU / 2.5 GB DDR2 / 2-500GB HDs / On-board Lan / 3Com Network Card)

---

### Post by Bachstelze on 2010-07-26
Well, what is the network supposed to do (i.e. which services should it provide)?

---

### Post by arrrghhh on 2010-07-26
> **Bachstelze said:**
> Well, what is the network supposed to do (i.e. which services should it provide)?

+1.

If the Windows server was just providing file/print sharing, there should be no problem going to Linux.  If however it was acting as a domain controller and applying group policy or allowing remote logins... then probably not.

From the sounds of it, that Windows server was just doing some file sharing.  Which a Linux box could replace quite easily.

So let us know what you're replacing!  We need to know what the Windows server was providing :D

---

### Post by drdos2006 on 2010-07-26
I found this HOWTO very informative.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by arrrghhh on 2010-07-26
Huh?  I see you post this as the end-all solution to everyone's responses.  I don't get why... Why can't you try to answer their question or help out at all?  I'm sure that link does have some good info, but plastering it as the be-all, end-all server guide is not a good practice.

Don't get me wrong, it's a good guide... if someone wants a from-scratch how do I kind of guide.  So don't stop answering posts, just tailor them a little for the OP :D

---

### Post by wojox on 2010-07-26
Try this as well [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html")

---

### Post by Thunderbolt1164 on 2010-07-26
Well I was hoping to  use it to run ALL Applications and PXE-Boot the rest with it. (Diskless (Approx. 12 computers))
I would set up different Groups for Administration, Accounting, Reception, and general users

---

### Post by Thunderbolt1164 on 2010-07-26
That maybe why it is always crashing....there is NO server,,,,it has been setup like a home network.

---

### Post by v1ad on 2010-07-26
used both ubuntu & fedora for servers. they are both great. but i don't see any reason that you would have to disconnect the network. all it does is assign dhcp addresses.

---

### Post by arrrghhh on 2010-07-26
> **Thunderbolt1164 said:**
> Well I was hoping to  use it to run ALL Applications and PXE-Boot the rest with it. (Diskless (Approx. 12 computers))
I would set up different Groups for Administration, Accounting, Reception, and general users

Ah, why didn't you say so?  That's not too shabby, and depending on what the clients are running, your server specs look fine for that... However, you may want to bump the ram up either way and I'm not sure if that processor is single core you may have issues.

With that said, the [Ubuntu LTSP wiki](https://help.ubuntu.com/community/UbuntuLTSP) will have all you need.

---

### Post by Thunderbolt1164 on 2010-07-27
arrrghhh

It is a Duo-Core 64 Bit CPU, and I can boost ram up to 4 GB.

v1ad

something is wrong I can get to the Internet using eth1 but can not PXE-BOOT Clients on eth0, but then disconnect eth1 and am able to PXE-BOOT Clients on eth0

---

### Post by BenWuan on 2010-07-27
Drdos2006, thanks for your post! very clear Linux info. Thankyou,Thankyou,Thankyou.

---

### Post by KHS21 on 2010-07-28
> **drdos2006 said:**
> I found this HOWTO very informative.



regards

I had a little read through and it's very good. I will bookmark that to read over later, thanks.

---

### Post by Thunderbolt1164 on 2010-08-31
Well I finally got it to work (some what)

It will allow PXE-Booting

But there still must be some bugs in it,  every once in awhile I will click on an Icon (like Firefox) and it will kick me back to to login screen.

I can work with that, but is very aggravating.

It seemed that Ubuntu 10.04 LTSP was not setting up my Client Network right. I had to go in and change it  from 192.168.0.1 to 192.168.1.1 so I guess that it could setup it's own network.

thanks for all of your help

---

