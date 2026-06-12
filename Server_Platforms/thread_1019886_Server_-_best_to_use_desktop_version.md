---
title: "Server - best to use desktop version?"
date: 2008-12-23
forum: Server Platforms
---

### Post by neomaximus2k on 2008-12-23
Hey guys, I have been running Ubuntu 8.10 Server edition for a few days now, and dispite following tutorials here and having a basic understanding of *nix systems I have hit nothing but problems.

My question is this, would it be more feasable to install the desktop version of ubuntu 8.10?  I am trying to develop a cost effective server, I have the server pricing to under £200 for a quad core 2.1Ghz system with 4Gb of ram and now just need to get ubuntu doing what I need it to do (of course using the GUI would be more helpful for the business user as well)

I would need the server to do the following
[LIST]
[*]File Server for Windows based machines (2000, xp, vista)
[*]Domain Server to centralise user accounts
[*]Mail Server (it would either dial in to the mail server on the website and fetch the emails or MX records for the domain would be altered to point to the IP of the server)
[*]VPN To allow users to dial-in while they are out of the office
[*]Exchange Server to allow synchronisation between outlook, other users calendar entries and also mobile phones
[*]Print server to share printers attached via USB and networked printers
[*]LAMP Server (this isn't an issue as i'm a web developer and have setup multiple linux systems with apache, php, ruby and mysql)
[*]Some sort of Virtual Connection that would allow me to dial-in to the server and then take control of it as if I was there (I know I could use SSH for this and SSH would be installed and setup but I would then need to connect to other machines on the network and take control of them as well)
[*]FTP Server (PROFTPD)
[*]Some sort of SPAM system for the email side of things
[*]Anti Virus, as the machines connected to it would mainly be windows machines it would be a good idea to offer them some sort of protection
[/LIST]

I know there is a LOT of options there but despite setting up the LAMP server perfectly, the VPN using OpenVPN failed misserably during the make and the SAMBA server is on but doesn't show the files, if i re-install it shows the fiels untill reboot (the files are still accessable)

So my basic question is would it be best to install the desktop version instead of the server version, at least I would have a better chance I think.

What do you recommend I use and what software would you recommend for each of the points above.

---

### Post by pytheas22 on 2008-12-23
Sure, you can install the desktop edition if you're more comfortable working through a GUI when possible.  The desktop edition, unlike the server, doesn't come with most of the stuff you need installed by default, but you can easily install it using the package manager (System>Administration>Synaptic Package Manager if you want a GUI, or 'apt-get' on the command-line).

It sounds like you may not be familiar with the package manager in Ubuntu, since you refer above to compiling openVPN from source.  You should not need to compile anything from source in order to install the applications you list.  They can all be installed through Synaptic or apt-get.  For example, to install openVPN, you could just type:
```

sudo apt-get install openvpn
```

and it will download and install everything for you.

I can't recommend individual applications for all of the tasks you list, but they should all be available, with the possible exception of the Exchange and Domain servers.  I'm not sure if these are available on Linux.  I think there might be some third-party implementations available, but hopefully someone else will know more about them.

---

### Post by neomaximus2k on 2008-12-23
I am aware of the apt-get method of ubuntu, i'm more used to the yum version I have with linpus on my acer aspire one byt have used apt-get a lot, the apt-get version didn't do the configuring it was meant to so I downloaded directly from openVPN and followed their instructions only to get compile errors galore as the required libraries were not available in the server edition or some crap like that.

---

### Post by windependence on 2008-12-24
> **neomaximus2k said:**
> Hey guys, I have been running Ubuntu 8.10 Server edition for a few days now, and dispite following tutorials here and having a basic understanding of *nix systems I have hit nothing but problems.

My question is this, would it be more feasable to install the desktop version of ubuntu 8.10?  I am trying to develop a cost effective server, I have the server pricing to under £200 for a quad core 2.1Ghz system with 4Gb of ram and now just need to get ubuntu doing what I need it to do (of course using the GUI would be more helpful for the business user as well)

I would need the server to do the following
[LIST]
[*]File Server for Windows based machines (2000, xp, vista)
[/LIST]
There would be no reason for the business user to touch this if you set up SAMBA. the configuration files are simple text files. Edit with nano over ssh, much easier than vi for a new user
> **neomaximus2k said:**
> 

[LIST]
[*]Domain Server to centralise user accounts
[/LIST]
Domain controller is certainly possible but probably not necessary unless you have lots of users, otherwise just set up a simple workgroup
> **neomaximus2k said:**
> 

