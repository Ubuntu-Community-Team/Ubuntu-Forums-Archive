---
title: "Will a Flush and Fill Kill Rootkits?"
date: 2016-10-30
forum: Security
---

### Post by poisonfor3 on 2016-10-30
New to Ubuntu and Linux but not computers in general. Trying to learn a little more about how to keep free of rootkits. I have searched this site and the web. It is an endless topic and I do not want to go to far down that rabbit hole here. Yet I am puzzled a bit about some things that I just can not seem to find and please tell me if I am thinking right on this. 

Running with the idea that you have downloaded a nice clean Ubuntu and have it on a DVD-R.

I am thinking that it is better to NOT make a clone of your Hard Drive as a way to back up (Albeit the most simple and easy way) BUT to backup just what you need like the home folder and a few other select things and then put a new up-to-date OS on your hard drive. This is what I have been doing since the dawn of the XP age to help keep my computer clean. Would this get rid of any rootkits? 

I am thinking they do not hide in your home folder I am thinking they are at a much lower level under the OS.

Now I have a 1TB SSD. So if a rootkit is hiding under the OS I can not just Format the SSD like the old HDDs can I? Even if I could would that be of any use?

What are the Odds of the Rootkit being hiding in say the Keyboards or Video Card? I have read that it can be done but is that in the wild or just something that is only in the lab and/or Nation States are going?

Since they are "under" the OS. AND the OS is what tells/give your computer the program language to run in. What program language are rootkit made in? Surely no one wrote them out by hand in "machine code" so are made in assembler language?

I know this is a topic that can get complex and I am not a programer.  :P ??? So thanks for not talking over my head to much ???   :P

-Annie

---

### Post by TheFu on 2016-10-31
Rootkits work the same on Windows as they do on other OSes. They get installed during the boot portion of system startup and have code to intercept low-level calls to prevent any programs from seeing them.  They can be hiding anywhere on any media that allows updates.  That means **anywhere** on a HDD - including HOME.

Bit-for-bit is simpler, but highly inefficient as a backup method and requires downtime to make backups of that type.  For most businesses, that is entirely unacceptable.  Only home users make backups with images.  

If you aren't a programmer, knowing what language a rootkit is written in doesn't really help.  All programs are converted to "machine code" ... so the source language doesn't matter.  Any HID (human interface device) can be used to infiltrate a computer. OSes have to trust keyboards, right? If there is physical access, all bets are off most of the time.  There are other devices that some computers trust - like USB network devices are trusted by Windows.  When a USB network adapter is plugged in, even to a locked Windows machine, drivers are loaded and code is run at the level of permissions the driver requires, automatically. A convenient way to crack any running Windows machine with just a few minutes of physical access. 

Actually, the most secure OS that I know today is ChromeOS running on a Chromebook.  This is because the OS is tied to the hardware and the entire boot process it locked down by default with signed code and TPM HW.  Odd that the company grabbing all the personal data they can from everyone in the world created the most secure platform/OS.

BTW, the way things work on Windows deep-down is different from the way things work on every other OS. Using that as the model for how computers work only gets you so far even if the GUIs appear to be similar, under the covers, there are very different architectures compared to Unix-like OSes. Almost every OS you see today that isn't Windows is based on Unix, FYI.  "Computers" doesn't automatically mean "Windows", BTW.

---

### Post by poisonfor3 on 2016-10-31
@[[COLOR=#000000] TheFu[/COLOR]]("https://ubuntuforums.org/member.php?u=1037685") 	 
						
I forgot that "All programs are converted to machine code" so the rootkit would be in machine code and written in whatever the programer wanted. Thanks for reminding me.

I did not know that about chromebook. Makes sense when you think about it. You said "Odd that the company grabbing all the personal data they can from everyone in the world created the most secure platform/OS." well . . . they want all the data in the world FOR THEMSELVES. Why would they want other people to have your information. 

That answers my questions but brings up another. I understand that rootkits can be in my home folder. Would backing up just the home folder, and then putting in new OS. Then picking the stuff I want out of the home folder when I reload my information even help. By that I mean of the KNOWN rootkits would that get rid of at least most of them and I can feel like I did something good or am I just completely wasting my time*?

*Yes a new OS would be cleaner and more up to date and thus safer and better but I am talking about wasting my time trying to get rid of rootkits and other bugs.

-thanks

---

### Post by TheFu on 2016-10-31
With Linux, a rootkit is extremely unlikely. Rootkits written for other OSes don't matter.  At that level, it has be specific to the OS.
What makes you believe you have a rootkit?  I've never actually seen one on a Unix system. I know they exist and see false positives from some of the tools claiming to find them.  

Bugs are bugs. Nothing end-users can do except report them to the appropriate project team.  I use only LTS releases and since most bugs happen in GUI code, I avoid GUI stuff.  For me, the desktop is just a way to have more terminals open so I can get more work done. ;)  Not saying a don't use a GUI for email and browsing the web and a few other things, but right now I have about 15 windows open and 5 are GUI programs, the rest are terminals into this and other systems. That is the nature of my work. I wouldn't expect my mother to use her Linux system the same way.

The chromebook comment was only about chromebooks running chromeOS.  I have a few, but don't run chromeOS, so mine are NOT as secure, though I do take steps to make them more secure than an average system.

You should have daily, versioned, backups anyways.  Anything less is a failure in my book. Versioned backups are critical from a security perspective.  Versioned backups are my #1 security technique and solve about 10,000 other issues.

If you don't trust the OS, you need to blow it away and start over.  Data isn't part of the OS, so I wouldn't worry about it, provided there aren't hidden files and directories there.

---

### Post by 1clue on 2016-11-01
I've been owned by a Linux rootkit more than once. Go read [https://www.ubuntu.com/usn/](https://www.ubuntu.com/usn/) and [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) and [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security).

After that google around for linux rootkit and pay attention.

There's a lot of misinformation out there. There's plenty of malware for UNIX-style operating systems. There's lots of vulnerabilities for software we use, and there are lots of ways that carelessness can cause something to be vulnerable that wouldn't be normally. Some of the stuff written for web browsers or documents with macro languages built-in will work the same on Linux as they work on Windows.

There's no such thing as a foolproof system. Your only defense is to educate yourself. Doesn't matter what OS you use.

---

### Post by poisonfor3 on 2016-11-13
Sorry all I was thinking this as closed and did not check back. I did enjoy your replies.

@[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685")
I believe in free speech and equal rights and governments to not like people that are vocal about such topics, so they like to spy on people that are like me. I just assume that I am being watched at all times. I know for a fact that EVERYTIME I go through the airport they search my luggage that I check in. I know this because they always leave a note in there that they searched it. I hate the idea that they are spending so much time on me and other law abiding people when there are gangs roaming the streets and terrorists bombing building and shooters killing people. BUT lets not get off topic here.


I have 3 backups. I have daily, weekly and Monthly. Albeit not 100% like that it is kinda close. I want to make one for Yearly and just store it so I will never be 100% destroyed but I am already doing so much more than most.


@[**[COLOR=#000000]1clue[/COLOR]**]("https://ubuntuforums.org/member.php?u=799622")
Yes there is no such thing as a foolproof system. Unless you made the CPU and the whole computer yourself starting from sand and made all the code yourself with no emulators, and that is just not possible for one person to do. So there will always be some level of trust and risk with anything electronic. I too have also hard that Linux OS attacks have been on the rise. I do not think it is because we are getting targeted any more per-say I think it is because Windows is getting harder to bake into. I just do not care if Windows is the hardest system in the world to bake into I want nothing to do with it anymore on so many levels. Again I am getting a little off topic here too.

---

