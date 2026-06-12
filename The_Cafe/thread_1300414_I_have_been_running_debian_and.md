---
title: "I have been running debian and"
date: 2009-10-25
forum: The Cafe
---

### Post by kixome on 2009-10-25
I noticed debian lenny is a bit faster than all the ubuntu's I have tried, and i am wondering: 

1. why is this? ubuntu is based on debian so why is it slower for me.
2. Are the ubuntu guys just changing too many packages/scripts.
3. does ubuntu have more processes running?
4. How much do they really change in ubuntu, vs debian?
5. Does anyone know the questions to all those answers?
6. (generally /not just related to debian) How do I get a manually installed program to be recognized universally at the command line. (I.E.) pidgin/firefox so that a launcher I create only needs the name of the program?

7.How do i get a program do be the default for something i double click, I.E. .txt file = open gedit?

---

### Post by cariboo on 2009-10-25
You didn't mention what desktop you are using, Gnome is Gnome no matter what distribution you are using.

---

### Post by Warpnow on 2009-10-25
Debian's gnome does not have compiz by default, though.

Debian simply has fewer packages by default than ubuntu. Command line installs of both with the same set of packages would be identical.

---

### Post by renkinjutsu on 2009-10-25
i run debian in a VM, so i can't really compare

also, to get your programs universally recognized, you usually dump it into a bin folder, or symlink it or maybe even add the whole directory to your PATH variable

---

### Post by JillSwift on 2009-10-25
Have you quantified this, or is this based on personal perception?

---

### Post by gnuisancev3 on 2009-10-25
> **cariboo907 said:**
> You didn't mention what desktop you are using, Gnome is Gnome no matter what distribution you are using.
Ubuntu does provide modifications to gnome that other distros do not.

---

### Post by kerry_s on 2009-10-25
i don't think you should mix a poll with help questions. pick 1 or the other next time.

> How do I get a manually installed program to be recognized universally at the command line. (I.E.) pidgin/firefox so that a launcher I create only needs the name of the program?

create a "bin" folder in you home & put or link the executables there.

> How do i get a program do be the default for something i double click, I.E. .txt file = open gedit? 

right click properties-> open with


i'm currently using debian lenny xfce4

---

### Post by misfitpierce on 2009-10-25
I marked no cause I tried Debian... forgot which one but at the time it had no difference really in speed compared to the Ubuntu I was running. Forgot which it was for both... Maybe 2 releases ago or so. It didn't seem to have speed differences to me so it was whatever. Maybe something just not set up and running on Debian like compiz and you getting speed boost from that, who knows.

---

### Post by lisati on 2009-10-25
> **kixome said:**
> 5. Does anyone know the questions to all those answers?
What is the ultimate question of life, the universe and everything, to which the answer is 42?

Sadly my experience of Debian is largely limited to the derivative known as Ubuntu.

---

### Post by renkinjutsu on 2009-10-25
Also, there are people that report speed improvements by switching to Ubuntu derivatives, like Mint .... it seems like everything that's **NOT** Ubuntu is faster

could be all just placebo effect though.

---

### Post by unknownPoster on 2009-10-25
> **Warpnow said:**
> Command line installs of both with the same set of packages would be identical.

Assuming you only use their respective default repositories, I'd have to disagree. I'd imagine that the kernels would be different as Ubuntu patches it quite a bit. As a matter of fact, Ubuntu patches quite a bit from upstream, so they would not be identical.

---

### Post by misfitpierce on 2009-10-25
> **renkinjutsu said:**
> Also, there are people that report speed improvements by switching to Ubuntu derivatives, like Mint .... it seems like everything that's **NOT** Ubuntu is faster

could be all just placebo effect though.

Exactly... I have heard that with Mint as well but when I ran Mint and actually documented specs and timed things some things were even slower than Ubuntu... It may seem it when you go onto a new OS and then again some things may be faster and some slower depending on how they have their app's set up and they may not have as much stuff starting on boot which makes startup faster etc but overall they are all about the same speed if all using the same kernel with same app's and same GUI ex: Gnome, KDE, Fluxbox, etc etc.

---

### Post by mkendall on 2009-10-25
> **kixome said:**
> 7.How do i get a program do be the default for something i double click, I.E. .txt file = open gedit?

Right click on a file of the type you want to set, select Properties, then choose your "Open With" option. This sets the system for all files of that type.

