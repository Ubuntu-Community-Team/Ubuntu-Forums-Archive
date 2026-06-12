---
title: "What's the best Firewall? and a serious threat question."
date: 2010-06-21
forum: Security
---

### Post by quirkification on 2010-06-21
So I have a security question and a question about firewalls.

1. I use Firestarter which apparently isn't a proper firewall, but I still get some issues blocked. And one is a recurring serious threat. A UDP from Samba trying to access a IP on my network...What could this be? A hack? We believe our network is being run up and that's why it gets so loaded so often.

2. What do you use as your firewall, how good is it and how easy to set-up?

Thanks
](*,)

---

### Post by cariboo on 2010-06-21
> **quirkification said:**
> So I have a security question and a question about firewalls.

1. I use Firestarter which apparently isn't a proper firewall, but I still get some issues blocked. And one is a recurring serious threat. A UDP from Samba trying to access a IP on my network...What could this be? A hack? We believe our network is being run up and that's why it gets so loaded so often.

Are you running samba on your system?

> 2. What do you use as your firewall, how good is it and how easy to set-up?

Thanks
](*,)

I use a Linksys router, for my home/businees network. I use ufw to turn on the default iptables rules when I'm out and about with my netbook.

---

### Post by linuxyogi on 2010-06-21
> **quirkification said:**
> I use Firestarter which apparently isn't a proper firewall
](*,)

What makes you say that ?

You can visit my thread (about ubuntu security) -------

[http://ubuntuforums.org/showthread.php?t=1409849]("http://ubuntuforums.org/showthread.php?t=1409849")

Try to read the entire thread.  

):P

---

### Post by Rubi1200 on 2010-06-21
From the security sticky by bodhi.zazen:

> A source of confusion sometimes occurs when users feel the need to be running firestarter/Guarddog for their firewall to be active. **This is untrue !** Keep in mind that these applications are not firewalls, but rather configuration tools for ip tables. These applications should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Scroll down and read the section on firewalls.

---

### Post by wojox on 2010-06-21
I also run a Linksys router (Cisco) it's great blocks everything on my server.

---

### Post by yeleek on 2010-06-21
> **quirkification said:**
> So I have a security question and a question about firewalls.

1. I use Firestarter which apparently isn't a proper firewall, but I still get some issues blocked. And one is a recurring serious threat. A UDP from Samba trying to access a IP on my network...What could this be? A hack? We believe our network is being run up and that's why it gets so loaded so often.

2. What do you use as your firewall, how good is it and how easy to set-up?

Thanks
](*,)

1) Whats the port/source?  Sure its not just the windows clients broadcasting?  (master browser, SMB, etc etc).  

2) IPTABLES is built into the kernel,  and Firestarter is just a newbie gui for it - it is a proper firewall, just doesn't have the raft of configurations options that you do if you do it yourself via terminal.  
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

'We believe our network is being run up and that's why it gets so loaded so often' - Could be one of many things, not all malicious, could be that the network is too 'chatty' and that it could do with separation into different broadcast domains (i.e. imagine a room with 20 people all talking at one, no-one can hear anyone else, split them into 4 different rooms though, and then you can hear the people in that room speak far easier).

---

### Post by quirkification on 2010-06-21
> **cariboo907 said:**
> Are you running samba on your system?
Yes, But I installed it in an attempt to set up my printer and have not used it otherwise, I could probably uninstall it.

> **linuxyogi said:**
> What makes you say that ?
):P
I was on another thread where I was told that firestarter is not a true firewall. As well as, Rubi2100, seconding this motion.

> **yeleek said:**
> 1) Whats the port/source?  Sure its not just the windows clients broadcasting?  (master browser, SMB, etc etc).  

port 137, source 192.168.1.3, destination 192.168.1.2, tos 0x00, service samba


1. Hey I said it was a question, I didn't say it was not a dumb one :lolflag:. I am still learning more about firewalls, I was a mildly intelligent windows user, hoping to be a decent Linux user.

2. I have to go to class, I will read up on these forums when I get back, Firewalls are technical stuff. Firestarter is good for me because I am still a newbie, but I want to know what to do to have a good security system on my laptop.

