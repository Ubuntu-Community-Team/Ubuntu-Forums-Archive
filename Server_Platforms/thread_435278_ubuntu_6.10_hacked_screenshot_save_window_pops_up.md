---
title: "ubuntu 6.10 hacked screenshot save window pops up"
date: 2007-05-06
forum: Server Platforms
---

### Post by pcrudy on 2007-05-06
when i turn on ubuntu, i get pop up window to save screenshot; cpu runs at 100%  cannot close or cancel screenshot.  can boot with knoppix etc but don't know what files to delete.  i think system is hacked.  any quick fixes how to stop this from running at startup?  what process can i try to kill etc.

---

### Post by hartz on 2007-05-08
Hi,
Have you learned anything more about this?

The steps would be:
Boot into another OS, eg Knoppix, or even the recovery mode.
Depending on what you use, it may be necessary to then manually mount the file systems on your disks, or it may already be mounted.  You can Use the "df" or the "mount" commands to find out what file systems are mounted and where.
Next steps would be to start looking at configuration changes, eg what are programs set to "auto-run" after login, what are in your log files, reset your passwords, and potentially look for installed root-kits.  Some of the other guru's on this forum might be able to give you more ideas/suggestions.

---

### Post by suntin on 2007-05-08
Boot to terminal not Gnome (when you enter password there are options on the screen for session type)
and edit the startup files. however not sure which ubuntu uses....

/etc/init.d

Someone here is bound to step in and fill in the blanks in my head...

---

### Post by pcrudy on 2007-05-08
thanks.  i tried knoppix but since i am not sure what files do what, etc.  i was gun shy about deleting things etc.  i rebuilt the system from scratch and it started again!  all of a sudden save screenshot window pops up and cpu goes to 100%.  i am going to use bartpe and diskpart to wipe clean the hard drive and redo it again.  i had a vmware server windows install.  i will test with just ubunut; if that works will reload vmware.   if it happens again not sure what i will do.  thanks for the tips though.;

---

### Post by hartz on 2007-05-08
Did you delete/wipe your home directory during the re-install?

If not, I suspect that this is a user specific setting!

---

### Post by pcrudy on 2007-05-08
thanks for replying; i wiped the hard drive during two basic (accept the defaults) reinstallations and used two different versions of ubuntu, server and desktop.    the last time i reinstalled everything the install did not find the nic card so i was not connected to the Internet and the same thing happened.  all of a sudden the 'wheel' appears and the pop up 'save screenshot' dialog box opens and the cpu runs at 100%; sometimes you can close the dialog box but sometimes you cannot.  since it's not being attacked from the internet and i have wiped the hard drive twice using linux partition and diskpart, i am going to erase the hard drive with our disk eraser that wipes out hard drives and the data according to the  department of defense specifications; then i am going to use a new download ISO for ubuntu.  if that does not fix things i am going to try a different hard drive.  if that does not work, i am going back to windows! (ugh!)

---

### Post by MJN on 2007-05-09
Are you sure your 'Prt Sc' (Print Screen) key isn't stuck down? Might be worth trying a different keyboard in case it's either the key, or a dodgy controller sending the keycode.
 
Or try booting without a keyboard plugged in...
 
Mathew
 
P.S. Don't take this the wrong way but what is it with people's paranoia and hysteria? All too often the slightest 'weird' problem results in someone thinking they've been hacked!  ;)

---

### Post by Trefenwyd on 2007-05-14
I have a similar problem in Ubuntu 6.10 and 7.04.  I get many many "Save a screenshot" popups and I don't hit the "print screen" button.  It doesn't happen all the time, but when it does, sometimes the computer becomes unresponsive.  Any suggestions?

---

### Post by DarthImpala on 2007-05-14
I am also having this problem in 7.04. I've had it happen while I'm logging in and randomly during normal usage. It just started today and I can't find a pattern to it. Sometimes 100+ windows will popup and other times more so that gnome crashes and I have to reach for the power button on my laptop because its completely locked up. I don't have a stuck key and its even happened when when I'm just using the mouse.

Thanks in advance

---

### Post by primski on 2007-05-15
Have you beryl/compiz enabled?

i remember once had similar problem, before official feisty release compiz made 'save screenshot' pop up on every mouse click. Took me a while to figure it out i was poping the window with mouse clicks.

---

### Post by Trefenwyd on 2007-05-15
I did not have beryl/compiz running at the time.  In fact, I never run either of those programs because my laptop is so old.

Any suggestions on how to fix this would be very much appreciated.

Thanks
Kyle

---

### Post by DarthImpala on 2007-05-15
I also dont have beryl/compiz/xgl running. Last time my laptop survived through this the keyboard nolonger functioned. Is it possible to uninstall only the save screen shot window?

Thanks

---

### Post by dmizer on 2007-05-16
try a different keyboard.  if your keyboard is usb, try a ps/2 port keyboard.  is your computer sitting on the floor?  i had some serious (and similar) problems with usb and static discharge from my usb keyboard and mouse.

edit:
ugh ... just read that you're using a laptop.  that'll make things difficult.  but this is not a hack, it's a hardware problem.

---

### Post by Trefenwyd on 2007-05-16
I managed to fix my problem.  I disabled the print screen button for gnome screenshot.  i know it's not a sticking key, but I have a similar problem with my shift key getting stuck.  I just fixed that one just by hitting the shift key.

I think the biggest issue is my laptop is just so old :( HP ze4560us.

If there is another reason, please help me shed some light.

Thanks,
Kyle

---

