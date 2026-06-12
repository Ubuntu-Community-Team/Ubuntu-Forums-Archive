---
title: "Next 18.10 will be cosmic"
date: 2018-05-03
forum: Ubuntu Development Version
---

### Post by corradoventu on 2018-05-03
[http://archive.ubuntu.com/ubuntu/dists/cosmic/](http://archive.ubuntu.com/ubuntu/dists/cosmic/)
[https://launchpad.net/ubuntu/cosmic](https://launchpad.net/ubuntu/cosmic)

---

### Post by dino99 on 2018-05-03
yeah, the archive is already opened, and the first packages being built  :p

---

### Post by #&amp;thj^% on 2018-05-03
Just found this a couple of days ago:[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-18.10-Cosmic-Canimal](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-18.10-Cosmic-Canimal)
So checked here:[https://launchpad.net/ubuntu/cosmic](https://launchpad.net/ubuntu/cosmic)
But nothing official from Mark yet on the name. (Cosmic CANIMAL)

---

### Post by harry332 on 2018-05-03
Yes the Cosmic tool chain has been uploaded.
They begin with the ncurses6 and libtinfo6 soname change.

---

### Post by cariboo on 2018-05-03
I'd suggest holding off, until we get official notification from Ubuntu.

---

### Post by cecilpierce on 2018-05-03
Just D/L the 5-3 iso to a flash drive and it crashed half way through, I try a dvd and see if that works.

Up and running from dvd.

---

### Post by harry332 on 2018-05-04
In the changelog of the package base-list it says:
[COLOR=#ff0000]              [/COLOR][COLOR=#ff0000]base-files (10.1ubuntu3) cosmic; urgency=medium
  * /etc/issue{,.net}, /etc/{lsb,os}-release: Welcome to** Cosmic CANIMAL!**
 -- Adam Conrad <email address hidden>  Wed, 02 May 2018 05:44:20 -0600[/COLOR][COLOR=#ff0000]      [/COLOR]

---

### Post by IanW on 2018-05-04
> **1fallen said:**
> But nothing official from Mark yet on the name. (Cosmic CANIMAL)

My guess is that CANIMAL (or [C-Animal]("https://a-z-animals.com/animals/pictures/C/")) is a placeholder  for Camel or Capybara or Coyote etc.

---

### Post by thenailedone on 2018-05-04
Highlight of each release cycle, the new name :)

---

### Post by corradoventu on 2018-05-04
Installed from USB key. /var/log/installer/telemetry is:
```
{"Media": "Ubuntu 18.10 \"Cosmic CANIMAL\" - Alpha amd64 (20180503.1)", "Type": "GTK", "PartitionMethod": "manual", "DownloadUpdates": true, "Language": "en", "Minimal": false, "RestrictedAddons": true,
 "Stages": {"0": "language", "7": "console_setup", "14": "console_setup", "20": "prepare", "118": "partman", "128": "partman", "131": "partman", "173": "partman", "174": "partman", "185": "partman", "188": "start_install", "193": "timezone", "215": "usersetup", "273": "user_done", "800": "done"}}
```

---

### Post by pqwoerituytrueiwoq on 2018-05-04
> **1fallen said:**
> Just found this a couple of days ago:[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-18.10-Cosmic-Canimal](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-18.10-Cosmic-Canimal)
So checked here:[https://launchpad.net/ubuntu/cosmic](https://launchpad.net/ubuntu/cosmic)
But nothing official from Mark yet on the name. (Cosmic CANIMAL)
So is it not to lake to call it Cosmic Cat and use something like  [this for the wallpaper](https://i.imgur.com/bq1LmMM.jpg)?

---

### Post by flocculant on 2018-05-04
> **IanW said:**
> My guess is that CANIMAL (or [C-Animal]("https://a-z-animals.com/animals/pictures/C/")) is a placeholder  for Camel or Capybara or Coyote etc.

Unless they decide to just use it - this is exactly right. It is logged as such on IRC logs.

---

### Post by #&amp;thj^% on 2018-05-04
> **pqwoerituytrueiwoq said:**
> So is it not to late to call it Cosmic Cat and use something like  [this for the wallpaper](https://i.imgur.com/bq1LmMM.jpg)?
:D I Like that! ;)


> **flocculant said:**
> Unless they decide to just use it - this is exactly right. It is logged as such on IRC logs.

Thanks flocculant. :)

---

### Post by corradoventu on 2018-05-04
> **pqwoerituytrueiwoq said:**
> So is it not to lake to call it Cosmic Cat and use something like  [this for the wallpaper](https://i.imgur.com/bq1LmMM.jpg)?
beautiful wallpaper, but i need a 1920x1080 one!

---

### Post by pqwoerituytrueiwoq on 2018-05-04
> **corradoventu said:**
> beautiful wallpaper, but i need a 1920x1080 one!

alt wallpaper: [http://st.gde-fon.com/wallpapers_original/158478_kot_kosmos_sinij_1920x1200_www.Gde-Fon.com.jpg](http://st.gde-fon.com/wallpapers_original/158478_kot_kosmos_sinij_1920x1200_www.Gde-Fon.com.jpg)

---

### Post by PaulW2U on 2018-05-05
> **cariboo said:**
> I'd suggest holding off, until we get official notification from Ubuntu.
ISO images are already being built - [http://cdimage.ubuntu.com/daily-live/20180505/](http://cdimage.ubuntu.com/daily-live/20180505/) - so Cosmic <Csomething> it is. :)
> **cecilpierce said:**
> Just D/L the 5-3 iso to a flash drive and it crashed half way through, I try a dvd and see if that works.
I used the quick and dirty method :
```
sudo sed -i s/bionic/cosmic/ /etc/apt/sources.list
```
264 updates so far and yes I can quickly revert to a stable bionic installation if it all goes wrong.

---

### Post by #&amp;thj^% on 2018-05-05
> **PaulW2U said:**
> ISO images are already being built - [http://cdimage.ubuntu.com/daily-live/20180505/](http://cdimage.ubuntu.com/daily-live/20180505/) - so Cosmic <Csomething> it is. :)

I used the quick and dirty method :
```
sudo sed -i s/bionic/cosmic/ /etc/apt/sources.list
```
264 updates so far and yes I can quickly revert to a stable bionic installation if it all goes wrong.
Good to see you here again, even if it is only occasionally. :D
Yep same here 
```
sudo sed -i s/bionic/cosmic/ /etc/apt/sources.list
```
264 updates
Best Rgards

---

### Post by oldfred on 2018-05-05
I zsync the ISO.
I first copy last daily or final release to new name and zsync that.

 zsync [http://cdimage.ubuntu.com/daily-live/20180505/cosmic-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/20180505/cosmic-desktop-amd64.iso.zsync)
Normally it says daily not 20180505so had to change that. daily did not work.

Read cosmic-desktop-amd64.iso. Target 88.4% complete.      
downloading from [http://cdimage.ubuntu.com/daily-live/20180505/cosmic-desktop-amd64.iso:](http://cdimage.ubuntu.com/daily-live/20180505/cosmic-desktop-amd64.iso:)
#################### 100.0% 3774.8 kBps DONE      

verifying download...checksum matches OK
used 1699971072 local, fetched 224984034

---

### Post by #&amp;thj^% on 2018-05-05
> **oldfred said:**
> I zsync the ISO.
I first copy last daily or final release to new name and zsync that.

 zsync [http://cdimage.ubuntu.com/daily-live/20180505/cosmic-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/20180505/cosmic-desktop-amd64.iso.zsync)
Normally it says daily not 20180505so had to change that. daily did not work.

Read cosmic-desktop-amd64.iso. Target 88.4% complete.      
downloading from [http://cdimage.ubuntu.com/daily-live/20180505/cosmic-desktop-amd64.iso:](http://cdimage.ubuntu.com/daily-live/20180505/cosmic-desktop-amd64.iso:)
#################### 100.0% 3774.8 kBps DONE      

verifying download...checksum matches OK
used 1699971072 local, fetched 224984034
Thanks oldfred :), you know I'm going to have to break out of my old habits and give this whirl sometime. (You know the old saying "Old Dog new tricks" ;)) 
I'm such a creature of old habits at times.
Regards

---

### Post by P-I H on 2018-05-06
Upgraded an old installation. installed as 17.04, upgraded to 17.10, 18.04 and used "sudo sed -i s/bionic/cosmic/ /etc/apt/sources.list" to upgrade to cosmic what ever CANIMAL.

---

### Post by corradoventu on 2018-05-08
Cosmic Cuttlefish
[http://www.markshuttleworth.com/archives/1521](http://www.markshuttleworth.com/archives/1521)

---

### Post by thenailedone on 2018-05-08
> **corradoventu said:**
> Cosmic Cuttlefish
[http://www.markshuttleworth.com/archives/1521](http://www.markshuttleworth.com/archives/1521)

Seems there weren't that many clever words to use starting with "c"... except for c-curity ;)

---

### Post by john wagner on 2018-05-08
Cosmic Cthulhu

---

### Post by PaulW2U on 2018-05-08
Just updated:```
paul@N1642u~> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Cosmic [COLOR="#FF0000"]Cuttlefish[/COLOR] (development branch)
Release:	18.10
Codename:	cosmic
```

---

### Post by P-I H on 2018-05-09
Correct name with today's update.

---

### Post by cecilpierce on 2018-05-09
Cuttlefish ?

---

