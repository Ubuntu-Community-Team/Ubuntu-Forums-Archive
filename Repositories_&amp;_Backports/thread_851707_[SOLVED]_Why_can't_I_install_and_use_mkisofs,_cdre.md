---
title: "[SOLVED] Why can't I install and use mkisofs, cdrecord instead of genisoimage and wod"
date: 2008-07-06
forum: Repositories &amp; Backports
---

### Post by mytwobears on 2008-07-06
For the better part of today, I have been trying to install and use cdrtools and the various elements of it, ie,mkisofs, cdrecord etc.  However, it has become abundantly clear to me that this is impossible, at least for the average user. 

Clearly, Hardy Heron has been coded to disallow the user the choice to use these tools.  Every time I install these programs, whether from the Ubuntu repo. or compiled from source, I am instructed to install genisoimage and wodim instead. The cdrtool programs have been installed in the optional directory by default but Ubuntu keeps telling me that they are not installed and I should install genisoimage and wodim.  

This is troubling; I came to linux, open source, and Ubuntu because of the freedom and control espoused, but this is clearly a restrictive and oppressive practice, disallowing the user the ability to choose what packages she wants to use in the operating system she has installed on her computer.  

I have searched through the forums and the internet and have tried a number of procedures but have not been able to do two simple things: (1) remove genisoimage and wodim without removing half of my entire system and (2) install the current version of cdrtools and have Ubuntu recognize that they are installed and use them as backends for programs and from the terminal.  

Please let me know if there is some way I can do this and please provide detailed directions on how.  Thank you so much for your time and help.

---

### Post by mytwobears on 2008-07-11
OK, I solved this issue myself.  I had to remove all the hard and sym links that linked the genisoimage and wodim files to mkisofs and cdrecord, then I deleted the files that i removed the links from (ie, genisoimage, cdrecord and mkisofs) from the bin folder, then I moved the mkisofs and cdrecord files that had been installed by default in the optional folder to the bin folder.  This allowed me to use mkisofs without it calling genisoimage.  To use mkisofs and cdrecord as the defaults in Brasero, I had to delete the genisoimage and wodim files from the Brasero plugin folder.  

I was able to make an iso file using mkisofs and use Brasero to burn the image to a blank CD without any errors and I can watch the CD in both Ubuntu and Windows.

Hope this helps someone :).

---

