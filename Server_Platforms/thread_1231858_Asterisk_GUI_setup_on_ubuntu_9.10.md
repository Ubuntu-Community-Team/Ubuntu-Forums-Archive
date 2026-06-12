---
title: "Asterisk GUI setup on ubuntu 9.10"
date: 2009-08-05
forum: Server Platforms
---

### Post by kustomjs on 2009-08-05
alright guys I need some help on installing Asterisk gui on ubuntu server 9.10 and how I installed Asterisk was doing sudo apt-get install Asterisk  but now I need help getting Asterisk gui installed what is the best way of doing this?

---

### Post by kustomjs on 2009-08-05
after 37 views and still no reply's?

---

### Post by kustomjs on 2009-08-05
back on top after 47 views and still no reply's.

---

### Post by cariboo on 2009-08-06
I don't know if there is a gui for asterisk, but [this]("http://www.voipphreak.ca/2007/11/03/freepbx-ubuntu-howto/") howto may help.

BTW, please don't bump a thread until at least 24 hours has elapsed. We are all volunteers here, and the person that may be able to answer your question may not have seen it yet.

---

### Post by kustomjs on 2009-08-06
of course nobody is going to see it if keeps getting moved over to page 2 that is why I keep bumping it because most people only look at the first page and move on. but thanks for that link there cariboo907.

---

### Post by oprogue on 2010-02-10
> **kustomjs said:**
> of course nobody is going to see it if keeps getting moved over to page 2 that is why I keep bumping it because most people only look at the first page and move on. but thanks for that link there cariboo907.

what's the story on this ... were you able to get Asterisk up and running?  I added Asterisk using Synamptic but haven't gotten any further than that.

Any guidance is greatly appreciate.

Thanks in advance.

---

### Post by kartook on 2010-04-01
I know this is old thread  .The same time i need to say some thing here .Asterisk is good PBX system . 

I tried to install all LINUX and UNIX flavor  on cli everything good and amazing work .

After install Asterisk-GUI 2.0 or 1.0 , i never get a login screen in my 4 months work .

i created and installed more than 60 Different versions and linux flavors . Googled  a lot and asked many forums even asterisk forum ,blogs IRC u name it 

:(


No use . Some thing is there  sharing is the only way i think .

so please share some one here what is that trick is there ......

---

### Post by snpz on 2010-04-01
A couple of things about Asterisk:
1) Asterisk is a fantastic PBX, but forget about Asterisk distribution install (have seen some - none of them worked like we wanted);
2) install it from source and try to configure without GUI (there is a lot of documentation how to do it);
3) are you going to install just for testing, or for practical useage (PRI, BRI, SIP trunk)?!

---

### Post by fang0654 on 2010-04-01
Asterisk is a complex beast, that misconfigured can actually cost you quite a bit of money.

If you are looking to set it up to play with it, I'd recommend going the very easy way and looking at [PBX In a Flash]("http://pbxinaflash.net").  There is a great set up howto here:

[Orgasmatron Installer]("http://nerdvittles.com/?p=675")

Granted, it isn't Ubuntu based (is CentOS based).  But it will give you a fully working, secure system that you can cut your teeth on, and if you feel like building it all on Ubuntu, you will at least have an idea how to do it securely.

---

### Post by kartook on 2010-04-02
Thanks to everyone 

Just i want to know how to install Asterisk-gui 2.0  ... I need to find where i am wrong ... 
:)

I tried following pages 

