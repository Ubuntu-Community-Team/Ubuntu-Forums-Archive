---
title: "lost windows password / data retrieval with ubuntu"
date: 2008-09-15
forum: Windows
---

### Post by beginner's love on 2008-09-15
I have a Vaio laptop and decided to put a password which I forgot, and I do not have a password CD-Rom. I can reinstall the Windows Vista OS but I would in that case destroy the personal data (pictures mainly) inside the computer. I tried therefore to start the laptop with ubuntu CD and succeeded but to my surprise it seems that ubuntu cannot see the hard disk because I do not see any of my data when I go to Ubuntu file manager. Do you have an idea of what I could do?:confused:
Looking for legal solutions (otherwise this thread will be closed anyway)
Best regards,
Richard

---

### Post by Sycron on 2008-09-15
What do you mean it does not see. Please post the output of ```
sudo fdisk -l
```

---

### Post by oilchangeguy on 2008-09-15
> **beginner's love said:**
> I have a Vaio laptop and decided to put a password which I forgot, and I do not have a password CD-Rom. I can reinstall the Windows Vista OS but I would in that case destroy the personal data (pictures mainly) inside the computer. I tried therefore to start the laptop with ubuntu CD and succeeded but to my surprise it seems that ubuntu cannot see the hard disk because I do not see any of my data when I go to Ubuntu file manager. Do you have an idea of what I could do?:confused:
Looking for legal solutions (otherwise this thread will be closed anyway)
Best regards,
Richard

i'm not sure about vista. but with xp if you'll start the computer, and press f8 until a menu appears, then select safe mode. when the welcome screen appears it will show an admin id and the other user id's. click on the admin id (hopefully this is not password protected as well) then go to the control panel, user accounts, select the user account you need to change, and change or remove the password for that account. like i said, not sure if the steps are the same for vista.

---

### Post by Steve1961 on 2008-09-15
> **Sycron said:**
> What do you mean it does not see. Please post the output of ```
sudo fdisk -l
```

I work as an IT technician and often have to recover windows passwords.  The best bet is to download the [ophcrack]("http://ophcrack.sourceforge.net/") live cd.  Just boot from the cd and it will automatically read the password hashes.  After about 5 minutes you should have your password.

Failing that try booting into safe mode by hitting the f8 key.  Then see if you can get into the Administartor account without a password.  If so, you can change your account password to something new from there.

---

### Post by europa on 2008-09-15
There is a way to retrieve your windows password.  I'm not sure about windows vista but I have done this many times using windows xp.

There is a program called NTPassword. This program can boot off of a cdrom or floppy.  All this program does is change your windows password.  Any encrypted files will be lost.

Also, you can download your SAM file (if you can get access to your drive) and use a program such as l0phtcrack to decrypt your password.

I'm not sure about accessing your hard drive but i think it auto-mounts it somewhere. If not im sure you can find a mount command somewhere on the forum.

---

### Post by beginner's love on 2008-09-15
> **oilchangeguy said:**
> i'm not sure about vista. but with xp if you'll start the computer, and press f8 until a menu appears, then select safe mode. when the welcome screen appears it will show an admin id and the other user id's. click on the admin id (hopefully this is not password protected as well) then go to the control panel, user accounts, select the user account you need to change, and change or remove the password for that account. like i said, not sure if the steps are the same for vista.

It was a new computer, only one user me and it is also the administrator and I put the password to access it, that's the PB.

---

### Post by beginner's love on 2008-09-15
[QUOTE=Steve1961;5792979]The best bet is to download the [ophcrack]("http://ophcrack.sourceforge.net/") live cd.  Just boot from the cd and it will automatically read the password hashes.  After about 5 minutes you should have your password.

My system is Vista, I only used ubuntu to get access to my data. So if I understand you well, I do not need ubuntu to get the password, just I need to boot from a CD with the ophcrack live?
Thanks a lot

---

### Post by Steve1961 on 2008-09-15
> **beginner's love said:**
> [QUOTE=Steve1961;5792979]The best bet is to download the [ophcrack]("http://ophcrack.sourceforge.net/") live cd.  Just boot from the cd and it will automatically read the password hashes.  After about 5 minutes you should have your password.

