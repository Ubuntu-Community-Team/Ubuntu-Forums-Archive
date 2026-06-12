---
title: "virtualbox usb printer greyed out other usb ok"
date: 2009-10-24
forum: Virtualisation
---

### Post by curracruisers on 2009-10-24
virtualbox usb printer greyed out but other usb devices ok, VB user permissions  ok, when printer is unplugged it leaves the usb list in VB and comes back when plugged in but is greyed out and not detected by windows. It is like this even before Windows starts. In VB "setting" the printer is there and not greyed out until the guest is started.

Any ideas????

Ububtu 9.10 beta (host)
VirtualBox 3.0.8
Windows 7 (guest)

---

### Post by Cybie257 on 2009-10-24
I'm having the exact Opposite issue. Printer works find, nothing else does, even though I set the filter(s) and it is listed (greyed out) of my list of USB devices via VirtualBox

-Cybie

---

### Post by rliegh on 2009-10-24
I'm using 3.0.8 on 9.04/i386 and I can't attatch any sort of USB device.

---

### Post by Aviendha09 on 2009-10-29
Same here with printer. winxp guest, host: karmic, latest VB.

---

### Post by B00R4dL3y on 2009-10-31
+1 here

Other USB devices show up in the list - usb printer is greyed out.  Tried my VM (Windows XP) on two computers (Ubuntu 9.10 and VB 3.0.10) and the same thing.

---

### Post by Aviendha09 on 2009-10-31
?? Has anyone tried (with a more powerful computer than mine) to install a virtual machine inside a virtual guest....?   Hmmmmmm.... :-\"

---

### Post by alexfish on 2009-10-31
> **B00R4dL3y said:**
> +1 here

Other USB devices show up in the list - usb printer is greyed out.  Tried my VM (Windows XP) on two computers (Ubuntu 9.10 and VB 3.0.10) and the same thing.

Go to system users and groups
 unlock
 
click manage groups

find vboxusers  its near the bottom list

click vboxusers
click properties

if you see your self 

tick the box

DONT repeat dont tick ROOT

---

### Post by Aviendha09 on 2009-10-31
hmmmmm...didn't work...

---

### Post by fjf on 2009-10-31
Same problem here...Karmic amd64 and usb printer unusable im an XP guest...

---

### Post by vttay03 on 2009-11-01
+1 here - had this working fine in 9.04 but when I upgraded to 9.10 and setup VirtualBox my printer appeared greyed out :(

---

### Post by anowis on 2009-11-01
For me
VBOX_USB=USBFS VirtualBox
helped.

I guess that's not the best solution, but it may work until they fix this (to me seems to be a 3.0.8-problem)

Good luck

---

### Post by mattydee on 2009-11-01
Same problem here using Karmic + vbox 3.0.10

Usb devices are all recognized but the usb printer remains greyed out.

Maybe a problem with the karmic kernel drivers? vbox 3.0.10 works fine in Slackware.

---

### Post by mattydee on 2009-11-01
> **anowis said:**
> For me
VBOX_USB=USBFS VirtualBox
helped.

I guess that's not the best solution, but it may work until they fix this (to me seems to be a 3.0.8-problem)

Good luck

Didn't work for me...

---

### Post by vttay03 on 2009-11-01
> 
For me
VBOX_USB=USBFS VirtualBox
helped.

I guess that's not the best solution, but it may work until they fix this (to me seems to be a 3.0.8-problem)

Good luck 


I couldn't get this to work for me either...sounded promising enough.  Oh well...

---

### Post by mattydee on 2009-11-02
Hmmm... nobody mentioned the printer in question they were using.

Mine is the Brother MFC-3100c

---

### Post by mattydee on 2009-11-02
AHA!!! 

I just ran virtualbox as root and the usb printer is detected. So it must be a permissions issue! Trying to figure it out now...

---

### Post by mattydee on 2009-11-02
Got it:

add yourselves to the "lp" group. Not sure why...

---

### Post by sigdrifa on 2009-11-02
> **mattydee said:**
> Got it:

add yourselves to the "lp" group. Not sure why...

Same problem here, the above didn't work for me.

I have this problem on the desktop with a Canon IP 3300 since the Karmic upgrade. On the laptop I use an HP Photosmart a636, which works fine even after the upgrade.

Like some of the other posters in this thread said, all other USB devices (e.g. a Canon scanner) work just fine.

On the desktop where I have that problem I'm running VirtualBox 3.0.10-54097_Ubuntu_karmic.

---

### Post by vttay03 on 2009-11-02
> 
Got it:

add yourselves to the "lp" group. Not sure why...


Sweeeet!  This working for me as well.  One note - logout and log back in for the change to take effect.  The printer will still be greyed out if you attempt to fire up virtualbox right after you make the change during the same session.

---

### Post by mattydee on 2009-11-02
> **sigdrifa said:**
> Same problem here, the above didn't work for me.

I have this problem on the desktop with a Canon IP 3300 since the Karmic upgrade. On the laptop I use an HP Photosmart a636, which works fine even after the upgrade.

Like some of the other posters in this thread said, all other USB devices (e.g. a Canon scanner) work just fine.

On the desktop where I have that problem I'm running VirtualBox 3.0.10-54097_Ubuntu_karmic.

Make sure to log out and back in for group changes to take effect. If that still doesn't solve it, try to run VirtualBox as root to see if its a permissions issue. 
```
sudo VirtualBox
```

If root can access the printer, then its a perms issue so you have to 

a) find out which group your user needs to be part of 
or
b) modify the appropriate udev rules to allow users to access it.

