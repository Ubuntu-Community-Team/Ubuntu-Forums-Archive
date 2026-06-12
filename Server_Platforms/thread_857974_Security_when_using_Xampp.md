---
title: "Security when using Xampp"
date: 2008-07-13
forum: Server Platforms
---

### Post by masoud23 on 2008-07-13
Hi

I use Xampp (packet with Apache, php, Mysql). As far as i know to run my php files on localhost I most have them in htdocs which is under File System. As i have learned saving and up and downloading files to File System can be risky! can i run my php file at localhost from another map which is not under File System? If so How? If not, how risky is it? For ex i given FileZilla root access, is there risks even when FilZilla is disconnected? Is there risks (from intruders) when program like Nautilus or Bluefish have root access? place explain with detail I am a newbie in Linux?

---

### Post by Dr Small on 2008-07-13
Don't worry about it. Everything on your system *is under the filesystem*. This is no cause for panic. As long as the htdoc's directory has 755 permissons, everything should be O.K.

Dr Small

---

