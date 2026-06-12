---
title: "Business Server Setup"
date: 2008-05-28
forum: Server Platforms
---

### Post by blackouttech on 2008-05-28
I am fairly new at Ubuntu Linux although I have dabbled here and there for years. I own a computer sales and service shop in Louisiana (yes, to answer your question, Louisiana IS backwards when it comes to technology).

I have set up a little P3 dell box with 8.04 Server on it. In the install, I chose LAMP, DNS, Mail, and...well, pretty much everything for server options. I tried to install it all, just in case I needed it. Now the Apache does work, but I need help with the mail servers mainly. I want to install Zimbra for a webmail GUI, but other than that, I am lost. I have read three or four online tutorials for it, but they always end up messing something up. Last one killed my apache.

Any help is welcome!

---

### Post by The Devil Is A Squirrel on 2008-05-28
I tried to install Zimbra, too, but without any success. I guess Zimbra is yet not at the point to be installed by a newbie. However, I figured that Zimbra is especially picky when it comes to DNS. If your DNS settings are not properly configured, the installation will fail for sure.

Sorry if this post doesn't help you much...at least you know you are not alone  ;-)

---

### Post by majikins on 2008-05-28
I'm about to attempt this as well - from what I have read, Zimbra has its own preconfigured LAMP and has to run in its own space.  Hence a dedicated box or run it in a Xen, virtual environment.  I haven't got there yet but hope to soon :-)

---

### Post by blackouttech on 2008-05-28
For now I just want the pop3/imap and smtp to work. then I think I will take on Zimbra.

---

### Post by NateMan on 2008-05-28
Why don't you go back and manually install those packages, the default setups are not the best. I mean if you do it yourself then you will learn so much more about how all of this works, and maybe your zimbra installation would be a ton easier if you knew were the os stored necessary files and folders for that sort of thing. I have never had good luck with the autosetup stuff. And if you don't know what it did then your stuck with whatever it did, whether or not its what you needed. Id try the perfect server guide, then go back and install a webbased email program on top of it. If your having that much trouble with getting something to work and its killing other installs then maybe you should see how they work together and then the problems are normally quite clear. 

As for the south being technologically backwards, I'm from Mississippi, and I can tell you I know quite a few people who are very technically proficient and few who are not, but imagine that there are people everywhere who don't know much. Did you know mississippi is in the top 10 for supercomputing? (ranked 6) There are numerous technology and research centers spread out over the south, so I imagine we are not that technologically backwards. Even in Louisiana.

---

### Post by The Devil Is A Squirrel on 2008-05-28
I just found this: 
[http://www.zimbra.com/forums/installation/18530-ubuntu-8-04lts-5-0-6-community-release.html](http://www.zimbra.com/forums/installation/18530-ubuntu-8-04lts-5-0-6-community-release.html)
[http://varlogmessages.vroomvroom.org/](http://varlogmessages.vroomvroom.org/)

---

### Post by blackouttech on 2008-05-28
I know the south is not completely backwards. Barksdale AFB (an hour away) is the where the Air Force is putting the Cyber Command Center to keep an eye on cyber-space, but when you have 18 year old students asking you how to save a document in MS word, It scares you. I have lived in several states from Vermont and New York to Louisiana and several in between. Louisiana is not the worst, but in the area I am in, its pretty far down the list.

---

### Post by NateMan on 2008-05-28
Yeah its cool. I'm sure that there are people everywhere who can't save documents...

But seriously I'd try to go with a fresh groundwork install. I know people hate to hear that, but I tell that to everyone who has a halfway working linux server setup. Its probably not worth the time and effort you've put into it already to fix it. I mean why not go in and try the good old way and see what you can get working from there. I'd be more than happy to help, but again a bad foundation just isn't worth it to me. It only takes about half an hour to install linux server on a sloooow machine. Now manually configuring it, that takes an hour or so, but is completely worth it.

---

### Post by blackouttech on 2008-05-28
Well after apache got corrupted, I did go ahead and reinstall server edition again and got the apache working with the domain name and what not (not a whole lot to that) so basically it is now a clean install, if you cant help me from here

---

### Post by bmathis on 2008-05-28
I currently have 4 Zimbra servers installed and working. Zimbra requires it own server or, atleast, a change in ports in order for everything to work together. Its best to start off with a clean default installation of Ubuntu, installing bind and setting up a zone for your domain name (this is for internal use only). After that, you download the Zimbra package and follow the prompts during the install. 

Use this guide and make sure you're using Ubuntu 6.06 as they dont support anything newer at this time. [http://wiki.zimbra.com/index.php?title=Beginner%27s_Guide_to_installing_Zimbra_on_Ubuntu_6.06_Server]("http://wiki.zimbra.com/index.php?title=Beginner%27s_Guide_to_installing_Zimbra_on_Ubuntu_6.06_Server")

After the install is complete, then you can go into the Zimbra server and change the ports for the webmail. Make sure that no other ports needed by a program that you'll be installing are being used by Zimbra or else youre going to have some issues.

Its not so bad once you get started, it took me a few tries before I got a full server going as well. I plan on writing a howto with some extra steps soon, which Ill post here and on my blog. I plan on having this done by the first week of June.

- B

---

### Post by blackouttech on 2008-05-28
do I use the server version of ubuntu or just a regualr desktop version so i have a GUI? And this will be not be just for intranet, but open to the public as I will have a site on an apache too. I am looking forward to your howto, but I dont know if I can wait that long...I guess I may have to

---

### Post by bmathis on 2008-05-28
you can use either, but a GUI will use unnecesary resources and install software that you wont use, I would suggest the server edition if you're okay enough to work with the command line.

The first week of June is only 1 1/2 weeks away so its not that bad. If I have the free time this week, I'll get it out earlier.

---

### Post by windependence on 2008-05-28
Bmathis is right here, don't install anything else besides the default install. Zimbra installs all the packages you need by itself, except for a few things it will tell you to install. If you install more than that ahead of time, you will have problems. Also, it's not supported on 8.04 yet so like he said, use 6.06, and you can upgrade both Ubuntu and Zimbra later.

-Tim

---

### Post by windependence on 2008-05-28
> **blackouttech said:**
> do I use the server version of ubuntu or just a regualr desktop version so i have a GUI? And this will be not be just for intranet, but open to the public as I will have a site on an apache too. I am looking forward to your howto, but I dont know if I can wait that long...I guess I may have to

If you are going to run other stuff on the box then you should probably install VMware server and use two separate virtual machines for this because Zimbra wants to have a dedicated machine.


-Tim

---

### Post by hyper_ch on 2008-05-29
Two easy howtos.... should all work on debian and current ubuntu

[http://www.howtoforge.com/zimbra-collaboration-suite-5.0-on-debian-etch](http://www.howtoforge.com/zimbra-collaboration-suite-5.0-on-debian-etch)

[http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu](http://www.howtoforge.com/installing_zimbra_collaboration_suite_on_ubuntu)

---

### Post by lrsorey on 2008-05-29
Hello NateMan,

I too am from Mississippi. We are using Ubuntu 8.04 to serve as our main Java based Video Streaming Server. Our next move is to setup multiple Ubuntu servers in a clustered environment for an Origin / Edge distributed Live Streaming and Video On Demand. Dang, is that mud I see between my toes? : )

---

