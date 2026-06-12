---
title: "Virus? No, thank you"
date: 2009-02-16
forum: Testimonials &amp; Experiences
---

### Post by gabo.cr on 2009-02-16
So there is a very weird file or (window$ virus-malware?) bugging everybody in my town.
Almost everybody has it, and no one can delete it, not even formatting!
They get it by just connecting the flash drive in an infected computer, and it stays there doing nothing but taking a lot of space out of the USB drive. (and I mean a lot).
So I took my brother's flash drive with the virus, and tried to delete it with Ubuntu, I couldn't do it from the GUI.
So I changed the file rights using **chmod** in terminal. I was able to delete that weird file and of course, that was not the last time I had to do it after that day.
One more reason to keep using Ubuntu.
:guitar:

---

### Post by HotShotDJ on 2009-02-16
> **gabo.cr said:**
> So there is a very weird file or (window$ virus-malware?) bugging everybody in my town.
Almost everybody has it, and no one can delete it, not even formatting!
They get it by just connecting the flash drive in an infected computer, and it stays there doing nothing but taking a lot of space out of the USB drive. (and I mean a lot).Sounds like U3

---

### Post by damis648 on 2009-02-16
Just install gparted:
```
sudo apt-get install gparted
```
and then launch it
```
gksudo gparted
```
and then select any flash drive to clear and delete all the partitions and then create one brand new one.

---

### Post by gabo.cr on 2009-02-16
Gparted didn't work either.
I'm telling you that file is weird !

:D

---

### Post by yther on 2009-02-16
I've been hearing about some nasty malware that spreads via USB drives, then sometimes causes the infected Windows box to not get on the Internet.  My company distributes a lot of documents on thumb drives, so last week when I got some back, I decided to use my laptop (running Kubuntu of course) to format them.  :)

Not only is it much faster (plug in, wait for automatic popup so I know it's recognized, "mkdosfs -F 32 /dev/sdb1", wait two seconds, yank it out) but I have no worries about my system getting infected by anything that might be on there!  On Windows I have to plug it in, wait like 5 seconds for a window to pop up, then disappear, then pop up again; close window myself; right-click the drive and hit Format, etc.  Hooray for CLI tools!  ;)

---

### Post by Tamlynmac on 2009-02-16
:shock:


I'm shocked - A Windows Virus. 



All this time I've been deceived - I feel so violated. 



No doubt, it will require years of structured support simply to overcome this or I could just continue using Ubuntu. :wink:

---