---

### Post by Aviendha09 on 2009-11-02
> **mattydee said:**
> Got it:

add yourselves to the "lp" group. Not sure why...

Hehe! Working for me too! Thx!

---

### Post by thepisu on 2009-11-03
> **mattydee said:**
> Got it:

add yourselves to the "lp" group. Not sure why...

Worked also for me!!  The command is: 

sudo usermod -a lp stefano

I had also to logoff and logon on my GNOME session.

I think this is because, the usb printer device is mapped here in /dev/usb/lp0, and this node has owner "root" and group "lp", and permissions only for user and group.

---

### Post by mattydee on 2009-11-03
> **thepisu said:**
> 
I think this is because, the usb printer device is mapped here in /dev/usb/lp0, and this node has owner "root" and group "lp", and permissions only for user and group.

Hmm... I found this:
[http://ubuntuforums.org/showthread.php?t=192800](http://ubuntuforums.org/showthread.php?t=192800)

So it seems that Karmic thinks our usb printers are line printers (parallel port)... weird.

---

### Post by B00R4dL3y on 2009-11-05
Adding myself to the lp group and re-logging back in worked for me as well.  Thanks.\\:D/

---

### Post by danni-la on 2009-11-08
Thanks mattydee worked for me too! :D

---

### Post by Jim_in_Germany on 2009-11-12
Worked for me too. Thanks!!
> 
The command is:
sudo usermod -a lp stefano

However, I had to use: > sudo usermod -a **-G** lp jim

---

### Post by welshmike on 2009-11-12
> **mattydee said:**
> Got it:

add yourselves to the "lp" group. Not sure why...

Many, many thanks mattydee.:KS That got my Canon IP2600 printer working.
One more step away from having to dual boot XP & Ubuntu.

---

### Post by leifjonny on 2009-11-14
> **alexfish said:**
> Go to system users and groups
 unlock
 
click manage groups

find vboxusers  its near the bottom list

click vboxusers
click properties

if you see your self 

tick the box

DONT repeat dont tick ROOT

This works for me, but I had to log out and in again. The usb devices are no longer greyed and I can use them.

---

### Post by alexfish on 2009-11-15
are you the only user  + in virtual box you have to enable the usb devices prior to booting any virtual device.  then when its running check the boxes of the devices you require. at the bottom of the window it will show any active device it will be interesting to know the results

---

### Post by agitdd99 on 2009-11-21
> **mattydee said:**
> AHA!!! 

I just ran virtualbox as root and the usb printer is detected. So it must be a permissions issue! Trying to figure it out now...

I follow your hints, and you're right!
this is what i did and it works! :
1. Press Alt+F2 and type "VirtualBox".
2. add "sudo" before "VirtualBox" and tick the "run in terminal" option. Press Enter. you will prompt for administrator password.
3. for the first time there will be registration procedure. follow the instructions.
4. make your own VirtualBox OS. and the printer just run perfectly.

I don't know what are the consequences of running application like this. please let me know.

update: i haven't try the other solution as written above. but i will try it.

---

### Post by DXM31 on 2009-11-22
I've added myself to lp, registered VirtualBox restarted a few times, and I don't have a group called vboxusers??
Anyway, I am running the same versions of Ubuntu and VB as others on this thread.
Except I am running Windows 7 and trying to us a USB TV tuner that has no drivers for Linux.
I also have a mouse and bluetooth hooked up to USB and like others the mouse works, don't know about bluetooth.
So is there a definite solution?

---

### Post by michaelaly on 2009-11-22
Adding myself to the lp group worked perfectly. Thanks.

---

### Post by mattydee on 2009-11-22
> **DXM31 said:**
> I've added myself to lp, registered VirtualBox restarted a few times, and I don't have a group called vboxusers??
Anyway, I am running the same versions of Ubuntu and VB as others on this thread.
Except I am running Windows 7 and trying to us a USB TV tuner that has no drivers for Linux.
I also have a mouse and bluetooth hooked up to USB and like others the mouse works, don't know about bluetooth.
So is there a definite solution?

Adding yourself to the lp group probably won't make a difference since it's for usb printers. It sounds like your problem lies with the fact that you don't have a vboxusers group that you need to add yourself to. 

Try to reconfigure/re-install VB. Also, are you using the open source edition? AFAIK the OSE doesn't support usb devices, you need to download the non-OSE from the virtualbox website.

Also keep in mind the when you add yourself to a group, you need log out and back into ubuntu for the changes to take effect.

---

### Post by mattydee on 2009-11-22
> **agitdd99 said:**
> I follow your hints, and you're right!
this is what i did and it works! :
1. Press Alt+F2 and type "VirtualBox".
2. add "sudo" before "VirtualBox" and tick the "run in terminal" option. Press Enter. you will prompt for administrator password.
3. for the first time there will be registration procedure. follow the instructions.
4. make your own VirtualBox OS. and the printer just run perfectly.

I don't know what are the consequences of running application like this. please let me know.

update: i haven't try the other solution as written above. but i will try it.

Running as root was only for testing purposes. It is strongly advised not to run user applications as root, so adding your self to the proper group (vboxusers + lp) is the recommended solution. 

The consequences are that if something goes wrong with the application (either a bug or exploit) it can possibly affect your whole system. An application running as a normal user on the other hand, can only affect what in is the user's home folder (usually... depending on how the system is configured).

---

### Post by curracruisers on 2009-11-23
This worked for me as well although, just adding a user did not complete the job, using the -G (to the group) option did. When the user was add to the group that user was not automaticlly active in the group for some reason even after log out and in. So I suppose it is still a bug needing to be fixed. Thanks all.

---

### Post by DXM31 on 2009-11-23
> **curracruisers said:**
> This worked for me as well although, just adding a user did not complete the job, using the -G (to the group) option did. When the user was add to the group that user was not automaticlly active in the group for some reason even after log out and in. So I suppose it is still a bug needing to be fixed. Thanks all.

What is the -G(to the group)?? I guess I need to reread the thread.
Too I reinstalled VB from a DEB so now I have the user group.
Maybe the -G is the thing left to do.

The good new is I gots USB so even though I wasn't trying to hook up a printer, I was able to get my non-Linux supported USB TVtuner to work, sort of, not enough memory to run it with 2 OS's...Rats

---

### Post by Portable_Jim on 2009-11-30
I needed to

[LIST]
[*]Make sure I was part of the vbox group, and root was not.
[*]make sure I was part of the lp group.
[/LIST]
This is not a bug that is created but a bug that is fixed.
For example...
Say I locked down a computer so that only certain users could print (by being part of the LP group), but any user could use Virtualbox. Before this version, any user could just create a VM and then be able to print. Now, only specified users can use the printer in or out of Virtualbox.

---

### Post by dinklyink on 2009-12-02
> **alexfish said:**
> Go to system users and groups
 unlock
 
click manage groups

find vboxusers  its near the bottom list

click vboxusers
click properties

if you see your self 

tick the box

DONT repeat dont tick ROOT

Thanks Alexfish

This worked a treat. Naturally, one must log out and then back in for the changes to work.

Nice one l8erz

---

### Post by bmc5311 on 2009-12-27
> **mattydee said:**
> Got it:

add yourselves to the "lp" group. Not sure why...

excellent!  worked for me (running debian squeeze).  thanks  :)

