---
title: "is it still beta?"
date: 2006-05-27
forum: The Cafe
---

### Post by medya on 2006-05-27
hey guys I havent followed your news...

I saw a link in digg.com but still confused ... is the new ubuntu version still in Beta ? 

if not why when I go to download ubuntu  [http://www.ubuntulinux.org/download](http://www.ubuntulinux.org/download)
, it still has breey ubuntu to download ?


I want to upgrade my ubuntu Just when it is final releaase I hate Betas.


by the what is "REALLY" new in the new ubuntu ? do u see any Feel-Able diffrence?

---

### Post by mostwanted on 2006-05-27
New default theme, new Gnome, newer versions of all apps. A bit hard to summarise any more :)

Edit: no wait, I forgot: newer kernel, faster boot process, splash screens for starting up *and* powering down.

---

### Post by meng on 2006-05-27
Official release June 1, you won't have to wait long. I'm sure the testimonials for all the eye candy (ahem), uh and ... increased functionality, yeah! ... will be flooding in soon.

---

### Post by Minyaliel on 2006-05-27
There shouldn't be much of a difference from the beta version as it stands now and the official release. At least, I can't possibly think that Dapper could behave better than it does now. (Well, except for the wifi- issue, that is. Why doesn't it recognize my card... *cry*)

---

### Post by IYY on 2006-05-27
It's still beta, even though almost everything works as it will in the final version. The final version will be released on June 1st. 

> by the what is "REALLY" new in the new ubuntu ? do u see any Feel-Able diffrence?

Yes. Even visually, you'll see a huge change:

[http://shots.osdir.com/slideshows/slideshow.php?release=651&slide=3&title=ubuntu+6.06+rc+screenshots](http://shots.osdir.com/slideshows/slideshow.php?release=651&slide=3&title=ubuntu+6.06+rc+screenshots)

It also has better hardware support, more programs, newer programs, a newer version of Gnome, it's much faster (working and loading), more stable, easier to install XGL/Compiz on... Good stuff.

---

### Post by RAV TUX on 2006-05-27
RC link

[http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)

---

### Post by medya on 2006-05-27
to upgrade  my breezy, do  I have to download an ISO and burn it ?
or I  should  upgrade by command or something...

---

### Post by Iandefor on 2006-05-27
[quote=medya]to upgrade  my breezy, do  I have to download an ISO and burn it ?
or I  should  upgrade by command or something...[/quote] You *could* upgrade by dist-upgrading, but it's usually recommended that you don't do that. I'd do a fresh install.

---

### Post by medya on 2006-05-27
would I loose the programs which I have installed , with a Fresh install ?

and why it is recommmended that I dont do dist-upgrading...?

---

### Post by Iandefor on 2006-05-27
[quote=medya]would I loose the programs which I have installed , with a Fresh install ?

and why it is recommmended that I dont do dist-upgrading...?[/quote] Yes, you'd basically be reinstalling Ubuntu... but with Dapper Drake. You'd be wise to back up your data before you did it.

It's recommended that you not dist-upgrade because it forces apt to upgrade no matter what- even if it can lead to breakage on your computer.

---

### Post by drogoh on 2006-05-27
[QUOTE=Iandefor]
It's recommended that you not dist-upgrade because it forces apt to upgrade no matter what- even if it can lead to breakage on your computer.[/QUOTE]

Actually, dist-upgrade upgrades your packages and installs whatever else is required by any of those packages.  A fresh install isn't required.  apt is quite intelligent at figuring out what needs to be installed for N program to work and is all and all pretty safe.  If you specify the "force" option, then yes it would "upgrade no matter what", but you don't want to force something.

---

### Post by jacksaff on 2006-05-28
You can now upgrade using the update manager. Install it if you don't already have it. Just updated xubuntu by this method with no issues.

---

### Post by medya on 2006-05-28
I am confused... somebody just tell me what to do...

I have a ubuntu, I have spent much time on downloading and installing programs for it...  what should I do now to upgrade ? 
please give me the exact command .

---

### Post by Engnome on 2006-05-28
[QUOTE=medya]I am confused... somebody just tell me what to do...

I have a ubuntu, I have spent much time on downloading and installing programs for it...  what should I do now to upgrade ? 
please give me the exact command .[/QUOTE]

sudo apt-get update
sudo apt-get dist-upgrade

Warning: do a backup of your files first!

---

### Post by medya on 2006-05-28
am I supposed to loose any file ? or u say it just because of more saftey?

---

### Post by GarethMB on 2006-05-28
[QUOTE=medya]am I supposed to loose any file ? or u say it just because of more saftey?[/QUOTE]
You *shouldn't* lose any files, but if it went wrong you could. Especially if you don't have a partitioned hard drive.

First of all to upgrade you need to edit as root your sources list replacing breezy with dapper.

```
 sudo gedit /etc/apt/sources.list
```

Now just use the replace tool to replace all occurences of Breezy with Dapper. You should note that if you have custom repo's they might not neccessairily have a dapper version.

then

```
 sudo apt-get update
sudo apt-get dist-upgrade
```

I don't know what people are saying about the update manager method. I haven't used this method. Pretty much all the people using Dapper now will have used this method, if they were using a breezy install before.

---

### Post by 3rdalbum on 2006-05-28
[QUOTE=medya]am I supposed to loose any file ? or u say it just because of more saftey?[/QUOTE]

More because of safety, I think. As I have my home directory on the same partition as everything else, I will definately back it up to CDs before upgrading. If your home directory is on a seperate partition, you almost certainly won't need to back it up.

---

### Post by beercz on 2006-05-28
[QUOTE=3rdalbum]More because of safety, I think. As I have my home directory on the same partition as everything else, I will definately back it up to CDs before upgrading. If your home directory is on a seperate partition, you almost certainly won't need to back it up.[/QUOTE]
I would DEFINATELY back up - I backup daily!!!

---

### Post by GarethMB on 2006-05-28
[QUOTE=beercz]I would DEFINATELY back up - I backup daily!!![/QUOTE]
I never back up. Even when i installed linux. I also messed it up and lost everything. But i wasn't particularly bothered.

---

### Post by Minyaliel on 2006-05-28
I backed up my stuff... well, the most important of it, anyway, like unfinished assignments for school and stuff. But if you want to test dapper first, to see the difference, you should make an iso... see, it works as a live CD, only with an option to install the whole thing if you like it. So you could basically just take a look at it and then click an icon to start installing it.

---

### Post by Stew2 on 2006-05-28
[QUOTE=Minyaliel]I backed up my stuff... well, the most important of it, anyway, like unfinished assignments for school and stuff. But if you want to test dapper first, to see the difference, you should make an iso... see, it works as a live CD, only with an option to install the whole thing if you like it. So you could basically just take a look at it and then click an icon to start installing it.[/QUOTE]

Excellent advice :D. This is how I would reccomend doing it as well, also remember that after you back up your data, make a list if you have a lot of programs that you put on after you installed Ubuntu as you will have to reinstall these as well. I have had no problems since I upgraded to Dapper and the speed diffrence and new gnome layout are very appealing! Just dont rush into anything, back up your data first so you can reinstall it after you install Dapper if you go the iso route. Happy Ubuntuing! :D

---

### Post by medya on 2006-05-28
my internet speed is so slow , (64Kb) I can not re-download all those program which I have installed on my breezy.

unfortuntely there is no EASY way to put Deb files on a CD and make the package manger to use the CD as a repository...

last time I tried to do that but it never worked out...

by the way, are the Media Players of Dapper , the same as the breezy's media player ?

all my breezy needs is a good media player... I am sick of having 1000 diffrent media players and still not be able to see some videos.

---

### Post by GarethMB on 2006-05-28
[QUOTE=medya]my internet speed is so slow , (64Kb) I can not re-download all those program which I have installed on my breezy.

unfortuntely there is no EASY way to put Deb files on a CD and make the package manger to use the CD as a repository...[/quote] gdebi makes installing .deb files a snap. But breezy .debs won't necessairily work. Perhaps ordering an install CD will be better for you

> 
by the way, are the Media Players of Dapper , the same as the breezy's media player ?

all my breezy needs is a good media player... I am sick of having 1000 diffrent media players and still not be able to see some videos.Thats a codec issue. Nothing to do with the video clients.

---

### Post by medya on 2006-05-28
the other thign that my breezy needs is Yahoo messenger (with voice webcam and public chatrooms support) (even if it be by wine...but as long as I know even wine can not do that)

if dapper donest give me that, I wont waste time on donwloading / backing up data and /upgrading  .

I am happy with my breezy .

---

### Post by ssam on 2006-05-28
read [http://www.ubuntu.com/testing/dapperrc](http://www.ubuntu.com/testing/dapperrc)

it has the recommend upgrade methods.

also note.
*back up anything that is important.
*if you have installed lots of third party stuff then that may cause problems. the developers test lots of different upgrade situations, but they can't test everything. maybe unistall any weird stuff you have added outside of the package manager. things from universe and multiverse should be ok.
* remember that this is not the final release yet. it is very close, but there are most likely a few bugs there now, that wont be in the final release. (though the devs are only really looking at major bugs currently)

---