---

### Post by kixome on 2009-10-25
i am using gnome, and no gnome is faster on debian (much snappier) the same with kde and slackware.

---

### Post by kixome on 2009-10-25
> **mkendall said:**
> Right click on a file of the type you want to set, select Properties, then choose your "Open With" option. This sets the system for all files of that type.


thank you very much
one of those really simple things i happened to miss by trying to be to complex.

---

### Post by kixome on 2009-10-25
oh, the gnome thing may be because debian uses an older version.

---

### Post by kixome on 2009-10-25
> **renkinjutsu said:**
> i run debian in a VM, so i can't really compare

also, to get your programs universally recognized, you usually dump it into a bin folder, or symlink it or maybe even add the whole directory to your PATH variable

thank you as well!

---

### Post by kixome on 2009-10-25
> **renkinjutsu said:**
> Also, there are people that report speed improvements by switching to Ubuntu derivatives, like Mint .... it seems like everything that's **NOT** Ubuntu is faster

could be all just placebo effect though.

i have never tried the derivatives? but debian and slack both seem a bit snappier to open programs, and I haven't enabled compiz on debian or ubuntu though in ubuntu it is installed, and both of the alternative distro's just snap faster. I think it may be because they arent afraid to use a larger memory footprint, I.E. ubuntu for me uses 268M while debian uses 340M and slack (with xfce) uses 280M

---

### Post by kixome on 2009-10-25
here is the main beat all for me: the distro, no matter which one must run hulu in 1280X1024 fullscreen without chopping on an hpa630N/2.8ghzHT intel/1.7gigs ram/ WD sata 2X 40Gig/ intel 915 graphics and chipset. Debian does with firefox 3.5 and flash 10. The same applies to slack. Ubuntu 8.04-9.10 has not been able to do this. The only way I can get fullscreen to play decently at flash video sites, not just hulu, is to change resolution to 1024X768 and set the video to low quality, even with shiretoko/firefox 3.5.3 installed and flash 10. 
There is no hope for it to work for me with firefox 3.0.x and flash 10. Tried that and ubuntu would not do it. Slack 12.2 would, did not try in debian.

---

### Post by kixome on 2009-10-25
> **JillSwift said:**
> Have you quantified this, or is this based on personal perception?

quantified it!

---

### Post by kixome on 2009-10-25
> **kerry_s said:**
> i don't think you should mix a poll with help questions. pick 1 or the other next time.



create a "bin" folder in you home & put or link the executables there.



right click properties-> open with


i'm currently using debian lenny xfce4


If the option is there, then that is a matter of opinion and the option should't be there if you didn't want me to do it. Take the option away and i won't do it, or subcategorize the forums where you cannot do this I.E. help or poll, but when i go to submit and it asks do i want to include a poll, and I do, then I am just exercising my rights the same as I would with a cop.

---

### Post by kerry_s on 2009-10-25
> **kixome said:**
> If the option is there, then that is a matter of opinion and the option should't be there if you didn't want me to do it. Take the option away and i won't do it, or subcategorize the forums where you cannot do this I.E. help or poll, but when i go to submit and it asks do i want to include a poll, and I do, then I am just exercising my rights the same as I would with a cop.

i'm just saying it makes it confusing, when others are searching for the same answers & they see the poll.

but your right the choice is yours & you have every right to do it the way you want. :)

---

### Post by Exodist on 2009-10-25
I havnt got debian to install yet.. Something quirky with their installer and having a seperate /home folder on a separate drive.

---

### Post by kixome on 2009-10-29
what distro, I use lenny and have the home folder on a serperate drive, though my drives are exact same type, size, format wd sata 40gig

---

### Post by kixome on 2009-10-29
Also an update, i am starting to think it is the gvfs-fuse daemon that is slowing ubuntu, debian, and slack seem to use the filesystem correctly where-as ubuntu reads everything as a scsi drive, I was wondering if this had something to do with fuse or the kernel. Also I notice desian has nothing mounted with fuse.

---

### Post by kixome on 2009-10-29
> **kerry_s said:**
> i'm just saying it makes it confusing, when others are searching for the same answers & they see the poll.

but your right the choice is yours & you have every right to do it the way you want. :)

10-4 didn't mean to throw a hissy, I am used to other forums where they would ban you for questioning their authority, so I took it the wrong way. I understand what you meant now.

---