[LIST]
[*]Mail Server (it would either dial in to the mail server on the website and fetch the emails or MX records for the domain would be altered to point to the IP of the server)
[/LIST]
You can use the Zimbra open source edition or use Citadel. Spam control, anti-virus, and exchange integration are built in, and both are simple to install. This will address several of your other concerns down the list, however, your e-mail server really should be on a separate machine.
> **neomaximus2k said:**
> 

[LIST]
[*]VPN To allow users to dial-in while they are out of the office
[/LIST]
OpenVPN installed from the Ubuntu package OR you could build a simple gateway box from a very old PC using pfsense. This could take care of your firewall/VPN/Router needs all in one place.

> **neomaximus2k said:**
> 

[LIST]
[*]Exchange Server to allow synchronisation between outlook, other users calendar entries and also mobile phones
[/LIST]
Zimbra or Citadel as answered above.

> **neomaximus2k said:**
> 

[LIST]
[*]Print server to share printers attached via USB and networked printers
[/LIST]
This is usually installed by default and should work out of the box - CUPS
> **neomaximus2k said:**
> 

[LIST]
[*]LAMP Server (this isn't an issue as i'm a web developer and have setup multiple linux systems with apache, php, ruby and mysql)
[/LIST]
Again, this should probably be on a separate box but you COULD run it on the same box if your traffic is light.

> **neomaximus2k said:**
> 

[LIST]
[*]Some sort of Virtual Connection that would allow me to dial-in to the server and then take control of it as if I was there (I know I could use SSH for this and SSH would be installed and setup but I would then need to connect to other machines on the network and take control of them as well)
[/LIST]
You are pretty green on this. :) You can connect to the box and then go anywhere you want from that box simply by sshing to another box from the first one. (if that makes sense). Remote control software is usually not too secure.
> **neomaximus2k said:**
> 


[LIST]
[*]FTP Server (PROFTPD)
[/LIST]
Again, you probably don't need this. If ssh is installed you could use WinSCP to transfer your web files securely, or you could use sftp.

> **neomaximus2k said:**
> 

[LIST]
[*]Some sort of SPAM system for the email side of things
[/LIST]
This could be done at the mail server with Zimbra or Citadel, or at the gateway box I suggested.

> **neomaximus2k said:**
> 

[LIST]
[*]Anti Virus, as the machines connected to it would mainly be windows machines it would be a good idea to offer them some sort of protection
[/LIST]
Same as above, built in to the mail server or use ClamAV at the gateway box.

> **neomaximus2k said:**
> I know there is a LOT of options there but despite setting up the LAMP server perfectly, the VPN using OpenVPN failed misserably during the make and the SAMBA server is on but doesn't show the files, if i re-install it shows the fiels untill reboot (the files are still accessable)

Re-installing seems to be the "in" thing with Windows users. It is rarely necessary on a Linux box and usually will not fix the problem. In fact, it can make the problem worse. You need to use the Ubuntu package manager to install and uninstall packages.

> **neomaximus2k said:**
>  So my basic question is would it be best to install the desktop version instead of the server version, at least I would have a better chance I think.

What do you recommend I use and what software would you recommend for each of the points above.

You will likely have the same problem with the desktop version but with a GUI it will be even EASIER for you to mess things up and you will never understand how all this stuff works. A GUI is just a crutch. The CLI is not hard in Linux because almost everything has a well commented text file for configuration. The GUI just obscures what is really happening. I recommended some software above. 

I really think you are trying to do too much on one single box though. Find yourself a few old PCs and jam them full of memory, then use them for specific tasks.

-Tim

---

### Post by neomaximus2k on 2008-12-24
> **windependence said:**
> 
There would be no reason for the business user to touch this if you set up SAMBA. the configuration files are simple text files. Edit with nano over ssh, much easier than vi for a new user

You're correct ont that front but human nature dictates that people will try and mess and its easier talking someone through a GUI than it is command line, have you ever tried talking someone through how to refresh an ip address under windows? does my head in sometimes!!  When I installed SAMBA the first time round it worked fine, set the workgroup to WORKGROUP and all the systems could see it, but then when the server was rebooted it was no longer there for anyone :(


> **windependence said:**
> 
You can use the Zimbra open source edition or use Citadel. Spam control, anti-virus, and exchange integration are built in, and both are simple to install. This will address several of your other concerns down the list, however, your e-mail server really should be on a separate machine.

I agree mail should be on a seperate server however the traffic on the system would be low, it would route the internet traffic through to the modem or in many cases just add-on to the router already setup.

> **windependence said:**
> 
OpenVPN installed from the Ubuntu package OR you could build a simple gateway box from a very old PC using pfsense. This could take care of your firewall/VPN/Router needs all in one place.

