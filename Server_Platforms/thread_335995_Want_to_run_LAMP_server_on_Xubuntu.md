---
title: "Want to run LAMP server on Xubuntu"
date: 2007-01-11
forum: Server Platforms
---

### Post by butu on 2007-01-11
Hi All,

I have PIII, 1.13Gz of processor with 128MB SD RAM(later buy another stick of 128MB RAM).

I am still unbale to install Ubuntu. Buts its okay. That is not neccessity. Then I tried Xubuntu it is working fine.

But since it is not pre-installed with LAMP so I have to go for Ubuntu Server edition.

Now I have Ubuntu Server Edition. I am new to Linux but passionate about learning thing quickly. So since a week
or so I am trying to play with commandline. The journey is quite fun :-) as of now.

I could able to play with MySQL, Apache but could not able to test my PHP script. And to be honest I do not have internet
connection in home. And not planning to get one soon. But I want to feel totally web developement under LAMP. But since
server edition lack the GUI feature. So unable to decide whether to stick with it or not.

I know this is not a Server mailing list. But still I post this mail hope to get any response from some where. I don't want rich
GNOME or KDE functionality but just need to get my work done. I am not afraid to work on command line although I am a
new user. But still I want to test the look and feel of my website at the same time want to work on power of Linux.

This is my first in any mailing list. Hope I got some reply and it will encourage me to participate in the community.

Please let me know in case of more clarification required.

Thanks!
Butu

---

### Post by flossgeek on 2007-01-11
Go back to XFCE so you have some browsers like firefox available. You then simply install the required packages.

Here is a guide I wrote on my blog to set it up:-

[http://www.ossgeeks.co.uk/?p=15](http://www.ossgeeks.co.uk/?p=15)

Hope this helps...

---

### Post by PetePete on 2007-01-11
if you want to learn things i'd say install xubuntu and then install apache/php/mysql etc seperatly.

you'll learn much more knowing how to install each individual compenent together. and ifyou get stuck post something here!

---

### Post by MrHorus on 2007-01-11
> **butu said:**
> 
But since it is not pre-installed with LAMP so I have to go for Ubuntu Server edition.


```
apt-get install mysql-server php5 apache2
```

Problem solved :)

---

### Post by Brazen on 2007-01-11
Ok, to explain what MrHorus said, which was also what I was thinking of...  You can go back to using Xubuntu and then run that block of code in a terminal (except add a sudo in front of it).  That will give you everything you get with the LAMP install, but you'll have it on Xubuntu.

---

### Post by aberry5555 on 2007-01-16
you can easily get the ubuntu desktop by typing in "sudo apt-get ubuntu-desktop"

---

### Post by butu on 2007-02-02
Thanks very much!!!

I installed Xubuntu and then the LAMP stack...everything seemed to be fine....

---

