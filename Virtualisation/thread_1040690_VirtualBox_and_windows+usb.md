---
title: "VirtualBox and windows+usb"
date: 2009-01-15
forum: Virtualisation
---

### Post by Stargazer989 on 2009-01-15
Hey guys, just trying to get VirtualBox to recognize USB within Windows XP... Ubuntu being the Host and Windows XP being the Guest. i need my external hard drive(via usb/firewire) and iPod to be recognized.

any suggestions ?

~Stargazer

---

### Post by HotShotDJ on 2009-01-15
Its always best to start with the Virtualization Mega-Thread at the top of the virtualization forum.

The Mega-Thread: [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)
The USB Part of The Mega-Thread: [http://ubuntuforums.org/showpost.php?p=6122145&postcount=4](http://ubuntuforums.org/showpost.php?p=6122145&postcount=4)
The VirtualBox USB HowTo referenced in The Mega-Thread: [http://ubuntuforums.org/showthread.php?t=1015763](http://ubuntuforums.org/showthread.php?t=1015763)

NOTE:  There are some people who are giving obsolete advise regarding editing /etc/init.d/mountdevsubfs.sh -- don't try to edit this file.  It is at best unnecessary and at worse may make things worse.

---

### Post by binbash on 2009-01-16
> **HotShotDJ said:**
> Its always best to start with the Visualization Mega-Thread at the top of the visualization forum.

The Mega-Thread: [http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)
The USB Part of The Mega-Thread: [http://ubuntuforums.org/showpost.php?p=6122145&postcount=4](http://ubuntuforums.org/showpost.php?p=6122145&postcount=4)
The VirtualBox USB HowTo referenced in The Mega-Thread: [http://ubuntuforums.org/showthread.php?t=1015763](http://ubuntuforums.org/showthread.php?t=1015763)

NOTE:  There are some people who are giving obsolete advise regarding editing /etc/init.d/mountdevsubfs.sh -- don't try to edit this file.  It is at best unnecessary and at worse may make things worse.

THanks for the link, it helped me a lot.

---

### Post by Stargazer989 on 2009-01-16
that didn't help me. :<
XP is still not seeing my iPod or External Hard Drive.

---

### Post by HotShotDJ on 2009-01-16
> **Stargazer989 said:**
> that didn't help me. :<
XP is still not seeing my iPod or External Hard Drive.Ok... let's see what we can do.  First of all, did you install the PUEL version in the manner described in my HowTo?  Did you enable USB Support in the manner described in my HowTo?

If so, start VirtualBox and your Guest OS.  Once the guest has booted up, make sure it is NOT in full screen mode (Right-Ctrl+F to get it back into windowed mode, if necessary).  You will see a series of icons in the lower-right portion of the windows.  Click on the icon that looks like a USB plug.  Left-Click on it to see the list of USB devices attached and detected. (EDIT: You can also access this menu through the Devices menu at the top of your VM windows.. Devices --> USB Devices.) You should see the Harddrive and/or iPod listed.  If not, let me know and we can continue to debug.

If the device is listed, click on it to mount it in VirtualBox. It should now be accessible via "My Computer" (XP) or "Computer" (Vista). DO NOT select any USB Keyboard or USB Mouse.  This will result in erratic keyboard and/or mouse behavior.

---

### Post by Stargazer989 on 2009-01-17
I did everything that was in the USB section of the 'HowTo' that i was linked to by you. here's a screeny: [*click*]("http://adam.pcriot.com/r/no_usb.png")


*** EDIT: get this: [Devices are greyed out]("http://adam.pcriot.com/r/usb_devices.png")

---

### Post by HotShotDJ on 2009-01-17
> **Stargazer989 said:**
> I did everything that was in the USB section of the 'HowTo' that i was linked to by you. here's a screeny I looked at the screenshot.  I'm nearly certain that it is a permission problem with USB access for the user.  Please post the contents of your /etc/fstab file.

---

### Post by Stargazer989 on 2009-01-17
fstab is [*here*]("http://paste.stirk.org/49340").

---

### Post by albinootje on 2009-01-17
> **Stargazer989 said:**
> fstab is [*here*]("http://paste.stirk.org/49340").

And the output of :
```

mount

```
please.

---

### Post by HotShotDJ on 2009-01-17
> **Stargazer989 said:**
> fstab is [*here*]("http://paste.stirk.org/49340").Please double check that group ID number -- you may have written it down wrong. Go to System &#8594; Administration &#8594; Users & Groups. Unlock "Users Settings" then click on “Manage Groups.”  Select the “vboxusers” group then click on the “Properties” button. What is the Group ID Number listed? If it is something other than 125, change devgid=### to match.  You'll need to reboot for the change to take effect.

---

### Post by Stargazer989 on 2009-01-17
for both albinootje and  HotShotDJ: [*screeny*]("http://adam.pcriot.com/r/info.png").

---

### Post by Stargazer989 on 2009-01-18
I've noticed something... the drives have one thing in common: the group permissions is on 'root'.

i've been trying for the past hour, hour and a half to change the Groups part... no luck so far.

---

### Post by HotShotDJ on 2009-01-18
Disregard... I misread the screenshot

---

### Post by albinootje on 2009-01-18
> **Stargazer989 said:**
> for both albinootje and  HotShotDJ: *screeny*[/url].

Thanks for the screenshot.
Your normal user is not in the vboxusers group.
Why is that ? 
Are you running everything as root ?

And remember, adding your username to a group means that your user needs to log out of the graphical environment, and then log back in before those changes are active.

---

### Post by albinootje on 2009-01-18
And which Ubuntu release are you using ? 8.04 or 8.10 ?
In 8.10 it's much easier to make usb working for VirtualBox, but between 8.04 and 8.10 there are some differences to remember.

Any reason that your vboxusers group has gid 125 ?
That could cause problems.
Mine has 126.
You can also use this command to check which groups your username is in :
```

id

```

---

### Post by HotShotDJ on 2009-01-18
> **albinootje said:**
> Thanks for the screenshot.
Your normal user is not in the vboxusers group.
Why is that ? 
Are you running everything as root ?Good catch, albinootje!  I didn't notice that the first time round.  It looks like the correct Group ID is, in fact, 125 on stargazer's system.

Which leaves the question... why isn't there a regular user listed and checked off for vboxusers?

Stargazer -- have you blocked out important information from those screenshots?  It seems pretty clear that you are running as the user "adam" on your system, yet there is no user named "adam" in the list of users in the vboxusers group properties dialog box.

Also, albinootje brings up another point -- what verson of Ubuntu are you using.  I can verify that my method of setting up USB support will work for Gutsy (7.10), Hardy (8.04), and Intrepid (8.10).

---

### Post by Stargazer989 on 2009-01-18
i thought i could go without revealing my user name. :\
anyways, yeah i colored out the name just for safety(~paranoid).
i **am** using Intrepid...

ooohh... i see where 'adam' was retrieved from! gotta remember that...

---

### Post by HotShotDJ on 2009-01-18
> **Stargazer989 said:**
> ooohh... i see where 'adam' was retrieved from! gotta remember that...Just for future... when you withhold relevant information and alter screenshots (other than to block irrelevant private data), it can impede our ability to help you.  And really, we can't "hack" your computer based on adam@BigFish. 

Having said that... I can't see anything obvious that would be keeping you from accessing your USB devices.  Another option is to create a group called usbusers --

Go to System &#8594; Administration &#8594; Users & Groups. Unlock "Users Settings" using the "Unlock" button near the lower right of the box (next to the close button) then click on “Manage Groups”[LIST=1]
[*]Click on "+ Add Group"
[*]In the "Group Name" text box, type "usbuser"
[*]Write down the Group ID number on a piece of paper
[*]Click on your user name in the "Group Members" table -- a check mark will appear in front of the user name.  Do this for each user you wish to allow USB access in VirtualBox
[*]Click OK, and then Close, then Close again.
[/LIST]

Open Applications -> Accessories -> Terminal and type "gksudo gedit /etc/fstab" (without the quotes).  Edit the following line:```

none	/proc/bus/usb	usbfs	devgid=**####**,devmode=664	0	0
```Replace **####** with the Group ID number that you wrote down in step 3 above.  Save the edited file (File -> Save) and then exit gedit.  Now reboot your system.

Let us know if this improves the situation.

---

### Post by Stargazer989 on 2009-01-18
same as before... is there any relevance to the fact that i am using a laptop ? maybe there's something different in a laptop than a desktop ?

---

### Post by HotShotDJ on 2009-01-18
> **Stargazer989 said:**
> same as before... is there any relevance to the fact that i am using a laptop ? maybe there's something different in a laptop than a desktop ?No.. I also use a laptop and have no difficulty.  I'm not seeing any obvious issues here... You seem to have gone through all the steps for installing VirtualBox and enabling USB support.  One last thing (I'm really not sure it should make a difference) have you installed the Guest Additions?

If not, start up your guest OS in windowed mode (not Full Screen or seamless).  After it has completely booted, open the Devices menu in the VirtualBox menu and select "Install Guest Additions."  If it doesn't autostart (be patient, it takes time to load), you'll have to go to My Computer in Windows and manually start it by opening it (Guest Additions will appear as a CD).  Follow onscreen instructions.  When the Guest Additions finish installing, restart your guest OS.  See if USB devices are selectable now.

---

### Post by Stargazer989 on 2009-01-18
maybe there's a trick you're not telling me or maybe there's a system that works better with VirtualBox ? this is kinda starting to get old. i'm willing to install another Linux OS that **will** work better... i've tried to install windows... it crashed just as it tried to 'start windows'.

---

### Post by HotShotDJ on 2009-01-18
> **Stargazer989 said:**
> maybe there's a trick you're not telling me or maybe there's a system that works better with VirtualBox ? I, and many others, have had success with VirtualBox running on Ubuntu.  And I have certainly given you all the information that I have.  If I didn't want to help, I would not have spent any time with you at all.  I have better things to do than to try to mislead people.

Have you tried the "guest additions" route?  Beyond that, I just don't know what the problem may be.

---

### Post by albinootje on 2009-01-18
> **Stargazer989 said:**
> maybe there's a trick you're not telling me or maybe there's a system that works better with VirtualBox ? this is kinda starting to get old. i'm willing to install another Linux OS that **will** work better... i've tried to install windows... it crashed just as it tried to 'start windows'.

VirtualBox 2.1 is the first VirtualBox i have seen crashing, never saw that with 1.6 or 2.0
With the VirtualBox repositories enabled you can still install VirtualBox 2.0 and see how that goes.

---

### Post by Stargazer989 on 2009-01-18
HotShotDJ, i have installed the guest additions... the devices are still greyed out and the info on it tells the item is 'unavailable'. i might try what albinootje suggested... probably not though. if 2.1 is having problems with something 2.0 didn't have it would be a regression, right ? [VBox_guest_addtions]("http://adam.pcriot.com/r/guest_additions.png")

---

### Post by albinootje on 2009-01-18
Do you have the repositories enabled ?

If not, here's instructions how to enable them :
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
> 
Debian-based Linux distributions: Add one of the following lines according to your distribution to your /etc/apt/sources.list:

I'm not sure whether :
```

sudo apt-get install virtualbox-2.0

```
will remove virtualbox-2.1 but you will see.

---

### Post by Stargazer989 on 2009-01-18
> E: Couldn't find package VirtualBox-2.0
it's not available using apt-get. used: > deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free as the repo... know where i could get it other than the repos ?

---

### Post by albinootje on 2009-01-18
> **Stargazer989 said:**
> it's not available using apt-get. used:  as the repo... know where i could get it other than the repos ?

I'm using Hardy right now, perhaps you forgot to do :
```

sudo apt-get update

```
?
> 
apt-cache search virtualbox-2
virtualbox-2.0 - Sun xVM VirtualBox
virtualbox-2.1 - Sun xVM VirtualBox


---

### Post by albinootje on 2009-01-18
It's there also :
[http://download.virtualbox.org/virtualbox/debian/pool/non-free/v/virtualbox-2.0/](http://download.virtualbox.org/virtualbox/debian/pool/non-free/v/virtualbox-2.0/)

---

### Post by Stargazer989 on 2009-01-18
OH NO! [Critical Error]("http://adam.pcriot.com/r/critical_error.png"). :/

---

### Post by albinootje on 2009-01-18
> **Stargazer989 said:**
> OH NO! [Critical Error]("http://adam.pcriot.com/r/critical_error.png"). :/

Can you do the following :
```

mv ~/.VirtualBox ~/.VirtualBox-old

```
and start VirtualBox again.
After that move your .vdi files into ~/.VirtualBox and redo the configuration for the guest VM.

---

### Post by surelock22 on 2009-01-18
> **HotShotDJ said:**
> .....
If the device is listed, click on it to mount it in VirtualBox. It should now be accessible via "My Computer" (XP) or "Computer" (Vista). DO NOT select any USB Keyboard or USB Mouse.  This will result in erratic keyboard and/or mouse behavior.

Here's my problem: I've gotten this far, it's showing the devices, but it will not allow me to select them. They're "greyed out", and clicking it just puts a check there that disappears. If I just put the mouse over top of the USB icon on the bottom right, it informs me that 0 (zero) devices are connected.

When the VM is off, I added the ipod as a device, and it sure looks ready to go, but no cigar. No familliar "duh-do" sound Windows makes when it recognizes new hardware/usb connects, nothin.

Me writing a blues song::guitar:

---

### Post by surelock22 on 2009-01-18
I WILL find a way, and I WILL post how I got past this. It seems to me like it's a permissions setting. I'm gonna work on this until I fall asleep sitting up on my PC if I have to...

---

### Post by albinootje on 2009-01-18
> **surelock22 said:**
> Here's my problem: I've gotten this far, it's showing the devices, but it will not allow me to select them. They're "greyed out", and clicking it just puts a check there that disappears.

You're having the same problem as the OP.
Are you also using 8.10 ? 
And which howto did you follow ?

---

### Post by HotShotDJ on 2009-01-18
> **surelock22 said:**
> I WILL find a way, and I WILL post how I got past this. It seems to me like it's a permissions setting. I'm gonna work on this until I fall asleep sitting up on my PC if I have to...Yes.  Please do.  I'm at a loss to explain the problems in this thread.  Most people (at least those who have responded, and myself) get good results by following my HowTo... but clearly a minority of people are having problems getting USB set up.  If it is figured out and the fix can be confirmed, I'd like to update my HowTo with the information.

---

### Post by Stargazer989 on 2009-01-18
Surelock22 just explained **exactly** what i'm seeing. surelock22, are you also trying it with Windows XP pro, SP3 ?

---

### Post by Stargazer989 on 2009-01-18
I'm about to give up on XP and actually use Vista. :(
I seriously don't wanna use Vista. >:\

---

### Post by albinootje on 2009-01-19
> **Stargazer989 said:**
> I'm about to give up on XP and actually use Vista. :(
I seriously don't wanna use Vista. >:\

There must be something wrong somewhere in your setup.
A few weeks ago I've successfully used some usb scanner inside a MS-w2k guest VM on Ubuntu Hardy at work.

---

### Post by HotShotDJ on 2009-01-19
I've been researching this issue some more because, quite frankly, its been driving me crazy.  I have not yet found anything definitive, other than your USB under VirtualBox SHOULD be working if you followed the [HowTo]("http://ubuntuforums.org/showthread.php?t=1015763").  Obviously, for a few people, this is not happening.  So, I'd like to do some trouble shooting just to be sure we didn't miss anything.  I know we've done most of this with Stargazer already, but just humor me so that we can get this solved.

1: Did you edit /etc/init.d/mountkernfs.sh in a previous attempt to enable USB support in VirtualBox?  If yes, please remove or comment out your changes.

2: Did you edit /etc/init.d/mountdevsubfs.sh in a previous attempt to enable USB support in VirtualBox?  If yes, please remove or comment out your changes.

3. Did you edit /etc/udev/rules.d/40-permissions or /etc/udev/rules.d/40-basic-permissions-rules in a previous attempt to enable USB support in VirtualBox?  If yes, please remove or comment out your changes.

4. If you've had to change any of the above files, please reboot your system.  Now, start up VirtualBox and your guest OS.  Does USB work now?  If not, continue...

5. Make sure that your guest OS is shut down.  Now, select it (but don't start it) and click on Settings and then select USB.  Verify that "Enable USB Controler"  and "Enable USB 2.0" are checked off.  Click OK.  If you had to check either box off, start your guest OS.  Does USB work now?  If not, continue...

6: Please run the following commands, one line at a time, in a terminal (Applications --> Accessories --> Terminal) and post the output.  DO NOT cover up, block out, or otherwise alter the information from these commands.  There is no information that can be used to hack your computer, and all of the information is relevant to diagnosing the problem.```
mount | grep usb
cat /etc/group | grep vboxusers
cat /etc/fstab
```

---

### Post by Stargazer989 on 2009-01-19
[QUOTE="HotShotDJ"]1: Did you edit **/etc/init.d/mountkernfs.sh** in a previous attempt to enable USB support in VirtualBox? If yes, please remove or comment out your changes.

2: Did you edit **/etc/init.d/mountdevsubfs.sh** in a previous attempt to enable USB support in VirtualBox? If yes, please remove or comment out your changes.

3. Did you edit **/etc/udev/rules.d/40-permissions** in a previous attempt to enable USB support in VirtualBox? If yes, please remove or comment out your changes.[/QUOTE]

so, um, where could i get a default replacement for these files ? o.o;

---

### Post by HotShotDJ on 2009-01-19
> **Stargazer989 said:**
> so, um, where could i get a default replacement for these files ? o.o;Which ones did you edit?  I can probably walk you through fixing them up.

EDIT: Here are some things to look for --

If you edited /etc/init.d/mountdevsubfs.sh, find the lines that look like this and either comment them out (by adding a # in front of the line) or deleting the lines:```
#
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb
```
If you edited /etc/udev/rules.d/40-permissions (or /etc/udev/rules.d/40-basic-permissions-rules), find the lines that look like this and either comment them out (by adding a # in front of the line) or deleting the lines:```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="vboxusers"
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"
```
If you edited /etc/init.d/mountkernfs.sh, find the lines that look like this and either comment them out (by adding a # in front of the line) or deleting the lines:```
domount usbfs "" /proc/bus/usb usbdevfs -onoexec,nosuid,nodev,devgid=<gid>,devmode=664
```

---

### Post by Stargazer989 on 2009-01-20
I wa just wondering... do these files, in any way, affect the system ?

---

### Post by HotShotDJ on 2009-01-20
> **Stargazer989 said:**
> I wa just wondering... do these files, in any way, affect the system ?Yes.  In fact, you can render your system inoperable if you are not careful when you edit them.  This is why it is good practice to back up any configuration files before you make changes to them  (I typically use the command "cp <filename> <filename.bak> before I edit my system files).  Then, if anything breaks, you'll be able to restore the original file.

The portions that I've asked you to look at are portions that you may have edited in previous attempts to enable USB support in VirtualBox.  You need to restore those files (if you altered them) because the changes that I highlighted could be interfering with the proper operation your USB devices from within your virtual machines.

If you believe that I am trying to harm your system by suggesting those changes, then there is not much I can do to help you.  Perhaps you will be more trusting if your recognize that I would have been banned from ubuntuforums.org long ago if that were the kind of maliciousness in which I participated.  Of course, even the best of intentions can result in unintended consequences.  This is why you should back up files before making any suggested changes.

---

### Post by N9TA on 2009-01-20
I'm having EXACTLY the same problem that stargazer is....the devices are greyed out and not selectable in the Devices dropdown at the top/left of the VM....although they show up fine in the settings (filters) page of the guest.

I've had this working like a champ until I just recently (Last night) installed 8.10 64 bit. I had no problem with 8.10 32 bit....could it be related to the 64 bit flavor?? Also, on this incarnation of my system I have an awesome Compiz theme going on with all the little eye candy....could THAT have any effect??

I'm just grasping at straws here....I'm pulling my hair out and I don't have much to spare  :-)

---

### Post by N9TA on 2009-01-20
OK....I'm not real sure why....but mine started working. I noticed a subtle difference in stargazers fstab file. Here's a paste of what's working so far:

none    /proc/bus/usb       usbfs  devgid=128,devmode=664    0  0

The number "128" in the above is the ID number
of the "Virtualbox" group on my system.
I also REMOVED all the USB listings on the Setup page for the VM (The Filters section).

After I did the above two things the previously GRAYED OUT menu items on the Device drop down menu at the top left of the VM are no longer grayed out.

Don't ask me why....I'm struggling with Linux myself....but it's working.

---

### Post by Stargazer989 on 2009-01-20
nonono... HotShotDJ... i edited them and, well... I think i locked my system into read-only mode. gonna try and edit them.

---

### Post by HotShotDJ on 2009-01-20
> **Stargazer989 said:**
> nonono... HotShotDJ... i edited them and, well... I think i locked my system into read-only mode. gonna try and edit them.OH.. Ok... that explains your earlier concerns. :)

Keep in mind that system files are SUPPOSED to be read-only for regular users.  You should only be able to edit them in superuser mode (sudo or gksudo).  For example, to edit /etc/init.d/mountdevsubfs.sh, you would open a terminal and type:```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```I hope we are getting near the solution to this mystery.

---

### Post by HotShotDJ on 2009-01-20
> **N9TA said:**
> OK....I'm not real sure why....but mine started working. I noticed a subtle difference in stargazers fstab file. Here's a paste of what's working so far:

none    /proc/bus/usb       usbfs  devgid=128,devmode=664    0  0

The number "128" in the above is the ID number of the "Virtualbox" group on my system.The proper group ID number will vary from system to system depending on many different variables.  For Stargazer, the vboxusers group ID is 125.  On my system, it is 126.  In any case, we've been able to verify that stargazer has used the correct group ID in fstab.
> **N9TA said:**
> I also REMOVED all the USB listings on the Setup page for the VM (The Filters section).

After I did the above two things the previously GRAYED OUT menu items on the Device drop down menu at the top left of the VM are no longer grayed out.This is good information to have.  I will include the removal of any previously defined USB Device Filters as part of future trouble shooting.  Thank you for reporting your success!

---

### Post by vmatherly on 2009-01-20
There is a a bunch of post on how to get USB working. This one is the only one that works consistently for me:

[http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy](http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy) 

I have used this many times

---

### Post by HotShotDJ on 2009-01-20
> **vmatherly said:**
> There is a a bunch of post on how to get USB working. This one is the only one that works consistently for me:

[http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy](http://www.davidgrant.ca/virtualbox_usb_windows_xp_guest_ubuntu_hardy) 

I have used this many timesI've seen this method and tested it.  It works exactly the same way as the way I've suggested.  The only difference is that I have people mount the usbfs using fstab, while David's method uses a script in /etc/init.d.  Both do the same thing.

As you can see from the last few posts in this thread, one of the problems we are dealing with is that stargazer has been editing files based on several different methods which has probably got things all gummed up.  We need to get those files restored, and then stick with a single method (that also works nearly 100% of the time).

---

### Post by Stargazer989 on 2009-01-20
HotShotDJ, those files are moreorless the same, right ? so, in theory, i could use a file that someone linked me to, correct ? could you link me to a copy of these files ?

---

### Post by HotShotDJ on 2009-01-20
> **Stargazer989 said:**
> HotShotDJ, those files are moreorless the same, right ? so, in theory, i could use a file that someone linked me to, correct ? could you link me to a copy of these files ?I don't know if they are the same from system to system.  I'm sure they are similar... and possibly the same, but I don't know for sure.

What problems are you having with the edits I suggested?  It is best that you simply reverse the changes you made and leave the rest of the file alone.  Simply dropping in somebody else's configuration file into your system can have unintended (and bad) consequences.

---

### Post by Stargazer989 on 2009-01-20
well, to be honest i may just go with a fresh-install on my backup partition(pre-formatted 25gB@EXT3) and start-over... this wouldn't be the first time i had to start-over because i did something wrong somewhere... like when i initially purchased this laptop... i installed a 64bit copy of ubuntu i just burnt... turns out there were errors i didn't test for and, well, that copy went into the trash immediately. this was a good burn, in all honesty I've had a good time with this install(aside from this Gateway attempting to adjust the screen's brightness when a change in light occured and Ubuntu going "WDF?!" and freezing. :/). 

I'll install on the seperate partition and try your method, if anything i would probably be able to take the files from there and plaster them in the right place and keep going with the current situation.

---

### Post by albinootje on 2009-01-22
In case you didn't read it yet, the newest VirtualBox has better USB support.
I'm very curious whether this will remove the need for the usb howto for all Ubuntu releases.

I'd like to test it later today on Ubuntu Hardy.

> 
today Sun released VirtualBox 2.1.2 which is a maintenance release.
See the ChangeLog

  [http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)

for more details. Some highlights:

 * full support for Windows 7 as host and guest (first product in
   the market to support Win7!)
 * better USB support on modern Linux hosts (without usbfs)
 * a combined 32/64bit package for Solaris hosts (yes, finally)

The binaries and the manual can be downloaded here:

  [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)


---

### Post by HotShotDJ on 2009-01-22
> **albinootje said:**
> In case you didn't read it yet, the newest VirtualBox has better USB supportHmmm... this might change everything!

---

### Post by albinootje on 2009-01-22
> **HotShotDJ said:**
> Hmmm... this might change everything!

I should have been more clear perhaps.
This announcement came out today, 22nd of january 2009! :)

---

### Post by HotShotDJ on 2009-01-22
> **albinootje said:**
> I should have been more clear perhaps.
This announcement came out today, 22nd of january 2009! :)Actually, I did understand.  I've just now reverted my /etc/fstab back to default and am installing the new version (it is already in the virtualbox repository!!).  Now I just have to reboot and see what happens.

---

### Post by HotShotDJ on 2009-01-22
So far... USB 1.0 works "out-of-the-box" but USB 2.0 appears broken.  I'm still working on it.

EDIT:  Ok... while USB 1.0 seemed to work, it did not.  After going back and adding the appropriate line back into /etc/fstab -- and then deleting and recreating my device filters, USB 1.0 and USB 2.0 work again.

Looks like nothing changes.

NOTE: Also, you'll have to run the following command after upgrading to 2.1.2```
sudo rm -rf /var/lib/dkms/vboxnetflt
```This fixes a problem with DKMS not unregistering the 2.1.0 stuff.

---

### Post by albinootje on 2009-01-22
> **HotShotDJ said:**
> So far... USB 1.0 works "out-of-the-box" but USB 2.0 appears broken.  I'm still working on it.


I upgraded to VirtualBox 2.1.2 without problems, and tried it tonight on my Ubuntu Hardy machine.
I tested using an usb-stick inside a XP guest VM, and I could read the contents from that usb-stick without problems.

I just found out this new file 
/etc/udev/rules.d/60-vboxdrv.rules 
which contains the following :
```

KERNEL=="vboxdrv", NAME="vboxdrv", OWNER="root", GROUP="root", MODE="0600"
SUBSYSTEM=="usb_device", GROUP="vboxusers", MODE="0664"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="vboxusers", MODE="0664"

```

This file is created with the postinst file, which I'm attaching here as a text file.

---

### Post by albinootje on 2009-01-22
I've added more info to my last comment, and like to add that I did enable usb 2.0 in my test setup from the last comment.

---

### Post by HotShotDJ on 2009-01-23
> **albinootje said:**
> I just found out this new file 
/etc/udev/rules.d/60-vboxdrv.rules Ok... I looked and I also have that file, yet without the modifications to my fstab, I had no joy trying to connect my flash drive or my external hard drive.  Did you also reverse the changes you previously made for the purpose of enabling USB support in VirtualBox?

From what I can tell, that new file (60-vboxdrv.rules) SHOULD do the trick.

---

### Post by albinootje on 2009-01-23
> **HotShotDJ said:**
> Ok... I looked and I also have that file, yet without the modifications to my fstab, I had no joy trying to connect my flash drive or my external hard drive.  Did you also reverse the changes you previously made for the purpose of enabling USB support in VirtualBox?

From what I can tell, that new file (60-vboxdrv.rules) SHOULD do the trick.

I'm using a fresh Ubuntu Hardy install (up to date : 8.04.2).

$ cat /etc/fstab|grep usb
$ mount|grep usb
$ ls -la /dev/vboxdrv
crw------- 1 root vboxusers 10, 62 2009-01-23 10:47 /dev/vboxdrv
$ VirtualBox -h|grep 2.1
Sun xVM VirtualBox Graphical User Interface 2.1.2

---

### Post by albinootje on 2009-01-23
By the way. 
Perhaps it's a bit disappointing for you that you've just started this usb-for-virtualbox-howto, and now Sun comes out with this update.
But in general for new Ubuntu (and possibly other Linux distributions) users this is great news.
At least for me it worked out-of-the-box on Ubuntu Hardy.
I wonder why it doesn't work on Ubuntu Intrepid.

---

### Post by HotShotDJ on 2009-01-23
> **albinootje said:**
> By the way. 
Perhaps it's a bit disappointing for you that you've just started this usb-for-virtualbox-howto, and now Sun comes out with this update.
But in general for new Ubuntu (and possibly other Linux distributions) users this is great news.I'd be pleased to have my "HowTo" obsoleted by USB working as expected out-of-the-box.  The more things that work without users having to fiddle around with configuration files, the better!

I'm thinking that I've missed something that is causing it not to work properly for me.  I may work on it some more over the weekend.

---

### Post by jameskeagie on 2009-01-24
So I just installed VirtualBox 2.1.2 on a completely updated Ubuntu Hardy 8.04.  

As always - everythings works great, installed XP as a guest OS, and now tried to get USB to work (something I'd never messed with before).  

Tried adding USB filters as suggested, and no matter what the devices were still greyed out in XP.  

I read the Vbox manual (very helpful!) and saw that you have to be a member of vboxusers in Linux (In other words, vboxusers needs access to your devices) and unlike older versions of virtualbox, it will actually still boot without warning you about this discrepency.

SO!  I got it working by going to:

System -> Administration -> Users & Groups (unlock if you have security) -> Manage Groups

Scroll down to vboxusers, click on properties, and make sure your user name is checked.  

Restart X (Ctrl+Alt+Backspace), Relogin, start up vbox again, and bam, you should/may have USB if this were your problem!

This may be connected to your other issues as I saw similar group Id's floating around in the brief read-through of the rest of these posts.  And since 2.1.2 evidently lets you run w/o being part of the group, this may be a problem for a lot of people (I think there was a question during the install abt if I wanted to keep the existing group or not).

---

### Post by Stargazer989 on 2009-01-28
OK!!! i've successfully installed VBox and now have USB running!
had an error( [WinXPErrorOnVBox]("http://adam.pcriot.com/r/VBox_error_for_WinXP.png") ) but someone on VBox's official channel on Freenode helped me. something about running ```
sudo /etc/init.d/vboxdrv setup
``` i don't know anything about it... just it did **something** and i ran XP perfectly.

.. now only if Daemon Tools didn't give me an error 256. >:\

---

### Post by albinootje on 2009-01-28
> **Stargazer989 said:**
> OK!!! i've successfully installed VBox and now have USB running!
had an error( [WinXPErrorOnVBox]("http://adam.pcriot.com/r/VBox_error_for_WinXP.png") ) but someone on VBox's official channel on Freenode helped me. something about running ```
sudo /etc/init.d/vboxdrv setup
``` i don't know anything about it... just it did **something** and i ran XP perfectly.

Excellent! Congrats!

(Next time try to read the error messages carefully, because the solution was mentioned in the error message) :)

---

### Post by Stargazer989 on 2009-01-29
i guess i panicked when i saw the error message. :/

do you know if it's possible to mount a disc in Ubuntu and it would show up on XP ?

---

### Post by albinootje on 2009-01-29
> **Stargazer989 said:**
> i guess i panicked when i saw the error message. :/

No problem.
> 
do you know if it's possible to mount a disc in Ubuntu and it would show up on XP ?
You can use the menu, see attached screenshot.

---

### Post by Stargazer989 on 2009-01-30
to be specific:```
mount -o loop -t iso9660 -r /path/to/file.iso /mnt/point
```I like to rip game CDs and make them into ISOs so i can, 1: prolong the CD's life and 2: prolong the life of my CD drive. ;D

---

### Post by albinootje on 2009-01-30
> **Stargazer989 said:**
> I like to rip game CDs and make them into ISOs so i can, 1: prolong the CD's life and 2: prolong the life of my CD drive. ;D

Okay ;-)
Well, you can try this :
```

dd if=/dev/cdrom of=~/my_cdrom.iso

```
or with k3b (or another cd burning program) and choose the "create image only" option from the copy cdrom section.

YMMV though, a few weeks ago I bought some software I wanted to run in VirtualBox or Wine without using the noisy cdrom drive, and both k3b and dd failed to make an exact copy :(

---

### Post by Stargazer989 on 2009-01-30
i either use: Brasero or ImgBurn(wine needed), but both have been faltering for movies... and a few games. might start using k9copy.

---

