---
title: "Day One, just venting!"
date: 2008-08-11
forum: Testimonials &amp; Experiences
---

### Post by Diya on 2008-08-11
Hey guys/gals!

After using Windows OS for 11 years, I've finally decided that I'm not really a big fan of Mr. Bill Gates, and his over-priced stuff. So, I decided it's time to switched to Linux, and I installed Ubuntu 8.04 Hardy Heron yesterday.

It was really frustrating getting used to a completely new OS, especially when it's not really newbie-friendly at all. It took me a while trying to figure out the gnome-terminal, and the whole "permission" thing.

After getting most of things figured-out, I really loved Ubuntu, and I thought with a little bit more work it can become way better than Windows OS (IMHO). However, I decided to update my drivers that's when all hell broke loose! ](*,)

The sound driver somehow corrupted a file called libasound.so.2, and I got an error message, and couldn't login. I tried everything people said, but nothing worked for me, so I had to re-install Ubuntu at the end of the day.

Pros (Compared to Windows XP):
- The interface is much better, and more user-friendly.
- The Package Manager is really amazing, it makes one's life easier.
- It's Free!, sometimes 'inexpensive' suits it better.
- Very secured.

Cons (Compared to Windows XP):
- The manual installation of programs, and drivers' updates really is a CHORE!
- Installing new drivers would mess up the system completely, I'm afraid of installing my graphics card already!
- No system Checkpoints, no system restore, no system repair through the CD.
- I'm not comfortable with working on one big directory, I used to have C:/ and D:/ partitions on Windows, but now I only have one big directory that contains everything.
- Many programs I used to have aren't compatible with Linux system (i.e. Du Super Controler), but I found a substitution called "Wondershaper", isn't as good as Du, but should be enough for me.

Overall, I really like Ubuntu as my main OS now.

---

### Post by Canis familiaris on 2008-08-11
Why did you manually install the drivers when the hardware was working?

---

### Post by kaivalagi on 2008-08-11
> **Anurag_panda said:**
> Why did you manually install the drivers when the hardware was working?

+1

Stick with default drivers if they work...

---

### Post by HermanAB on 2008-08-11
"Don't fix it if it ain't broke".

Most Linux trouble is caused by updates.  The obvious solution is not to do them.  A properly working Linux system will keep working properly for years, so there is no need to do updates all the time.  I update most of my systems once a year.  However, some systems I never update and replace every 3 or 4 years - zero maintenance == zero cost.

Cheers,

Herman

---

### Post by wolfen69 on 2008-08-11
> **Diya said:**
> 

After using Windows OS for 11 years

that says it all. just think if you had used linux for 11 years. remember to be patient. no one is born with the knowledge of how to use linux. it is not harder, just different. once you learn it, the payoff is immense. have fun.

don't worry about re-installing a few times, i've done it probably over 70 times. it was all worth it too. now i'm set for life. windows free.

---

### Post by Tom--d on 2008-08-11
> **Diya said:**
> I'm not comfortable with working on one big directory, I used to have C:/ and D:/ partitions on Windows, but now I only have one big directory that contains everything.


Thats just default for ubuntu to stick everything on one Partition. 

For example.
I have 2 partitions. 