Thanks for the help thus far.

---

### Post by yeleek on 2010-06-21
137 is part of Netbios, 445 being the other for SMB

[http://support.microsoft.com/kb/832017](http://support.microsoft.com/kb/832017)
[http://samba.anu.edu.au/cifs/docs/what-is-smb.html](http://samba.anu.edu.au/cifs/docs/what-is-smb.html)

These are not necessarily indicative of a hack, malicious use etc, but are required ports by wintel systems for domain authentication, file transfer, master browser, blah blah blah.

Have to be careful with the firewall logs for example, I'm on a closed network with one other machine at the moment.  Yet my iptables.log lists lots of 137 connection attempts, its just the way windows does things (and yes the windows machine has no access to the internet).

At the risk of going off subject, if network resource usage is really a concern suggest you do some performance testing, try to establish a baseline and see if the issues you face are load related.

Meant nothing by previous comments, just that Firestarter is basic...

---

### Post by Primus1 on 2010-06-21
One of the confusing things for a new user like me is this - some say Firestarter for example IS a firewall and others say it IS NOT a firewall but a front end to make iptables easier to configure. Discussions seem to go on and no definitive answer to end all doubt. Just an observation, not a criticism of anyone here.

---

### Post by yeleek on 2010-06-21
[http://articles.techrepublic.com.com/5100-10878_11-5708627.html](http://articles.techrepublic.com.com/5100-10878_11-5708627.html)

'When you're working with a Linux firewall, manipulating iptables can be daunting. Even comprehensive packages like Shorewall require a fair amount of knowledge and time to configure. Using a GUI tool with a walk-through wizard, such as Firestarter, is typically much easier than fiddling with text-based configuration files and shell scripts. However, you should note that Firestarter still identifies iptables as a pre-requisite, because it simply configures iptables rules for your firewall.'

Which I guess is why some people say Firestarter isn't a proper firewall, its a front end to a firewall which is already built into Ubuntu.  Also gets confusing because people presume when they reboot and the Firestarter icon isn't in their system tray, then Firestarter must not be running (this is incorrect).  TBH if Firestarter does what you need, then use it, don't let others convince you its not fit for purpose etc.  If however you want more configuration possibilities then look at IPtables directly.

---

### Post by Primus1 on 2010-06-21
> **yeleek said:**
> [http://articles.techrepublic.com.com/5100-10878_11-5708627.html](http://articles.techrepublic.com.com/5100-10878_11-5708627.html)

  Also gets confusing because people presume when they reboot and the Firestarter icon isn't in their system tray, then Firestarter must not be running (this is incorrect). 
 
Ha! been there, I panicked, I get it now, thanks for the answer.

---

### Post by quirkification on 2010-06-21
> **linuxyogi said:**
> What makes you say that ?

You can visit my thread (about ubuntu security) -------

[http://ubuntuforums.org/showthread.php?t=1409849]("http://ubuntuforums.org/showthread.php?t=1409849")

Try to read the entire thread.  

):P

hahaha... an 8 page thread with 3 links on page one...This could take a while.:popcorn:

---

### Post by d3v1150m471c on 2010-06-21
Firestarter is only a graphical front-end to iptables and a decent traffic monitor. How you set it up will ultimately determine its effectiveness. Samba is a file sharing system. Do you use samba? Since you asked, I use firestarter to edit my firewall/iptables which is currently very secure.

---

### Post by quirkification on 2010-06-23
[SIZE="4"]**[code for activating default firewall to max levels]("http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/")**[/SIZE]

found that on one of the links and followed the basics to block out everything; because, I am not running a server.

---

### Post by bodhi.zazen on 2010-06-24
> **quirkification said:**
> [SIZE=4]**[code for activating default firewall to max levels]("http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/")**[/SIZE]

found that on one of the links and followed the basics to block out everything; because, I am not running a server.

Nice link =)

---

### Post by quirkification on 2010-06-24
> **bodhi.zazen said:**
> Nice link =)

nice post :lol:

---

