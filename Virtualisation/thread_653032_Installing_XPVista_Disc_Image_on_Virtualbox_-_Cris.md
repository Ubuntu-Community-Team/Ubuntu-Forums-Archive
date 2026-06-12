---
title: "Installing XP/Vista Disc Image on Virtualbox - Crisis, HELP!"
date: 2007-12-29
forum: Virtualisation
---

### Post by Sedivy 94 on 2007-12-29
Hey guys... I'm a new user  when it comes to Ubuntu (been using Ubuntu for about 7 months).  I'm able to comprehend some of this stuff, but eventually I get lost in all the acronyms and phrases used. Currently, every possible problem that has arisen inched me closer to setting up a Windows VM.  I recently received an iPod Classic for Christmas, so that greatly motivates me.  

So I download Windows Vista from Microsoft (don't ask how I did it) and it comes with three files... 

- boot.wim 
- install.wim
- X13-49120.exe

Guess what... wine will not run the fricking .exe file....  the .exe file is what compiles the three files into a folder with directories, which is to be burned onto a dvd.  

I am extremely frustrated.  I'm deciding on creating a Windows XP VM (using my OS disc of course) and compiling the Vista folders on that XP VM, hoping to create a Vista VM after burning it to disc and setting it up.

But I hit a little bump in the road... how do I create a VM using a Windows XP CD and Virtualbox?  I understand Virtualbox uses .vdi files (Virtual Disc Image?) How am I turn "convert" this OS Disc into a .vdi file?

Extreme help needed before I.... well... meltdown.

Any help GREATLY appreciated.
----------------
Now playing: [U2 - The Saints Are Coming](http://www.foxytunes.com/artist/u2/track/the_saints_are_coming)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by K.Mandla on 2007-12-29
Hmm. :-k The filenames you describe suggest you're working with an illegal copy of Windows, and discussion of that would be a violation of forum policy.

I'll close this thread now; contact a staff member via PM if you want the thread reopened.

Edit: I've discussed the thread with the OPer and I'm satisfied this isn't illegal, so I'm reopening the thread. If anyone can offer a solution, I would be appreciative too.

---

### Post by K.Mandla on 2008-01-01
Bump after reopening. ;)

---

### Post by Sedivy 94 on 2008-01-01
Thankyou for re-opening the topic... I figured out how to put a disc image on Virtualbox but... I get these errors.

When I go to settings I get this error message (sorry, couldn't copy and paste)
[IMG]http://www.imagehosting.com/out.php/i1480372_ScreenshotVirtualBoxError1.png[/IMG]

When I start the Virtual Machine (Windows XP) I get this error message
[IMG]http://www.imagehosting.com/out.php/i1480371_ScreenshotVirtualBoxError.png[/IMG]

What's wrong with it?  I'm assuming it's Virtualbox's fault and not the disc image's fault....  right?

---

### Post by popch on 2008-01-02
The second one is easy. You should add your Ubuntu Linux user account to the group named vboxusers.

Look in the Systems menu under Administrative tasks/user accounts or some such. Sorry, I can not be more specific as I am not near my Ubuntu computer right now.

The first one derives probably from the fact that you are trying to run an Windows in a virtual box which was installed on a real hardware computer. The message seems to be about some hardware not being where it is expected.

---

### Post by lancerocke on 2008-02-14
How did this work out for you?

---

### Post by purpledavec on 2008-02-17
If you look on the help section of Virtual Box website I think you will find some information about the first error message, if I recall may be because you are trying to install a 32bit OS within a 64bit one or vice versa. Hope this helps..

---

### Post by benhur99ph on 2008-07-06
I think the first problem is with the USB. There is a file that you should edit first to enable USB inside virtualbox. Follow this guide right here -- [How To: Install VirtualBox on Ubuntu 8.04LTS (Hardy Heron) [Tutorial]]("http://ph.ubuntuforums.com/showthread.php?t=770745").

---

