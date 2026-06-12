---
title: "Windows Worm - when will it end?"
date: 2009-01-21
forum: Windows
---

### Post by Tom Mann on 2009-01-21
Taken from the BBC: ([http://news.bbc.co.uk/1/hi/technology/7842013.stm]("http://news.bbc.co.uk/1/hi/technology/7842013.stm"))

> 
The Conficker virus has opened a new can of worms for security experts.

Drives such as USB sticks infected with the virus trick users into installing the worm, according to researchers.

The "Autoplay" function in Vista and early versions of Windows 7 automatically searches for programs on removable drives.

However, the virus hijacks this process, masquerading as a folder to be opened. When clicked, the worm installs itself.


The image on the BBC's website shows the Virus popping up on the autoplay menu as "Open folder to view files". This is only going to be noticed by the most eagle-eyed, cautious and otherwise (un?)lucky computer users. With OS X and Linux rising slowly-but-steadily when will they take computer security seriously?

[IMG]http://http://newsimg.bbc.co.uk/media/images/45397000/jpg/_45397705_windows_vista_open_folder_to_view_files.jpg[/IMG]

---

### Post by Sealbhach on 2009-01-21
Apparently it's very difficult to remove and it turns off the updates service once it gets in. This could go on for a long time. Apparently the people who wrote it have not exploited its full potential to harm (yet).

It's not funny when hospitals are hit by this:

> There are also reports that more than 800 computers (out of a userbase of more than 7000) from the City Hospital Network of Sheffield have been compromised by the Conficker worm as the system administrators had decided to turn off Windows security updates.

[http://network.itproportal.com/articles/2009/01/21/linux-windows-7-beta-could-be-hit-downadup-worm/](http://network.itproportal.com/articles/2009/01/21/linux-windows-7-beta-could-be-hit-downadup-worm/)



.

---

### Post by Peronix on 2009-01-21
Imagine if someone created a virus that could evolve. :-({|=

---

### Post by Sense on 2009-01-21
Using Windows has never been a wise decision when you care about security, but setting the security updates off? That sys-admin was asking for trouble. 

Linux/Ubuntu may not be as polished as Windows at some areas, but it is a lot safer. If only the common users would get to know that... ;)

---

### Post by gjoellee on 2009-01-21
It will be stopped if the worm maintainer stops the maintenance and you update Windows often.

---

### Post by piousp on 2009-01-21
> **gjoellee said:**
> It will be stopped if the worm maintainer stops the maintenance and you update Windows often.

It will stop for that person after a lot of trouble

---

### Post by unoodles on 2009-01-21
It's quite an amazing piece of software. I have been trying to get it to run in wine, but its not perfect.
I got a copy from offensivecomputing.net

---

### Post by Sealbhach on 2009-01-21
> **unoodles said:**
> It's quite an amazing piece of software. I have been trying to get it to run in wine, but its not perfect.
I got a copy from offensivecomputing.net

It's not compatible with Wine? Oh noes!!!:p


.

---

### Post by Sense on 2009-01-21
> **Sealbhach said:**
> It's not compatible with Wine? Oh noes!!!:p


.

How would WineHQ react when an AppDB entry would be created for the worm? :P

---

### Post by glotz on 2009-01-21
It will end once personal computers are no longer available to Joe and Jane Blogs.

---

### Post by MaxIBoy on 2009-01-21
> **Sealbhach said:**
> Apparently it's very difficult to remove and it turns off the updates service once it gets in. This could go on for a long time. Apparently the people who wrote it have not exploited its full potential to harm (yet).

It's not funny when hospitals are hit by this:



[http://network.itproportal.com/articles/2009/01/21/linux-windows-7-beta-could-be-hit-downadup-worm/](http://network.itproportal.com/articles/2009/01/21/linux-windows-7-beta-could-be-hit-downadup-worm/)



."I'm so sorry the defibrillator is encoding commonly-used passwords into binary and sending them through the electrodes-- it has a virus."

If someone dies because this, the virus makers need to be sentenced to life in prison for first-degree murder.

---

### Post by gletob on 2009-01-21
I'm glad I just got this wifi dongle so I can go back to Ubuntu full time.

---

### Post by Skripka on 2009-01-21
> **Sense said:**
> Using Windows has never been a wise decision when you care about security, but setting the security updates off? That sys-admin was asking for trouble. 


damn.  THAT is a bone-headed sys-admin right there.

---

### Post by 3rdalbum on 2009-01-21
If it "tricks users into installing the worm", then it's not a worm, it's a trojan.

A worm gets into the computer without any human input.

I'd like to hope that viruses will finally end when software companies take security seriously, everyone from primary school upwards gets taught how to safely use their computer, and Windows users stop treating computer security as "Buy this software that will sap your CPU power".

---

### Post by cardinals_fan on 2009-01-21
> **3rdalbum said:**
> 
i'd like to hope that viruses will finally end when software companies take security seriously, everyone from primary school upwards gets taught how to safely use their computer, and windows users stop treating computer security as "buy this software that will sap your cpu power".
+1

---

### Post by jrusso2 on 2009-01-21
> **Skripka said:**
> damn.  THAT is a bone-headed sys-admin right there.

Most large corporations will leave auto updates off.  They need to be tested that they don't break anything before we can take a chance on installing them.

---

### Post by CBNorrie on 2009-02-01
In the world out there outside of the Linux community there is virtually nobody telling Windows users that they can avoid malware infections by installin Ubuntu as their OS.  You can check this in Google News by typing Conficker and Ubuntu into the search box and see how many hits you get.

Please help set up a viral marketing campaign by politely and informatively telling Windows users how they can avoid malware forever.

---

### Post by tsali on 2009-02-01
It's worth mentioning that "autoplay" is not enabled by default in a new retail Vista install.

I leave it off.

---

### Post by bakedbeans4life on 2009-02-01
> **CBNorrie said:**
> In the world out there outside of the Linux community there is virtually nobody telling Windows users that they can avoid malware infections by installin Ubuntu as their OS.  You can check this in Google News by typing Conficker and Ubuntu into the search box and see how many hits you get.

Please help set up a viral marketing campaign by politely and informatively telling Windows users how they can avoid malware forever.

I have given up trying to educate Windows users about the dangers of blindly clicking every pop-up while running as admin all the time. Some of Microsoft's design and architecture decisions are questionable, but even they try to mitigate against many of the dumbass actions of their userbase.

Linux has had me tearing my hair out trying to get a simple usb wi-fi dongle working, even though it's supposed to be supported. The odd half functional driver aside, you can't say Linux security is quite as bad as Windows. I just wish Microsoft would take something from *NIX as far as operating system building blocks and infastructure go (executable binaries by file extension alone, I'm looking at you).

Preaching from the Linux pulpit to the Windows choir will get you nowhere. I know I tried, it always ends in failure. These days I simply refuse to apply plasters, bandages and splints to Windows machines when the owner can't even be bothered to keep their anti-virus software up to date.

I'll take my rant cap off now and place it next to the tin-foil one.

---

### Post by cmat on 2009-02-02
> **Sense said:**
> Using Windows has never been a wise decision when you care about security, but setting the security updates off? That sys-admin was asking for trouble. 

Linux/Ubuntu may not be as polished as Windows at some areas, but it is a lot safer. If only the common users would get to know that... ;)

Windows is safe under the right practises. Unfortunately most IT guys I've walked into with various Microsoft certifications don't know how to manage PCs if their life depended on it. It boils down it either being to complicated or time consuming. Someone should teach these guys how to use DCOM properly instead of them sipping coffee all day in the nice A/C server room and blaming downtime on the hardware.

I did do some IT work for a few months. I remember making an application to admin the PCs with great success. Dear God I hope they aren't still using it. I haven't written a patch for years. D:

---

### Post by PB_G3 on 2009-02-08
> **cmat said:**
> Windows is safe under the right practises. Unfortunately most IT guys I've walked into with various Microsoft certifications don't know how to manage PCs if their life depended on it. It boils down it either being to complicated or time consuming. Someone should teach these guys how to use DCOM properly instead of them sipping coffee all day in the nice A/C server room and blaming downtime on the hardware.

I did do some IT work for a few months. I remember making an application to admin the PCs with great success. Dear God I hope they aren't still using it. I haven't written a patch for years. D:

lol ;)

---

