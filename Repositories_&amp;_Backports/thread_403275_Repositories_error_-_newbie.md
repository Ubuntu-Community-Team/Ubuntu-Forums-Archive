---
title: "Repositories error - newbie"
date: 2007-04-06
forum: Repositories &amp; Backports
---

### Post by christinanilsen on 2007-04-06
Hi -

First I was trying to download a Java plugin for ubuntu.  Then, when it didn't work, I read I needed to add the multiverse repositories.  I followed the instructions in the documentation (System/Administration/SoftwareProperties), where I attempted to Add the Multiverse Repository.  Result = error 

message:[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Type "Add" is not known on line 32 in source list /etc/ apt/sources.list

Unable to lock the list.directory

anyone know how to resolve this?  and then, finally, get the java plugin?

thx
christina

---

### Post by qamelian on 2007-04-06
Can you post the contents of /etc/apt/sources.list?

---

### Post by christinanilsen on 2007-04-06
newbie here.  this is my first day with ubuntu.

how do i locate that?

---

### Post by wesley_of_course on 2007-04-06
Wesley here ; maybe ???


sudo gedit   /etc/apt/sources.list

---

### Post by christinanilsen on 2007-04-07
here it is:

deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
Add Channel
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by qamelian on 2007-04-07
oops

---

### Post by qamelian on 2007-04-07
> **christinanilsen said:**
> [COLOR=Red]Add Channel[/COLOR]
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
In the terminal, type:
```
 sudo gedit   /etc/apt/sources.list
```

Delete the line that says Add Channel and save the file. That's not a valid line in a sources.list file.


Also in the terminal type: ```
sudo apt-get update
``` 
You should be okay now.

---

### Post by christinanilsen on 2007-04-08
ok, thanks.  that seems to have worked, insofar as i was able to reconfigure the software properties (to add repositories).  

but i still haven't resolved my original issue.  i'm trying to play internet radio (Belgian radio [Klara]("http://www.klara.be/html/fs_audio.html") 

the radiospeler seems to require Java, which I've downloaded for Linux here: [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

but the download files are of type .bin and won't open to install.

what should i do to install Java (or otherwise get this radioplayer working?)

thanks!!!
christina

---