My system is Vista, I only used ubuntu to get access to my data. So if I understand you well, I do not need ubuntu to get the password, just I need to boot from a CD with the ophcrack live?
Thanks a lot

That's right.  There's an xp version and a vista version.

---

### Post by beginner's love on 2008-09-15
> **Sycron said:**
> What do you mean it does not see. Please post the output of ```
sudo fdisk -l
```

It does not recognize the windows file and repertories on the hard disk, so when I go to places I do not see any of my files...

Not sure to understand what you mean also by "please post the output of ```
sudo fdisk -l
```"?????

---

### Post by oilchangeguy on 2008-09-15
> **beginner's love said:**
> It does not recognize the windows file and repertories on the hard disk, so when I go to places I do not see any of my files...

Not sure to understand what you mean also by "please post the output of ```
sudo fdisk -l
```"?????

trying to get your password by using ubuntu is not going to work. just use the password cracking cd from the link another poster provided. you're wasting time by posting the output of this and that. there's no point.

---

### Post by tarps87 on 2008-09-15
Open the terminal under applications -> accessories -> terminal and type
```

sudo fdisk -l
```
(That's a lower case L)
your drive will probably be mounted automaticaly, it will probably have the drive size in the name

---

### Post by Sycron on 2008-09-15
Go to a terminal Applications--Accesories--Terminal,then type ```
sudo fdisk -l
```

And copy-paste the lines after ***sudo fdisk -l*** ...

---

### Post by beginner's love on 2008-09-15
> **Steve1961 said:**
> [QUOTE=beginner's love;5793044]

That's right.  There's an xp version and a vista version.

And I will not only get my passwork back but also the data stored previously on the hard disk? There is no risk of loosing them by running this opcrack software as a boot?

---

### Post by 0004tom on 2008-09-15
Anyone who know's about installing a Windows OS, knows that if you overwrite a previous windows OS then the Windows Installation process copys the orignal files, and puts then in a folder called "windows.old"

Then you could have got your personal data back that way, then deleted the "windows.old" floder, to free space.

---

### Post by tarps87 on 2008-09-15
> **oilchangeguy said:**
> trying to get your password by using ubuntu is not going to work. just use the password cracking cd from the link another poster provided. you're wasting time by posting the output of this and that. there's no point.

The point in the fdisk is the OP asked how to get the data off, not how to get the password. Although both are valid solutions to the problem.

---

### Post by Sycron on 2008-09-15
No, you will get the data back...

---

### Post by Steve1961 on 2008-09-15
> **beginner's love said:**
> [QUOTE=Steve1961;5793058]

And I will not only get my passwork back but also the data stored previously on the hard disk? There is no risk of loosing them by running this opcrack software as a boot?

All ophcrack does is boot up a live linux environment with the tools pre-loaded to read password hashes.  It won't change your system in any way, it will just read the passwords.  The live cd is configured so that once it starts it goes to work.  You'll probably need to leave it to do its job for about 5 minutes but no user interaction is required.  Once you have the password just reboot into windows and log in.  Simple as that.

---

### Post by aysiu on 2008-09-15
This may help you:
[How to reset a Windows XP password with Ubuntu](http://www.psychocats.net/ubuntucat/how-to-reset-a-windows-xp-password-with-ubuntu/)

---

### Post by Steve1961 on 2008-09-15
> **aysiu said:**
> This may help you:
[How to reset a Windows XP password with Ubuntu](http://www.psychocats.net/ubuntucat/how-to-reset-a-windows-xp-password-with-ubuntu/)

I didn't know about that!  Very useful, thanks :)

---

### Post by beginner's love on 2008-09-15
Dear aysiu, thanks a lot for this answer however I use windows Vista, do you think it works also?

---

### Post by aysiu on 2008-09-15
> **beginner's love said:**
> Dear aysiu, thanks a lot for this answer however I use windows Vista, do you think it works also?
According to the *chntpw* homepage, it's supposed to work for both XP and Vista: > This is a utility to (re)set the password of any user that has a valid (local) account on your Windows NT/2k/XP/Vista etc system.  I have used it on only XP, though.

At the very least, you should be able to mount the Vista partition and copy over your files.

---

### Post by houbysoft.xf.cz on 2008-09-15
The ophcrack CD will work. Just burn it under Ubuntu, and boot it. Like I said in the thread that was closed.

---

### Post by beginner's love on 2008-09-16
> **Sycron said:**
> Go to a terminal Applications--Accesories--Terminal,then type ```
sudo fdisk -l
```

And copy-paste the lines after ***sudo fdisk -l*** ...

I tried this command yesterday and I cannot copy-paste the result to send it to you on this forum (I use ubuntu live CD to access my laptop but no other application is installed like openoffice and... I never used Linux before!).

Appears on the list one NTFS partition located at /dev/sda2.

So, from there what should I do? Is it my drive? How can I access the data I want to retrieve (pictures only, which were located on my windows partition C: in "My Pictures" directory) and how do I copy them to an external hard-disk?
:guitar:

---

### Post by beginner's love on 2008-09-16
> **europa said:**
> 
There is a program called NTPassword. This program can boot off of a cdrom or floppy.  All this program does is change your windows password.  Any encrypted files will be lost.

Also, you can download your SAM file (if you can get access to your drive) 

I'm not sure about accessing your hard drive but i think it auto-mounts it somewhere. If not im sure you can find a mount command somewhere on the forum.

Q1: I checked the NTPassword on google, it does not seem available for Vista
Q2: what is a SAM file and how you download it?
Q3: How do you know your hard drive is automounted? Does it mean it appears in "places"? This is not the case for me. How do you mount it then?
:popcorn:

---

### Post by tarps87 on 2008-09-16
This is probably your hard drive, you can check by looking at the size of the partition. If you are trying to save the output you can type ```

