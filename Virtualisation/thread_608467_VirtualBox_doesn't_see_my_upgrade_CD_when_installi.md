---
title: "VirtualBox doesn't see my upgrade CD when installing Win2k"
date: 2007-11-10
forum: Virtualisation
---

### Post by timzak on 2007-11-10
I just started installing Windows2000 through VirtualBox and all was going well until it asked me to insert my Windows98 CD (Win2000 is an upgrade version).  The Win2000 installer doesn't recognize the Win98 CD.  I've tried repeatedly, and tried a Win95 CD as well (it's a legitimate option to use with Win2000 upgrade) and got the same non-response with the Win95 CD.

Any suggestions?

---

### Post by viking777 on 2007-11-10
Do you have a W2000 vm window?

If you do click on 'Devices | MountCD/DVD Rom | Host Drive and see if that helps.

If you haven't got as far as having a vm window I probably can't help you.

---

### Post by timzak on 2007-11-10
viking,

Yes, I have a vm window.  I am installing Win2000 in it, I see the install process and I get stuck when it asks me for a Win98 CD to prove I have a good reason to be using an upgrade CD instead of a full version.  For some reason, it doesn't recognize my Win98 CD, even though Ubuntu does (it pops open a Nautilus window with the CDs contents when the Win2000 vm installation asks me to insert it).

Thanks.

---

### Post by timzak on 2007-11-11
Okay, now I am trying to install Win98 first, then upgrade to Win2000, to bypass this problem.  My new problem is Win98 requires a boot floppy to install and VirtualBox is not recognizing my boot floppy (it works outside the VM).  I set VirtualBox to boot from the floppy first, but it's not accessing the floppy drive.  So I can't seem to install either Win98 or Win2k.  

Any ideas?

---

### Post by viking777 on 2007-11-12
Sorry, but I can only repeat what I said above.

If I want to change cd's when using a vm I first click 'Devices | Unmount CD rom' then eject the cd and then click 'Devices | Mount CDrom | Host Device' 

One other thing that worries me though is that you said that Nautilus pops up a window with the contents of the cd, which obviously means that it has mounted the cd. I use kde which does not behave in this way, when I pop in a cd it opens a dialog box which asks what you want to do with the cd. One option is to display its contents, another option is to 'Do Nothing'. I always choose the latter since I don't think that the same cd can be mounted in a host and guest machine at the same time (though I may be wrong I am only a noob at this myself). 

Is there a way you can prevent Nautilus from mounting your Win98 cd when you insert it (holding down shift key  might work) and then mounting it in the guest vm?

---

### Post by timzak on 2007-11-12
viking,

I just want to make sure I'm understanding you correctly.  Are you talking about mounting/unmounting the CD drive in VirtualBox, or in Ubuntu?

I ask because in VirtualBox (I'm using 1.5.2) there is no "Devices" menu.  I think it's called "Settings" and I'm not sure if you're talking about that or something else.

Your theory sounds very plausible.  I will check it out (I'm not sure how to disable automatic mounting of CDs either).

Thanks for your help.

---

### Post by viking777 on 2007-11-14
> **timzak said:**
> viking,

I just want to make sure I'm understanding you correctly.  Are you talking about mounting/unmounting the CD drive in VirtualBox, or in Ubuntu?

I ask because in VirtualBox (I'm using 1.5.2) there is no "Devices" menu.  I think it's called "Settings" and I'm not sure if you're talking about that or something else.

Your theory sounds very plausible.  I will check it out (I'm not sure how to disable automatic mounting of CDs either).

Thanks for your help.

No I was talking about mounting/unmounting  in virtualbox (although as I speculated before I don't think you can have a cd mounted in both at the same time).

If you go back to the first post I made you will notice that the first thing I asked is 'Do you have a w2000 vm window'. If you don't have that window you wont have the 'devices' menu and it seems you dont which is probably why my instructions don't make sense.

The 'Settings' menu that you refer to is on the Virtualbox program window but not on the 'virtual machine' window - unless of course you are using a different version to mine with a different layout. Mine is version 1.5.2

---

### Post by wolf.b on 2007-11-14
Until someone posts clear instructions how to unmount a CD correctly let me add my two cents: I have had similar problems and this worked for me:
I closed the filemanager that shows the newly inserted CDROM.
I opened a terminal window with root priviledges, admin priviledges were not enough.
I entered something like: unmount /media/cdrom0
 After that VirtualBox recognized the change of CD.
All this is written from memory, written by a new linux user, and may help to point in the right direction and it may even be sufficient for you to continue setting up Win2000.

I don't know about Win2k upgrade but Win98 upgrade disk was satisfied when I pointed it to the location of a file called setup.exe. That particular file was copied on its own from the Win95 CD to a folder on a floppy disk. This is not the answer to your question, but if you find a way to copy your setup.exe from the Win98 CD into a location that is accessible when the WIN2000 installer asks for it, who knows ... I don't think the installer will verify the entire Win98 CD, it just checks for the existence of some file or other. Maybe it is worth a try. It did work for me in a completely different situation (Win95 to Win98 ).

Please forgive me for posting a suggestion of a workaround, I realize this is not what you asked for.


Greetings
Wolf

---

### Post by timzak on 2007-11-15
Wolf and Viking:

Thanks both for your help.  I haven't had a chance yet to try your suggestions, but I appreciate both of them.  Wolf, I'm not picky about the help that is offered here.  I appreciate it all.  Thanks again.  I'll report back when I have a chance to try out these things.  I think once I get Win2k installed, I'll be fine.  It's just getting past this installation hump that's kicking my butt.  

Regards,

---

### Post by timzak on 2007-11-17
Viking,

You were right all along.  For some reason I wasn't making the mental connection about the W2000 VM window.  Now that I realize what you're talking about (you explained it well, I was just having a brain freeze), it did work to unmount/mount from the Devices dropdown menu.  I got past the compliance check and am now installing the OS.  :guitar:

Thanks again.  Hopefully the rest of the installation goes smoothly and I don't have to come back for more help.  :)

---

### Post by viking777 on 2007-11-19
> **timzak said:**
> Viking,

You were right all along.  For some reason I wasn't making the mental connection about the W2000 VM window.  Now that I realize what you're talking about (you explained it well, I was just having a brain freeze), it did work to unmount/mount from the Devices dropdown menu.  I got past the compliance check and am now installing the OS.  :guitar:

Thanks again.  Hopefully the rest of the installation goes smoothly and I don't have to come back for more help.  :)

Great news timzak - glad I could help,

---

