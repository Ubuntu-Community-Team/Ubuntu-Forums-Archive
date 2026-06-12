---
title: "Initial Setup and Config of fresh Install"
date: 2007-07-03
forum: Ubuntu Christian Edition
---

### Post by TravMan63 on 2007-07-03
hmmm me thinks might be a good idea for a sticky?:KS

Here's what I have going...
Just installed 7.04 CE on son #2 laptop.  Install was very quick - about 15 minutes.:D

I removed :
the administrator privileges (from users and group gui?) for his account
removed boot-ability from all devices other than HD.
password protected BIOS/CMOS

Changed the password for root

I think that should lock things down pretty tightly, but there's probably a few more items to address.

Q1 - isn't IE4S a hole that can bypass Dansguardian?

--Then - part 2...
I read in another post that the 1st user is automatically assigned as root.  Um, well ok - but I demoted that user.  (Would be good idea to mention that in setup...(that root user is being created)) (used method mentioned above)

Now I need to either create another user as root - if possible, or learn the bash commands for all the menu items that disappeared.  (Especially add/remove and automatix - I can-do synaptic - (but that isn't as encompassing as the others... right?)

TM

---

### Post by mysticrider92 on 2007-07-03
1. There are methods of getting around Dansguardian, but as far as I know, most have been patched so they will not work.

2. I would recommend making another user instead of demoting the 1st user, but there are ways to limit the first user. You might want to make sure you can still use sudo, otherwise you could end up with problems when you need root access (e.g. updates, installing programs, fixing problems, etc.). 

Synaptic is a GUI for the Debian apt package manager, so it actually does a lot more that Automatix or Add/Remove programs. Those are easy ways to install certain things, Synaptic gives access to approximately 20,000 packages that require a bit more digging but are the same thing. 

Also, the terminal command for a program is quite often the program name. For example "sudo automatix" is the same as clicking on the icon in the Applications menu.

---

### Post by TravMan63 on 2007-07-03
Thank you mysticrider92

Yes... I suppose I can 're promote' the 1st user... (since I already demoted him - which removed many entries from menus)

I can su fine - which is 'the same' as sudo - pretty much except that you stay logged in as su...

So --- can I give 1st user a new name, and 'restore his super cow powers' ? - or is it best to leave that alone and create a new administrator account?

I've used Synaptic before - can I add the codecs from there as well?  I know there were other restricted repositories etc etc... 

hmmm - I think I tried 'sudo automatix' - and ...


...
(nothing happened)



TM

---

### Post by NeoLithium on 2007-07-03
A good guide to getting the necessary repositories and a wealth of programs, is [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  After that you'll be able to grab stuff with synaptic to your hearts content :)   As well, if you really want the GUI to deal with the administrative stuff in users and groups, you can log into gnome as the root user. However, be aware this is VERY unsecure and potentially damaging.  You can boot into recovery mode and at the command line just type: startx

Then you'll be able to go into users and groups, readd the first user to administrator and such.  Then you can just create a new user that is for your son, with something such as the desktop user privilages.

Hope this helps,

---

### Post by TravMan63 on 2007-07-03
Thanks for the additional info NeoLithium,

I KNEW there was a users guide... but it's good to be reminded of that... gonna hafta dig out my Linux books too...

I did just use synaptic - via su - sudo synaptic would not work... nor would sudo automatix (when logged in as the default user - that I 'demoted') 'user is not in the sudo users list this will be reported'. Or when pw is entered, it doesn't work.
Synaptic does - as mysticrider92 stated, require more digging.  Using add/remove or automatix allowed me to install the correct java package for Firefox to run runescape.... I installed a package - but it gave warnings when Firefox attempted to run the java applet...

I really need to learn more BASH commands anyway.  I've added users in DSL and changed passwords etc.... it's just trying to recall them (the commands)... and - speaking of BASH - all it takes is using the up arrow key... to access history etc... but I guess you need root password after that - perhaps su is, in that instance, more 'secure' than sudo application'; I'm thinking that history would be unavailable to users other than root...

I canNOT log in as the root user (I assume you mean the default log on screen) there is an error 'similar to 'root cannot log in from this screen'...

Definitely sounds like a good plan.. thanks again...

Disabling the onboard NIC would help also

TM

---

### Post by mhancoc7 on 2007-07-03
> **TravMan63 said:**
> 
Q1 - isn't IE4S a hole that can bypass Dansguardian?
TM

Yes, IEs4Linux is a way around the filter. However, the IEs4Linux Installer that comes with Ubuntu CE requires root access to install IEs4Linux. 

However, I just tested the IEs4Linux installer and there is a hole that I need to patch. I don't want to go into details, but thank you for pointing me to it.

For now I would advise you to simply remove the internet-explorer-6-ubuntu_1.7_all from synaptic.

God Bless, Jereme

---

### Post by TravMan63 on 2007-07-03
Well, I'm sure you could disable the onboard NIC -but another way would be to give that ethx device a static IP address that won't connect to the DHCP server/cable modem ... and that device (the modem) is easy to enable and disable the wireless (and it's password protected)

[http://www.slackbook.org/html/network-configuration-tcpip.html](http://www.slackbook.org/html/network-configuration-tcpip.html)

/etc/rc.d/rc.inet1.conf

I guess it's the same location for ubuntu.

Thanks for the info on the uninstall of IE Jeremy, that was my plan...

And Jeremy - thanks - for all your work on making this distro - available!
=D>

-------
me thinks this (section in particular) feels more like a 'community' every day :popcorn:
------
TM

---

### Post by NeoLithium on 2007-07-03
Well, you can't log in as root through the GDM Login Manager, however you can log in via Recovery Mode, which will take you to the command line console as root; then just type
startx
Which will bring you in to gnome, it's of course, easy to break a great deal of things, however in a pinch, it works.  To get to recovery mode, just reboot your computer, hit ESC at the grub screen and it will give you a kernel list. Then you just need to select the one with (Recovery Mode) on it, and boom; you're good.

---

### Post by mysticrider92 on 2007-07-03
> **TravMan63 said:**
> So --- can I give 1st user a new name, and 'restore his super cow powers' ? - or is it best to leave that alone and create a new administrator account?

I've used Synaptic before - can I add the codecs from there as well?  I know there were other restricted repositories etc etc... 

hmmm - I think I tried 'sudo automatix' - and ...

TM
Oops, my bad, the command is just 'automatix2' (without sudo, it will prompt for a password on its own).

It should be fairly easy to give back the user its powers, but I don't know how to do that (and my guess would probably give the user full root powers, as in without needing sudo).

---

### Post by TravMan63 on 2007-07-04
Thanks again for the input.

The config file for network isn't as stated in my previous post but here:

```
/etc/network/interfaces
```

But there's 'something fishy' about gnome and that file - I changed the IP address to static, and then gnome wouldn't start (or gedit or terminal) with the ethernet cable plugged in... but KDE would

Gnome starts if it's unplugged, then receives an IP address from DHCP - soon after I replug it...
[http://ubuntuforums.org/showthread.php?t=492100](http://ubuntuforums.org/showthread.php?t=492100)

This still relates to the setup/config - if you are wanting to limit the users to wireless access only, and disable the ability to get an IP address with the onboard NIC.

-
As far as giving back 'rights' to the intial user, installing KDE - placed all the menu items (or most of them) that were deleted when removing the rights from intial user.  However, sudo prompts for password, and doesn't accept it. 
I've tried this in terminal: su ... (root with password works) - then passwd sudo - but sudo isn't a user - must be tied to the initial user account.
>edit - I think gksu users-admin will take care of this (kde had the name in a window title)
--
At least by installing KDE, the user can browse add/remove (friendlier than synaptic) and find out what they want installed, then I can install it for them.  I would guess that could be performed in gnome as well by creating a launcher pointing to the 'add/remove' file...

--

---

### Post by TravMan63 on 2007-07-04
> It should be fairly easy to give back the user its powers, but I don't know how to do that (and my guess would probably give the user full root powers, as in without needing sudo).

Right - with gksu users-admin.  I did that... now it's lots of 'fun' because permissions and ownership of files etc are all wrong. (errors include no home folder, and can't write to .gnome_private (?) and various permission errors)

So - 'Initial setup' - keeping the 1st user as admin is better than changing it later... lots less work

(users can't log on now - had to create a home/user folder for the 1st user (changed his name to mine) - then added the second user - using the 1st users name...)

... depends on one's definition of 'fairly easy'... :)

--
edit 6:17PM
you will need to reboot in recovery mode - log on as root... and then perform a chown username * and a chown username .* in the home folder.  Also had to change (maybe I was wrong in doing this) - chmod of home folder to 766 <edit - recovery mode is needed if you want the gui - otherwise you can control alt f2 for cli...>
This enables the 1st user (actually the 2nd user - with the 1st users name) - to keep the home settings etc...

I also used a chown username -R -v - but I don't think the -R was needed ... all the files in the subdirs must have perms changed as well... I think the '.*' takes care of that

>edit 7:00 PM
the correct syntax is
```
 chown -hR username /home/username 
```
omitting the -R changed the permissions of BOTH users

---

### Post by mysticrider92 on 2007-07-04
I guess it isn't that easy after all. I have never really worried about user privleges since I am the only one who uses my Linux computer. I just use the first account I made in Ubuntu and the root account in Gentoo. I know I should make a daily user for Gentoo, but I am still getting it working how I want, and using the root account to do that is much easier.

---

### Post by TravMan63 on 2007-07-04
Hopefully it will be easier if 'when' someone else tackles this and searches for this thread and (hopefully) finds an answer.

And it IS easy - once the syntax is correct

I would also add - the new user gnome account - is not configured as the default CE - 
the panel with 3 menus is on top, sound isn't working... no gdesklets ....

--
again, thanks to mysticrider92 :KS , NeoLithium :KS  and mhancoc7 :KS... 
... remember ... it's better to teach a man to fish than to give him a fish...
(and that you did - thank you thank you)

---
sound ez fix - under user configurations - use audio devices was disabled - I may have did that with the mouse (it's a laptop and I find it selects items I'm not trying to...)

---

