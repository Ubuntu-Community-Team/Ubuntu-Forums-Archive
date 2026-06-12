---
title: "[SOLVED] virtualbox shared folders....?"
date: 2007-11-30
forum: Virtualisation
---

### Post by kamitsukai on 2007-11-30
How do u set-up shared folders with virtual box running xp and ubuntu 7.10? i cant find any info in he manual but his could just be me being dence....

thnx in advance

---

### Post by forestpixie on 2007-11-30
Start settings in virtualbox, go to shared folders and browse to the folder you want to share

---

### Post by kamitsukai on 2007-11-30
ok thnx but now i have done that i cant find out how to access the folder from windows!?.....

---

### Post by forestpixie on 2007-11-30
which is running as a virtual - I have win as a virtual and accessed my shared folder in ubuntu as a network folder in windows

---

### Post by kamitsukai on 2007-11-30
windows is the virtual and ubuntu is the host

---

### Post by forestpixie on 2007-11-30
> I have win as a virtual and accessed my shared folder in ubuntu as a network folder in windows that's how it worked for me

---

### Post by StuipedandUgly on 2007-12-01
here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out

---

### Post by He|iX on 2007-12-03
How do you mount the windows share in ubuntu if ubuntu is the VM?

---

### Post by mersonmathew on 2008-02-09
> **StuipedandUgly said:**
> here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out


Thanks! I was stuck trying to access the hard disk partitions. Just one thing to add. On clicking Devises->Install Guest Additions I felt nothing was happening. But actually the install script was being mounted as a virtual cdrom.

---

### Post by daniel3ub on 2008-08-30
Well, didn't work for me :(
Any idea? Do I have to do something in Ubuntu to make this work?

---

### Post by akikoo on 2008-09-03
I also had problems with shared folder on WinXP guest (on Ubuntu Hardy 8.04 host) - I couldn't see my shared folder at all on the guest. Just reinstalling Guest Additions solved it!

---

### Post by jimmysheldon on 2008-09-03
hello, just tried this

> **StuipedandUgly said:**
> here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out

but when i type 'net use t: \\vboxsvr\shared' (my folder is called shared) i get: "System error 53. Network path not found."

can anyone help out with this? not sure i've set the folder up right.

---

### Post by pyjamashark on 2008-11-29
worked like a charm for me - thanks

---

### Post by ImpelGD on 2008-12-05
> **jimmysheldon said:**
> hello, just tried this



but when i type 'net use t: \\vboxsvr\shared' (my folder is called shared) i get: "System error 53. Network path not found."

can anyone help out with this? not sure i've set the folder up right.

I'm finding the same.

I've installed Guest Additions from Google Code (VirtualBox couldn't download it) and set up my folder in VB shared folders. But Windows (the virtual host in Ubuntu VirtualBox) can't mount or see it.

Windows *can* access the internet, so the network adapter is working in case that's required.

---

### Post by bodhi.zazen on 2008-12-05
> **ImpelGD said:**
> I'm finding the same.

I've installed Guest Additions from Google Code (VirtualBox couldn't download it) and set up my folder in VB shared folders. But Windows (the virtual host in Ubuntu VirtualBox) can't mount or see it.

Windows *can* access the internet, so the network adapter is working in case that's required.

You have to install the Additions on the Windows XP guest.

You should use the additions that came with Virtualbox. It is in the menu Install Additions.

---

### Post by ImpelGD on 2008-12-05
> **bodhi.zazen said:**
> You have to install the Additions on the Windows XP guest.

You should use the additions that came with Virtualbox. It is in the menu Install Additions.

Hi and thanks for the reply.

I did install the Guest Additions in the XP guest. I couldn't simply use the menu because it showed as 0 bytes and wouldn't download. Timed out.

Special mouse integration etc. is working fine.

---

### Post by bodhi.zazen on 2008-12-05
Well, they patched the Additions to fix your problem so you need the patched version.

Shut down windows XP.

Make sure there is nothing loaded, no iso, in the CD slot.

Make sure the OS type listed is Windows XP

Fire the windows guest back up.

Log into windows.

In the Virtualbox window with the XP guest use the menu

Devices -> Install Guest additions.

This should then mount a "CD" in the Windows guest, on the CD are the .exe ;)

---

### Post by ImpelGD on 2008-12-06
The download doesn't work directly, but I'm downloading the 2.0.4 in FF and will try that - thanks.

Edit: the new version works. :) Thanks again.

This was it:

