---
title: "Ubuntu suckage"
date: 2008-02-11
forum: Testimonials &amp; Experiences
---

### Post by zugu on 2008-02-11
I have used Ubuntu 5.10 and 6.06 for more than a year. Sometime ago I dumped Ubuntu because it didn't allow me complete freedom in installing binary packages.

Anyway, I decided to install it yesterday, just to see how things are going.

I have 2 Ethernet cards, both PCI, and my connection to the internet is wired through one of these cards. The LiveCD displayed the cards as eth0 and eth1, but I had no means of telling which is which. I should mention that my internet settings have to be manually input, so I was unable to set up the connection.

Well, that wasn't a problem as I was just going to install Ubuntu, right? At 82% progress, the installer said something about *Scanning the mirror...* . Now this is weird. **What mirror? Why does it need scanning?** And most importantly, I had no internet connection set up, **why was the installer trying to connect to the internet?** I waited 20 minutes before giving up and closing the installer.

At reboot time, the Windows XP NTLDR was missing (as I was trying to install a dual-boot system). Thanks to the Windows XP Recovery Console I was able to restore Windows.

Overall, Ubuntu was a bad experience. Why can't the developers add a freaking check for active internet connections when the installer starts? **Why is an internet connection needed at install time?**

The LiveCD environment is rough and unpolished. I wonder why the screensaver is active and starts when the Ubuntu installer is middle through its job, even if the video card is not properly installed and configured, resulting not in a screensaver, but in a black screen. I wonder why Gparted, after applying the tasks given scans the hard drive and then **suddenly exists**, as if it crashed (I don't think it crashed, but inexperienced users might think it did). I wonder why is there no estimate of the time needed to complete the overall installation. And so on. Small things make all the difference in the world. Unpolished is the word of the day.

And then, of course, there's my fundamentally different view on how package management should be done, but that's another story.

As a side note, Gparted is plain awful: I told it to create an ext3 partition, it bragged about formatting it and then the Ubuntu installer told me the partition needed formatting. And it surely wasn't formatted, because 212 MB of disk space on it was used. I don't know by what, who or why, but I swear it was freshly created and "formatted".

On a personal note, I very much dislike the current 7.10 default look, 6.06, or even 7.04 were much better, IMHO.

My conclusion: Ubuntu is still bad. Gonna check it again in a couple of years.

---

### Post by yabbadabbadont on 2008-02-11
Just an FYI on the "212 MB of disk space".  That would be the space used by the journal.  ext3 is a journaled filesystem and the journal has to go somewhere.  ;)

I agree about the internet connection issue.  If the network hasn't been configured, then the installer should just create a default sources.lst file that points to the primary mirror.  This is especially true if you are setting up an entire room full of machines that are not (yet) connected to the internet.  I understand why they do it, they are trying to make things easier for the noobs, but it is annoying all the same.

---

### Post by hyperair on 2008-02-11
There's a 5% amount of space kept aside for the root user in event of file system clogging. Then the root user can use that 5% to shift files around and clear up space. To free up the 5%, do this:
```
sudo tune2fs -r 0 /dev/sda1
```

Replace /dev/sda1 with whatever partition you have.

---

### Post by mauser on 2008-02-11
Hello Folks,

Wow...  I have tried various other distro's on this laptop, and 7.10 with some reading/searches I have gotten everything running great.  I am sorry to have read about your plight.  

HP/Compaq C551NR my $399 Best Buy Special.   :)

---

### Post by ukripper on 2008-02-11
I like the subject! Never had any such problems.

---

### Post by ebharv on 2008-02-11
I've installed Ubuntu on my Desktop 4 times 6.06, 7.04,  7.10, and 7.10 64bit, each time was a clean install not an update. I've never had any problems within any of them. So far it has been the easiest OS install I've ever done, including Win95, 98, 98SE, XPSP2, [Mandriva]("http://www.mandriva.com/"), and [Sabayon]("http://www.sabayonlinux.org/"). If I can recall correctly, each one of these OS has had more than 6 steps before the OS starts to install. And while it may not display how much time is left, (but I think it does) it does show a installation meter and percentage done. 