### Post by IgnorantGuru on 2008-08-08
I think it is horrible the way they have replaced the genuine cdrecord with the buggy garbage called "wodim".  It is creating an unending list of bugs (which are going completely unaddressed).  Read about this issue here... [http://cdrecord.berlios.de/old/private/linux-dist.html](http://cdrecord.berlios.de/old/private/linux-dist.html)

Politics, and obviously Debian/Ubuntu is taking the fascist road.

I can't find any repository for Kubuntu Hardy cdrtools - any help?  And if you could write a little step-by-step guide on how to replace wodim I would appreciate it.  Thanks to a wodim bug I can't burn any CDs now.

---

### Post by IgnorantGuru on 2008-08-08
Answering my own question, here is what worked for me.  Use at your own risk.

Replacing wodim with cdrtools

The issue:
[http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)

"If you are not running the original software, get recent original software from the "Download recent" or from the "Download latest"  location. Unpack, compile by running "make" and install. Make sure that all programs that send (SCSI) commands to CD/DVD/Blu-Ray drives are installed to be suid root.

If you are running cdrtools frontends like k3b and others and do not like to replace these programs with original versions, you should remove files like /usr/bin/wodim, /usr/bin/genisoimage, /usr/bin/icedax, /usr/bin/readom and replace them by links to the original software."


Download latest cdrtools from [http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)
Unpack
CD to the directory cdrtools is in.
sudo make
sudo make install
sudo make clean

Files are installed to /opt/schily
(you may want to change their ownership to root:root)

Move the following files (some will be links) from /usr/bin to a junk folder...
	cdrecord
	genisoimage
	mkisofs
	readom
	wodim

Create links:
	/usr/bin/cdrecord --> /opt/schily/bin/cdrecord
	/usr/bin/genisoimage --> /opt/schily/bin/mkisofs
	/usr/bin/mkisofs --> /opt/schily/bin/mkisofs
	/usr/bin/readom --> /opt/schily/bin/readcd     (correct?)
	/usr/bin/wodim --> /opt/schily/bin/cdrecord
	/usr/bin/readcd --> /opt/schily/bin/readcd
	/usr/bin/mkhybrid --> /opt/schily/bin/mkhybrid
	/usr/bin/cdda2wav --> /opt/schily/bin/cdda2wav


Related Links:
[http://ge.ubuntuforums.com/showthread.php?p=5216386#post5216386](http://ge.ubuntuforums.com/showthread.php?p=5216386#post5216386)
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/149076)
[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/226650](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/226650)

---

### Post by IgnorantGuru on 2008-08-09
Someone asked me for a more detailed step-by-step so I will post it here.  Please note that this is a brute force method for replacing wodim - your package manager will not be aware of the change and subsequent updates may break the software (though repeating these steps should restore it).  However, since the Ubuntu folks refuse to release a package for cdrtools, this is one way to work around that.

```
# Open a terminal window (Konsole in Kubuntu) and enter
# the following commands

# install compiler tools
sudo apt-get install build-essential

# Make sure you're in the home folder
cd ~

# Make a working folder and change to it
mkdir cdrtools
cd cdrtools

# Download latest cdrtools from http://cdrecord.berlios.de/private/linux-dist.html
wget ftp://ftp.berlios.de/pub/cdrecord/alpha/cdrtools-beta.tar.gz

# Unpack
tar xzf cdrtools-beta.tar.gz

# CD to the directory cdrtools is in.
cd cdrtools-2.01.01

# Compile and install
make
sudo make install

# Files are installed to /opt/schily
# (you may want to change their ownership to root:root)
sudo chown root:root /opt/schily/bin/*

# Move the following files (some will be links) from /usr/bin to a junk folder...
sudo mkdir /opt/schily/replacedfiles
sudo mv /usr/bin/cdrecord /opt/schily/replacedfiles
sudo mv /usr/bin/genisoimage /opt/schily/replacedfiles
sudo mv /usr/bin/mkisofs /opt/schily/replacedfiles
sudo mv /usr/bin/readom /opt/schily/replacedfiles
sudo mv /usr/bin/wodim /opt/schily/replacedfiles

# Create links:
sudo ln -s /opt/schily/bin/cdrecord /usr/bin/cdrecord
sudo ln -s /opt/schily/bin/mkisofs /usr/bin/genisoimage
sudo ln -s /opt/schily/bin/mkisofs /usr/bin/mkisofs
sudo ln -s /opt/schily/bin/readcd /usr/bin/readom
sudo ln -s /opt/schily/bin/cdrecord /usr/bin/wodim
sudo ln -s /opt/schily/bin/readcd /usr/bin/readcd
sudo ln -s /opt/schily/bin/mkhybrid /usr/bin/mkhybrid
sudo ln -s /opt/schily/bin/cdda2wav /usr/bin/cdda2wav

# Remove working folder
cd ~
sudo rm -r cdrtools
```

---

### Post by etfloyd on 2008-09-03
Thank you! I followed your step-by-step and the froze the cdrkit-based packages. All the bugs and problems promptly went away. 

This has been an interesting debugging journey. The cdrkit tools (wodim, et al) on Hardy have bugs that don't show up until later and, in my case, if I hadn't had an XP system to test on, would have resulted in a huge waste of time, energy, money, and good will. And, the bugs have been known for quite some time and have not been addressed in Hardy. I don't trust cdrkit any more. I understand that there are strong personalities involved and licensing subtleties that matter to distribution support. However, for my personal use, I just really couldn't care less about any of that. 

Bottom line, I need for the tools to work reliably; cdrkit doesn't, cdrtools does. If there are licensing issues, well, that's what the "free nonfree" good/bad/ugly repositories are all about, right?  I'm marginally Linux-competent, enough to get cdrtools working, with your guidance. What about the poor Windows user trying out Ubuntu for the first time?

There's absolutely no excuse for not packaging cdrtools and making them available in an alternative repository. The average user should have a choice.

---

### Post by coldcoffee on 2008-09-28
Thank you ignorantguru. I followed your little tutorial and it went off with no hitches. And I did a little googling and readom and readcd are in fact the same.

I have used ubuntu for about a year now and love it. So far this is the only complaint I have, this issue here. But at least it is less than the issues I have with other operating systems. I wish they would find it in their heart to give us the choice without having to do these work arounds.

Thank you very much. I for one am very greatful.

---

### Post by IgnorantGuru on 2008-09-30
Glad it worked for you coldcoffee.  I agree that the positives of Ubuntu far outweigh the negatives, but we have to complain about *something*.  :)  It's also important to remind the devs to leave users in control of their systems, as much as the devs are tempted to centralize control.  I don't mind their changing the default cd burner for the dist, etc., but when they begin burning books there's a problem.

