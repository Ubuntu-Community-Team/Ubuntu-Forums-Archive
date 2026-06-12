---
title: "Samba and Windows 7"
date: 2011-01-07
forum: Server Platforms
---

### Post by ally_uk on 2011-01-07
Hi guys I want to setup a file server using Ubuntu, The first thing I want to get off the ground is just simple file shares, is Windows 7 still having problems with Samba or has this been fixed?

Secondly does anyone have a plain noob freindly guide on how to setup and get Samba off the ground, I want something very easy to understand, don't want to be trawling through man pages for decades.

Many Thanks

---

### Post by James78 on 2011-01-07
I would imagine this page will have more than enough information to help you get started. ;)
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by aceofspades686 on 2011-01-07
I run a home network with 2 Windows 7 machines, 2 Windows XP Machines, 2 Ubuntu Desktop machines, and an Ubuntu Server running Samba, I haven't noticed any issues with any of them seeing the Samba shares.

---

### Post by elico on 2011-01-07
there is a major thing with windows 7 and samba 3.* for a long time.
the problem is in windows 7 and not the samba.
you need to first remove "windows live sign in" components and also to change the sharing to simple file sharing and not the homegroup else you wont be able to access the shares on the samba machine and from the samba machine to windows 7 machine.

worked for me in like a sec.

---

### Post by ally_uk on 2011-01-07
How did you guys learn the art of Linux? I come from a windows background myself, I am pretty comfty at using the cli updating packages etc, but want to get my feet wet and actually setup a linux server, the ideal goal is to get both Linux and Windows 7 to get along with each other.

So how did you guys learn the art of setting up servers? did you spend ages running around in circles reading man pages? and out of date guides on the internet? 

seems like a real pain to try and make a transition from Windows to linux, Someone needs to write a clear and concise noob freindly guide on how to get stuff done.

Can someone show me a example of a Samba config that will work with Windows 7, the guy earlier posted a link to the ubuntu main samba resource but isn't that like out of date? Swat is ancient right?

Thanks

---

