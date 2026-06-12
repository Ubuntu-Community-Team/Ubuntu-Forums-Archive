---
title: "M-Audio Midisport 4x4 setup-weird USB issue"
date: 2008-10-21
forum: Ubuntu Studio
---

### Post by jukingeo on 2008-10-21
Hello all,

I just recently purchased a USB M-Audio Midisport 4x4 because I had the smaller Midisport 2x2 which worked fine in Linux.  In fact that device was automatically detected.

For some reason the Midisport 4x4 is NOT automatically detected.  THe USB light doesn't light up at all.   This device is of the same type as my 2x2 (the older style Blue and Yellow box with the old Midiman logo on it).  

So I don't get why the 2x2 works and the 4x4 doesn't.  I also have a Korg Kontrol 49 keyboard that is also USB and that works fine as well.

However...this is where things get strange.  I am on a triple boot system and if I boot into Windows XP using the Midisport 4x4, the USB light DOES come on.

If I now reboot my machine and go into Ubuntu or Puppy Linux the USB light STAYS on throughout the whole reboot procedure and then becomes fully recognized in the Linux distribution.

If I turn off my computer completely (shutdown mode) and then turn it back on and boot into a Linux distribution the light doesn't come on once again.

To me it seems that the driver in Windows some how "kick starts" the device and it stays running as long as there is power going to it despite a change in OS's.

While I can use the Midisport 4x4 by first booting into Windows and then reboot into Linux, I find this unacceptable as I intend the Midisport 4x4 for a future Linux only machine.

Can anyone tell me what is happening and how can I fix this?

Thank You,

Geo

---

### Post by jukingeo on 2008-10-25
bump,

Anyone have any ideas of how I can start my Midisport 4x4 in Linux without having to "start it up" in Windows?  I would like to move ahead with my project, but I want to set this up on a Linux only system, so I need to know how to property start it WITHOUT relying on Windows XP.

Edit:

I found this out today:

