---
title: "Is there a way to download a package and all related dependencies without..."
date: 2005-10-13
forum: Repositories &amp; Backports
---

### Post by magomago on 2005-10-13
getting one by one? I want to let my little brother use Ubuntu back at home[I've had him on Gentoo +Fluxbox and he is getting the hang of it, but I wanna ease his load on him for now and give him something easier to work with so he doesn't have to mount /dev/cdrom0 /mnt/cdrom everytime ;)], but over ther we only have a 56k modem.  So I figured I will send home 5.10 and then a disc full of alll the relevant software he needs.  

But going through the list I noticed I have to download things one by one, which is a huggge hassle.  Package A will list B C D E as dependencies.  Is there a way to get  B C D E at the same time?  I ask this because I need to get audio codecs, and some other programs (such as gcc 3.4 for compiling his modem drivers) onto a Disc and each lists quite a bit when it comes to dependencies

Thanks!

---

### Post by invalid on 2005-10-13
apt-get / synaptic will automatically download and install required dependencies.

If you are trying to get a slew of unrelated packages, you can:
sudo apt-get install package1 package2 package3 etc...
or select multiple packages with synaptic

I hope this is what you were looking for, if not someone else may be able to answer better.

Cheers,
Cb

---

### Post by magomago on 2005-10-13
What I mean speciically is

PC A has broadband connection

PC B over 60 miles away doesn't

I plan to put Ubuntu on PC B

Howvever, PC B will require several things from apt-get.  However, it will take too long

With PC A I can search the respositories and get what is needed.  However, due to dependencies this takes too long.  IE: Program 1 required c d e f as dependencies

Is there a way for PC A to get the packages i need for PC B faster, without having to go through the mundane tastk of getting all of program 1s dependencies?

---

### Post by doclivingston on 2005-10-13
1) run ```
apt-get --print-uris install packagea package b
``` on computer B to get a list of the files you need (including dependencies). You can do this on computer A *if it has the same things installed*.
2) go to computer A and download everything from step 1
3) get the files to computer B and either
  a) install them with "sudo dpkg -i file1.deb file2.deb ...", or
  b) put them in /var/cache/apt/archives/, and then use apt-get or synaptic to install the packages.

---

