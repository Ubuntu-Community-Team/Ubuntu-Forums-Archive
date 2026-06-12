---
title: "World first: Live-CD that saves back to CD"
date: 2005-03-08
forum: The Cafe
---

### Post by BWF89 on 2005-03-08
[http://lxer.com/module/newswire/view/32666/index.html](http://lxer.com/module/newswire/view/32666/index.html)

---

### Post by BWF89 on 2005-03-08
It wouldn't work for me. Anyone else have luck?

---

### Post by bored2k on 2005-03-08
[QUOTE=BWF89]It wouldn't work for me. Anyone else have luck?[/QUOTE]
 Where there any instructions on how and what parameters to burn the disc on ? Because if you fixate/close the disc, there is no way it is overwriting anything ... As far as im concerned, burning a .iso image implies fixating the disc.

 [http://www.goosee.com/puppy/](http://www.goosee.com/puppy/)

Personally i think what the website u gave implies is bogus, completely.

They shoudlva said it is so small, that the distro gets loaded into RAM so you can insert a blank disc and use the cdrom at will. I dont see on the official website the "burn to disc" feature, i only read "Booting from CD, Puppy will load totally into RAM so that the CD drive is then free for other purposes.".


Its just another small live disc, just like DSL, only really small [IMHO]. If im wrong somebody correct me.

edit > I don't know much, but I have burned one or two .iso images, and the second I select .iso burn, automatically I get finish/fixate disc, wich would kill a r/w environment .

---

### Post by TravisNewman on 2005-03-08
what are you using to burn the iso? All you have to do is make it multisession and it won't fixate the disc. If you're using Nautilus to burn, I'm pretty sure you don't have that option.

---

### Post by bored2k on 2005-03-08
[QUOTE=panickedthumb]what are you using to burn the iso? All you have to do is make it multisession and it won't fixate the disc. If you're using Nautilus to burn, I'm pretty sure you don't have that option.[/QUOTE]

K3B and Nero [oont use them anymore but  I havent burned any DL .isos on gnomebaker].

I **really** thought you had to close the session of a .iso image, specially a bootable disc ... I still would fixate the disc if its a .iso but now i know that .

---

### Post by TravisNewman on 2005-03-08
You have to close the *session* but not the disc totally.

---

### Post by bored2k on 2005-03-08
[QUOTE=panickedthumb]You have to close the *session* but not the disc totally.[/QUOTE]
Interesting ... I remember getting disc is full if tried on the said applications, but never really tried looking around. Ill give that **shot next** time/

---

### Post by BWF89 on 2005-03-08
I'm useing Burn4Free but when I go to boot up the disk it won't go past the part where all the things go down the screen terminal style.

---

### Post by bored2k on 2005-03-08
[QUOTE=BWF89]I'm useing Burn4Free but when I go to boot up the disk it won't go past the part where all the things go down the screen terminal style.[/QUOTE]
 Speed of recording ? Did you md5check the .iso?

---

### Post by BWF89 on 2005-03-09
[QUOTE=bored2k]Speed of recording ?** Did you md5check the .iso?**[/QUOTE]
What?

---

### Post by bored2k on 2005-03-09
[QUOTE=BWF89]What?[/QUOTE]
 [http://www.fastsum.com/](http://www.fastsum.com/)
File verifier for Windows.

Every file has a "number" to identify it. Where you downloaded the .iso most probably there is a link called md5sums where you can see the correct number.

1. get the file md5sum, compare it to the one the site says it should have.
If they match, the download was correct.

---

### Post by Buffalo Soldier on 2005-03-15
[QUOTE=BWF89]What?[/QUOTE]
Basically it's two basic things that newbies usually missed out when they have problem burning, booting and installing using Linux CD.

In simple English what bored2k had asked were:
[list=1]
[*] **Speed of recording?**
How fast did you set your CD burner or  CD writer?

[*] **Did you md5check the .iso?**
md5check is the method to check the integrity of a file. It's one of the surest way to know whether you have a corrupted download or not. Basically md5check is used to check the checksum of the file. Usually the checksum is written in a md5sums file at the server.
[/list]

---