---

### Post by Phil Doomen on 2010-03-01
I am having the same problem both on home PC and Canon printer and work laptop with Brother printer.  Different printers but both running 9.10. Both printers are greyed out in USB device list.  Did this ever get resolved?

---

### Post by welshmike on 2010-03-02
Please see my reply dated November 12th, 2009 :


Quote:
Originally Posted by mattydee View Post
Got it:

**add yourselves to the "lp" group**. Not sure why...
EndQuote

Many, many thanks mattydee. That got my Canon IP2600 printer working.

---

### Post by smilingfrog on 2010-03-18
Success!
user must be a member of both virtualbox and lp in order to use a usb printer.
Thanks

---

### Post by CiaoCiao on 2010-04-13
Added myself as a user to lp and fixed it!  Thanks all!

---

### Post by RottNKorpse on 2010-04-20
> **mattydee said:**
> Got it:

add yourselves to the "lp" group. Not sure why...
Worked like a charm...and thank you very much!

I have a relative that is using an old printer with a parrallel port and they upgraded their computer and of course no more parallel ports. So I had to think of a way to get it working...so I bought an adapter and turns out the printer doesn't have drivers for Linux (of course) but also not even Windows 7 so I needed to make it work and the only way I could think of was in a XP VM...which thanks to your efforts of finding out the ip issue...now works so I can run this really old printer just fine now. Thanks again.

