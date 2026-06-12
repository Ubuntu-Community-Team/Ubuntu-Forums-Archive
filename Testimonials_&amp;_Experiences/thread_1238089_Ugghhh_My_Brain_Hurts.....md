---
title: "Ugghhh My Brain Hurts...."
date: 2009-08-12
forum: Testimonials &amp; Experiences
---

### Post by Hamma Hedd on 2009-08-12
Arrgghhhhh NETWORKING...

Trying to connect two Ubuntu PC's.... reading things and all that.

And I am thinking "This whole thing is just sooooooooooo wrong".

It's all configured back to front.

Ideally it should be no more difficult than hooking 2 PC's with a cable and going "Connect".

I mean it works for power tools and extension cords.

I can also appreciate all the more technical aspects of designing networks for specific applications, with security and administrative privileges etc.

But that OUGHT to be coming AFTER all of the simple of principle of "Hook it up and do it" - and NOT before it.

I don't want to have to go into several different networking programs and then having to research the MAC and Network Address settings from other parts of the system, and then code all of those in and and and and and and and and .... hoping it works.

And IF I didn't have an internet connection, then I wouldn't be able to figure it all out - without a LOT of educated guess's, and hard work because the inhouse Ubuntu manual has very little material to cover these issues....

Then there are the Ubuntu manuals that one can download and or buy and then have to study and HOPE they cover the issues and any peculiarities that may arise.

I think it's about time that this whole networking issue was reworked to be as easy to do - from the outset, to make is as simple as mounting external drives, USB sticks and all this other jazz.

And then make the options available to harden the simple stuff up with restrictions and authorisations etc. via tick boxes in a GUI panel.

Anyway - back to doing my research, research, research and testing, coding, configuring and hoping it works or spending more of my time - working out how to do it, because the people responsible for doing it - couldn't make it a simple "Plug and Play" process in the first place.

---

### Post by Hamma Hedd on 2009-08-12
OK I have raised a legitimate grievance - that there are lots of people who have simple needs and basic networks who just want to transfer data and or back stuff up - without having to research and learn and apply and hope it works, and then possibly repeat - add infinitum - until it does.

I do live and work in remote location, and IF the settings for all the internet stuff gets lost and or misplaced and or the back up codes fail to be recorded faithfully; = no internet = then it's a reinstallation.....

OK I have two computers - a laptop and a stand along PC. 

Both are running Edubuntu 9.04. 

The laptop is pretty old and it's only outputs are a CD burner, a USB 1.1 port and a network cable.

I have to transfer about 14Gig of data - and can either do that in 2 lots on a single 8G USB memory stick - through the 1.1 port at USB 1.1 speeds.. 

That is both unreliable and it's going to take a LONG time.

The CD burner - well I want to keep that for emergencies only as the burners are impossible to get and I don't want to wear it out.

With the network cable - It hooks up and runs to the internet via a router - that works fine.

I also have a CAT 5 cross over cable for linking the 2 computers directly - done it in the past using windows OS's and older Ubuntu's.

I know that I can connect the two computers via the router.....

But I am really busy - I have enormous amounts of work to do.

What I would really like is to be able to link the two computers together via the cross over cable and press "Connect" and each system is completely visible to each other - for transferring files and sorting data etc.

But this whole thing - can be another adventure that I don't want to participate in.

I just want to flick the switch to turn on the light. I don't want to fell the tree to get the wood to make the boat to hunt the whale to get the oil to light the lamp...

So given that I am runnning Edubuntu 9.04 on two PC's and I can link them directly via a cross over cable or via a router; what is the straight forward way to connect them?


Any guidance that works would be appreciated.

---

### Post by tomBorgia on 2009-08-12
Connect via the router and use NFS - Sure there's a guide on hear somewhere.

Seriously though... Power tools and extension cords?

---

### Post by 3rdalbum on 2009-08-12
1. Have you got Samba server installed?

2. You need to do folder sharing on at least one computer. Right-click on a folder that you have permission for, go to Properties, and then click the "Sharing" tab. The rest is fairly self-explanatory, allow guest access and all that jazz, and then click "Create Share". I'm not sure if it requires a reboot or not, but afterwards the client computer should be able to see your new shared folder by going to Places > Network.

And if you have a firewall running on either of the computers, turn it off.

If you want to customise things further, you can install the system-config-samba package.

---

### Post by Hamma Hedd on 2009-08-12
Cool Thankyou... ever so much.

The more I use Linux the more I appreciate all the hard work so many of you all put in to make it soooooo good.

In my explorations of the issues.... well I can see with some ignorance of the issues and variations of them, that with the Edubuntu - that with all the possible network settings - that properly set up - that this would be an excellent system based upon how good it is to use and it's resistance to being hacked, rigged and crashed by the adventurous youth.....

Where it all falls to bits is that I just want to back up a heap of data from computer A to computer B, on a private system - with no kids or hackers., in my own home, and whe I'd LOVE to learn it all and get a PHD in Asprophysics  - I honestly don't have the time - and that is where overworked and slightly simple man meets industrial strength networking software - with the aim to do a simple "copy to back up" data transfer.....

And I don't have a spare week to become self taught on the subject. 

No SAMBA; (ignorant reply... assuming I have servers?) - I have just two standalone PC's that need to be connected... looked into SAMBA more here... for starters

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

[http://ubuntuforums.org/showthread.php?t=217347](http://ubuntuforums.org/showthread.php?t=217347)

Yeah I also have it on my system, getting some more features... via synaptic. It's in there, just have never seen a "Samba" application like Open Office Writer - must learn about it.

Look into NSF

[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

[http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html](http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html)


Get / find / install SAMBA - yeah it's on my system - will look up and see on how to use it.

Disconnect from the net.

OK Firewalls OFF.

Share some folders (properties.....) 

use brain and do it.

Thanks.

---

### Post by bear24rw on 2009-08-12
> So given that I am runnning Edubuntu 9.04 on two PC's and I can link them directly via a cross over cable or via a router; what is the straight forward way to connect them?
```
aptitude install openssh-server filezilla
```

do that on both computers then use filezilla to connect to other computer, get ip adress with ifconfig, and click and drag your files over.. easy as that

---

### Post by Tamlynmac on 2009-08-12
> Hamma Hedd

Perhaps, the best place to seek assistance is in the "Help Sections". Rather than continually posting in this section, one might consider asking specific questions in the appropriate help section.

Assuming of course - one desires assistance.

Just a thought.

---

### Post by juancarlospaco on 2009-08-12
[B]sudo apt-get update ; sudo apt-get install openssh-server ; sudo apt-get autoclean ; ping remote-ip ; ssh -X remote-user@remote-ip nautilus
[/B]
It brings remote nautilus locally, go click and read anything you want,
compressed, encrypted, easy.
:)

---