gedit [\code] in a terminal, sorry I can't remember what menu its under.
In the file explorer type thing there should be a icon of a pc and label computer or system clicking this may list the hard drive if not you will need to mount it manualy.
I will post the exact command when I get home, but is something like
[code]sudo mount ntfs /dev/sda2 /media/name[\code]
/media/name is a folder you have created in the media folder
[code]mkdir /media/name
```
I will be home in about 2hrs so will check it then

---

### Post by beginner's love on 2008-09-16
Thanks so much, will keep on line:KS

---

### Post by beginner's love on 2008-09-16
> **houbysoft.xf.cz said:**
> The ophcrack CD will work. Just burn it under Ubuntu, and boot it. Like I said in the thread that was closed.

I just did this and you have the oprah window opening asking you which mode you want: graphic, graphic VESA or text. Before I had time reading (I think default mode is graphic), the routine was launched and after a few minutes, the disappointing result appears in a text-like window entitled launch.sh: No partition containing hashes found!
I just opened a bottle ov wisky

---

### Post by beginner's love on 2008-09-16
> **tarps87 said:**
> This is probably your hard drive, you can check by looking at the size of the partition. If you are trying to save the output you can type ```

gedit [\code] in a terminal, sorry I can't remember what menu its under.
In the file explorer type thing there should be a icon of a pc and label computer or system clicking this may list the hard drive if not you will need to mount it manualy.
I will post the exact command when I get home, but is something like
[code]sudo mount ntfs /dev/sda2 /media/name[\code]
/media/name is a folder you have created in the media folder
[code]mkdir /media/name
```
I will be home in about 2hrs so will check it then

to save the output what command you type after the prompt? what is [\code] and [code]?

---

### Post by az on 2008-09-16
> **Steve1961 said:**
> The best bet is to download the [ophcrack]("http://ophcrack.sourceforge.net/") live cd.  Just boot from the cd and it will automatically read the password hashes.  After about 5 minutes you should have your password.


[http://packages.ubuntu.com/hardy/ophcrack](http://packages.ubuntu.com/hardy/ophcrack)

Ophcrack is already in Ubuntu.  No need to download another live cd.  Just boot the Ubuntu live cd and install it from the add/remove programs menu.

---

### Post by beginner's love on 2008-09-16
> **tarps87 said:**
> This is probably your hard drive, you can check by looking at the size of the partition. If you are trying to save the output you can type [code]
gedit [\code] in a terminal, sorry I can't remember what menu its under.

There is progress I saved the output and attached it to this message (plain text document):)

---

### Post by tarps87 on 2008-09-16
> **beginner's love said:**
> to save the output what command you type after the prompt? what is [\code] and ```
?

