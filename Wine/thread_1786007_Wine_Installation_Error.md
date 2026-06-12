---
title: "Wine Installation Error"
date: 2011-06-19
forum: Wine
---

### Post by AmontilladoMason on 2011-06-19
I tried to install Wine from the Software Center, I followed the instructions, added what needed to be added, yadda yadda yadda. Everything I could find through Google and these forums that needs to be done was done. It got about halfway through the installation, then an error message popped up saying "Failed to download package files" and told me to check my internet connection, even though I'm on the internet right now. This is the text in that error message.

Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3_1.3.22-0ubuntu1~ppa1~maverick1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3_1.3.22-0ubuntu1~ppa1~maverick1_i386.deb) Hash Sum mismatch
Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3-gecko/wine1.3-gecko_1.2.0-0ubuntu1~maverickppa1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3-gecko/wine1.3-gecko_1.2.0-0ubuntu1~maverickppa1_i386.deb) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.5.4~dfsg-1ubuntu8.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.5.4~dfsg-1ubuntu8.4_i386.deb) Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/ttf-umefont/ttf-umefont_416-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/ttf-umefont/ttf-umefont_416-2_all.deb) Hash Sum mismatch

I also tried to install it via the terminal, as was instructed by some of the other threads I've seen. These are the errors I received near the end of the text.

Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3_1.3.22-0ubuntu1~ppa1~maverick1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3_1.3.22-0ubuntu1~ppa1~maverick1_i386.deb)  Hash Sum mismatch
Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3-gecko/wine1.3-gecko_1.2.0-0ubuntu1~maverickppa1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3-gecko/wine1.3-gecko_1.2.0-0ubuntu1~maverickppa1_i386.deb)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.5.4~dfsg-1ubuntu8.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.5.4~dfsg-1ubuntu8.4_i386.deb)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/t/ttf-umefont/ttf-umefont_416-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/t/ttf-umefont/ttf-umefont_416-2_all.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

One point I'd like to make, that (in my admittedly naive and uneducated opinion) may have something to do with it, is that I'm currently test running Moon Linux, I haven't installed it. The installation is at a standstill at the "Getting the time from a network server", I'm currently stuck on the "Who are you?" phase of the installation. If you would be kind enough to help, please keep in mind I'm INCREDIBLY ignorant when it comes to Linux, so if you could, start from the top in any feedback or support you'll be giving.

---

### Post by dino99 on 2011-06-19
can you post here: cat /etc/apt/sources.list

and you might use instead: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by AmontilladoMason on 2011-06-19
> **dino99 said:**
> can you post here: cat /etc/apt/sources.list

and you might use instead: [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

I tried the link you sent me, but it didn't change anything from what I can tell. I'm still getting the error message. Here's what I got when I copied and pasted what you requested into my terminal.

deb [http://moonos.linuxfreedom.com/moonos](http://moonos.linuxfreedom.com/moonos) neak main upstream
deb-src [http://moonos.linuxfreedom.com/moonos](http://moonos.linuxfreedom.com/moonos) neak main upstream #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted universe multiverse #Added by software-properties

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted universe multiverse #Added by software-properties

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted universe multiverse #Added by software-properties
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main

---

### Post by AmontilladoMason on 2011-06-19
Also I'm using MoonOS if that makes any difference.

---

