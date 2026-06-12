---
title: "Recommended distro(s) for P3-866 desktop?"
date: 2016-01-16
forum: Ubuntu, Linux and OS Chat
---

### Post by vector3 on 2016-01-16
[FONT=comic sans ms][FONT=arial]In searching for lightweight Linux distributions for my older desktop I find Xubuntu and Lubuntu as useful options.  I attempted to determine if my Pentium III supports PAE yet, was unable to do so definitively.  I suspect it supports PAE and referenced 1) [https://help.ubuntu.com/](https://help.ubuntu.com/) community/PAE and 2) [https://help.ubuntu.com/community/PAE/PentiumM](https://help.ubuntu.com/community/PAE/PentiumM).  The pc in question currently works on Win2k Pro so, I need to consider dual boot capability.  Please provide me with additional OS options, instructions and, references.[/FONT]


[/FONT]

---

### Post by sudodus on 2016-01-16
Welcome to the Ubuntu Forums :-)

As far as I know, all Pentium III processors support PAE.

But there are other things that make it hard to use a computer with Pentium III processor nowadays. Please read the following link

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

If your computer does not work well enough with Lubuntu, I suggest that you try some ultra-light linux distro, for example ***ToriOS***, ***Wary Puppy***, ***TahrPup*** or ***Tiny Core***.

---

### Post by ajgreeny on 2016-01-16
How much ram does it have?
You really need at least 256MB to use the graphical installer of any of the *ubunt family, but if you don't have that much there is always the [minimum-install CD]("https://help.ubuntu.com/community/Installation/MinimalCD") that can be used to install a command-line system from which, assuming you have a network connection, you can then install lubuntu-desktop package which will give you exactly the same OS as using the lubuntu iso install image.

---

### Post by vector3 on 2016-01-16
Thank you for the prompt and thorough responses.  My apologies as I should have stated this pc has 512 MB of RAM.  Clearly, there are better exercises of time but, I will read the references your provided and look for information on the lighter distro's mentioned.

---

### Post by sudodus on 2016-01-16
512 MB RAM works with Lubuntu :-)

But the graphics card/chip might be another obstable (as you can see in the link 'Old hardware brought back to life' in post #2).

---

### Post by vector3 on 2016-01-17
Yes, the graphics hardware may be an issue.  I will look into this thoroughly in a day or two.  I suspect I have 3 video cards from this vintage of pc hardware so, I should collect these and their relevant documentation before attempting to make progress analyzing this aspect of my resurrection effort.

I have read some of the information regarding Lubuntu and it appears I should utilize the alternate install procedure so, I have downloaded the iso specific to this installation method.  However, in reviewing partition issues I learned something new from my previous efforts with Linux and Windows.  This is, I will be in a better position if I install *ubuntu natively and virtualize Windows as is referenced in the introduction here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


However, I came to an abrupt end in that I was not able to substantiate how this is accomplished.  The references at the bottom of the webpage of the url I pasted above provide a lengthy list of phrases featuring the term virtualization yet, I was unable to narrow the list to a useful subset of reading material.  Can someone provide me with more specific information regarding virtualizing Windows?  I do not mind starting over because, I own the install CD.  I returned the system to life with Win2K Pro after the initial HD failed yet, never returned the backup on the HDD with new OS.  I performed my backup with Nero and a Sony dual layer dvd drive so, these 3 backup disks remain well protected and can be accessed at any time.  It may be useful for me to mention that this WD HDD was too larger (~160 GB?) for the OS so, it came with a disk utility to format the drive as a single partition.  I know I still have this WD utility/instructions so, I can integrate this into the effort as well if needed.  I suspect *ubuntu can meet these needs without the WD utility.

---

### Post by sudodus on 2016-01-17
To run Windows in a virtual machine (for example using VirtualBox) is a good idea in a fairly new and powerful machine. It is definitely not an option in your old computer with a Pentium III processor and only 512 MB RAM. Dual boot is a better alternative.

---

### Post by mörgæs on 2016-01-18
For a Pentium 3 I would not recommend Windows. None of the supported versions run on this hardware.

---

### Post by Bucky Ball on 2016-01-18
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Welcome. Virtual machine definitely not an option with that amount of RAM. [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") is probably your best option but [Xubuntu]("http://xubuntu.org/") may also work.

[Here]("http://www.ubuntu.com/download/desktop/install-ubuntu-desktop") are some instructions for installing. All you really need to do for now is create install media, boot from it, 'Try *buntu' and run a live session from install media. This will give you an idea of how an installed version is going run without changing anything on your hard drive. 

If all is good, you can use the 'Install' icon on the desktop to install to hard drive. If you have Win and are looking to dual-boot (Win on one partition, Ubuntu on the other), have a look [here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352").

* I've moved this thread because, at this point, you are asking for opinions, not technical support. If you have issues installing, by all means, post a new thread with a descriptive title and plenty of detail about your problem in a support area. Good luck. :)

---

### Post by matt_symes on 2016-01-18
Welcome to the forums vector3.

Please use the standard font when posting a message on these forums.

'comic sans' is not so easy to read on some devices.

---

### Post by help_me2 on 2016-01-18
I would recommend Puppy Linux.

---