Buy [code] gedit [\code]
I meant [code]
gedit 
```

Edit:
Sorry its a bit later than I said.
try:
```
 sudo mkdir /media/vista 
```
This makes as new directory, sudo gives you root permissions. Then:
```
 sudo mount -t ntfs /dev/sda2 /media/vista 
```
This mounts the drive sda2 with the format ntfs (this is read only ntfs-3g will allow read/write but this needs installing separately). It will be mounted to /media/vista. Typing:
```
 nautilus /media/vista 
```
Will open the file explorer (nautilus) where your vista drive is. This next step will be copping the data off, what are you planing on copping it onto

---

### Post by beginner's love on 2008-09-16
> **aysiu said:**
> This may help you:
[How to reset a Windows XP password with Ubuntu](http://www.psychocats.net/ubuntucat/how-to-reset-a-windows-xp-password-with-ubuntu/)

Dear Aysiu, I tried this but was blocked when I reloaded in Synaptic package manager: there is no access to internet with firefox on my ubuntu live CD. What should I do?:confused:

---

### Post by aysiu on 2008-09-16
> **beginner's love said:**
> Dear Aysiu, I tried this but was blocked when I reloaded in Synaptic package manager: there is no access to internet with firefox on my ubuntu live CD. What should I do?:confused:
Transfer the installer files from another computer with a USB stick.

---

### Post by beginner's love on 2008-09-16
> **aysiu said:**
> Transfer the installer files from another computer with a USB stick.

sorry, installer files for firefox? where to find?

---

### Post by beginner's love on 2008-09-16
> **tarps87 said:**
> Buy ```
 gedit [\code]
 Then:
[code] sudo -t ntfs /dev/sda2 /media/vista 
```
This mounts the drive sda2 with the format ntfs (this is read only ntfs-3g will allow read/write but this needs installing separately). It will be mounted to /media/vista. Typing:
```
 nautilus /media/vista 
```
Will open the file explorer (nautilus) where your vista drive is. This next step will be copping the data off, what are you planing on copping it onto

I tried but I get the message attached. If you find the solution, I promiss to send you a single islay malt bottle!:(

---

### Post by aysiu on 2008-09-16
> **beginner's love said:**
> sorry, installer files for firefox? where to find?
No, installer files for *chntpw*

You might have missed this part in the middle of the tutorial: > That method for installing chntpw assumes you have a working internet connection on the computer in question. If you don&#8217;t (or regularly do, but not when you boot the Ubuntu CD), you can also download chntpw from [one of these mirrors](http://packages.ubuntu.com/hardy/i386/chntpw/download), transfer it to the computer in question (via USB stick), and then double-click the download file to install it. 

---

### Post by tarps87 on 2008-09-17
> **beginner's love said:**
> I tried but I get the message attached.

I can't find the attachment. was it the sudo mount or the nautilus command that caused it?

---

### Post by beginner's love on 2008-09-17
> **tarps87 said:**
> I can't find the attachment. was it the sudo mount or the nautilus command that caused it?

Hi,
I attach the terminal screen output (two txt files) which appear after I type fdisk -l (txt file named "unsaved document 1") and, respectively sudo mount -t ntfs /dev/sda2 /media/vista (txt file named "output").
What can I do next?
:confused:

---

### Post by europa on 2008-09-25
> **beginner's love said:**
> Q1: I checked the NTPassword on google, it does not seem available for Vista
Q2: what is a SAM file and how you download it?
Q3: How do you know your hard drive is automounted? Does it mean it appears in "places"? This is not the case for me. How do you mount it then?
:popcorn:

[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

"Forgot your Windows NT/2k/XP/Vista admin password?
Reinstall? Oh no... But not any more... "

---

### Post by tarps87 on 2008-09-26
NTFS signature is missing.
This sounds like it can't understand the drives partition data or the windows partition, this is why it didn't auto mount. Do you know what is on the other partition?
If you haven't made any changes since you lost the password, e.g. changing the partition size, there are only to thing that I can think of that may cause this, one is the drive is encrypted but I don't think this is likely. The other windows was improperly shut-down so it has lock the drive, this happens to be when I'm duel booting and press the reset button instead of shutting it down

---