### Post by kevinthecomputerguy on 2011-01-07
You mean like this?
[http://woodel.com](http://woodel.com)
 
here is my samba conf, no win 7 problems. Disabling win7 home groups is great advice
 
```
#####
#blah blah blah
#======================= Global Settings =======================
[global]
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 obey pam restrictions = yes
 show add printer wizard = no
 passwd program = /usr/bin/passwd %u
 allow hosts = 127.0.0.1 192.168.2.0/24
 dns proxy = no
 netbios name = deb64server1
 delete readonly = yes
 writeable = yes
 workgroup = KHOME
 os level = 20
 socket address = 192.168.2.1
 security = user
 max connections = 100
 disable spoolss = yes
 max log size = 1000
 directory mode = 700
 log file = /var/log/samba/log.%m
 load printers = no
 socket options = TCP_NODELAY
 sync always = yes
 interfaces = eth1
 encrypt passwords = true
 passdb backend = tdbsam
 server string = %h server
 wide links = no
 unix password sync = yes
 syslog = 0
 create mode = 700
 panic action = /usr/share/samba/panic-action %d
 bind interfaces only = yes
 pam password change = yes
#======================= Share Definitions =======================
[Media_Not_Raided]
 read list = mcenter,public
 path = /mymounts/sata4n/high_performance_media
 write list = kelwood,melwood
 only user = yes
 comment = NOT BACKED UP! NOT RAIDED!
 create mode = 760
 user = @shareusersourhouse
 directory mode = 770

[Tech_Not_Raided]
 path = /mymounts/sata4n/tech
 only user = yes
 write list = kelwood,melwood,mcenter,public
 comment = NOT BACKED UP! NOT RAIDED!
 create mode = 760
 user = @shareusersourhouse
 directory mode = 770
 
[Pictures]
 read list = mcenter,public
 path = /options/other_raided_shares/PIX
 write list = melwood,kelwood
 only user = yes
 comment = Raid5 and Backed UP
 create mode = 760
 user = @shareusersourhouse
 directory mode = 770
#======================
```

---

### Post by CharlesA on 2011-01-07
I experimented. Haven't run into any problems on either XP, Vista, or 7 with the Samba server running on my Ubuntu box.

---

### Post by aceofspades686 on 2011-01-07
Oh, I had forgotten one minor issue that I ran across, because it has long since been disabled.  Windows 7 has the homegroup feature that can mess with any file sharing outside of Windows 7 -> Windows 7 sharing, so you probably want to look up disabling that.

> **ally_uk said:**
> How did you guys learn the art of Linux? I come from a windows background myself, I am pretty comfty at using the cli updating packages etc, but want to get my feet wet and actually setup a linux server, the ideal goal is to get both Linux and Windows 7 to get along with each other.

So how did you guys learn the art of setting up servers? did you spend ages running around in circles reading man pages? and out of date guides on the internet? 

seems like a real pain to try and make a transition from Windows to linux, Someone needs to write a clear and concise noob freindly guide on how to get stuff done.

Can someone show me a example of a Samba config that will work with Windows 7, the guy earlier posted a link to the ubuntu main samba resource but isn't that like out of date? Swat is ancient right?

Thanks

A lot of learning this stuff it rolling up your sleeves and digging in. My first venture into linux was one day when I was about 13 I got bored and Windows was acting stupid, so I had heard about this "linux thing" and downloaded and tried.. I believe it was Red Hat 8.  Used it on and off for several years (biggest downfall for me being that I'm also a gamer) and all the knowledge about it just sort of snowballed.

As far as guides, I've found some of the best ones on HowTo Forge ([http://howtoforge.com/howtos/linux/ubuntu](http://howtoforge.com/howtos/linux/ubuntu)) They keep a fairly up to date group, although they naturally don't have everything.

EDIT:
Also, that samba page was last updated in October, so it should be reasonably up to date ;)

---

### Post by NIT006.5 on 2011-01-07
> **ally_uk said:**
> is Windows 7 still having problems with Samba or has this been fixed?

One minor point: make sure you're on a recent version of Ubuntu. Changes to Samba for Win 7 compatibility weren't backported to older releases, even if they were LTS. So minimum to go with is 10.04 I think. I know this applies to Samba domain controllers, but I'm not certain about your situation.

> **ally_uk said:**
> How did you guys learn the art of Linux? I come from a windows background myself

I also came from a Windows background and it was frustrating, especially having to try and find the "right" answers on the net, because there are plenty of wrong answers too. Even though I administered Linux servers for a while (the very basics), I never really got my feet wet until I moved over to Ubuntu desktop too. It does take a lot of research though, and for me a very systematic approach. For instance, start with a particular server solution (like a Samba file server) and get to know it inside out. Then move onto something else like mail servers. I would also recommend using the official Ubuntu Server Guides as your starting point, instead of just googling for howto's which are unofficial and might not provide the correct or best method of configuring things.

It's well worth the effort though! Good luck ;)

---

### Post by lykwydchykyn on 2011-01-07
> **ally_uk said:**
> How did you guys learn the art of Linux? 

So how did you guys learn the art of setting up servers? did you spend ages running around in circles reading man pages? and out of date guides on the internet? 

seems like a real pain to try and make a transition from Windows to linux, Someone needs to write a clear and concise noob freindly guide on how to get stuff done.



I learned Linux by running bleeding-edge distros that broke all the time, forcing me to understand them so I could fix them.  It's the tried-and-true method ;).

Seriously, people write great concise guides to things all the time, but then they get out of date.  I've written a few myself, and I'm not keen on the idea of going back and updating them (in some cases, I've moved on from using the software I was writing about anyway).

Something like samba doesn't really change much over the years, though.  I haven't had any trouble with my samba servers with windows 7 (at least none that I didn't have with other versions of windows).

I'm pretty sure the default samba configuration "works" with Windows 7, but of course nothing is shared by default.  I think the operative questions are:

 - What features do you need from your samba server?
 - How is it not working with windows 7?

---

### Post by R.Bucky on 2011-01-07
Yup, had the same problem at work and home with mixed Win7, XP, and Linux boxes. Check out this blog post. [http://nwlinux.com/access-samba-shares-with-windows7-professional/]("http://nwlinux.com/access-samba-shares-with-windows7-professional/")

---

### Post by CharlesA on 2011-01-07
I have a semi decent Samba howto [here]("http://charlesa.net/tutorials/linux/samba.php").

---

### Post by Vegan on 2011-01-07
my experience with *ix goes back to the days of the 80386 CPU.

today Linux is the popular choice, but the old BSD is still afloat.

---

### Post by ally_uk on 2011-01-10
Has anyone had any success setting up a Linux PDC which works with Windows 7 machines, can it be done?

---

### Post by CharlesA on 2011-01-10
Haven't done it, so I don't know if it'll work.

I do know you can get Win7 (and Vista) to authenticate to an NT Domain Controller, but you have to change a security setting on Vista/7.

Maybe that can be a starting point?

---

### Post by CharlesA on 2011-01-10
Haven't done it, so I don't know if it'll work.

I do know you can get Win7 (and Vista) to authenticate to an NT Domain Controller, but you have to change a security setting on Vista/7.

Maybe that can be a starting point?

---

### Post by CharlesA on 2011-01-10
Haven't done it, so I don't know if it'll work.

I do know you can get Win7 (and Vista) to authenticate to an NT Domain Controller, but you have to change a security setting on Vista/7.

Maybe that can be a starting point?

---

### Post by CharlesA on 2011-01-10
Haven't done it, so I don't know if it'll work.

I do know you can get Win7 (and Vista) to authenticate to an NT Domain Controller, but you have to change a security setting on Vista/7.

Maybe that can be a starting point?

---

### Post by NIT006.5 on 2011-01-10
> **ally_uk said:**
> Has anyone had any success setting up a Linux PDC which works with Windows 7 machines, can it be done?

Yes, I've just been working on this recently and did succeed. As mentioned in my previous post on this thread though, don't try with an older Ubuntu version (unless you want to mess around with recompiling Samba). The support for Windows 7 was considered a new feature, rather than a "fix" and therefore wasn't backported to older versions of Samba. So originally when I tried on 8.04 I hit a brick wall. However, I have a PDC running 10.04 server which is successfully authenticating Windows 7 clients. Admittedly I have not done extensive testing and its not running in a production environment yet, but I could join the Windows 7 PC to the domain and authentication was working perfectly (with squid and dovecot also authenticating with LDAP). I would recommend using the official 10.04 server guide as your starting point.

However, I also had to apply a registry patch on the Win 7 client (patch is available on the Samba site). Since I don't use Win 7 myself, I was testing with a pre-release version, so I'm not sure if the registry patch is still required on an up-to-date Win 7 install.

I should have this running in a live environment (school setup) within the next couple of weeks, so will only know then if there are any major issues I guess. Fingers crossed.

---

### Post by ally_uk on 2011-01-11
That sounds interesting do you have a guide or resource on how to setup the PDC? many thanks

---

### Post by NIT006.5 on 2011-01-11
> **ally_uk said:**
> That sounds interesting do you have a guide or resource on how to setup the PDC? many thanks

I haven't come across a single up-to-date how-to that incorporates everything (although there was an older one floating around for 8.04), but you should be able to get what you need from the following:

[https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/C/samba-dc.html)
[https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html)
[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)

This can be configured with or without LDAP (although LDAP is recommended for larger environments), so you'll have to look through and see which setup you want to go with. I had originally used an old how-to for 8.04 (before realising the lack of Win 7 support) and only afterwards used these docs, so I'm not sure if there's anything in my setup that isn't covered in those docs, but those should get you going.

One important note, which I don't remember seeing mentioned in these, is that even though the server is the PDC, you still need to specifically add it to the domain at the end, otherwise it causes issues with winbind authentication which results in authentication time-outs after the server has just booted (for as long as 5 minutes after booting).

---

### Post by NIT006.5 on 2011-01-11
Oh sorry, and those docs don't cover LDAP authentication for other services - you might need to refer to the documentation for each service that you want to use with LDAP (squid, dovecot, etc.)... BUT although I had already configured these for LDAP auth, I realised afterwards that it might not be necessary, with the use of nsswitch. For instance, apache set up for pam auth, also authenticates ldap users with no additional config. I haven't done enough digging around there to understand fully how the authentication works, so you might need to experiment a bit.

---

### Post by ally_uk on 2011-01-11
Thanks although seems like I have bitten off more then I can chew, lol all seems a bit daunting to me. how long have you been using Linux for you seem pretty damm knowledgeable. Did you come from a windows background whats the key to learning Linux? just tinker and stick at it?

---

### Post by BenWuan on 2011-01-11
ally_uk-
 
Did you read Kevinthecomputerguy's reply?
 
He has a fantastic website, taught me everything i needed to become a linux user.

---

### Post by NIT006.5 on 2011-01-12
> **ally_uk said:**
> Thanks although seems like I have bitten off more then I can chew, lol all seems a bit daunting to me. how long have you been using Linux for you seem pretty damm knowledgeable. Did you come from a windows background whats the key to learning Linux? just tinker and stick at it?

Lol, thanks. I can promise you though, there are a lot of guys here who are way more knowledgeable than me :)

Yes, I also came from a Windows background and was basically forced into Linux because the company I was working for at the time was going native Ubuntu. I actually resisted the change initially, mostly because I was intimidated by Linux. Having done some minor/basic admin stuff on Fedora servers for about a year, I only really started getting into Linux when I moved to an Ubuntu desktop in 2007. After three or so frustrating months, everything started to click and I suddenly found myself passionately advocating Linux (specifically Ubuntu). In another couple of months I was so fully converted that I started the Zimbabwe LoCo Team... so that alone should say something about how awesome Ubuntu is :P

In short, I think the best way to learn is to use Linux as much as possible... including on your desktop if that's an option. The more you use it, the more sense it starts to make. And yes, you have to stick at it, do tons of research and reading, a lot of trial and error, etc. And if something seems daunting, try tackle something slightly smaller first. I remember spending several weeks (almost solid) trying to get dhcp and dynamic dns working on a Fedora server, and that was one of my first real server projects. It was extremely frustrating, but the satisfaction when you succeed (at any little project) is that much better!! So keep at it and don't ever admit defeat lol. :)

What really worked for me, was actually making a list of all the stuff I wanted to be able to configure... and working through the list one by one on a test server.

---

### Post by castalla on 2011-01-15
I hope I'm not hijacking this thread.  But I have one massive problem with file shares (and Samba) which is driving me nuts.  I think I'm searching for the Holy Grail ... which doesn't exists.

Briefly, using a variety of devices (with a variety of linuxes) I can see and access Win 7 shares (with no password/user logins).  And vice versa - Win 7 sees the other device shares.

However, one device which sees all the other shares (including Samba on Android) will not access Win 7.  It throws up a login screen which fails each and every time.

I have been told in various other forum this is because Win 7 has removed the MS-RAP protocol.  The only solution MS offered was advice to run Xp-mode in Win 7.  (Some advice! Run a virtual OS on a virtual disk, just to get file sharing).  Sadly there is no way to access the linux on the failing device (a media player).

Does anyone have an idea on a fix or workaround?  I have tried every possible combination of network setup (on Win 7) - I even stepped down to smb1 thinking this might have backward compatability.  Still get this damned failing login.

PS: this is the classic catch-22 - MS say the protocol is not supported, the device manufacturers say they won't change the network protocol.

Sorry if this is off-topic .... but even some moral support would be encouraging.

---

### Post by bbrabender on 2011-01-22
Hello,

I'm having trouble browsing my external drives that have been shared. I have no problems accessing them from Win 7. The weird part is that from Ubuntu 10.10 I can access the shared folder that is on the same partition as the OS but cannot access the external hard drive folders that have been shared. I've looked at fstab and smb.conf and all seems right. Does anyone have any suggestions that could help me access these folders from Ubuntu? 

Thank you in advance.

---

### Post by Vegan on 2011-01-22
SAMBA works fine, if you are having a problem connecting or seeing it, check you Windows box for network problems generally.

---

### Post by bbrabender on 2011-01-23
I'm not having issues viewing the shares on my Windows Box. Where I am having trouble is that I can see the shares in Linux but cannot mount the ones that are external hard drives. If I share a folder in my home directory it can be browsed just fine, but if the shared folder is on an external drive I can not browse it. I hope that makes a little more sense. I'm not really to worried about it because I primarily access the folders from a windows box. 

I am here to see if there is a solution to the problem that I am having. If there is any more information that I can provide to help with this issue just let me know. Thank you.

---

### Post by CharlesA on 2011-01-24
Sounds like a permission issue to me.

---