[http://ubuntuforums.org/showthread.php?t=96506](http://ubuntuforums.org/showthread.php?t=96506)

Scroll to the 3rd page near the bottom for my post.

While I have "partially" solved the problem on my own, I have to resort to a desktop icon in which I have to click it AND type in my sudo password every time I want to use the USB interface.  While this DOES get it going without going to Windows first, it is a pain in the but for something that should be detected and ready to be used on startup.

Again, any assistance would be appreciated.


Thank You,

Geo

---

### Post by markbuntu on 2008-10-26
The problem with that particular piece of hardware is that it needs to load firmware to operate correctly. That is why you need to run windows first, to load the firmware. It is a cheap and dirty way for manufacturers to get their hardware working. You should bug m-audio to make a firmware loader for linux.

---

### Post by jukingeo on 2008-10-27
> **markbuntu said:**
> The problem with that particular piece of hardware is that it needs to load firmware to operate correctly. That is why you need to run windows first, to load the firmware. It is a cheap and dirty way for manufacturers to get their hardware working. You should bug m-audio to make a firmware loader for linux.

Well, I have found and loaded the firmware on my machine.  BUT the problem is that a command has to be invoked each time I want to use the unit.  I created a button on my desktop that supposed to invoke  the necessary command, but it only works part of the time and the reason for that is that the address port for the Midisport changes every time on boot up.  So I have to go back into my start up script and edit the command line.  I do that by first doing an lsusb in my terminal to find out the assigned address.  I change the address in the command line and then save the file and click on my start up button and boom!  I am in business.  So now I do not have to go into Windows XP, which is a HUGE improvement.  But, this is still a pain to do every time.  There is a script on the same post I got the information to install the firmware on.  It is right here:

[http://ubuntuforums.org/showthread.php?t=96506](http://ubuntuforums.org/showthread.php?t=96506)

scroll down to the section on creating a script.

However, for some reason I can't get it to work.  I think it is because of the permissions because sudo needs to invoke the command.  So that would mean a password each and every time.  I would like to find a way to bypass that, have the script start up my USB device AND finally do it all on startup of Ubuntu.  I know that seems like alot, but I don't think I am asking too much.

Now here is the kicker...I have a smaller Midisport 2x2 device and I didn't have to go through all of this.  It was automagically detected in my Linux distributions.  So it does get me to ask why does one device and not the other IN THE SAME series work?  After thinking about it a bit I did wonder that perhaps the 4x4 device I have is a bit older than the 2x2 device.   The 2x2 device could have come out when USB class compliance became standard.  I have another USB device, a Korg Kontrol49 keyboard that is supposedly NOT recognized by Linux, but yet it is because the device is class compliant.  I can just plug it in and go.

---

### Post by markbuntu on 2008-10-27
Well, that is good you got the firmware thing figured out. If you want that device to have the same device number on each boot, there is a section in this thread on one way to do that:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

There is also a link from here for multiple sound cards that explains using aliases to do the same thing:
 
[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

### Post by jukingeo on 2008-10-28
> **markbuntu said:**
> Well, that is good you got the firmware thing figured out.

Well, I have not totally figured it out.  I have set up an icon that can start up the midisport on my desktop, but sometimes the ID changes and I have to go back and edit it.

A nicer approach would be to have a script automatically find the port/buss number and then execute the start up command.  From reading that one page I posted above, it seems that the script does that, however, it fails to execute the firmware.  I don't know why it doesn't work.  But if I find the port and bus manually and then manually execute the command that loads the firmware, it works!

>  If you want that device to have the same device number on each boot, there is a section in this thread on one way to do that:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

There is also a link from here for multiple sound cards that explains using aliases to do the same thing:
 
[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

Wow!  Both those pages are over my head.  The first one seems to be geared to sound cards.  I don't see much in regards to USB interfaces.

At any rate, I just really need some help in fixing that script file.  It DOES automatically find the port/buss, but it doesn't execute.  My guess is that is has something to do with the super user password.  With my desktop launcher I DO have to enter my password in for it to work.  I DON'T want to do that.

Idealistically I would just like to plug the device in and have it boot up on it's own.  Realistically I am fine with clicking a launcher button every time I need the unit upon boot up.  I just need something a bit better than what I am doing now.

Thanx,

Geo

---

### Post by SpaceApache on 2008-12-02
Hello.

What you probably need to do is create an init script, that is run during Ubuntu's startup. This will have full root access and should have automagic bus detection. Which, considering the scripting language, shouldn't be majorly difficult (unless you know zilch about Linux shell scripting).

Unfortunately, I do not have any MIDIsport devices (I used to, appropriated through a friend who owned one, but the device was a dead man walking). I am looking to get one or more MIDIsport 4x4's for a future project.

The init script would need to be loaded after USB initialisation, so that lsusb could function. It would then be a matter of grep'ing and gawk'ing the desired information, and using that to load the firmware and initialise the 4x4.

I hope this helps, PM me if I can be of any more help.

SpaceApache.

---

### Post by jukingeo on 2008-12-07
> **SpaceApache said:**
> Hello.

What you probably need to do is create an init script, that is run during Ubuntu's startup. This will have full root access and should have automagic bus detection. Which, considering the scripting language, shouldn't be majorly difficult (unless you know zilch about Linux shell scripting).

Unfortunately, I do not have any MIDIsport devices (I used to, appropriated through a friend who owned one, but the device was a dead man walking). I am looking to get one or more MIDIsport 4x4's for a future project.

The init script would need to be loaded after USB initialisation, so that lsusb could function. It would then be a matter of grep'ing and gawk'ing the desired information, and using that to load the firmware and initialise the 4x4.

I hope this helps, PM me if I can be of any more help.

SpaceApache.

Yes, I did that already.  I followed the guide for that and did get it to work when the computer turns on.  Then I do have a desktop icon that I "start" it if I plug it in after Ubuntu is running.

What WOULD be nice is if it would be recognized as soon as I plug it in.

Geo

---

### Post by osterchrisi on 2009-02-23
Hey guys!

I have the same problem with Ubuntu 8.10 an my Midisport 4x4. It seems as you already solved your problem (at least to 90%), so could you plz tell me the way you finally fixed it? I would really appreciate that!

Thanks a lot!

---

### Post by jukingeo on 2009-02-24
> **osterchrisi said:**
> Hey guys!

I have the same problem with Ubuntu 8.10 an my Midisport 4x4. It seems as you already solved your problem (at least to 90%), so could you plz tell me the way you finally fixed it? I would really appreciate that!

Thanks a lot!

Read this entire post, I did provide links to the sources that helped me fix my problems.  HOWEVER, keep in mind I am (still) using Ubuntu 8.04 (Hardy).  You mentioned you have version 8.10.  Version 8.10 is known to have issues with audio and USB.  So the threads that I linked to may or may not help you.  It depends if the threads are updated with new information to get the Midisport devices to work in 8.10.  For now I am sticking with version 8.04.

So outside of the information here, I am sorry I can't be of further assistance as I am not on version 8.10 as of yet.

Have a good day and lots of luck getting your unit to work.  If you DO get it to work, do reciprocate your findings by posting the information here.

Thank You,

Geo

---

