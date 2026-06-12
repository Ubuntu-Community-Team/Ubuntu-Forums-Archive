---
title: "Ubuntu Workstation"
date: 2008-08-01
forum: Ubuntu Brainstorm
---

### Post by otterpop81 on 2008-08-01
Hello,

As many of you may have noticed already I'm new to posting around this forum, so if I step on anyone's toes or come across like a total moron, I apologize. Feel free to ignore me.

I've been using Ubuntu at home since about 5.04, and I've recently been putting it on some boxes at work, and with these recent installs, the biggest annoyance of Ubuntu has been bothering me. It's basically this: Ubuntu doesn't have a "workstation" variant.

After I install Ubuntu, I have to put together a build environment myself. Yes I know about build-essential, but that only gets you enough to make "hello world" and use standard UNIX services. Every single other thing I want to build with I have to install myself. Man pages? no chance! Those are separate too.

I understand that the Ubuntu devs like to have the distro small enough to fit on a single CDROM and have a standard installation where the user doesn't have to dig through packages and select them on or off like in RedHat. However, I'd be willing to download a second ISO, or burn a DVD instead, to be able to do an install and be immediately productive. So since this isn't likely to just happen right away, I figured I'd go ahead and start a list of packages that I'd consider to be necessary for a "workstation." Feel free to add your own.

Development:
build-essential
libjpeg-dev
libpng-dev
libgif-dev
libz-dev
libbz2-deb
libgtk2.0-dev
libgtkhtml2.0-dev
libglade2-dev
libgtkmm-2.4.dev
libglademm-dev
libgnome2-dev (and all that goes with it)
libgnomemm-dev
lesstif-dev
libqt4-dev (along with -mysql -odbc -java -perl etc.)
OpenGL headers (libgl-dev, but mine come from nvidia-glx-new-dev)
libglut-dev
A java JDK
libpcap-dev
libgdbm-dev
libdb-dev

Docs:
manpages
manpages-dev
manpages-posix-dev


Programs:
vim (full up vim)
emacs (I don't use it, but it should be there)
joe (editor, because I like it :) )
minicom
ncftp
glade
wireshark
lynx/links
imagemagick


While I understand that Ubuntu's motto is "Linux for Humans," one has to also realize that Ubuntu's installed base is currently mostly computer geeks. While it's a fine distro for the computer illiterate to check email, it's just too much work to set up for productivity (i.e.: things that geeks do). Maybe I'm barking up the wrong tree here, and maybe some of you will say "go back to Red Hat," but the reason I'm writing here is because I really do like the things that Ubuntu has gotten right like the ease of install and its utilization of dpkg and apt. In addition, Ubuntu's services seem to work pretty well. Compare that to Red Hat where up2date crashes or hangs frequently.

Thanks for letting me rant on your forum.

Alan.

---

### Post by ad_267 on 2008-08-01
There is a dvd but I'm not sure what's on it exactly: [http://cdimage.ubuntu.com/releases/hardy/release/](http://cdimage.ubuntu.com/releases/hardy/release/)

Also you should add vim to your list as only vim-tiny is installed by default.

---

### Post by otterpop81 on 2008-08-01
They sure have the DVD hidden away. I went back to the Ubuntu site and looked for it on the download page and it's nowhere to be found. The only mention of it is where they show that you can buy it on the "How can I get Ubuntu" page.

Thanks for the info. Now to find some blank DVDs.

Alan.

---

### Post by smartboyathome on 2008-08-01
If you want a distro for geeks, get another distro or make your own (you can use [Remastersys]("http://www.remastersys.klikit-linux.com/")). This distro is not meant for geeks, never will be.

---

### Post by otterpop81 on 2008-08-02
> **smartboyathome said:**
> If you want a distro for geeks, get another distro or make your own ... This distro is not meant for geeks, never will be.

Yeah that sounds familiar, and is the quick and convenient answer. Yes, Ubuntu isn't designed for geeks. I get that. The reality is though, that people who use Linux (Ubuntu included) are geeks. Computer programmers, computer enthusiasts, Slashdot readers, etc. It's one thing to make something easy to use, but does it make it _harder_ for the computer illiterate to use if it has a development environment or manpages? No, it doesn't.

All I'm saying is that Ubuntu is a fine distribution for general purpose use once you apt-get the useful tools. What's wrong with having a variant where that stuff is provided for you?


By the way, I downloaded and installed the DVD to find out that the extra packages on it aren't installed at all. They just sit there while the standard distribution is installed to you computer. You can point your apt system to use the DVD, but what's the point of that when you can pull them down directly from the online repos? In addition, the DVD doesn't even have many development headers on it. There are only about 50 debs which have "-dev" in their names at all. (What's in the 4GB that's on that DVD is anyone's guess really. Very little of what I looked for was actually there).

Alan.

---

### Post by smartboyathome on 2008-08-02
Ubuntu isn't providing for the geeks, the way the head developers think is that if a geek wants something, they can get it. It provides support for the computer illiterate who are just learning. The way you worded that, it sounded like we should tailor it to what you feel needs to be in it.

> **otterpop81 said:**
> All I'm saying is that Ubuntu is a fine distribution for general purpose use once you apt-get the useful tools. What's wrong with having a variant where that stuff is provided for you?

Nothing is wrong, you can make your own Devbuntu varient if you like. It is just that Canonical has enough projects on their hands, the developer community can make this one better since they are the ones who will use it.

---

### Post by cszikszoy on 2008-08-02
I think its a pretty good idea.  I don't think the OP is advocating including all of these tools in the basic Ubuntu flavor.  I think he is in favor of making an officially supported workstation version, for power users or more development/work related individuals.  There's nothing wrong with choice.

And besides, its not like the Ubuntu admins _only_ make the standard Ubuntu distribution.  They already have Ubuntu Studio, which is tailored towards media creation, and the Ubuntu netbook remix, which is more suited for the netbook laptops and such.

It seems only logical to me that if they can create an official version of Ubuntu that caters to media creation, then they could (and maybe should) also create a version that caters more towards programming / software development.

I'll give this idea a +1.

---

### Post by borris.morris on 2008-10-30
I +1 it too..

---