[http://www.asteriskguru.com/tutorials/asterisk_gui.html](http://www.asteriskguru.com/tutorials/asterisk_gui.html)
[http://astrecipes.net/?n=217](http://astrecipes.net/?n=217)
[http://www.asterisk.org/asterisknow/developers/gui-guide](http://www.asterisk.org/asterisknow/developers/gui-guide)

and many more ...... 


### Note : FIle was moved the path to another path 


More than than i did on freepbx and works fine .I always use to manage for asterisk servers 

Webmin 
Asterisk
FreePbx 
Sangoma Cards 

Successfully up and running with out any issue .. :)

---

### Post by Jonners59 on 2010-08-04
I'm the same.  I have my own thread asking this question.

I have a 3CX system I installed some time ago on a Vista machine, but I want to move away from MS and on to Ubuntu.  The 3CX and others I tried were so easy to install on MS and set up, even my kids could do it.  I have set up my machine to host it, I just need the Asterix installed, accessible, configured and working, then I switch over.

There is Asterix in the Synaptic, but after install, nothing happens and it does not even appear anywhere.  It's crazy.  Then I spend MONTHS and MONTHS looking and trying different sites, WiKi and the like, nothing works.

Why is this so difficult in Ubuntu?  This should be off the shelf stuff.
):P

---

### Post by kodb on 2010-08-09
Hey all,
I tried all of that and ultimately just set up a separate machine using AsteriskNOW!.  It basically almost worked out of the box itself and I ended up buying a couple hours of paid support not to configure the FreePBX per se but to do the SIP phone setup.  I bought the phones from VOIPSupply.com and it is now working as a production system in my surgical office.  I run a Windows 2003SBS for the windows centric programs i need (my EMR) and an Ubuntu Server 9.10 box as the other server for BDC and storage.  All of my home machines and personal computers run Ubuntu 9.10 pending upgrade to 10.04.   If I could figure out how to get Asterisk to run on Ubuntu I would do so but ultimatley gave up and went with the CentOS based version (AsteriskNow).   If anyone knows how, I much like the OP would love to learn!
Regards,
Bob

---

### Post by Jonners59 on 2010-08-16
> **kodb said:**
> 
Hey all,
I tried all of that and ultimately just set up a separate machine using AsteriskNOW!.  It basically almost worked out of the box itself 

> **kodb said:**
>  If I could figure out how to get Asterisk to run on Ubuntu I would do so but ultimatley gave up and went with the CentOS based version (AsteriskNow).   If anyone knows how, I much like the OP would love to learn!
Regards,
Bob

Bob
Exactly.  I am so very surprised that Ubuntu is not making any real efforts here.  All the other OS are, including Microsoft.  I am the same as you, wasting lots of time on this and have an out of the box on a different OS that I would love to swap for Ubuntu. Non of the Ubuntu forum big names or developers have sprung up to help either.[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG] 

I am running 10.4 on all bar my wife's XP PC - she will not let me touch it!

---

### Post by ajoliveira on 2010-09-14
Will give it a try, i just have to do it to replace an old fedora 6 box where i have asterisk+freepbx running. Will let you know...I just tried it, used a shortcut script for debian lenny and have to reformat the partition, eheheh...my mistake...

---

### Post by kartook on 2010-09-16
Guys  found the solution for any flavorer of LINUX 

Try the Asterisk old version 1.4 and install AsteriskGUI 2.0 

it works cool

---

### Post by Jonners59 on 2010-09-16
Could you give a step by step guide?

---

### Post by Baked- on 2010-09-16
> **snpz said:**
> A couple of things about Asterisk:
1) Asterisk is a fantastic PBX, but forget about Asterisk distribution install (have seen some - none of them worked like we wanted);
2) install it from source and try to configure without GUI (there is a lot of documentation how to do it);
3) are you going to install just for testing, or for practical useage (PRI, BRI, SIP trunk)?!


Agreed on #2
The only GUI app i use to manage my asterisk system (~15K calls/day) is visual dialplan and I made a little php website to manage the sip peers/phone provisioning in about 2 hours of work.   I have tried asterisknow, pbx in a flash, elsatix, etc and found it much easier to understand and deal with text config files.

---

### Post by Jonners59 on 2010-10-18
I give up...  I have reverted to virtualbox and just installed Windows 7 with my 3CX in the virtual machine.

This is not very user friendly.  Still geekish

---

### Post by ajoliveira on 2010-10-27
> **ajoliveira said:**
> Will give it a try, i just have to do it to replace an old fedora 6 box where i have asterisk+freepbx running. Will let you know...I just tried it, used a shortcut script for debian lenny and have to reformat the partition, eheheh...my mistake...

ok, did it, just took me about 2 hours, now I have to repeat the process on another pc just to make sure I am not making mistakes and I will come back to you. I used asterisk as installed by apt-get install, no messy compiles and no running as root.

Will be back from November 10 on, got work to do...

Will meanwhile be loading the config to make sure it all works, then a step-by-step guide will pop-up.

It was somewhat messy but still traceable.

---