---

### Post by konsty on 2010-05-31
> **mattydee said:**
> so adding your self to the proper group (vboxusers + lp) is the recommended solution. 


+1!
Worked for me, thanks

---

### Post by bayvista on 2010-06-17
Same problem with Lucid.

---

### Post by MrVas on 2010-07-11
+1 to adding user id to vboxusers group.  I had a similar issue with 64-bit Lucid Lynx (10.04) as host and USB devices being grayed out.  Added my uid to the vboxusers group (/etc/groups) and restarted my system to resolve this issue.

More here:

[http://forums.virtualbox.org/viewtopic.php?f=7&t=30219](http://forums.virtualbox.org/viewtopic.php?f=7&t=30219)

Vas

---

### Post by KMilburn on 2010-07-13
I had the same problem, however I found a simple solution.

Edit cups.
   /etc/cups/cupsd.conf
The 7th line from the top remove the # so that it reads:
Enable printer sharing and shared printers

Following this correction I started WinXP in VB and the USB was found.  Previous attempts of installation did not have the driver, but the new installation (copy 1) works.

---

### Post by Suncoaster on 2010-10-16
Many, many thanks mattydee, that also got my Canon Pixma IP6600D working also.:guitar:  Thats what I like about these forums the knowledge base is great.

Dave

---

### Post by mattydee on 2010-10-17
I'm still getting thanked for this almost a year later! Glad to see I've help so many people! Your all welcome :D

---

### Post by RottNKorpse on 2010-10-22
> **mattydee said:**
> I'm still getting thanked for this almost a year later! Glad to see I've help so many people! Your all welcome :D
thanks again as it helped me once more because I was removed from the lp group for some reason when I upgraded to 10.10 - so thanks again.

---

### Post by xile_ on 2010-11-21
Virtualbox 3.2.10
Host: Ubuntu 10.10
Guest OS: WinXP SP3

Tried adding my user to the lp and the vboxusers groups, unfortunately no luck.

However running Virtualbox as root did the trick - so I can confirm that this is a permission issue.

---

### Post by mattydee on 2010-11-21
> **xile_ said:**
> Virtualbox 3.2.10
Host: Ubuntu 10.10
Guest OS: WinXP SP3

Tried adding my user to the lp and the vboxusers groups, unfortunately no luck.

However running Virtualbox as root did the trick - so I can confirm that this is a permission issue.

Did you make sure to log out and back in again? You need to do that when adding yourself to groups before they take effect.

---

### Post by RottNKorpse on 2010-11-21
> **mattydee said:**
> Did you make sure to log out and back in again? You need to do that when adding yourself to groups before they take effect.
yea that is what most people forget to do...come to think of it I am pretty sure I did that the first time I started with this issue.

---

### Post by xile_ on 2010-11-22
> **mattydee said:**
> Did you make sure to log out and back in again? You need to do that when adding yourself to groups before they take effect.

Did remember to log out, and then in again.
However, it still did not have the intended effect... BUT...
A day later, when I had shutdown the computer, and tried again, everything worked like a charm - however, by that time, I had already exported the virtual machine and imported in Virtualbox when logged in as root - but for the sake of argument - adding yourself to the vboxuser and lp group DOES solve the problem.

Once again, thanks mayttydee ;)

---

### Post by Diametric on 2010-11-24
This thread FINALLY answered my question - to get USB to work I ran VirtualBox from sudo.  thanks!

---

### Post by misanthropist on 2011-05-14
Adding the FUSE group to my permissions seemed to fix the problem for me (at least I think that was what did it).

---