Throughout the OS installs Mandriva, crashed  twice, Sabayon took longer but it was as easier than all but Ubuntu. It [[Sabayon]("http://www.sabayonlinux.org/")] does have a much more intriguing default look though.  (just didn't like the packaging system might try it again later). It takes hours to update Windows drivers, software, etc. Not to mention the viruses, spam, malware, and other nonsense aimed at Windows machines that you absolutely must protect yourself from. That's why I left Windows, well at least for home computing anyway.

I think Ubuntu is the best\\:D/.

---

### Post by ukripper on 2008-02-11
> **ebharv said:**
> 

I think Ubuntu is the best\\:D/.

Can't agree more!

---

### Post by dr340 on 2008-02-11
**why was the installer trying to connect to the internet? **

Ignoring it.:guitar:

It took me 1 mouth to play the ubuntu well,and I installed it again and again...:)But finally everything is OK!

I really like it, UBUNTU.

---

### Post by karellen on 2008-02-11
installed gutsy today. true for the mirror scanning stuff. otherwise it worked ok, the livecd installer never failed me

---

### Post by HappyFeet on 2008-02-11
> My conclusion: Ubuntu is still bad. Gonna check it again in a couple of years
if it was that bad, there wouldnt be millions of users.

---

### Post by zugu on 2008-02-11
> **HappyFeet said:**
> if it was that bad, there wouldnt be millions of users.

Using your reasoning, I come to the conclusion that Windows XP is the best operating system ever.

OTOH, I think I'll submit a bug against the installer about the mirror-scanning thingy.

---

### Post by stchman on 2008-02-11
> **zugu said:**
> I have used Ubuntu 5.10 and 6.06 for more than a year. Sometime ago I dumped Ubuntu because it didn't allow me complete freedom in installing binary packages.

Anyway, I decided to install it yesterday, just to see how things are going.

I have 2 Ethernet cards, both PCI, and my connection to the internet is wired through one of these cards. The LiveCD displayed the cards as eth0 and eth1, but I had no means of telling which is which. I should mention that my internet settings have to be manually input, so I was unable to set up the connection.

Well, that wasn't a problem as I was just going to install Ubuntu, right? At 82% progress, the installer said something about *Scanning the mirror...* . Now this is weird. **What mirror? Why does it need scanning?** And most importantly, I had no internet connection set up, **why was the installer trying to connect to the internet?** I waited 20 minutes before giving up and closing the installer.

At reboot time, the Windows XP NTLDR was missing (as I was trying to install a dual-boot system). Thanks to the Windows XP Recovery Console I was able to restore Windows.

Overall, Ubuntu was a bad experience. Why can't the developers add a freaking check for active internet connections when the installer starts? **Why is an internet connection needed at install time?**

The LiveCD environment is rough and unpolished. I wonder why the screensaver is active and starts when the Ubuntu installer is middle through its job, even if the video card is not properly installed and configured, resulting not in a screensaver, but in a black screen. I wonder why Gparted, after applying the tasks given scans the hard drive and then **suddenly exists**, as if it crashed (I don't think it crashed, but inexperienced users might think it did). I wonder why is there no estimate of the time needed to complete the overall installation. And so on. Small things make all the difference in the world. Unpolished is the word of the day.

And then, of course, there's my fundamentally different view on how package management should be done, but that's another story.

As a side note, Gparted is plain awful: I told it to create an ext3 partition, it bragged about formatting it and then the Ubuntu installer told me the partition needed formatting. And it surely wasn't formatted, because 212 MB of disk space on it was used. I don't know by what, who or why, but I swear it was freshly created and "formatted".

On a personal note, I very much dislike the current 7.10 default look, 6.06, or even 7.04 were much better, IMHO.

My conclusion: Ubuntu is still bad. Gonna check it again in a couple of years.

You are free to not use it.  I find the OS very usable and stable.  Choice is a great thing.

---

### Post by ukripper on 2008-02-12
> **zugu said:**
> Using your reasoning, I come to the conclusion that Windows XP is the best operating system ever.

 
Well, it comes down to personal preference. In your opinion XP is the best but for someone it would differ. Depends on what you want your operating system to do if it does it well then that is the best one!

---

### Post by hyperair on 2008-02-12
I believe you just missed the point! zugu said that.. if "if it was that bad, there wouldnt be millions of users." was true, then Windows XP is the best operating system ever, because it's got the most users.

---

### Post by lespaul_rentals on 2008-02-13
Okay...bye, I guess?

---

