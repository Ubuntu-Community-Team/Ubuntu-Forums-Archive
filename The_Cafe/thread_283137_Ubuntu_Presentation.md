---
title: "Ubuntu Presentation"
date: 2006-10-23
forum: The Cafe
---

### Post by alecjw on 2006-10-23
I've written a presentation on ubuntu. It's attached to this post (version.number.tar.bz2). Please feel free to post your own slides for it/ideas for slides. I'm going to try to update it reguraly with people's suggestions and slides. You'll need the Ubuntu-title font which I've attached an installer for.(ubuntu-font.sh.bz2)

---

### Post by Abstract on 2006-10-23
I don't like it at all.

Firstly the text goes off the bottom of my screen and I can't read it all. Secondly the "oh I thought you were a Windows Program" thing is very childish and stupid. It also needs some grammar correction. I'm going to try and make it better.

---

### Post by codypumper on 2006-10-23
Your definately on to something, and have sparked me an idea, if that makes sense. Thanks. (grammar and stuff could use some work, but I've never seen your intriguing approach on anything similar to this, as short as it is)

---

### Post by alecjw on 2006-10-24
> **codypumper said:**
> Your definately on to something, and have sparked me an idea, if that makes sense. Thanks. (grammar and stuff could use some work, but I've never seen your intriguing approach on anything similar to this, as short as it is)

Yeah. It's only a start. It was 1:25AM and I was tired and i couldn't think of anything else. Ubuntu's become one of those things which I don't notice when it's there, but I probably would if it wasn't.

Maybe I should make the writing on it a bit more formal eg. "And you can get firefox for Ubuntu too; you don't need to abandon all of your existing applications."

The text probably goes off of the screen because you don't have the Ubuntu-title font installed. Did you run my installation script? If you did, try installing it manually instead. Download the font, un-bzip2 it and move it to fonts:///ubuntu-title.otf

---

### Post by DoctorMO on 2006-10-24
your script doesn't work at all, this is because there is no such place as fonts:/// and the system borks.

Can't you embed the font in the odf?

---

### Post by alecjw on 2006-10-24
> **DoctorMO said:**
> your script doesn't work at all, this is because there is no such place as fonts:/// and the system borks.

Can't you embed the font in the odf?

Oh. There is on my system. Try typing fonts: into the address bar in a nautilus window. I've got it on edgy. Maybe it doesn't exist on dapper. If it doesn't work, try /usr/share/fonts

I'll have to do some research about embedding fonts.

---

### Post by DoctorMO on 2006-10-24
your script uses bash so bash tried to move the file into ./fonts:/ which it fails to do.

Perhaps edgy has some new bash <=> Nautlus thingy ma jig but I've never seen it before and I'd hate to think what it could do. you should have a installFont program or some such or perhaps a nautlius command line program to take advantage of it's features with fish/ftp/smb etc

---

### Post by Tomosaur on 2006-10-24
I'm sorry, but I really don't like this. It looks poorly made, is poorly written, and generally just doesn't appeal to me. Granted, I did look at it in Windows so there are issues with fonts etc, but theres no excuse for poor writing skills.

---

### Post by phido on 2006-10-24
to install the font:
```
sudo apt-get install ttf-ubuntu-title
```I don't like it too, there is much more and important things then firefox and thunderbird which dont make a difference form windows

---

### Post by alecjw on 2006-10-24
> **phido said:**
> to install the font:
```
sudo apt-get install ttf-ubuntu-title
```I don't like it too, there is much more and important things then firefox and thunderbird which dont make a difference form windows

I know. It's just a start. I'm going to have things about OOo, the simplicity of installing programs with syanptic, wine, qemu/vmware etc. It was 1:25AM and I was tired.

---

### Post by DoctorMO on 2006-10-24
alecjw, keep it going and update us on when you have something material. it's a good plan; could you do some flyers as well?

---

### Post by codypumper on 2006-10-24
you may or may not want to look at [https://wiki.ubuntu.com/Presentations](https://wiki.ubuntu.com/Presentations)

---

### Post by .t. on 2006-10-24
It's a good start. Just note that if people who have watched your guide decide to install, they may come running back asking where Thunderbird is. You'd need to explain (perhaps in your software installation slide) where it is.

---

