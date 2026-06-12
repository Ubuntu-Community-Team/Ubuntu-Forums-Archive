---
title: "fedora linux"
date: 2010-01-13
forum: The Cafe
---

### Post by trixman on 2010-01-13
was just wondering if anyone has tried Linux fedora.

i am thinking of trying it out , any thoughts on the os

also does the package manager have these 2 programs in fedora
Tellico
Gcstar

thanks

---

### Post by k64 on 2010-01-13
Fedora doesn't have Apt-Get, it has Yum, which is more crippled.

Fedora also doesn't have Sudo, but instead has su -c, which is too harsh without a root password. I say you skimp on Fedora for now.

---

### Post by tad1073 on 2010-01-13
Fedora is a whole-nother beast from ubuntu. It is hard to find and install proprietary drivers such as nvidia drivers.

---

### Post by mamamia88 on 2010-01-13
it can't hurt to try it

---

### Post by kevCast on 2010-01-13
[http://ubuntuforums.org/showthread.php?t=1370421&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1370421&highlight=fedora")
[http://ubuntuforums.org/showthread.php?t=1376367&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1376367&highlight=fedora")
[http://ubuntuforums.org/showthread.php?t=1373111&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1373111&highlight=fedora")
[http://ubuntuforums.org/showthread.php?t=1321150&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1321150&highlight=fedora")
[http://ubuntuforums.org/showthread.php?t=1293609&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1293609&highlight=fedora")
[http://ubuntuforums.org/showthread.php?t=1278370&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1278370&highlight=fedora")
[http://ubuntuforums.org/showthread.php?t=1165265&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1165265&highlight=fedora")
[http://ubuntuforums.org/showthread.php?t=1154320&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1154320&highlight=fedora")
[http://ubuntuforums.org/showthread.php?t=1000470&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1000470&highlight=fedora")
[http://ubuntuforums.org/showthread.php?t=1094220&highlight=fedora]("http://ubuntuforums.org/showthread.php?t=1094220&highlight=fedora")

The forum search is your friend.

---

### Post by Dharmachakra on 2010-01-13
Both of those packages are available in the repositories and Yum is not crippled. Give it a whirl.

---

### Post by pirateghost on 2010-01-13
i run fedora 12 64bit on one of my laptops.  i wouldnt say its crippled, but there is definitely some work required to make everything work out of the box, unless you happen to get lucky with your hardware setup.  (broadcom wireless drivers are ANNOYING!!!!)

boot up a live distro and give it a shot...its always fun to learn a new distro, but it DEFINITELY is not as easy as UBUNTU to get going...

---

### Post by Impulser on 2010-01-13
Fedora is a pretty good Linux. If your new to Linux I suggest not updating as it hard to find and install drivers and you use the Terminal a lot more in Fedora then you use in Ubuntu. I like Fedora because you can update the version without burning another disc which is useful. Fedora and Ubuntu are very a like in the look so not much changes there. Like I said before if your new then don't change but definitely if you know Linux definitely give it a try it a pretty good distro of Linux.

---

### Post by kevCast on 2010-01-13
I'll say this. If you are looking for a job, skills with a Red Hat based OS will be much more marketable than a Debian based OS. There's always Virtualbox for that though.

---

### Post by MasterNetra on 2010-01-13
I use Fedora 12 on my storage computer. Its alright. I tend to have some trouble with sound. I mean sound works but not as well as it does on Ubuntu. I keep it on because most linux Distro's on it tend to freeze up visually. If you have a data transfer going like between hard drive and a USB drive it keeps going and finishes during it. But you can't see any changes and can't do anything but do a Hard Reboot. Left it going for several hours one time to see if it would come back to me but no luck. After installing Fedora 12 though they seem to be less and getting better as updates comes (which are more frequent then Ubuntu). All and all its not ideal to me for casual use but seems to work for a system where all your doing with it is storing data. Even got the Hard drive password protected with a 30+ char password.

---

### Post by RiceMonster on 2010-01-13
Yes, it's good; I use it all the time. Posting this from fedora 12. Just do a little research to find out more. It's not hard.

Oh, and to answer your question:
```
yum search gcstar tellico
Loaded plugins: presto, refresh-packagekit
=============================== Matched: gcstar ================================
gcstar.noarch : Personal collections manager

=============================== Matched: tellico ===============================
tellico.i686 : A collection manager
```

---

### Post by HappyFeet on 2010-01-13
> **trixman said:**
> was just wondering if anyone has tried Linux fedora.


I tried fedora 10 & 11 and it was *OK*, but I think 12 is pretty damn good. (but I realize everyones experience will differ) The default nouveau drivers for nvidia cards auto detected my twinview setup, (sweet!) and it was generally a good experience. But realize that fedora is a testing ground for Redhat and uses bleeding edge software. Those that NEED stable and proven software need not apply. But if ubuntu were to fold, fedora would be my first or second choice. (Mandriva is almost tied with fedora for me)

If you like the latest and greatest, with the possibility of having to "tweak" it,  then give it a whirl.

As far as package management, I still say apt/deb is the best out there, but fedora's implementation of rpm is pretty good. The only way to know for sure is to try it.

---

### Post by HappyFeet on 2010-01-13
> **k64 said:**
> I say you skimp on Fedora for now.

Why would you tell someone that without knowing what they expect/want from an OS? Some people LOVE bleeding edge distros.

---

### Post by Frak on 2010-01-13
> **k64 said:**
> Fedora doesn't have Apt-Get, it has Yum, which is more crippled.

Fedora also doesn't have Sudo, but instead has su -c, which is too harsh without a root password. I say you skimp on Fedora for now.
Heh, right, Yum is crippled. I wonder what that makes apt.

Anyways, to get sudo in Fedora, run

```
echo 'username ALL=(ALL) ALL' >> /etc/sudoers
```

Where **username** is **your** user name.

---

### Post by RiceMonster on 2010-01-13
Just noticed this post:

> **k64 said:**
> Fedora doesn't have Apt-Get, it has Yum, which is more crippled.

How exactly?

> **k64 said:**
> Fedora also doesn't have Sudo, but instead has su -c, which is too harsh without a root password. I say you skimp on Fedora for now.

O RLY? Add yourself to the sudoers file. It's there, you just don't have permission to run anything with sudo by default. What do you mean using su -c "is too harsh" and since when is there no root password? Really, I have no idea what you're talking about there.

---

### Post by k64 on 2010-01-13
If you really want a Linux distro that's crippleware I'd say it's Acer's custom Linux distro that went on the original Aspire Ones up to the AOA110-1545, which I have.

No desktop customization, no panel customization, an absolutely hidden package manager (and a crippled GUI for it), and an outdated repository (the Fedora 8 "Werewolf" repo). What's not to loathe about Acer and the crippled AOA110?

---

### Post by magmon on 2010-01-14
I had support for my crap ati card from the start, but my volume buttons made the OS crash. The good didn't counter the bad, needless to say.

---

### Post by 5dolla on 2010-01-14
well i wouldnt say fedora is a crippled os...but it does make you
work for your money :) I think my choice of distros would be 
ubuntu, mint, then arch in that order. ubuntu and mint have good 
stuff going for them in terms of new user support. if you wanna
try somthing a lil more daring than ubuntu try straight debian. 
I really enjoyed arch. they guys over on the arch forums are 
very helpful.

---

### Post by snowpine on 2010-01-14
Fedora's great, and an easy transition from Ubuntu. Yum is not crippled, sudo is not the default (but is easy to set up), and all the "non-free" stuff is available at rpmfusion. I can't honestly say the differences from Ubuntu are that great that I would recommend switching just for the sake of switching.

---