[http://dlc-cdn-rd.sun.com/c1/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso](http://dlc-cdn-rd.sun.com/c1/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso)

Don't know why VirtualBox couldn't download it itself.

I downloaded it to my Ubuntu desktop, mounted it as the CD drive in Windows XP guest and installed.

---

### Post by mitch_feaster on 2008-12-23
> **He|iX said:**
> How do you mount the windows share in ubuntu if ubuntu is the VM?

```
mount -t vboxsf share mount_point
```

---

### Post by frankieus on 2009-01-31
Use the "Add Network Place Wizard" in Windows. Follow the wizard and look for you shared folder, add it and you're done. ;)

---

### Post by Pixel on 2009-02-20
> **jimmysheldon said:**
> hello, just tried this



but when i type 'net use t: \\vboxsvr\shared' (my folder is called shared) i get: "System error 53. Network path not found."

can anyone help out with this? not sure i've set the folder up right.
If you open up windoes explorer, then click the folders button, from there click "My Network Places -> Entire Network -> VirtualBox Shared Folders".  You should then be able to see your shared folders in the there.

To make it easier, once you find your folders, right click on the and click on map drive, this will let you map a network drive (such as Z:), to the folder, so that it's easier to get to next time.

---

### Post by Robertjm on 2009-02-22
Since the "Thanks" icon isn't readily visible I'll post a Thanks! for the answer on the first page.

I'm running VBox 2.14 on Intrepid Ibex host w/Windows 7 Beta client and the instructions from StuipedandUgly to share worked like a charm.

Robert

---

### Post by dbsoundman on 2009-03-09
I'm on a Windows 7 client but I can't get it to work for the life of me! I actually did have a network share for a short time using my regular samba server on this computer in Ubuntu, but now that doesn't work, and the \\vboxsrv\share thing never has worked. I have the most recent copy of the Virtual Box Additions (2.0.4) on an iso file which I have installed and reinstalled on the client, but no change. Any ideas?

-Dan

---

### Post by bodhi.zazen on 2009-03-09
> **dbsoundman said:**
> I'm on a Windows 7 client but I can't get it to work for the life of me! I actually did have a network share for a short time using my regular samba server on this computer in Ubuntu, but now that doesn't work, and the \\vboxsrv\share thing never has worked. I have the most recent copy of the Virtual Box Additions (2.0.4) on an iso file which I have installed and reinstalled on the client, but no change. Any ideas?

-Dan

I do not know about a shared folder may I suggest an alternate ?

Personally I use network share protocols, Samba, ssh (scp), or if you are behind a router, ftp.

---

### Post by dbsoundman on 2009-03-09
I have a samba share on the server machine (which is the same machine that the client is on), but the Windows client doesn't "see" the samba share, and when I manually enter the address it fails. It worked initially for a short time, but doesn't anymore, and I don't know why. I do have a router but since both machines are on the same computer I didn't think it was an issue.

-Dan

---

### Post by bcerge on 2009-03-11
> **frankieus said:**
> Use the "Add Network Place Wizard" in Windows. Follow the wizard and look for you shared folder, add it and you're done. ;)

wow, after spending hours searching through forums...this worked first shot, thnx man!

---

### Post by mezhaka on 2009-04-16
> **He|iX said:**
> How do you mount the windows share in ubuntu if ubuntu is the VM?

have you found the solution?
i run ubuntu VM inside WinXp. have set up the folder to share through virtualbox. but don't know how to find it inside of my ubuntu VM. should i mount something?

---

### Post by meka4996 on 2009-05-07
Try this...
[http://ubuntuforums.org/showthread.php?p=7236471#post7236471](http://ubuntuforums.org/showthread.php?p=7236471#post7236471)

---

### Post by n3had on 2009-05-09
check my video tutorial

[http://www.youtube.com/watch?v=75FeKOkpSKk&feature=PlayList&p=512E30EA478B12D9&index=18](http://www.youtube.com/watch?v=75FeKOkpSKk&feature=PlayList&p=512E30EA478B12D9&index=18)

peace out

---

### Post by switch10 on 2009-05-12
> **StuipedandUgly said:**
> here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out


Thank You!!  It's been a few years since you posted this, but it's the only thing that worked for me.

---

### Post by slyboots on 2009-06-02
For me works!

---

### Post by Swerve1000 on 2009-06-30
> **StuipedandUgly said:**
> here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type **net use t: \\vboxsvr\Crimethinc**(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out

Hi, should this definetly be a **t:** drive or could it be another?

I still keep getting "System error 53. Network path not found."

I tried:
> 
Use the "Add Network Place Wizard" in Windows. Follow the wizard and look for you shared folder, add it and you're done.
 

but when I view this folder, none of the folders I created to share appear, it's just empty.

EDIT:
I found [THIS]("http://showmedo.com/videotutorials/video?name=3650010&fromSeriesID=365#") video tutorial on the matter and it works well. But nore that you need to install Guest Additions before following the video tutorial, then I use a folder called vb on the Desktop of Ubuntu, I right clicked on it and then selected... can't quite remember now, but that worked.

---

### Post by m3alnemer on 2009-07-15
> **n3had said:**
> check my video tutorial

[http://www.youtube.com/watch?v=75FeKOkpSKk&feature=PlayList&p=512E30EA478B12D9&index=18](http://www.youtube.com/watch?v=75FeKOkpSKk&feature=PlayList&p=512E30EA478B12D9&index=18)

peace out

thank you brother. It really helped me

---

### Post by elitefox on 2009-08-08
> **Swerve1000 said:**
> Hi, should this definetly be a **t:** drive or could it be another?

I still keep getting "System error 53. Network path not found."

I tried:
 

but when I view this folder, none of the folders I created to share appear, it's just empty.

EDIT:
I found [THIS]("http://showmedo.com/videotutorials/video?name=3650010&fromSeriesID=365#") video tutorial on the matter and it works well. But nore that you need to install Guest Additions before following the video tutorial, then I use a folder called vb on the Desktop of Ubuntu, I right clicked on it and then selected... can't quite remember now, but that worked.

This is my experience with Ubuntu Hardy and virtualbox-3.0
1) Install Guest additions
2) instead of \\vboxsvr\shared, try instead of \\vboxsvr\shared\

it work for me :D

---

### Post by gOLdenHaWK3D on 2009-08-16
> **StuipedandUgly said:**
> here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out

Thanks a ton. :P

---

### Post by mad-bee:) on 2009-08-20
-first **Install Guest Additions**.It is under the **Devices** menu on **VirtualBox**
-add which folder you want to share from **Shared Folders** option on **Virtualbox**
-open **My Network Places** on **XP** click to **View** **workgroup** **computers**
           (it can be different if you changed the default network name)
-look down to links with the header **Other Places**
-you will see **Microsoft Windows Network**.Click it
-you will see the **Entire Network** link and click it
-look at the page you will see **VirtualBox Shared Folder** 
:)
it was easy :)

---

### Post by joebeasley on 2009-08-30
After installing the additions on the ubuntu guest, start the services. (/etc/init.d/vboxadd start)  Then mount with mount -t vboxsf sharename /mountpoint.

---

### Post by mathend99 on 2009-09-08
> **StuipedandUgly said:**
> here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out
Thank you very much, I finally solved my problem.

---

### Post by cnbiz850 on 2009-10-14
> **StuipedandUgly said:**
> here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out

This only works for me to some extent.  OK, I can share files by copy/cut etc between Windows and Ubuntu.  But what I can't do is that when I have some .exe file in the folder and try to execute it in Windows and Windows complain that the path doesn't exist.  Some other .exe files works this way though.  I wonder what is going on?

---

### Post by cnbiz850 on 2009-10-15
> **cnbiz850 said:**
> This only works for me to some extent.  OK, I can share files by copy/cut etc between Windows and Ubuntu.  But what I can't do is that when I have some .exe file in the folder and try to execute it in Windows and Windows complain that the path doesn't exist.  Some other .exe files works this way though.  I wonder what is going on?

Sorry, if I access it through //vboxsvr/VM then it is OK.  But if I mount it to a network drive like Z: then it is as what I mentioned above.

---

### Post by il pepe on 2009-10-15
PROBLEM: 
I did all the things as written down in this forum.

All things work, and i have a shared folder.

XP is guest, Ubuntu jaunty the host.
The only problem i have that all files that make in XP are locked in Ubuntu.
the reason i think is the following: the files made in XP are made as root.
Is there a way to automatically change those the permissions?

---

### Post by utnubu001 on 2009-12-08
i have an ubuntu system, with another ubuntu system in VirtualBox.
I shared my /media directory through virtualbox so i can access my hard drives..
How do i access the shared folder inside virtualbox?

---

### Post by TWO on 2009-12-10
> **frankieus said:**
> Use the "Add Network Place Wizard" in Windows. Follow the wizard and look for you shared folder, add it and you're done. ;)

I don't know what happened to the 'thank' button, but THANK YOU frankieus! Your method worked first time and is the simplest of the lot! :D

---

### Post by unc0nn3ct3d on 2009-12-29
Just wanted to stop by and send my thanks, worked like a charm for me and I'm also enjoying all of the awesome addons that comes with the guest additions.  W00t w00t

---

### Post by plink on 2010-01-03
> **StuipedandUgly said:**
> here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out

I'm writing about installing Win Xp as a guest on a Karmic host.

The above is a great start, and it helped me a lot.  But I still had other items to deal with, and I'm listing them here.  (Most are very obvious.)  Many of these I picked up in this thread, and some on my own.

a. In Synaptic, install the virtualbox guest additions, utilities, etc. before trying above steps.
b. Start up Win XP guest as a Windows admin-level user. (I do most of my Windows work as a Power User to minimize viruses, so I had problems until I switched to an admin account.)
c. For step 2, realize that this only sets up the iso file, and does not complete the install.
d. After step 2, go into Win Explorer, find the Guest Additions drive, right-click and pick Auto-Play.  That will trigger the actual install, with the typical Windows install dialogs.
e. For step 4, go to top menu, Devices...Shared Folders.
f. For step 6, I think that the key thing is the Folder Name that you selected in the shared folders setup.  My path was /home/pete/videos, but the Folder Name was Videos, so I ran
net use t: \\vboxsvr\Videos and that worked fine.
g. When step 6 is done, you should be able to see the new drives in Win Explorer, plus the small folder icon on the bottom of the virtual session.

Hope this helps save someone some time and hassle.

Thanks to all the others who posted to this thread.

---

### Post by rany on 2010-01-04
> **He|iX said:**
> How do you mount the windows share in ubuntu if ubuntu is the VM?
i have the same problem, so far i could view the shared folder from win xp(the host) on ubuntu (guest) but i cant get full access ,eg. acant save any files on it or delete 
,,,
all u need to do is on vm ,when ubuntu is turned off(vm is off) goto option ,u will see 2 tabs,devices and options
under options , the 3rd row says shared files(disabled) double click on it and enable it 
then after u power on in network under places in ubuntu u suppose to see it , but it seems that is not enough cos u will need also to install vmtools , u can find alot of posts to install it and THE MOST IMPORTANT HINT U MUST 1ST LOG IN AS ROOT NOT AS REGULER USER TO UBUNTU WHEN U START TO INSTALL IT
most of this posts dont mention that ,then u get problems, if u need more details fellow up and i will do my best
still my problem cant edit or save any files on the shared folders, still trying

---

### Post by nortexoid on 2010-01-06
> **utnubu001 said:**
> i have an ubuntu system, with another ubuntu system in VirtualBox.
I shared my /media directory through virtualbox so i can access my hard drives..
How do i access the shared folder inside virtualbox?

I have the same question and nothing here has solved it. I'm running Kubuntu 9.10 inside Ubuntu 9.10 and I've selected folders to share, but I don't know how to access them in Kubuntu. It's as easy as pie in my XP host!

UPDATE: I found the solution here: [http://www.google.co.uk/url?q=http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/&ei=PsZES8icBY2s4QbZxcWqCA&sa=X&oi=spellmeleon_result&resnum=1&ct=result&ved=0CAcQhgIwAA&usg=AFQjCNGqrUqddKhOBm3KXKGEleLaaadSCw](http://www.google.co.uk/url?q=http://www.giannistsakiris.com/index.php/2008/04/09/virtualbox-access-windows-host-shared-folders-from-ubuntu-guest/&ei=PsZES8icBY2s4QbZxcWqCA&sa=X&oi=spellmeleon_result&resnum=1&ct=result&ved=0CAcQhgIwAA&usg=AFQjCNGqrUqddKhOBm3KXKGEleLaaadSCw)

---

### Post by sync00 on 2010-02-15
> **joebeasley said:**
> After installing the additions on the ubuntu guest, start the services. (/etc/init.d/vboxadd start)  Then mount with mount -t vboxsf sharename /mountpoint.
Is it possible to do this without using Terminal?

---

### Post by bodhi.zazen on 2010-02-15
> **sync00 said:**
> Is it possible to do this without using Terminal?

If you add an entry to fstab it should automatically mount.

---

### Post by smuwanga on 2010-03-13
Hey man, 

-After installing those networking addins so to speak, go into your Guest OS, like Windows Vista.

-Click on the start menu, navigate to Computer and  Right-Click .
-You should see a quick-menu. Click on ***Map Network Drive***
-type the following
   \\vboxsrv\*NameOfSharedFolder*
For instance, if Shared Desktop (/Users/username/Desktop) then use
In Windows Vista, Map Network Drive Z: to \\vboxsrv\Desktop

It worked for me.
I picked the solution from [http://www.ideaexcursion.com/2009/01/15/windows-7-in-virtualbox-shared-folders-workaround/](http://www.ideaexcursion.com/2009/01/15/windows-7-in-virtualbox-shared-folders-workaround/) 
Simon.

---

### Post by carra on 2010-04-19
> **frankieus said:**
> Use the "Add Network Place Wizard" in Windows. Follow the wizard and look for you shared folder, add it and you're done. ;)

Frankieus' hint did the trick for me!

---

### Post by TheFu on 2010-04-20
VirtualBox has a way to share host file directories with client VMs. Under Windows, it is fairly intuitive. Under Linux client OSes, the steps are less than clear. I don’t know whether they are documented in the users guide or not. I don’t recall it however.
 
[LIST=1]
[*]Load the Client OS Extensions.
[*]In Linux Client VM, verify that `lsmod | grep vbox` shows the vboxfs module.
[*]Host: Configure the extension to export a directory – I told it to share d:\Data from my Win7-x64 host as “Data”
[*]Client: sudo mount -t vboxsf Data /Data   – yes, the device is just the plain “Data” and it doesn’t show up in /dev like it should.
[/LIST]
 Run that last command and **BAM, it mounted**.  I updated the /etc/fstab with the necessary info, dismounted the drive and ran `mount -a` to test it.  [B]Joy.  The hardest part was learning that vbox doesn't honor the /dev/ directories for the device and  that the device name isn't intuitively named (the last 2 characters seem backwards to me).
[/B]

This worked for VirtualBox v2.0.4 - v3.x.

---

### Post by frncz on 2010-04-20
> **StuipedandUgly said:**
> here's a quick guide
1. start up virtual box then start up xp
2. go to the top panel click Devices-->Install Guest Editions
3. Download and install Guest Editions
4. Set up your shared folders in virtual box. Example share folder home/Crimthinc
5. start up windows go to Start-->Run enter cmd and press enter
6. once in the dos console deal type net use t: \\vboxsvr\Crimethinc(only put in the last folders name on the end of the command for example if you selected a folder under home/Crimthinc/music the command would be  net use t: \\vboxsvr\music)

This should work this is exactly what i did to get mine working its surprising how frustrated I got figuring this out

Many thanks StuipedandUgly. Worked fine

Mike

---

### Post by CeltaWeb on 2010-05-02
> **joebeasley said:**
> After installing the additions on the ubuntu guest, start the services. (/etc/init.d/vboxadd start)  Then mount with mount -t vboxsf sharename /mountpoint.

Thanks for this i needed to know the mount prefix of vboxsf to mount the drive in Linux.

---

### Post by uhappo on 2010-06-24
> **mad-bee:) said:**
> -first **Install Guest Additions**.It is under the **Devices** menu on **VirtualBox**
-add which folder you want to share from **Shared Folders** option on **Virtualbox**
-open **My Network Places** on **XP** click to **View** **workgroup** **computers**
           (it can be different if you changed the default network name)
-look down to links with the header **Other Places**
-you will see **Microsoft Windows Network**.Click it
-you will see the **Entire Network** link and click it
-look at the page you will see **VirtualBox Shared Folder** 
:)
it was easy :)

THANKS ALOT!!! So easy with this method

---

### Post by quatrecouleurs on 2010-07-22
Far more simple is that solution : 
[https://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/](https://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/)
Just select the folder in the virtualbox shared folders settings dialog box, then use the windows explorer to navigate to browse to entire network > VirtualBox shared folders > \\Vboxsvr > then you can expand all your previously configured shared folders here.

---

### Post by goltoof on 2010-08-19
>> Added shared folder "home\me\localhost"
>> installed guest additions / restarted 
>> mapped the shared folder "\\vboxsvr\localhost" as a network drive.

Presto.

---

### Post by michalurban on 2011-09-12
I know its been a while but (after being unable to make EOS Utility to use the network share, even if it was mounted) I finally ended up with another solution - my netbook I use when controlling the camera in the field is running WinXP, EOSutil saves pictures within the guest machine and after finishing the work, I have a .bat file moving the photos to the host machine. Not charming, but it works ...

---