5GB for / (root) the whole system. (thats all I need. :D)
The rest (around 115GB for /home (all my files)

Remember, Linux is not Windows. thus, no C:\ D:\

And yes, its a big blur at the beginning. But you've just installed something new. Something you have never used before. You will need to learn.
After that its a breeze and you will not look back :D
Well, I didn't and Windows Free! :D:D

---

### Post by original_jamingrit on 2008-08-11
Hey, welcome to Ubuntu

If you really want to get into using Ubuntu, we can help you out.  It takes a little patience on your part, especially if you don't have hardware that's perfectly compatible, but there's lots of info here on the forums for you and anyone having a bumpy transition.

> I decided to update my drivers that's when all hell broke loose!
Open a terminal and then copy and paste the output of the _lspci_ command in your next post.  This will show us what kind of hardware you have.  Also remember that drivers that were made for Windows will often not work in Ubuntu, unless you use ndiswrapper which is usually unnecessary.

> The manual installation of programs, and drivers' updates really is a CHORE!
You can download debs through [http://www.getdeb.net/](http://www.getdeb.net/).  Debs are software packages that are basically one-click installs, like .EXE files.  This might be more comfortable, but the best way to install stuff is using Synaptic Package Manager, which can be found at System->Administration->Synaptic.  All of the userland software that you'll ever need is in Synaptic, and it will automagically install dependencies for you as well.  As for drivers...
> Installing new drivers would mess up the system completely, I'm afraid of installing my graphics card already!
This is kind of unusual.  The best advice I can give is to make sure you follow a up-to-date walkthrough for every driver you need to manually install.  Searching the forums here, or just using Google, can sometimes give you out of date instructions.
> No system Checkpoints, no system restore, no system repair through the CD.
Quite right.  Most backup or system restore options are third party applications (See rsync, or grsync, or [this link]("http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html")).  Also, downloading the [Linux System Rescue CD]("http://www.sysresccd.org/Main_Page") may be helpful once you are a bit more familiar with working in a Linux environment.
> I'm not comfortable with working on one big directory, I used to have C:/ and D:/ partitions on Windows, but now I only have one big directory that contains everything.
You can partition with Linux as well.  Although I don't see why you would want to when you don't have to.  If you're really stuck on using extra partitions, there is a partition editor on the Ubuntu LiveCD you could use, and then you would have to mount your new partition and/or edit your /etc/fstab file.  You should probably get more familiar with Linux before going and doing that, though.
> Many programs I used to have aren't compatible with Linux system (i.e. Du Super Controler), but I found a substitution called "Wondershaper", isn't as good as Du, but should be enough for me.
You'll find that many things that don't work under WINE (windows compatibilty) often do have open source alternatives.  The quality varies, but most have a bit of a learning curve.

I hope this post helps.  And be sure to post your lspci and look at walkthroughs before manually installing any drivers.

---

### Post by mikjp on 2008-08-11
> **Diya said:**
> 
- I'm not comfortable with working on one big directory, I used to have C:/ and D:/ partitions on Windows, but now I only have one big directory that contains everything.

In the long run it is much easier. When you run out of C:/ in Windows, you cannot make it bigger than the hard drive. In Linux, OTOH, you can just add (mount) a new hard drive to any part of the huge directory tree.

You can have - and in fact should - have /home in a separate partition also in Linux. But users don't have to know which drive they are using, only the system administrator has to know it.

Just believe me: in the long run you will notice it is a great idea.

mikko

---

### Post by jpeddicord on 2008-08-11
Moved to Testimonials.

---

### Post by mikjp on 2008-08-11
> **original_jamingrit said:**
> 
You can partition with Linux as well.  Although I don't see why you would want to when you don't have to.  

It makes, for example, upgrading the system much easier. If you have a separate /home you can always do a fresh install while keeping your own files intact. You might even decide to move from Ubuntu to openSUSE or Mandriva or RedHat and still keep your /home with all the desktop settings and files there.

mikko

---

### Post by Canis familiaris on 2008-08-11
> **mikjp said:**
> In the long run it is much easier. When you run out of C:/ in Windows, you cannot make it bigger than the hard drive. In Linux, OTOH, you can just add (mount) a new hard drive to any part of the huge directory tree.

Actually in XP Pro you can too mount a partition in a directory but Linux way is actually better.
/off topic

---

### Post by Comhra on 2008-08-11
It takes a bit of getting used to but you'll become comfortable with it in awhile.  I've been using it for a year now and while many things are still a mystery, I've managed to solve some major issues on my own this weekend.

---

### Post by bmac on 2008-08-11
> After using Windows OS for 11 years
> I'm not comfortable with working on one big directory, I used to have C:/ and D:/ partitions on Windows, but now I only have one big directory that contains everything.

OMG It's not Windows..... How can that be????? This OS needs to be fixed - It doesn't work like Windows!!!!!  It just sucks.....

Imagine that, after 11 years running Windows and now what????

I don't understand why people install Ubuntu and expect it to be just like Windows. I think Ubuntu's installation screen should read:
**"UBUNTU IS NOT A MS WINDOWS ENVIRONMENT AND DOES NOT FUNCTION LIKE MS WINDOWS"**

With a disclaimer stating:
**"IF YOU DON"T HAVE THE TIME OR DESIRE TO LEARN A NEW OPERATING - THEN _PLEASE_ DO NOT INSTALL THIS OS"**

This would provide individuals with one last opportunity to re-evaluate their decision and may effectively reduce the number of individuals installing Ubuntu expecting an MS clone...:-k

---

### Post by Diya on 2008-08-12
Thanks everyone for replying!

Just to make things clear. I am _fully_ aware that Ubuntu is a completely different system than Windows. I _do not_ expect it to function just like Windows, and I _do not_ think Ubuntu sucks, not even a bit. I was merely listing the stuff I would miss in Windows, hence the "just venting!" in the topic title. I've been very patient with Ubuntu, and now learning new things everyday.

> "Don't fix it if it ain't broke"
Yes, I learned that the hard way.

> Open a terminal and then copy and paste the output of the lspci command in your next post. This will show us what kind of hardware you have.

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

Thanks everyone for info!

---

### Post by hyper_ch on 2008-08-12
> **Diya said:**
> It was really frustrating getting used to a completely new OS, especially when it's not really newbie-friendly at all. It took me a while trying to figure out the gnome-terminal, and the whole "permission" thing.
Linux is newbie-friendly. Just because you have 11 years of experience with windows are indoctrinated with the way windows does things you may find it difficult to change your habits. User-friendlyness and familiarity are two different things.


> **Diya said:**
> 
- The interface is much better, and more user-friendly.

You can have different user interfaces. If you get your way around linux a bit you may want to also to try KDE and Xfce and Fluxbox...

> **Diya said:**
> 
Cons (Compared to Windows XP):
- The manual installation of programs, and drivers' updates really is a CHORE!
- Installing new drivers would mess up the system completely, I'm afraid of installing my graphics card already!
You normally don't install programs manually and neither drivers. If hardware is not working out of the box then do some research first if and how others got that hardware running.
However the restricted driver manager for the nvidia card should be fine.

> **Diya said:**
> 
- No system Checkpoints, no system restore, no system repair through the CD.
Not really needed... you have the power of "restoring" everything by either installing downgraded versions or default config files... there's no registry that gets corrupted or so. Just about everything can be recovered and put int a workable state again.

> **Diya said:**
> 
- I'm not comfortable with working on one big directory, I used to have C:/ and D:/ partitions on Windows, but now I only have one big directory that contains everything.
Normally you should be working in your home directory only anway. That would be /home/USERNAME - don't worry so much about the rest.

> **Diya said:**
> - Many programs I used to have aren't compatible with Linux system (i.e. Du Super Controler), but I found a substitution called "Wondershaper", isn't as good as Du, but should be enough for me.
Well, do you expect to run Playstation 3 games on Wii?

As to your lspci listing:
Intel is good and should work right out of the box (audio drivers).
For the nVidia card you may want to install the proprietary drivers (Restricted driver manager).

The rest should be fine.

When posting output from the command line or a config file enclose it in [noparse]```

```[/noparse] brackets because (a) it seperates it from the normal text and (b) makes it easier to read).

---

