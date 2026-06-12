---
title: "Dansguardian GUI and Mepis"
date: 2007-07-22
forum: Ubuntu Christian Edition
---

### Post by historyb on 2007-07-22
Hi,

I did a search but can't find any info on it. I installed the script of dansguardian with GUI and can't find it. Does anyone know where it might be?

---

### Post by tak1150 on 2007-07-23
The script is here;

[http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html]("http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html")

Is this what you needed?

---

### Post by historyb on 2007-07-26
No, thank you though. I got that I just couldn't find it on my system.

---

### Post by tak1150 on 2007-07-26
When you clicked on the link for e-sword installer, a pop-up should have prompted you to either save it or install it using deb package manager.

Assuming you did the latter, the e-sword installer icon should appear under accessories in the main menu (it looks like the windows start button in Ubuntu CE).

Does this help?

---

### Post by marianlibrarian on 2007-08-01
All  i want is dansguardian gui on my 6.06 dapper drake computer. I don't want christian ubuntu. Nor do I want to "convert" to chistian ubuntu.

when i 

sudo apt-get install dansguardian tinyproxy firehol

tinyproxy and firehol say okay

but dansguardian

Couldn't find package dansguardian

so i have downloaded something that looks like the zipped file of dansguardian and it still doesn' t find it. 

This worked several months ago and I do not recall being sent to "what would jesus download" site.

all I want is the dansguardian gui on dapper drake to go on a public library public use computer.

any help will be greatly appreciated. 

P.S. if it has something to do with "ensure "universe repository" is activated -- would someone please tell me where the activation thing is???

---

### Post by mhancoc7 on 2007-08-02
> **marianlibrarian said:**
> All  i want is dansguardian gui on my 6.06 dapper drake computer. I don't want christian ubuntu. Nor do I want to "convert" to chistian ubuntu.

when i 

sudo apt-get install dansguardian tinyproxy firehol

tinyproxy and firehol say okay

but dansguardian

Couldn't find package dansguardian

so i have downloaded something that looks like the zipped file of dansguardian and it still doesn' t find it. 

This worked several months ago and I do not recall being sent to "what would jesus download" site.

all I want is the dansguardian gui on dapper drake to go on a public library public use computer.

any help will be greatly appreciated. 

P.S. if it has something to do with "ensure "universe repository" is activated -- would someone please tell me where the activation thing is???

You can get the older version of the Ubuntu CE dansguardian GUI here.

[http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/previous/](http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/previous/)

Jereme

---

### Post by gulp35 on 2007-08-04
I am trying to install this Package to MEPIS 6.5 64-bit... note that the Window manager in MEPIS is KDE... so gksudo doesn't work in the "install-me" file.

I opened that script up and changed "gksudo" to "kdesu" and it fixes that problem but opens up another. 

zenity is also not installed by default in MEPIS. it might be wise to at least have a line in the install script to check if zenity is used since it is used so much.

It would be a little more helpful (at least to most of the tech heads around here) if you explained exactly what is going on with the script. I breifly looked through the ".start" script and saw nowhere that it was configured to start at boot. It would be greatly appreciated if there were an addendum to the readme that explained what the script that I was about to run was going to do to my system.

Thank you for taking the time to make this program. :)
However, I don't believe that it alone is enough to protect your children, The internet is a weird and creepy place, though there is a great wealth of knowledge there too. Talk to your kids and make sure that they feel comfortable talking to you about things they feel confused about. Setting up a content filter alone is a little too "hands-off".

sorry for the ranting, I just feel that it is an important part of raising children in this crazy mixed-up world of ours.

Thanks again,
 gulp35

---

### Post by gulp35 on 2007-08-04
ok two more dependencies..." gksu" and "gedit"...

---

### Post by gulp35 on 2007-08-04
ok now I am having issues with the GUI... in /usr/local/apps/parental-control/
the UbuntuCE_Parental_Controls file will not open in any way... It keeps on SegFaulting (gives me the same error when I change gksudo to kdesu).

```
root@[parental-control]# ./parental-control-gui.desktop
./parental-control-gui.desktop: line 1: [Desktop: command not found
./parental-control-gui.desktop: line 4: Parental: command not found
./parental-control-gui.desktop: line 5: graphical: command not found
Syntax error in project file.
Cannot preload libraries: Success
sizeof(CLASS) = 256 !
ERROR: #1: Out of memory
./parental-control-gui.desktop: line 6: 30832 Segmentation fault      Exec=gksudo /usr/local/apps/parental-control/UbuntuCE_Parental_Controls
./parental-control-gui.desktop: line 11: System: command not found
./parental-control-gui.desktop: line 11: Settings: command not found
./parental-control-gui.desktop: line 13: Parental: command not found
./parental-control-gui.desktop: line 14: graphical: command not found

```

---

