---
title: "after three days"
date: 2005-07-03
forum: Repositories &amp; Backports
---

### Post by ajtim on 2005-07-03
Are there anyone who nows an answer why three days is impossible to use Synapctic because is to slow? 
I have Ubuntu Hoary and for other pages i don't have a probleb, just [www.ubuntulinux.org](www.ubuntulinux.org) ans Synaptic. 
I saw that also some other user have the same problem but...

Thanks...

---

### Post by Lunde on 2005-07-03
[QUOTE=ajtim]Are there anyone who nows an answer why three days is impossible to use Synapctic because is to slow? 
I have Ubuntu Hoary and for other pages i don't have a probleb, just [www.ubuntulinux.org](www.ubuntulinux.org) ans Synaptic. 
I saw that also some other user have the same problem but...

Thanks...[/QUOTE]
 There may be something wrong with your repositories. For furter help, I think you have to post the output of your /etc/apt/sources.list

---

### Post by ajtim on 2005-07-03
[QUOTE=Lunde]There may be something wrong with your repositories. For furter help, I think you have to post the output of your /etc/apt/sources.list[/QUOTE]
My sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging bleeding main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging bleeding main universe multiverse restricted

---

### Post by ajtim on 2005-07-03
[QUOTE=ajtim]My sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging bleeding main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging bleeding main universe multiverse restricted[/QUOTE]

I forgot to wrote that i have problem wit security and us.archive.ubuntu. I tried archive.ubuntu but problem is same...

---

### Post by brossiter on 2005-07-04
Let me add that my repos are slow as molasses as well, and have been for the same aforementioned three day period.  Same slowness exists whether apt'ing or using Synaptic.  Here's my /etc/apt/sources.list:

[INDENT][COLOR=Navy][I]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/I]
[/COLOR][/INDENT]

---

### Post by ajtim on 2005-07-04
[QUOTE=brossiter]Let me add that my repos are slow as molasses as well, and have been for the same aforementioned three day period.  Same slowness exists whether apt'ing or using Synaptic.  Here's my /etc/apt/sources.list:

[INDENT][COLOR=Navy][I]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/I]
[/COLOR][/INDENT][/QUOTE]

How is your download? Did you save a problem? I asked also in the mailing list but nobody answer me. 
BTW with Debian i don't have a problem.

---

### Post by Lunde on 2005-07-04
[QUOTE=ajtim]How is your download? Did you save a problem? I asked also in the mailing list but nobody answer me. 
BTW with Debian i don't have a problem.[/QUOTE]
 Make a backup of the file and 
Try changing all the us. to ca. and see if there are any differences
ca. is canada right?

---

### Post by Lunde on 2005-07-04
Here are mine, and they are flying. No delay here

deb file::///mnt/iso hoary main restricted

deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by DarkManX4lf on 2005-07-04
i have the SAME EXACT problem, and i posted here

[http://www.ubuntuforums.org/showthread.php?t=45634](http://www.ubuntuforums.org/showthread.php?t=45634)

and no one was able to help, i thank those who tried


ive tried many different sources.list editing it w/e and its stil slow............

---

### Post by ajtim on 2005-07-04
[QUOTE=Lunde]Here are mine, and they are flying. No delay here

deb file::///mnt/iso hoary main restricted

deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/QUOTE]


I tried everything - Canada, Holland, Norway...same problem. For days ago was O.K. I didn't install nothing, nothing cgange... As i wrote before [www.ubuntulinux.org](www.ubuntulinux.org) loading slow...

---

### Post by ajtim on 2005-07-04
[QUOTE=DarkManX4lf]i have the SAME EXACT problem, and i posted here

[http://www.ubuntuforums.org/showthread.php?t=45634](http://www.ubuntuforums.org/showthread.php?t=45634)

and no one was able to help, i thank those who tried


ive tried many different sources.list editing it w/e and its stil slow............[/QUOTE]

I saved a problem as i changed us(or other countries).archive.ubuntu.com with mirrors.
Now my sources.list looks:

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging bleeding main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging bleeding main universe multiverse restricted 

deb [http://ubuntu.mirrors.tds.net/ubuntu/](http://ubuntu.mirrors.tds.net/ubuntu/) hoary main restricted universe multiverse
deb [http://ubuntu.mirrors.tds.net/ubuntu/](http://ubuntu.mirrors.tds.net/ubuntu/) hoary-updates main restricted universe multiverse
deb [http://ubuntu.mirrors.tds.net/ubuntu/](http://ubuntu.mirrors.tds.net/ubuntu/) hoary-security main restricted universe multiverse

Now works as before. I hope that server is same as archive.ubuntu.com

---

### Post by DarkManX4lf on 2005-07-04
[QUOTE=ajtim]I saved a problem as i changed us(or other countries).archive.ubuntu.com with mirrors.
Now my sources.list looks:

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging bleeding main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging bleeding main universe multiverse restricted 

deb [http://ubuntu.mirrors.tds.net/ubuntu/](http://ubuntu.mirrors.tds.net/ubuntu/) hoary main restricted universe multiverse
deb [http://ubuntu.mirrors.tds.net/ubuntu/](http://ubuntu.mirrors.tds.net/ubuntu/) hoary-updates main restricted universe multiverse
deb [http://ubuntu.mirrors.tds.net/ubuntu/](http://ubuntu.mirrors.tds.net/ubuntu/) hoary-security main restricted universe multiverse

Now works as before. I hope that server is same as archive.ubuntu.com[/QUOTE]


thanks but that didnt help, and the above post of the sources.list dindt help either i still download from the repositories at 3700 Bytes/second, and yes my network is configured fine i can download at m y cap from other websites just not from the repositories.....ah well...looks like i'll have to stick to windows till this gets fixed.

---

### Post by DarkManX4lf on 2005-07-04
well it still all slow....i dont know whats wrong.

---

### Post by ajtim on 2005-07-05
[QUOTE=DarkManX4lf]well it still all slow....i dont know whats wrong.[/QUOTE]

I tought that Ubuntu support is better...
Try to install Debian Sarge. I like it and support is VERY good...

---

