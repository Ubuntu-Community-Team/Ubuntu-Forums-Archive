---
title: "How do YOU install applications"
date: 2010-07-02
forum: The Cafe
---

### Post by grindboy on 2010-07-02
Hi Guys,

With the revamping of the Ubuntu Software Center I find myself using it more and more over synaptic or apt-get. I was wondering what the general use ratios were for each install method.

Thanks

---

### Post by BenAshton24 on 2010-07-02
Pacman + Yaourt, but I use Arch Linux so I'm not sure if it really counts.

---

### Post by Timmer1240 on 2010-07-02
Have used all methods usually use software center though package manager if I know exactly what I want aptget if I know the command that is sweet!And debs sometimes if I find a program of interest or need for!Its all good!

---

### Post by cgroza on 2010-07-02
I install via terminal and some times when i don't know the name of my package i simply search in in Software Center.

---

### Post by powerpleb on 2010-07-02
I tend to use aptitude on the cli the most.
Otherwise Ubuntu Software Centre if I'm not sure what I'm looking for or just browsing.

Very occasionally I use Synaptic, especially straight after a fresh installation of Ubuntu  when, all at once, I bulk remove all those fonts I can't read, all those packages I don't want and install all the stuff I need that isn't already there. 
For me that is about the only time when it is faster and easier to use synaptic than aptitude.

---

### Post by Palanthas on 2010-07-02
Generally I will use apt-get, although I like useing the Software Center as well, especially when I just feel like browsing for something interesting to play with. ;)

I don't mind .deb, etc... either. I will use which ever method is most handy at the time. If I HAD to choose to use only one, apt-get. :D

---

### Post by 2edgesword on 2010-07-02
I've used both the Ubuntu Software Center and apt-get to install new applications.

---

### Post by Chame_Wizard on 2010-07-02
Always with [Kpackagekit]("http://en.wikipedia.org/wiki/PackageKit"),aptitude and [dpkg]("http://en.wikipedia.org/wiki/Dpkg")/[gdebi]("https://launchpad.net/gdebi")(sometimes apt-get).:guitar:

---

### Post by Ruuki on 2010-07-02
If I know what software I want I just do alt + f2 and do apt-get 

If I'm browsing I use the software center

If it's not listed I use a deb package or .tar/terminal using the make method to install it (rarely)

---

### Post by teisho on 2010-07-02
I use apt-get too, and now I've started using apt-cache search and grep to find software packages.  It's much faster if you know what you're trying to find.

For example:

```
apt-cache search game | grep etris | grep ultiplayer
```

---

### Post by marshmallow1304 on 2010-07-02
aptitude (recently switched from apt-get) from the command line only (I strongly dislike the ncurses interface.)

I'll also use Synaptic occasionally, mainly for searching.

---

### Post by overdrank on 2010-07-03
Moved to  The Community Cafe

---

### Post by Sean Moran on 2010-07-03
I've begun to keep myh own repository, and so it's just a matter of clicking on the required .deb file/s although that sometimes neglects to see the dependencies in the /var/cache/apt/archives dir, in which case the Software Centre is usually the simplest means of reloading something I already installed but had the need to install again.  

Most of my standard stuff is part of a bash script of apt-get commands.


---o0o---

PS: The good thing about that little bash script, is how it saves the /var/cache/apt/archives content to another dir on another partitiion at the end of each new distro install, and then the next time I run the script, the first thing it does is to copy all the saved .deb files back into the new /var/cache/apt/archives dir, simple as that.

I'm upto over 400 of the Karmic kernel-22 .deb files by now, and here on this lowly cheap Thai hotel wi-fi, it saves 4-5 hours for each new custom distro I write to .iso and burn to flash drive.  It also saves some of the bandwidth on the server end, I suppose.

---

### Post by wkhasintha on 2010-07-03
I like to use terminal[apt-get,dpkg] more and Synaptic , I rarely use Software center .

---

### Post by sandyd on 2010-07-03
I mainly use gentoo right now @o from source it is.

---

### Post by wojox on 2010-07-03
zypper - openSUSE

yum - Fedora

---

### Post by phrostbyte on 2010-07-03
ins <package name>

---

### Post by Frogs Hair on 2010-07-03
All of the above , I try to use apt-get AMAP.

---

### Post by MaxIBoy on 2010-07-03
Apt-get and apt-cache search, except for sometimes when I use Synaptic.

---

### Post by sgosnell on 2010-07-03
All of the above.  It depends on the package, and on what is most convenient at the moment.

---

### Post by RiceMonster on 2010-07-03
yum install package
rpm -Uvh package

double click .exe

---

### Post by poisonkiller on 2010-07-03
yaourt -S package

---

### Post by Theft42 on 2010-07-03
The Ubuntu software Center... Sometimes .deb packages... and very rarely the terminal unless I know the code.

---

### Post by kaldor on 2010-07-03
OS X: .dmg and .pkg
Sabayon: .tar.* or Repos

---

### Post by chessnerd on 2010-07-03
I prefer Synaptic. It is the balance between the Software Center and using apt-get. 

The Software Center doesn't tell me what dependencies it is going to install and if I accidentally installed a KDE program it would eat up 500 MB of space in one go. Also, the Software Center seems slower.

You can't really search for packages with apt-get. If I know exactly what I'm trying to install I might use apt-get, but I typically go to Synaptic anyway.

I do install .deb packages occasionally, but I'll generally go for an older version from the repositories if it is available.

---

### Post by Hman242 on 2010-07-03
I use all of those ways, although Synaptic is probably used the least.

---

### Post by corrytonapple on 2010-07-03
Terminal and apt-get is faster. Plus you can see what its doing.:)

---

### Post by lisati on 2010-07-03
I voted "other" in the absence of "all of the above".....

---

### Post by undecim on 2010-07-03
No "compile from source" option?

Also, I use aptitude, but marked apt-get as my choice (since they're both CLI)

---

