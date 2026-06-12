---
title: "Can't access DVD drive in Win 7 under Kubuntu/VB"
date: 2014-10-19
forum: Virtualisation
---

### Post by Tom_ZeCat on 2014-10-19
Linux doesn't quite have all the DVD software that I want, so I want to use a few Windows programs.  I therefore have Windows 7 installed to run under VirtualBox.  However, in Win 7, I'm unable to access my physical DVD drive.  I've been googling around, but have yet to find a solution.  The consensus in the links I found in Google was that I needed to go to Settings ==> Storage ==> Controller IDE and then add my DVD drive there.  However, I've been unable to do so.  Here's a screen shot: 

[[img]http://s20.postimg.org/m1byskq99/Virtual_Box_DVD.png[/img]](http://postimage.org/)
[image upload](http://postimage.org/)

The Windows 2000 iso is there probably because I've also installed Windows 2000 under VirtualBox.  (Long story -- need to run some really old software.)

Anyway, when I click on that icon for adding my DVD drive, the menu comes up and shows all my external hard drives and thumb drives, but not my DVD drive -- if I have no DVD in the drive.  If I put a DVD in the drive, then the drive shows, but it doesn't get added when I select it.  What am I missing here?  

I can delete the Win 2K ISO if necessary.  It's already installed and running.

---

### Post by ajgreeny on 2014-10-19
I note there are some invalid user settings detected in your VM which you should put right.  I don't know if that will help with your problem, never having used a CD or DVD in any of my VMs, but it probably needs addressing in any case.

You may also find that installing the VBox Guest Additions which you can get from [Downloads &#8211; Oracle VM VirtualBox]("https://www.virtualbox.org/wiki/Downloads") will help with the problem.

---

### Post by TheFu on 2014-10-19
Actually, passing through the physical DVD from the hostOS is managed on the virtualbox popup menu from inside the running VM.  Something like "mount host CD/DVD drive" is the option. I vaguely recall that menu being in the top/center of the guestOS machine (when full-screen).  When not full-screen, it is under "Devices --> CD/DVD --> Host drive X:"

Or are you trying to boot off a DVD?  That is handled the way the OP spells out - through the storage menu **before** booting the OS from the optical media.  It may be easier to create an ISO from the media, then connect that to the guestOS VM instead.  I've done this a few times for MSFT stuff.

Is that not working or did I miss the point (again) completely?

---

### Post by Tom_ZeCat on 2014-10-19
> **TheFu said:**
> Actually, passing through the physical DVD from the hostOS is managed on the virtualbox popup menu from inside the running VM.  Something like "mount host CD/DVD drive" is the option. I vaguely recall that menu being in the top/center of the guestOS machine (when full-screen).  When not full-screen, it is under "Devices --> CD/DVD --> Host drive X:"

Or are you trying to boot off a DVD?  That is handled the way the OP spells out - through the storage menu **before** booting the OS from the optical media.  It may be easier to create an ISO from the media, then connect that to the guestOS VM instead.  I've done this a few times for MSFT stuff.

Is that not working or did I miss the point (again) completely?

You understood.  I'm not trying to boot to a DVD.  I'm trying to access one from within Windows 7.  I have sometimes used ISOs as you suggest.  That does work, but I'll be accessing a lot of physical DVD disks, and things would move along a lot more quickly if I could work with them directly in the Windows software.  

I'm going to try your suggestions now.  Thanks.

Edit: We're in business!  I was just able to access my DVD drive.  Thanks to everyone for their help.

---

### Post by ajgreeny on 2014-10-19
So, what was it that solved the problem?

---