---

### Post by Pidgin on 2008-10-04
> **IgnorantGuru said:**
> Someone asked me for a more detailed step-by-step so I will post it here.  Please note that this is a brute force method for replacing wodim - your package manager will not be aware of the change and subsequent updates may break the software (though repeating these steps should restore it).  However, since the Ubuntu folks refuse to release a package for cdrtools, this is one way to work around that.

```
# Open a terminal window (Konsole in Kubuntu) and enter
# the following commands

# Make sure you're in the home folder
cd ~

# Make a working folder and change to it
mkdir cdrtools
cd cdrtools

# Download latest cdrtools from http://cdrecord.berlios.de/private/linux-dist.html
wget ftp://ftp.berlios.de/pub/cdrecord/alpha/cdrtools-beta.tar.gz

# Unpack
tar xzf cdrtools-beta.tar.gz

# CD to the directory cdrtools is in.
cd cdrtools-2.01.01

# Compile and install
sudo make
sudo make install
sudo make clean

# Files are installed to /opt/schily
# (you may want to change their ownership to root:root)
sudo chown root:root /opt/schily/bin/*

# Move the following files (some will be links) from /usr/bin to a junk folder...
sudo mkdir /opt/schily/replacedfiles
sudo mv /usr/bin/cdrecord /opt/schily/replacedfiles
sudo mv /usr/bin/genisoimage /opt/schily/replacedfiles
sudo mv /usr/bin/mkisofs /opt/schily/replacedfiles
sudo mv /usr/bin/readom /opt/schily/replacedfiles
sudo mv /usr/bin/wodim /opt/schily/replacedfiles

# Create links:
sudo ln -s /opt/schily/bin/cdrecord /usr/bin/cdrecord
sudo ln -s /opt/schily/bin/cdrecord /usr/bin/cdrecord
sudo ln -s /opt/schily/bin/mkisofs /usr/bin/genisoimage
sudo ln -s /opt/schily/bin/mkisofs /usr/bin/mkisofs
# Is the following correct (is readcd a version of readom??)
sudo ln -s /opt/schily/bin/readcd /usr/bin/readom
sudo ln -s /opt/schily/bin/cdrecord /usr/bin/wodim
sudo ln -s /opt/schily/bin/readcd /usr/bin/readcd
sudo ln -s /opt/schily/bin/mkhybrid /usr/bin/mkhybrid
sudo ln -s /opt/schily/bin/cdda2wav /usr/bin/cdda2wav

# Remove working folder
cd ~
sudo rm -r cdrtools
```

Errors are generated in the process of compiling. Do I need some extra packages to compile the source?
That's perhaps a silly question. But I am just a newbie.
Thanks!

---

### Post by Pidgin on 2008-10-04
I think there is another way to install cdrtools. There is a team called the Ubuntu Burning Team. Check the page below:

[https://launchpad.net/~ubuntu-burning/+archive]("https://launchpad.net/~ubuntu-burning/+archive")

They have provided apt sources of cdrtools. I added that to my sources and attempted to install the package mkisofs. The result was that the package genisoimage replaced mkisofs. Then I tried to uninstall the package genisoimage. It was surprising that the system told me that the package ubuntu-desktop would also be uninstalled, thus preventing me to get rid of the package genisoimage. In that situation, the packages provided by the Ubuntu Burning Team seems unusable.

Does anyone have a solution?

Thanks!

---

### Post by IgnorantGuru on 2008-10-04
> **Pidgin said:**
> Errors are generated in the process of compiling. Do I need some extra packages to compile the source?
That's perhaps a silly question. But I am just a newbie.
Thanks!

I would try adding build-essential...
```
sudo apt-get install build-essential
```

I can't think what else it would be.  If that doesn't do it then you will need to examine the errors to see what you're missing, or post the error here.

---

### Post by Pidgin on 2008-10-04
> **IgnorantGuru said:**
> I would try adding build-essential...
```
sudo apt-get install build-essential
```

I can't think what else it would be.  If that doesn't do it then you will need to examine the errors to see what you're missing, or post the error here.

Thank you. I will have a try.

---

### Post by Pidgin on 2008-10-04
It works! After installing the package build-essential, I successfully compiled cdrtools and replaced cdrkit. Instead of creating links, I copied those files to /usr/bin/.

I think the files that should be replaced are:

```

btcflash
cdrecord
devdump
genisoimage
isodump
isoinfo
isovfy
mkisofs
readom
wodim

```

Move those files out to another place. And then copy files from /opt/schily/bin/ to /usr/bin.

Finally just make these links:

```

genisoimage -> mkisofs
wodim -> cdrecord
readom -> readcd

```

---

### Post by danielrb on 2008-10-09
I'm trying to install cdrtools but it seems that  [ftp://ftp.berlios.de/pub/cdrecord/alpha/cdrtools-beta.tar.gz](ftp://ftp.berlios.de/pub/cdrecord/alpha/cdrtools-beta.tar.gz) is not available, can you helpme?

---

### Post by IgnorantGuru on 2008-10-10
> **danielrb said:**
> I'm trying to install cdrtools but it seems that  [ftp://ftp.berlios.de/pub/cdrecord/alpha/cdrtools-beta.tar.gz](ftp://ftp.berlios.de/pub/cdrecord/alpha/cdrtools-beta.tar.gz) is not available, can you helpme?

I just tried it and it's available.  If you can't reach that site then maybe you can find it elsewhere.  
Current version is cdrtools-2.01.01a45.tar.gz  (2MB)

---

### Post by editrix on 2008-11-18
As I understand it, ubuntu-desktop is just a metapackage, and can be safely removed without breaking anything. If you search **remove ubuntu-desktop** at uboontu.com (last link in my sig) you'll see lots of (unnecessary) worries about it.

And, if you're brave enough to believe me ;-) then could you please post and tell us if the install went okay, anf if you can now burn CDs?

---

### Post by Dawa on 2008-11-24
delete

---

### Post by Alejandro Nova on 2009-01-12
I replied a similar thread and have to conclude something: this is a bug. A serious one. 

I understand that Debian (and Ubuntu) don't want to include cdrecord **in its main repository**. They think that the *choice of venue* clause present in the CDDL (the license that cdrecord uses) is incompatible with the DFSG (Debian Free Software Guidelines), and they decided to replace it with wodim. Understandable.

What I don't understand nor condone is what's really happening: **genisoimage and wodim try to destroy cdrecord, and to overwrite it if someone tries to install cdrecord through the packaging system**, and that hasn't anything to do with the main repo, of the lack of one. To put this in perspective: everyone knows that nVidia drivers are non free. The nVidia license, unlike CDDL, is a non free license. What would happen if Debian maintainers, suddenly, decide to "replace" the nVidia driver with the free, reverse engineered "nouveau" driver, **and write the nouveau packages specifically to overwrite and cripple the nvidia-glx component if you try to install the nVidia non free drivers**? The Internet would enrage against Debian, of course. Why, oh why, are they doing this to cdrecord?

If I want to use cdrecord instead of wodim, it's my business. I shouldn't be forced to use GPLvx software. If I want to use Skype, Flash or non-free software, I must be allowed to do so. If I want to use CDDL, MPL software (like a beautiful piece of software called Mozilla Firefox, for instance) or whatever-GPL-incompatible-but-freely-licensed-software I must **be allowed to do so**. No seek and destroy, please, and I'm talking to you, Debian. One thing is your main repo and another is the seek-and-destroy game, only equalled by Apple in their iPhone. Your DFSG is fine for your main repo, but **impeding me using a program I want to use irreversibly renders your distro non free, and renders it non free in a way that would be preferable for me to use Windows**.

---

### Post by maybeway36 on 2009-02-07
The cdrkit package is designed with the assumption that cdrtools is not present on your computer. This isn't malicious; it's just a design flaw.
Also, when you bold text like that it makes you sound angrier.

---

### Post by dasbooter on 2009-03-02
Hey everybody I just wanted to let you know that it appears some very kind people at launchpad have compiled packages for cdrtools up to intrepid. Here is the link [https://launchpad.net/~ubuntu-burning/+archive/ppa]("https://launchpad.net/%7Eubuntu-burning/+archive/ppa")....
I am wondering if I have to remove the links and stuff still in Intrepid as this thread suggests... I dont even know if this is going to fix my problem. I have had to dvd burners in this machine and I just cant seem to burn a rewritable? Sigh...


[COLOR=Red][SIZE="6"]Yaaaa Snaaap!![/SIZE][/COLOR]

I installed those packages and after a few pitfalls got stuff working.I installed the packages along side wodim and geniso and that was my first mistake. I went for ```
which cdrecord
``` looking for the newly installed cdrecord and it showed /usr/bin/cdrecord. So tried to write an iso from the terminal with ```
cdrecord -v -dao speed=4 dev=/dev/dvd /home/insertusernamehere/movie.iso

```and up popped Wodim which promptly choked and spat out an error and the dvd. So removed the packages in cdrkit(wodim and geniso and unfortunately ubuntu desktop and reistalled cdrecord and was able to write on a maiden dvd rewritable and force a format of the rewritable that wodim choked on and then write an iso onto that. Now I guess I am faced with installing a front end... most likely k3b and I suppose it will want to reinstall wodim and geniso right so I may have to also create those symlinks or I suppose I could compile my own k3b to use cdrecord either way I see it will be a pain in the a** to upgrade the distro...These burning problems make attracting other OS users a nonstarter and I can no longer blame it on my hardware!

Further to the saga I just used nero in vmware on the same machine to burn a movie to the same disk... I feels so icky all over god save me from the demon they call M$ oh well at least I have downlloaded the source for k3b but dont hold your breath :)

---

### Post by mgol on 2009-12-26
@Pidgin
IMHO You shouldn't invoke 'make' with root priviledges, there's no reason for that. In fact, one should avoid using root account for files in $HOME folder. There is also no need to invoke 'make clean' if You later delete the directory.

Corrected script attached, one can run it by:
```
chmod +x cdrtools-install.sh
./cdrtools-install.sh
```

EDIT: I changed script a little so that it's more reliable; I also attached a script allowing to restore original tools if one wants.

---

### Post by ryuragnas on 2009-12-27
I'm running Ubuntu 9.10, and have spent 3 days since installing, which was, ironically, 3 days ago, trying to install cdrtools. It installs (I think?) fine, but whenever i try to burn it fails, at 0%. I have tried using the scripts mgol has posted, but after running them, it still fails to burn.
I didn't compile with smake, so could that be the issue?

I'm using a ASUS Pro31Jc laptop with:

Kernel: Linux 2.6.31-16-generic
CPU: Intel(R) Core(TM)2 CPU         T5200  @ 1.60GHz
RAM: 2.0 GB
HDD: 320GB
DVD-Burner: QSI DVD+- RW SDW-082K

---

### Post by mgol on 2009-12-28
@ryuragnas
I also use Ubuntu Karmic (64-bit). I installed cdrtools using attached scripts and I was able to erase CD-RW and to record a few directories to it, starting multisession mode. Everything worked fine.

I don't use smake, just usual GNU make. What did You exactly have problem with? Did recording work with old tools (wodim etc.)?

EDIT: I modified scripts a little but it wasn't a large change.

P.S. If one wants to use man pages provided by Joerg Schilling, one should add the following to ~/.bashrc:
```
# cdrtools man path
unset MANPATH
export MANPATH=/opt/schily/man:$(manpath)
```

---

