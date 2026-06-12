---
title: "command to update to 12.04 from terminal"
date: 2012-01-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rburkartjo on 2012-01-07
i messsed up ubuntu again. too much playing. i want to upgrade 11.10 to 12.04 from the terminal note i get the error message gtk couldnt be initilized. so is there still a way i can upgrade from the terminal. this is just a quick fix. i dont want to lose any data on my ubuntu partition. i cant still access all my data on my ubuntu partition when in my linux mint partition.any thoughts. tks

---

### Post by collisionystm on 2012-01-07
> **rburkartjo said:**
> i messsed up ubuntu again. too much playing. i want to upgrade 11.10 to 12.04 from the terminal note i get the error message gtk couldnt be initilized. so is there still a way i can upgrade from the terminal. this is just a quick fix. i dont want to lose any data on my ubuntu partition. i cant still access all my data on my ubuntu partition when in my linux mint partition.any thoughts. tks

sudo do-release-upgrade -d

---

### Post by rburkartjo on 2012-01-07
tks coll will give it a try

---

### Post by rburkartjo on 2012-01-07
when i run get the message
no release found
know that 12.04 is avail for download
will just wait into it get it the repos
tks again

---

### Post by zika on 2012-01-07
Try with &#8222;update-manager -d&#8220;...

---

### Post by paul_in_london on 2012-01-07
> **rburkartjo said:**
> when i run get the message
no release found
know that 12.04 is avail for download
will just wait into it get it the repos
tks again

Try:

```
sudo do-release-upgrade --proposed
```

---

### Post by lucazade on 2012-01-07
alternative way..

```
sudo sed -i 's/oneiric/precise/g' /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get upgrade
```

---

### Post by paul_in_london on 2012-01-07
Btw, if you haven't already kicked off the upgrade now what's the output of:

```
lsb_release -a
```

And does **/etc/update-manager/release-upgrades** contain **“Prompt=normal”** (although that shouldn't really matter here since you're trying to upgrade to 12.04 which is an LTS release)?

---

### Post by rburkartjo on 2012-01-07
i think i have a bigger problem. went into my ubuntu partition while in mint and noticed that my source list was for ubuntu 11.04 not 11.10. no idea how that happened. would this work if someone had a copy of the ubuntu 11.10 source list and i pasted it into my ubuntu partion would that work.
cant find a copy of the 11.10 source list. tks

---

### Post by rburkartjo on 2012-01-07
luc good idea but didnt work. tried everything posted here.

---

### Post by rburkartjo on 2012-01-07
just noticed that i do have source list for 11.10 in my ubuntu partition it is just labeled for 11.04. i forget that other noticed this when upgraded to ubuntu 11.10.

---

### Post by rburkartjo on 2012-01-07
i also noticed that when i boot up to my ubuntu partition in the shell
i get the error message permission denied when i try to open
/etc/apt/sources

---

### Post by zika on 2012-01-08
> **rburkartjo said:**
> i think i have a bigger problem. went into my ubuntu partition while in mint and noticed that my source list was for ubuntu 11.04 not 11.10. no idea how that happened. would this work if someone had a copy of the ubuntu 11.10 source list and i pasted it into my ubuntu partion would that work.
cant find a copy of the 11.10 source list. tks
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by rburkartjo on 2012-01-08
zika tks but still didnt do the trick

---

### Post by rburkartjo on 2012-01-08
okay one more idea
would this work i have three partitions
one for linuxmint one for ubuntu and one blank for storage
from the ubuntu partition i could copy the home folder listed in the system file-has my home and my daughter home to the spare partition
and i could copy the application file in usr/share/applications to the spare partition
then i could reinstall ubuntu 11.10 and after that replace the copied files to my new install of 11.10
might have to reinstall some of the application to work

---

### Post by kansasnoob on 2012-01-08
Just curious, going back to your OP you said:

> i messsed up ubuntu again. too much playing. i want to upgrade 11.10 to 12.04 from the terminal note i get the error message gtk couldnt be initilized. so is there still a way i can upgrade from the terminal. this is just a quick fix. i dont want to lose any data on my ubuntu partition. **[COLOR="Red"]i cant still access all my data on my ubuntu partition when in my linux mint[/COLOR]** partition.any thoughts. tks

I wonder why you can't access your data on Ubuntu from Mint :confused:

I'd want to be sure you can read your data before making any huge decisions ;)

---

### Post by rburkartjo on 2012-01-08
kan yes i can read all my data from the mint partition.

---

### Post by rburkartjo on 2012-01-08
okay need some help and thanks for all the replies. and i thought i might run into this. got the old home copied in ubuntu 11.10. now i am getting the error message when i try to log in. couldnot update ice authority file/home/ray/,ice authority.know there is a way to fix from the terminal but been awhile since i had to and forgot/tks

---

### Post by rburkartjo on 2012-01-08
i know it has to be done with a live cd. and have the ubunyu 11.10 live cd

---

### Post by paul_in_london on 2012-01-08
> **rburkartjo said:**
> okay need some help and thanks for all the replies. and i thought i might run into this. got the old home copied in ubuntu 11.10. now i am getting the error message when i try to log in. couldnot update ice authority file/home/ray/,ice authority.know there is a way to fix from the terminal but been awhile since i had to and forgot/tks

Do you have rwx permission on your home folder (and the files inside it)? 

Try:

```
sudo chown <user>:<user> -R /home/<user> # if necessary
mv ~/.ICEauthority ~/.ICEauthority.backup
sudo reboot
```

Depending on the login manager you're using, you may also need something like (taking gdm as the example):

```
sudo chown gdm:gdm -R /var/lib/gdm/
```

---

### Post by rburkartjo on 2012-01-08
paul do i have to use the live cd or can i just login to a terminal shell

---

### Post by rburkartjo on 2012-01-08
also paul i might not have rwx permission. i installed ubuntu 11.10
deleted the home folder and replaced it with a copy of a home folder i had on a separate partition. no problem do it. but i was afraid that i might have messed up permissions(ownership)

---

### Post by paul_in_london on 2012-01-08
You should be able to sort out your permissions (using sudo) wihthout a live CD (e.g. boot your installed system into recovery mode). I'd suggest doing that first.

EDIT: In my case:

```
paul@precise-64:~$ ls -lad ~
drwxr-xr-x 47 paul paul 4096 Jan  9 00:05 /home/paul
```

So you may need to do:

```
chmod 755 /home/<your-username>
```

You might want to look at this thread which has stuff about permissions:

[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)

---

### Post by rburkartjo on 2012-01-08
tks paul for the info. will give it a try

---

### Post by rburkartjo on 2012-01-08
tks everyone not everything works. but still have my old home i can access on a separate partiton. have everything i need. just reinstall ubuntu on its own partition. somehow i actually installed ubuntu on my linux mint partition. go figure it works fine just have the option of switching to ubuntu while in the mint partition. why no idea and it works great.

---