I did setup an Internet Gateway machine at an old workplace of mine a few years ago, it managed to control all the internet traffic through two lines (Virgin & BT) and proved a treat but problems did arise with certain software not loking the idea, I never did get that fixed.

> **windependence said:**
> 
Again, this should probably be on a separate box but you COULD run it on the same box if your traffic is light.

In this instance it would only host a custom admin panel for the server whenever I get around to making it (similar to webmin and all that) so really it would only be a development system nothing more

> **windependence said:**
> 
You are pretty green on this. :) You can connect to the box and then go anywhere you want from that box simply by sshing to another box from the first one. (if that makes sense). Remote control software is usually not too secure.

green???? the purpose of this is to allow me to take control of machines on the network for when they are having trouble, I create a lot of Internet Applications and when they call saying its not working it is rather frustrating trying to get out of them what is actually happening, connecting to the machine and seeing for myself what is happening means i can find the fault in a fraction of the time.

> **windependence said:**
> 
Re-installing seems to be the "in" thing with Windows users. It is rarely necessary on a Linux box and usually will not fix the problem. In fact, it can make the problem worse. You need to use the Ubuntu package manager to install and uninstall packages.

I agree, re-installing on windows will overide some problems people get with files that go wondering off (happens all the time) but linux doesn't work like windows thank god!

> **windependence said:**
> 
You will likely have the same problem with the desktop version but with a GUI it will be even EASIER for you to mess things up and you will never understand how all this stuff works. A GUI is just a crutch. The CLI is not hard in Linux because almost everything has a well commented text file for configuration. The GUI just obscures what is really happening. I recommended some software above. 

I really think you are trying to do too much on one single box though. Find yourself a few old PCs and jam them full of memory, then use them for specific tasks.

-Tim

I agree there is soo much being done with one little box but not every box will be doing all these features! (mine will at home ofcourse, oh I missed off transcoding and streaming files to my 360, psp and ps3 lol) 

The funny thing is with the GUI version I would still be using the terminal window LOL I was unsure if it would make it easier or not, but as I found out lastnight changing the IP address via CLI meant the GUI reported the network was "un-mannaged" and then I could SSH in.

I will probably go back to the server version and stick with the CLI (i might install a light gui if i need to) its just a shame that half the things I have gotten working have then died on reboot.

---

### Post by neomaximus2k on 2008-12-24
Well I have a number of servers apps now running, even managed to get SAMBA running perfect with mutliplke file shares, got one tiny issue but have a theory on how to do that.  Not had chance to setup the Zimbra or Citadel software and once again OpenVPN says there are no VPN's defined so I gave up on that for now. (I forgot to explain that the machines connecting to the server via VPN would most likly be windows, so the method of username and password would be the best sollution here)

I have documented my steps and once completed I'll upload it here

Oh and can anybody recommend a decent control panel? eBox isn't supported as it has brocken libraries and webmin is frowned upon as it doesn't follow the guidelines set by ubuntu, I should also be able to setup virtual hosts for apache with it as well

---

### Post by namdung on 2008-12-24
Try Untangle which is one of the best Open Source UTM. 

It can installed in Windows XP, in Ubuntu/Debian or as a standalone Server.
[http://www.untangle.com/](http://www.untangle.com/)

---

### Post by neomaximus2k on 2008-12-24
> **namdung said:**
> Try Untangle which is one of the best Open Source UTM. 

It can installed in Windows XP, in Ubuntu/Debian or as a standalone Server.
[http://www.untangle.com/](http://www.untangle.com/)

I was unable to locate a download off their servers
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package untangle

```
also apt-cache search tang didn't come up with it in the list

---

### Post by windependence on 2008-12-24
You just burn the ISO file and install untangle but it must be installed on a separate box. He is talking about the gateway box. Check it out, it's really a nice product.

I'll post some OpenVPN info for you later on.

-Tim

---

### Post by troyready on 2008-12-24
Not to threadjack, but I wanted to thank you for the Untangle recommendation -- I hadn't heard of them and I really like what they're offering!

In turn, I'd like to nominate Zarafa ([www.zarafa.com](www.zarafa.com)) for consideration in the open-source mailserver space. The feature-set they provide in their open-source version is superior to Zimbra IMHO (i.e., Exchange Activesync, multi-company modes). If you use their non-Free (but free of cost) binary daemon, you also get the ability to connect 3 Outlook clients for no cost.

---

### Post by neomaximus2k on 2008-12-26
> **windependence said:**
> You just burn the ISO file and install untangle but it must be installed on a separate box. He is talking about the gateway box. Check it out, it's really a nice product.

I'll post some OpenVPN info for you later on.

-Tim

ah sadly for me it needs to be on the same box :(

---

