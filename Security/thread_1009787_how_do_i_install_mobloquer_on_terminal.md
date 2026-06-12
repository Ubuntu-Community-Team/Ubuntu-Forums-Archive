---
title: "how do i install mobloquer on terminal?"
date: 2008-12-13
forum: Security
---

### Post by shiningkenmonster on 2008-12-13
i downloaded the file mobloquer off the website, but i wasnt sure how to install it.

so how do i install it on the terminal?

---

### Post by blackened on 2008-12-13
There are packages for it if you don't want to compile the source. 

Follow the instructions at the bottom of the page here -> [http://moblock-deb.sourceforge.net/]("http://moblock-deb.sourceforge.net/")

---

### Post by fghi906 on 2008-12-15
[size=9pt]Pearlove.com lists the latest pearl jewelry products with affordable wholesale prices. Pearlove are willing to design different jewelry styles to meet different occasions, including wedding jewelries, birthday gift, anniversary jewelry, cocktail, Christmas jewelry, and etc. The jewelries are hand made of genuine cultured freshwater pearls, 925 silver materials, Swarovski crystals, corals, turquoises and gemstone beads. Pearlove.com, online jewelry wholesaler of Chinese fine jewelries, is launching the newest models on the webpage, and update new products everyday. To meet different market, Pearlove sorts the most suitable styles to make into jewelry sets and puts them in respectively corresponding products catalogues. For example, jewelry styles can be worn on Christmas Eve are put in catalogue &#8220;Christmas Gift Jewelry&#8221;; daily wear styles are in catalogue &#8220;Office & daily wear&#8221;; more details are showed on: [[color=#0000ff]http://www.pearlove.com/pearl-jewelry-c-5.html[/color]](http://www.pearlove.com/pearl-jewelry-c-5.html)  The styles listed in catalogue &#8220;Pearl Jewelry Set&#8221; are only part of Pearlove&#8217;s fantastic jewelries. Pearlove designs and hand crafts fine jewelry featured with a variety of materials, including gemstone beads, turquoises, corals and sterling silver fittings. Pearlove.com sells its products with reasonable wholesale prices. The beauty of Pearlove's designs continues to earn the company praise and reputation from clients who purchase its jewelry for wholesale business, personal or retail use. Because the range of designs provided by Pearlove Jewelry Inc. allows the company to fit a range of occasions and holidays, including weddings, anniversaries, birthdays and Christmas. What&#8217;s more, Pearlove&#8217;s designers also pay pretty attention to the assortment of both loveliness and versatility of the jewelry styles. They immit this spirit at every time they design jewelry styles. In this way, Pearlove&#8217;s Jewelry styles usually can be multi-used, one style jewelry usually can be used for at least 3 occasions. For instance, model NS49 can be worn in wedding party, anniversary party, birthday or daily. More details are showed on [[color=#800080]http://www.pearlove.com/christmas-gift-jewelry-cl-49.html[/color]](http://www.pearlove.com/christmas-gift-jewelry-cl-49.html) and [[color=#0000ff]https://www.pearlove.com/products_new.php[/color]](https://www.pearlove.com/products_new.php) . Pearlove Jewelry Inc. is able to keep the cost prices of their pearl jewelry down for a variety of reasons. The company lies in China, all pearls are directly from Chinese pearl farms at the lowest costs. In addition, the company can control the labor costs at a very low level. Pearlove owns a great and high efficiency working team which can cut down working cost during high efficiency team work. In this way, this company can offer medium and high quality pearl bridal jewelry at the lowest prices. About Pearlove Jewelry Inc.Pearlove Jewelry Inc. owns online jewelry store - [http://www.pearlove.com/](http://www.pearlove.com/). The jewelry products include freshwater pearl jewelries like necklaces, bracelets, earrings, pendants and rings, sterling silver jewelries and other gemstone jewelries such as coral, turquoises, shells, and etc.[/size]

---

### Post by shiningkenmonster on 2008-12-19
yeah, i tried to that. it said it was not found. or maybe i did something wrong.

I also went to:

[http://mobloquer.foutrelis.com/download](http://mobloquer.foutrelis.com/download)

under the Ubuntu/Debian packages section

i typed in the terminal:
> sudo apt-get update
sudo apt-get install moblock mobloquer

it says: Couldn't find package moblock. 
how do i install mobloquer in my Dell's version of Ubuntu?

---

### Post by blackened on 2008-12-19
You need to add their repository to apt's sources list

```
gksudo gedit /etc/apt/sources.list
```

Add the following to the end of the file that opens in gedit:

```
deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```

Save the file and close gedit.

Then add the verification key (in the terminal):

```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -

```

and finally

```
sudo apt-get update
sudo apt-get install moblock mobloquer
```

---

### Post by shiningkenmonster on 2008-12-19
thanks, i did all the steps and i got this error message

> Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Fetched 3221B in 2s (1152B/s)
W: Failed to fetch [http://moblock-deb.sourceforge.net/debian/dists/hardy/Release](http://moblock-deb.sourceforge.net/debian/dists/hardy/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
skenmon@skenmon:~$ sudo apt-get install moblock mobloquer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package moblock

---

### Post by blackened on 2008-12-20
> **shiningkenmonster said:**
> thanks, i did all the steps and i got this error message

Please post the contents of /etc/apt/sources.list wrapped in [CODE] tags.

---

### Post by jre on 2008-12-20
You seem to be on an unsupported architecture: lpia. I don't know this arch ...

To verify this you might post the output of "uname -a".

If your architecture is not supported gp to moblock-deb.sf.net and follow the steps under "*Build your own packages (all architectures)*"

---

### Post by shiningkenmonster on 2008-12-20
jkhgyfui

---

### Post by shiningkenmonster on 2008-12-20
here is the /etc/apt/sources.list
```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```


as for the uname -a command
```
Linux skenmon 2.6.24-19-lpia #1 SMP Tue Jul 29 14:02:05 UTC 2008 i686 GNU/Linux

```

LPIA stands for (Low Power on Intel Architecture) which is i686 architecture. Which was used for Intel M processor.

I am using the Intel Atom processor. (smaller than a penny/SIM card size)

as for "Build your own packages (all architectures)"
I have seen that. But I am really confuse on how to do that.
this is very similar to Skype problem that I had problems with. (and others had this problem too)

Same Architecture error.

someone on this other thread wrote this to me. I didn't get skype to work. but here it is. (this is used as an example relating to this problem that I am having to install mobloquer.)

> Here is method 1 :
I am reposting here, with links:

1. Download the Ubuntu package from Skype
2. open terminal (menu Accessories)
3. move into the folder you downloaded the package
4. Type:

Code:

sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb


And here is another :
Quote:
Originally Posted by feranick View Post
Really the i386 deb is a non issue. You can easily repackage any deb outside the repos into an lpia one. And really there aren't many. The reason you want lpia packages instead of forcing the i386, is that while the former will show up as an installed package on Synaptics, the later won't, so good luck uninstalling it. For example here's the directions to convert the stock i386 package for Skype into an lpia package:

1. Download the Ubuntu version of Skype
2. Use the Archive manager to uncompress it. Alternatively, right click on the deb package and select "extract here"
3. Rename the uncompressed folder, by changing the ending from i386 to lpia. (the folder should be now named: skype-debian_2.0.0.72-1_lpia)
4. Open the folder
5. There are 3 files. remove the debian-binary file
6. Decompress control.tar.gz. There are tree files in it.
7. Make a folder "DEBIAN" in the main folder, and placed the 3 files you just decompressed inside it.
8. Open one of the files inside DEBIAN, "control". Change the line "Architecture: i386" into "Architecture: lpia"
9. Open the other archive data.tar.gz. There is a folder "." inside. Open it (double click). Select both the folders (usr and etc) and select uncompress.
10. Remove the files control.tar.gz and data.tar.gz
11. You should now have your main folder with the following inside:
DEBIAN folder with tree text files in it (conffiles, control, md5sums); a "usr" folder and a "etc" folder.
12. You are now ready to prepare your lpia deb folder.
13. From the command line, go to the folder that contains your main skype folder you just prepared (most likely named: skype-debian_2.0.0.72-1_lpia).
14. type: dpkg --build skype-debian_2.0.0.72-1_lpia
15. Your deb package is ready. Double click on it and follow instruction. After installation it should appear in Synaptic, and from there you can remove it at any time.
16. Enjoy!!!


jre, I didn't get skype to install. And reading your website about building my own package architecture to install mobloquer. It got me confuse. it isn't a simple task to do by myself.

btw, firefox has already made their own LPIA architecture already released to the public.

---

### Post by shiningkenmonster on 2008-12-24
i still can't get mobloquer to install

---

### Post by gfdrha on 2008-12-24
> **shiningkenmonster said:**
> i downloaded the file mobloquer off the website, but i wasnt sure how to install it.

so how do i install it on the terminal?



Yeah, you are so clever, but i am sorry of that i cant help with you. i dont know of that.

---

### Post by jre on 2008-12-27
So it took me some time to answer. Follow the instructions on moblock-deb.sf.net as I already said.
**Following are the complete instructions for installing Moblock, moblock-control and mobloquer on a Ubuntu hardy system [COLOR="Red"]from source (not binary)[/COLOR] with the current (upstream) versions.** I've added a wildcard (*) for the concrete Debian package version and the architecture, so that the instructions are a bit more flexible.
[B]Make sure to go through it line for line, and stop if you receive an error message. A "warning" is ok.
[/B]Add the correct sources to your /etc/apt/sources.list. Important is this entry:
```
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```

Then do in a terminal:
```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -
sudo aptitude update

```

```
mkdir moblock
cd moblock
sudo apt-get build-dep moblock
apt-get source moblock
cd moblock-0.9~rc2
dpkg-buildpackage -rfakeroot
sudo dpkg -i ../moblock_0.9~rc2-*.deb

cd ..

mkdir moblock-control
cd moblock-control
sudo apt-get build-dep moblock-control
apt-get source moblock-control
cd moblock-control-1.1
dpkg-buildpackage -rfakeroot
sudo dpkg -i ../moblock-control_1.1-*.deb

cd ..

mkdir mobloquer
cd mobloquer
sudo apt-get build-dep mobloquer
apt-get source mobloquer
cd mobloquer-0.5
dpkg-buildpackage -rfakeroot
sudo dpkg -i ../mobloquer_0.5-*.deb

```

Note that during installing moblock-control you have to go through some "debconf" questions. Go through that process, don't abort!

You also have to give your user password once for "sudo".

If you experience problems paste the last lines from your terminal.
Greets
jre

---

### Post by shiningkenmonster on 2008-12-30
i did a 
```
skenmon@skenmon:~$ gksudo gedit /etc/apt/sources.list
```

and added ONLY
```
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```

than I followed your steps:
```
skenmon@skenmon:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
gpg: key 9072870B: "jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
skenmon@skenmon:~$ gpg --export --armor 9072870B | sudo apt-key add -
OK
skenmon@skenmon:~$ sudo aptitude update
Hit http://moblock-deb.sourceforge.net hardy Release.gpg
Hit http://moblock-deb.sourceforge.net hardy Release             
Hit http://dell-mini.archive.canonical.com hardy Release.gpg     
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Get:1 http://moblock-deb.sourceforge.net hardy/main Sources [896B]
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy/main Packages
Hit http://dell-mini.archive.canonical.com hardy/universe Packages
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-updates/main Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-security/main Sources
Ign http://dell-mini.archive.canonical.com hardy-security/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Fetched 896B in 3s (265B/s)
Reading package lists... Done
skenmon@skenmon:~$ mkdir moblock
mkdir: cannot create directory `moblock': File exists
skenmon@skenmon:~$ cd moblock
skenmon@skenmon:~/moblock$ sudo apt-get build-dep moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  build-essential debhelper dpatch dpkg-dev g++ g++-4.2 gettext html2text intltool-debian iptables-dev libc6-dev
  libnetfilter-queue-dev libnetfilter-queue1 libnfnetlink-dev libnfnetlink0 libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch po-debconf
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.4MB of archives.
After this operation, 39.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
skenmon@skenmon:~/moblock$ 

```

than I decided to use both of repos.
```
gksudo gedit /etc/apt/sources.list
```

```
deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```

and followed your steps:
```
skenmon@skenmon:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
gpg: key 9072870B: "jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
skenmon@skenmon:~$ gpg --export --armor 9072870B | sudo apt-key add -
OK
skenmon@skenmon:~$ sudo aptitude update
Hit http://moblock-deb.sourceforge.net hardy Release.gpg
Ign http://moblock-deb.sourceforge.net hardy/main Translation-en_US
Hit http://moblock-deb.sourceforge.net hardy Release             
Hit http://dell-mini.archive.canonical.com hardy Release.gpg     
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy/main Packages
Hit http://dell-mini.archive.canonical.com hardy/universe Packages
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-updates/main Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-security/main Sources
Ign http://dell-mini.archive.canonical.com hardy-security/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Reading package lists... Done
skenmon@skenmon:~$ mkdir moblock
mkdir: cannot create directory `moblock': File exists
skenmon@skenmon:~$ cd moblock
skenmon@skenmon:~/moblock$ sudo apt-get build-dep moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_hardy_main_source_Sources - open (2 No such file or directory)
skenmon@skenmon:~/moblock$ apt-get source moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_hardy_main_source_Sources - open (2 No such file or directory)
skenmon@skenmon:~/moblock$ cd moblock-0.9~rc2
bash: cd: moblock-0.9~rc2: No such file or directory
skenmon@skenmon:~/moblock$ dpkg-buildpackage -rfakeroot
bash: dpkg-buildpackage: command not found
skenmon@skenmon:~/moblock$ sudo dpkg -i ../moblock_0.9~rc2-*.deb
dpkg: error processing ../moblock_0.9~rc2-*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ../moblock_0.9~rc2-*.deb
skenmon@skenmon:~/moblock$ 
skenmon@skenmon:~/moblock$ cd ..
skenmon@skenmon:~$ 
skenmon@skenmon:~$ mkdir moblock-control
mkdir: cannot create directory `moblock-control': File exists
skenmon@skenmon:~$ cd moblock-control
skenmon@skenmon:~/moblock-control$ sudo apt-get build-dep moblock-control
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_hardy_main_source_Sources - open (2 No such file or directory)
skenmon@skenmon:~/moblock-control$ apt-get source moblock-control
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_hardy_main_source_Sources - open (2 No such file or directory)
skenmon@skenmon:~/moblock-control$ cd moblock-control-1.1
bash: cd: moblock-control-1.1: No such file or directory
skenmon@skenmon:~/moblock-control$ dpkg-buildpackage -rfakeroot
bash: dpkg-buildpackage: command not found
skenmon@skenmon:~/moblock-control$ sudo dpkg -i ../moblock-control_1.1-*.deb
dpkg: error processing ../moblock-control_1.1-*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ../moblock-control_1.1-*.deb
skenmon@skenmon:~/moblock-control$ 
skenmon@skenmon:~/moblock-control$ cd ..
skenmon@skenmon:~$ 
skenmon@skenmon:~$ mkdir mobloquer
mkdir: cannot create directory `mobloquer': File exists
skenmon@skenmon:~$ cd mobloquer
skenmon@skenmon:~/mobloquer$ sudo apt-get build-dep mobloquer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_hardy_main_source_Sources - open (2 No such file or directory)
skenmon@skenmon:~/mobloquer$ apt-get source mobloquer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_hardy_main_source_Sources - open (2 No such file or directory)
skenmon@skenmon:~/mobloquer$ cd mobloquer-0.5
bash: cd: mobloquer-0.5: No such file or directory
skenmon@skenmon:~/mobloquer$ dpkg-buildpackage -rfakeroot
bash: dpkg-buildpackage: command not found
skenmon@skenmon:~/mobloquer$ sudo dpkg -i ../mobloquer_0.5-*.deb
dpkg: error processing ../mobloquer_0.5-*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ../mobloquer_0.5-*.deb
skenmon@skenmon:~/mobloquer$ 

```

I did this twice on each alone: ```
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```

and
```
deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```

__________________
the folders of moblock and moblock-control exists. but there is nothing in them.

---

### Post by jre on 2009-01-01
Make a
sudo aptitude update

When you did the
sudo apt-get build-dep moblock
the process aborted because you presses "y". Make sure to press "Y" (capital letter) instead.

---

### Post by shiningkenmonster on 2009-01-07
```
skenmon@skenmon:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
gpg: key 9072870B: public key "jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
skenmon@skenmon:~$ gpg --export --armor 9072870B | sudo apt-key add -
OK
skenmon@skenmon:~$ sudo aptitude update
Hit http://dell-mini.archive.canonical.com hardy Release.gpg        
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Get:1 http://moblock-deb.sourceforge.net hardy Release.gpg [197B]
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Get:2 http://moblock-deb.sourceforge.net hardy Release [3024B]
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Get:3 http://moblock-deb.sourceforge.net hardy/main Sources [896B]
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy/main Packages
Hit http://dell-mini.archive.canonical.com hardy/universe Packages
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-updates/main Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-security/main Sources
Ign http://dell-mini.archive.canonical.com hardy-security/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Fetched 4117B in 2s (1469B/s)
Reading package lists... Done
skenmon@skenmon:~$ mkdir moblock
skenmon@skenmon:~$ cd moblock
skenmon@skenmon:~/moblock$ sudo apt-get build-dep moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  build-essential debhelper dpatch dpkg-dev g++ g++-4.2 gettext html2text intltool-debian iptables-dev libc6-dev
  libnetfilter-queue-dev libnetfilter-queue1 libnfnetlink-dev libnfnetlink0 libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch po-debconf
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.4MB of archives.
After this operation, 39.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
skenmon@skenmon:~/moblock$

```

and thats all it says and it does nothing else.

---

### Post by jre on 2009-01-08
D'oh, how strange.
Try it automatically with
```
sudo apt-get --assume-yes build-dep moblock
```

When I had a look at the man page I just read this for --assume-yes:
```
Automatic yes to prompts; assume "yes" as answer to all
prompts and run non-interactively. If an undesirable situation, 
such as changing a held package, trying to install a 
unauthenticated package or removing an essential package 
occurs then apt-get will abort.
```
So I wondered if there is probably a conflict in your package list (although nothing about that is stated in the output you posted.
So another solution might be to do this manually in aptitude. Please follow the next things carefully step by step. If anything goes wrong, paste here again, so take care to keep the output of aptitude!

Start it: ```
sudo aptitude
```
Then within you can search for packages, by typing "/".
As packagenames take
 build-essential
 debhelper
 dpatch
 dpkg-dev
 g\+\+
 g\+\+-4.2
 gettext
 html2text
 intltool-debian
 iptables-dev
 libc6-dev
 libnetfilter-queue-dev
 libnetfilter-queue1
 libnfnetlink-dev
 libnfnetlink0
 libstdc\+\+6-4.2-dev
 libtimedate-perl
 linux-libc-dev
 patch
 po-debconf

Select them by pressing "+".
Then the package will be marked to be installed, you will see a "pi" in the list. The "p" means that it isn't installed yet, and the "i" in the second column means that it is to be installed. If an "i" is in the first column the package is already installed and yo're fine. 

When you have marked all packages press "g". This will get you to a screen which shows all packages that will be installed. Verify that all are in

Then press "g" again and wait. You're finished when there's a
"Press return to continue."

Then you should have all necessary packages installed and can go on with the rest of the instructions I gave you.

---

### Post by shiningkenmonster on 2009-01-15
hey, the dell mini 9 with the custom edition of Ubuntu 8.04.1 which has the LPIA had a major update. Which was almost a 200 MB update to fix errors and updates and such. Skype installs just fine now with the i386 architecture file. (without modifying the file which i posted before on this thread)

I think its something to due with your server. It says LPIA architecture not found. (not sure if 'server' is the correct term or not)

---

### Post by shiningkenmonster on 2009-01-15
```
skenmon@skenmon:~$ gksudo gedit /etc/apt/sources.list
```
added
```
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```
SAVED

than:
```
skenmon@skenmon:~$ sudo apt-get --assume-yes build-dep moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/moblock-deb.sourceforge.net_debian_dists_hardy_main_source_Sources - open (2 No such file or directory)
skenmon@skenmon:~$ 

```

---

### Post by jre on 2009-01-17
After adding sources to sources.list, you need to do a "sudo aptitude update" first. This updates the list of available packages, but  not the packages themselves.

---

### Post by shiningkenmonster on 2009-01-18
```
skenmon@skenmon:~$ sudo aptitude update
[sudo] password for skenmon: 
Hit http://dell-mini.archive.canonical.com hardy Release.gpg
Get:1 http://moblock-deb.sourceforge.net hardy Release.gpg [197B]
Get:2 http://moblock-deb.sourceforge.net hardy Release [3024B]
Ign http://moblock-deb.sourceforge.net hardy Release
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Hit http://moblock-deb.sourceforge.net hardy/main Sources
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy/main Packages
Hit http://dell-mini.archive.canonical.com hardy/universe Packages
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Fetched 198B in 3s (52B/s)
Reading package lists... Done
W: GPG error: http://moblock-deb.sourceforge.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B
W: You may want to run apt-get update to correct these problems
skenmon@skenmon:~$ 


```

```
skenmon@skenmon:~$ sudo apt-get update
Get:1 http://moblock-deb.sourceforge.net hardy Release.gpg [197B]
Hit http://dell-mini.archive.canonical.com hardy Release.gpg
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Get:2 http://moblock-deb.sourceforge.net hardy Release [3024B]
Ign http://moblock-deb.sourceforge.net hardy Release
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release  
Hit http://dell-mini.archive.canonical.com hardy/main Packages
Hit http://dell-mini.archive.canonical.com hardy/universe Packages
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://moblock-deb.sourceforge.net hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Fetched 198B in 4s (43B/s)
Reading package lists... Done
W: GPG error: http://moblock-deb.sourceforge.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B
W: You may want to run apt-get update to correct these problems
skenmon@skenmon:~$ 


```

```
sudo apt-get --assume-yes build-dep moblock
```

it got cut off. but here is what is left:

```
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Fetched 198B in 3s (52B/s)
Reading package lists... Done
W: GPG error: http://moblock-deb.sourceforge.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B
W: You may want to run apt-get update to correct these problems
skenmon@skenmon:~$ sudo apt-get update
Get:1 http://moblock-deb.sourceforge.net hardy Release.gpg [197B]
Hit http://dell-mini.archive.canonical.com hardy Release.gpg
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Get:2 http://moblock-deb.sourceforge.net hardy Release [3024B]
Ign http://moblock-deb.sourceforge.net hardy Release
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release  
Hit http://dell-mini.archive.canonical.com hardy/main Packages
Hit http://dell-mini.archive.canonical.com hardy/universe Packages
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://moblock-deb.sourceforge.net hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Fetched 198B in 4s (43B/s)
Reading package lists... Done
W: GPG error: http://moblock-deb.sourceforge.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B
W: You may want to run apt-get update to correct these problems
skenmon@skenmon:~$ skenmon@skenmon:~$ sudo apt-get update
bash: skenmon@skenmon:~$: command not found
onical.com hardy-security/main Sources
skenmon@skenmon:~$ Get:1 http://moblock-deb.sourceforge.net hardy Release.gpg [197B]
bash: Get:1: command not found
Hit http://dell-mini.archive.canonical.com hardy-security/universe
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy Release.gpg
bash: Hit: command not found
Hit http://dell-mini.archive.canonical.com hardy-security/mu
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
bash: Ign: command not found
Hit http://dell-mini.archive.canonical.com hardy-security/restricted So
skenmon@skenmon:~$ Get:2 http://moblock-deb.sourceforge.net hardy Release [3024B]
bash: Get:2: command not found
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/
skenmon@skenmon:~$ Ign http://moblock-deb.sourceforge.net hardy Release
bash: Ign: command not found
Ign http://dell-mini.archive.canonical.com hardy-net
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
bash: Ign: command not found
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Pa
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
bash: Ign: command not found
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Pack
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
bash: Ign: command not found
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Igskenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updates Rease.gpg
n http://dell-mini.archive.canonical.com hardy-netbook-base/universe 
bash: Hit: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
bash: Ign: command not found
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Source
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
bash: Ign: command not found
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Igskenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-updates/muiverse Translation-en_US
bash: Ign: command not found
n http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dellskenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com harricted Translation-en_US
bash: Ign: command not found
-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.arcskenmon@skenmon:~$ Hit http://dell-mini.archive.canonicaease.gpgrdy-security Rel 
bash: Hit: command not found
hive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dellskenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com harn Translation-en_US
bash: Ign: command not found
-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mskenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hverse Translation-en_US
bash: Ign: command not found
ini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.cskenmon@skenmon:~$ Ign http://dell-mini.archive.cativerse Translation-en_USy/mul 
bash: Ign: command not found
anonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.coskenmon@skenmon:~$ Ign http://dell-minitricted Translation-en_USrdy-security/res 
bash: Ign: command not found
m hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dskenmon@skenmon:~$ Hit http:// Release.gpgchive.canonical.com hardy-netbook-base 
bash: Hit: command not found
ell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com harskenmon@skenmon:~$ Ign http://dell/main Translation-en_US.com hardy-netbook-base 
bash: Ign: command not found
dy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbooskenmon@skenmon:~$ Ign ht/universe Translation-en_USnical.com hardy-netbook-base 
bash: Ign: command not found
k-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/muskenmon@skenmon:/multiverse Translation-en_USve.canonical.com hardy-netbook-base 
bash: Ign: command not found
ltiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted skenmon/restricted Translation-en_USini.archive.canonical.com hardy-netbook-base 
bash: Ign: command not found
Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit httskenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-lease.gpg
bash: Hit: command not found
p://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
bash: Ign: command not found
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit hbash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
bash: Ign: command not found
ttp://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-miniskenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.costricted Translation-en_US
bash: Ign: command not found
.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.caskenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy Release
bash: Hit: command not found
nonical.com hardy-dell-mini/multiverse Packages
Hit http:skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updases Rele 
bash: Hit: command not found
//dell-mini.archive.canonical.com hardy-dell-mini/restricted Pack
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-security Release
bash: Hit: command not found
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main S
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
bash: Hit: command not found
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe S
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release  
bash: Hit: command not found
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multivers
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy/main Packages
bash: Hit: command not found
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/res
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy/universe Packages
bash: Hit: command not found
Fetched 198B in 4s (43B/s)
Reading package lists... Done
W: GPG erskenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy/mulackages P 
bash: Hit: command not found
ror: http://moblock-deb.sourceforge.net hardy Release: The following 
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
bash: Hit: command not found
W: You may want to run apt-get update to correct these problems
skenskenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy/main Sos
bash: Hit: command not found
mon@skenmon:~$ 

skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy/universe Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://moblock-deb.sourceforge.net hardy/main Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-security/universe
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-security/mu
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-security/restricted So
bash: Hit: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-netbook-base/
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-net
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Pa
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Pack
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe 
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Source
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
bash: Ign: command not found
skenmon@skenmon:~$ Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
bash: Ign: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Pack
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main S
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe S
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multivers
bash: Hit: command not found
skenmon@skenmon:~$ Hit http://dell-mini.archive.canonical.com hardy-dell-mini/res
bash: Hit: command not found
skenmon@skenmon:~$ Fetched 198B in 4s (43B/s)
bash: syntax error near unexpected token `('
skenmon@skenmon:~$ Reading package lists... Done
bash: Reading: command not found
skenmon@skenmon:~$ W: GPG error: http://moblock-deb.sourceforge.net hardy Release: The following 
bash: W:: command not found
skenmon@skenmon:~$ W: You may want to run apt-get update to correct these problems
bash: W:: command not found
skenmon@skenmon:~$ skenmon@skenmon:~$ 
bash: skenmon@skenmon:~$: command not found
skenmon@skenmon:~$ 
skenmon@skenmon:~$ 

```

as for:
```
sudo aptitude
```
Not too sure about your instructions, but a blue screen shows up.
The only options are:

--- Installed Packages
--- Not Installed Packages
--- Obsolete and Locally Created Packages
--- Virtual Packages
--- Tasks

---

### Post by jre on 2009-01-18
Don't know what happened in your last try. Somehow the output of the command was interpreted as commands itself. I've never seen that ....

```
W: GPG error: http://moblock-deb.sourceforge.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B
W: You may want to run apt-get update to correct these problems

```
You first need to get my gpg key as explained on moblock-deb.sourceforge.net. After that do the "apt-get update" or "aptitude update" - both commands do the same.

In aptitude just do what I told you, e.g. type ```
/gcc
```.
A search window will pop up on the "/". When you then type "gcc" the 5 lines that you posted will expand and show you all single packages.
Perhaps it is easier for you to use "synaptic" instead of aptitude. There should be plenty of documentation about that.

---

### Post by jre on 2009-01-18
Hmm, my answer is not shown, so again :-/

```
W: GPG error: [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B
W: You may want to run apt-get update to correct these problems
```
This is just a warning, not an error. (Either ignore it or) get my gpg key as described on moblock-deb.sourceforge.net. Afterwards do the "apt-get update" or "aptitude update".

I don't know what happened after your third command. Somehow the output of that command was interpreted as commands itself. This created a bunch of errors naturally. I've never seen that before ...

In aptitude just type e.g.
```
/gcc
```. This will open a search window (on "/"). On "gcc" the lines that you pasted will expand and show the single packets.
Alternatively you may use "synaptic" instead of "aptitude", if you like that app more.

---

### Post by shiningkenmonster on 2009-01-24
hey, I got a little lost with all the procedure(s). Even looking back to page one. I am not even sure if those commands are relevant with your current steps or not. Can you copy and paste which order to do all these things to install mobloquer.

---

### Post by jre on 2009-01-24
Instructions how to build and install moblock, mobloquer and moblock-control for an architecture, where no prebuilt packages are available. (You are on lpia, but not i386 or amd64)


**[SIZE="4"]A Prepare your system[/SIZE]**
**A.1. Remove old installations:**
```
sudo aptitude purge moblock moblock-control mobloquer

```

**A.2. Add the source repository to apt's sources list:**
Type in the terminal:
```
gksudo gedit /etc/apt/sources.list
```
Add this to the sources.list:
```
deb-src http://moblock-deb.sourceforge.net/debian hardy main
```

**A.3. Add the verification key (in the terminal):**
```
gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg --export --armor 9072870B | sudo apt-key add -
```

**A.4. Update your list of available packages and sources**
```
sudo aptitude update
```

**A.5. Make directory to work in.**
~/mypackages resolves automatically to /home/YOURNAME/mypackages
```
mkdir ~/mypackages
```

**[SIZE="4"]B. Install moblock[/SIZE]**

**B.1. Get to your working directory**
```
cd ~/mypackages
```

**B.2. Get the build dependencies**
```
sudo apt-get --assume-yes build-dep moblock
```
This step failed last time. Check your log for the files that were to be installed, and install them manually instead. Do this in synaptic or aptitude.

**B.3. Get the source**
```
apt-get source moblock
```

**B.4. Build the package**
```
cd moblock-0.9~rc2
dpkg-buildpackage -uc -us -rfakeroot
```

You should get this:
```
[...]
dpkg-deb: building package `moblock' in `../moblock_0.9~rc2-21_lpia.deb'.
 dpkg-genchanges  >../moblock_0.9~rc2-21_lpia.changes
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)

```

**B.5. Install moblock**
```
sudo dpkg -i ../moblock_0.9~rc2-*.deb
```


**[SIZE="4"]C. Install moblock-control[/SIZE]**

**C.1. Get to your working directory**
```
cd ~/mypackages
```

**C.2. Get the build dependencies**
```
sudo apt-get --assume-yes build-dep moblock-control
```
This step failed last time. Check your log for the files that were to be installed, and install them manually instead. Do this in synaptic or aptitude.

**C.3. Get the source**
```
apt-get source moblock-control
```

**C.4. Build the package**
```
cd moblock-control-1.2
dpkg-buildpackage -uc -us -rfakeroot
```

**C.5. Install moblock-control**
```
sudo dpkg -i ../moblock-control_1.2-*.deb
```

**[SIZE="4"]D. Install mobloquer[/SIZE]**

**D.1. Get to your working directory**
```
cd ~/mypackages
```

**D.2. Get the build dependencies**
```
sudo apt-get --assume-yes build-dep mobloquer
```
This step failed last time. Check your log for the files that were to be installed, and install them manually instead. Do this in synaptic or aptitude.

**D.3. Get the source**
```
apt-get source mobloquer
```

**D.4. Build the package**
```
cd mobloquer-0.5
dpkg-buildpackage -uc -us -rfakeroot
```

**D.5. Install mobloquer**
```
sudo dpkg -i ../mobloquer_0.5-*.deb
```

---

### Post by shiningkenmonster on 2009-01-26
hey I followed your steps to:

B.2. Get the build dependencies


```
sudo apt-get --assume-yes build-dep moblock
```

This step failed last time. Check your log for the files that were to be installed, and install them manually instead. Do this in synaptic or aptitude.

and I got this:
```
skenmon@skenmon:~$ sudo aptitude purge moblock moblock-control mobloquer
[sudo] password for skenmon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "moblock"
Couldn't find any package whose name or description matched "moblock-control"
Couldn't find any package whose name or description matched "mobloquer"
Couldn't find any package whose name or description matched "moblock"
Couldn't find any package whose name or description matched "moblock-control"
Couldn't find any package whose name or description matched "mobloquer"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
skenmon@skenmon:~$ gksudo gedit /etc/apt/sources.list
skenmon@skenmon:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv 9072870B
gpg: requesting key 9072870B from hkp server wwwkeys.eu.pgp.net
gpg: key 9072870B: public key "jre-phoenix (moblock-deb maintainer) <jre-phoenix@users.sourceforge.net>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
skenmon@skenmon:~$ gpg --export --armor 9072870B | sudo apt-key add -
OK
skenmon@skenmon:~$ sudo aptitude update
Get:1 http://moblock-deb.sourceforge.net hardy Release.gpg [197B]
Get:2 http://moblock-deb.sourceforge.net hardy Release [3024B]
Hit http://dell-mini.archive.canonical.com hardy Release.gpg
Ign http://dell-mini.archive.canonical.com hardy/main Translation-en_US
Get:3 http://moblock-deb.sourceforge.net hardy/main Sources [894B]
Ign http://dell-mini.archive.canonical.com hardy/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-updates Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-updates/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-updates/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-security Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-security/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-security/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release.gpg
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Translation-en_US
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Translation-en_US
Hit http://dell-mini.archive.canonical.com hardy Release
Hit http://dell-mini.archive.canonical.com hardy-updates Release
Hit http://dell-mini.archive.canonical.com hardy-security Release
Hit http://dell-mini.archive.canonical.com hardy-netbook-base Release
Hit http://dell-mini.archive.canonical.com hardy-dell-mini Release
Hit http://dell-mini.archive.canonical.com hardy/main Packages
Hit http://dell-mini.archive.canonical.com hardy/universe Packages
Hit http://dell-mini.archive.canonical.com hardy/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy/main Sources
Hit http://dell-mini.archive.canonical.com hardy/universe Sources
Hit http://dell-mini.archive.canonical.com hardy/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/main Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-updates/main Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-updates/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-security/main Packages
Hit http://dell-mini.archive.canonical.com hardy-security/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-security/main Sources
Hit http://dell-mini.archive.canonical.com hardy-security/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-security/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-security/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Ign http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/main Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-netbook-base/restricted Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Packages
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/main Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/universe Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/multiverse Sources
Hit http://dell-mini.archive.canonical.com hardy-dell-mini/restricted Sources
Fetched 4115B in 2s (1788B/s)
Reading package lists... Done
skenmon@skenmon:~$ mkdir ~/mypackages
skenmon@skenmon:~$ cd ~/mypackages
skenmon@skenmon:~/mypackages$ sudo apt-get --assume-yes build-dep moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  build-essential debhelper dpatch dpkg-dev g++ g++-4.2 gettext html2text
  intltool-debian iptables-dev libc6-dev libnetfilter-queue-dev
  libnetfilter-queue1 libnfnetlink-dev libnfnetlink0 libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch po-debconf
0 upgraded, 20 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.4MB of archives.
After this operation, 39.7MB of additional disk space will be used.
Get:1 http://dell-mini.archive.canonical.com hardy-dell-mini/main linux-libc-dev 2.6.24-19.41netbook11 [712kB]
Get:2 http://dell-mini.archive.canonical.com hardy/main libc6-dev 2.7-10ubuntu3 [2066kB]
Get:3 http://dell-mini.archive.canonical.com hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1173kB]
Get:4 http://dell-mini.archive.canonical.com hardy/main g++-4.2 4.2.3-2ubuntu7 [2635kB]
Get:5 http://dell-mini.archive.canonical.com hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1430B]
Get:6 http://dell-mini.archive.canonical.com hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:7 http://dell-mini.archive.canonical.com hardy/main patch 2.5.9-4 [98.5kB] 
Get:8 http://dell-mini.archive.canonical.com hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:9 http://dell-mini.archive.canonical.com hardy/main build-essential 11.3ubuntu1 [7064B]
Get:10 http://dell-mini.archive.canonical.com hardy/main html2text 1.3.2a-3build2 [89.1kB]
Get:11 http://dell-mini.archive.canonical.com hardy/main gettext 0.17-2ubuntu1 [1971kB]
Get:12 http://dell-mini.archive.canonical.com hardy/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:13 http://dell-mini.archive.canonical.com hardy/main po-debconf 1.0.10 [232kB]
Get:14 http://dell-mini.archive.canonical.com hardy/main debhelper 6.0.4ubuntu1 [516kB]
Get:15 http://dell-mini.archive.canonical.com hardy/main dpatch 2.0.28 [87.1kB]
Get:16 http://dell-mini.archive.canonical.com hardy/main iptables-dev 1.3.8.0debian1-1ubuntu2 [141kB]
Get:17 http://dell-mini.archive.canonical.com hardy/universe libnfnetlink0 0.0.30-2 [11.9kB]
Get:18 http://dell-mini.archive.canonical.com hardy/universe libnetfilter-queue1 0.0.13-1 [7048B]
Get:19 http://dell-mini.archive.canonical.com hardy/universe libnfnetlink-dev 0.0.30-2 [17.9kB]
Get:20 http://dell-mini.archive.canonical.com hardy/universe libnetfilter-queue-dev 0.0.13-1 [7602B]
Fetched 10.4MB in 27s (376kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 105422 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-19.41netbook11_lpia.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_lpia.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_lpia.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_lpia.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_lpia.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_lpia.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_lpia.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build2_lpia.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-2ubuntu1_lpia.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.10_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_6.0.4ubuntu1_all.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.28_all.deb) ...
Selecting previously deselected package iptables-dev.
Unpacking iptables-dev (from .../iptables-dev_1.3.8.0debian1-1ubuntu2_lpia.deb) ...
Selecting previously deselected package libnfnetlink0.
Unpacking libnfnetlink0 (from .../libnfnetlink0_0.0.30-2_lpia.deb) ...
Selecting previously deselected package libnetfilter-queue1.
Unpacking libnetfilter-queue1 (from .../libnetfilter-queue1_0.0.13-1_lpia.deb) ...
Selecting previously deselected package libnfnetlink-dev.
Unpacking libnfnetlink-dev (from .../libnfnetlink-dev_0.0.30-2_lpia.deb) ...
Selecting previously deselected package libnetfilter-queue-dev.
Unpacking libnetfilter-queue-dev (from .../libnetfilter-queue-dev_0.0.13-1_lpia.deb) ...
Setting up linux-libc-dev (2.6.24-19.41netbook11) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up html2text (1.3.2a-3build2) ...

Setting up gettext (0.17-2ubuntu1) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.10) ...

Setting up debhelper (6.0.4ubuntu1) ...
Setting up dpatch (2.0.28) ...
Setting up iptables-dev (1.3.8.0debian1-1ubuntu2) ...

Setting up libnfnetlink0 (0.0.30-2) ...

Setting up libnetfilter-queue1 (0.0.13-1) ...

Setting up libnfnetlink-dev (0.0.30-2) ...
Setting up libnetfilter-queue-dev (0.0.13-1) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
skenmon@skenmon:~/mypackages$ 

```

---

### Post by shiningkenmonster on 2009-01-26
```
skenmon@skenmon:~/mypackages$ apt-get source moblock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'moblock' packaging is maintained in the 'Svn' version control system at:
https://moblock-deb.svn.sourceforge.net/svnroot/moblock-deb/moblock/
Need to get 45.5kB of source archives.
Get:1 http://moblock-deb.sourceforge.net hardy/main moblock 0.9~rc2-21+hardy (dsc) [850B]
Get:2 http://moblock-deb.sourceforge.net hardy/main moblock 0.9~rc2-21+hardy (tar) [22.2kB]
Get:3 http://moblock-deb.sourceforge.net hardy/main moblock 0.9~rc2-21+hardy (diff) [22.4kB]
Fetched 45.5kB in 1s (25.8kB/s)
dpkg-source: extracting moblock in moblock-0.9~rc2
dpkg-source: unpacking moblock_0.9~rc2.orig.tar.gz
dpkg-source: applying ./moblock_0.9~rc2-21+hardy.diff.gz
skenmon@skenmon:~/mypackages$ cd moblock-0.9~rc2
skenmon@skenmon:~/mypackages/moblock-0.9~rc2$ dpkg-buildpackage -uc -us -rfakeroot
dpkg-buildpackage: error: fakeroot not found, either install the fakeroot
package, specify a command with the -r option, or run this as root
skenmon@skenmon:~/mypackages/moblock-0.9~rc2$ 

```

even using skenmon@skenmon:~$ 
still got the same results

---

### Post by jre on 2009-01-27
You're nearly there! The other packages were installed automatically this time, as it should be. You just need to install "fakeroot" manually:
```
sudo aptitude install fakeroot
```

Then go to the correct directory again:
```
cd ~/mypackages/moblock-0.9~rc2
```

And continue with B.4. Build the package
```
dpkg-buildpackage -uc -us -rfakeroot
```




BTW: I don't understand what you mean with
> even using skenmon@skenmon:~$
Never insert this as a command. You should be a normal user for the commands I've given you. And you have to be in the correct directory.

---

### Post by shiningkenmonster on 2009-01-28
Woohoo! It finally works! Its all installed. here is the proof, but it got cut off! :p

Thanks for the support. I couldn't of done it without you.

btw, Do I need to have the GUI mobloquer be open/on the desktop tray? while using bitorrent? or can i have it closed?  and one more thing, do I need to configure anything or update it regularly?

```
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.1.3-1ubuntu2_lpia.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.9.3-2_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.4-1_lpia.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-5ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a4.0-2ubuntu1_all.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a4.0.3-2_lpia.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1%3a1.1.9-1_lpia.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.3-2build1_lpia.deb) ...
Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_2.0.1-0ubuntu1_lpia.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.3.dfsg-7ubuntu1_lpia.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.3.5-1ubuntu4_lpia.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.5.0-2ubuntu3_lpia.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.12-2ubuntu5_lpia.deb) ...
Selecting previously deselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.1.3-1_lpia.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.0.2-1build1_lpia.deb) ...
Selecting previously deselected package libxmu-headers.
Unpacking libxmu-headers (from .../libxmu-headers_2%3a1.0.4-1_all.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.2.1-2_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_2%3a1.2.2-1_lpia.deb) ...
Selecting previously deselected package libxt-dev.
Unpacking libxt-dev (from .../libxt-dev_1%3a1.0.5-3_lpia.deb) ...
Selecting previously deselected package m4.
Unpacking m4 (from .../archives/m4_1.4.10-1_lpia.deb) ...
Selecting previously deselected package autoconf.
Unpacking autoconf (from .../autoconf_2.61-4_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20070725.1_all.deb) ...
Selecting previously deselected package automake1.7.
Unpacking automake1.7 (from .../automake1.7_1.7.9-9_all.deb) ...
Selecting previously deselected package fdupes.
Unpacking fdupes (from .../fdupes_1.40-4build1_lpia.deb) ...
Selecting previously deselected package intltool.
Unpacking intltool (from .../intltool_0.37.1-1ubuntu1_all.deb) ...
Selecting previously deselected package cdbs.
Unpacking cdbs (from .../cdbs_0.4.51ubuntu1_all.deb) ...
Selecting previously deselected package libglib2.0-dev.
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.16.4-0ubuntu3_lpia.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_7.0.3~rc2-1ubuntu3_all.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_7.0.3~rc2-1ubuntu3_all.deb) ...
Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_7.0.3~rc2-1ubuntu3_lpia.deb) ...
Selecting previously deselected package libglu1-xorg-dev.
Unpacking libglu1-xorg-dev (from .../libglu1-xorg-dev_1%3a7.3+10ubuntu10.2_all.deb) ...
Selecting previously deselected package libjpeg62-dev.
Unpacking libjpeg62-dev (from .../libjpeg62-dev_6b-14_lpia.deb) ...
Selecting previously deselected package libkadm55.
Unpacking libkadm55 (from .../libkadm55_1.6.dfsg.3~beta1-2ubuntu1_lpia.deb) ...
Selecting previously deselected package liblcms1-dev.
Unpacking liblcms1-dev (from .../liblcms1-dev_1.16-7ubuntu1_lpia.deb) ...
Selecting previously deselected package libmng-dev.
Unpacking libmng-dev (from .../libmng-dev_1.0.9-1_lpia.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.0.51a-3ubuntu5.1_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.51a-3ubuntu5.1_lpia.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.15~beta5-3_lpia.deb) ...
Selecting previously deselected package comerr-dev.
Unpacking comerr-dev (from .../comerr-dev_2.1-1.40.8-2ubuntu2_lpia.deb) ...
Selecting previously deselected package libkrb5-dev.
Unpacking libkrb5-dev (from .../libkrb5-dev_1.6.dfsg.3~beta1-2ubuntu1_lpia.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.3.3-0ubuntu0.8.04_lpia.deb) ...
Selecting previously deselected package libssl-dev.
Unpacking libssl-dev (from .../libssl-dev_0.9.8g-4ubuntu3.3_lpia.deb) ...
Selecting previously deselected package libpq-dev.
Unpacking libpq-dev (from .../libpq-dev_8.3.3-0ubuntu0.8.04_lpia.deb) ...
Selecting previously deselected package libaudio-dev.
Unpacking libaudio-dev (from .../libaudio-dev_1.9.1-1_lpia.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4.3.4-0ubuntu3_lpia.deb) ...
Selecting previously deselected package libqt4-qt3support.
Unpacking libqt4-qt3support (from .../libqt4-qt3support_4.3.4-0ubuntu3_lpia.deb) ...
Selecting previously deselected package libsqlite0-dev.
Unpacking libsqlite0-dev (from .../libsqlite0-dev_2.8.17-4build1_lpia.deb) ...
Selecting previously deselected package libxmu-dev.
Unpacking libxmu-dev (from .../libxmu-dev_2%3a1.0.4-1_lpia.deb) ...
Selecting previously deselected package libqt4-dev.
Unpacking libqt4-dev (from .../libqt4-dev_4.3.4-0ubuntu3_lpia.deb) ...
Setting up x11proto-core-dev (7.0.11-1) ...
Setting up libice-dev (2:1.0.4-1) ...
Setting up libsm-dev (2:1.0.3-1) ...
Setting up libxau-dev (1:1.0.3-2) ...
Setting up libpthread-stubs0 (0.1-2) ...
Setting up libpthread-stubs0-dev (0.1-2) ...
Setting up libxdmcp-dev (1:1.0.2-2) ...
Setting up libxcb1-dev (1.1-1ubuntu1) ...
Setting up libxcb-xlib0-dev (1.1-1ubuntu1) ...
Setting up x11proto-input-dev (1.4.2-1) ...
Setting up x11proto-kb-dev (1.0.3-2ubuntu1) ...
Setting up xtrans-dev (1.0.4-1) ...
Setting up libx11-dev (2:1.1.3-1ubuntu2) ...
Setting up x11proto-render-dev (2:0.9.3-2) ...
Setting up libxrender-dev (1:0.9.4-1) ...
Setting up x11proto-xext-dev (7.0.2-5ubuntu1) ...
Setting up x11proto-fixes-dev (1:4.0-2ubuntu1) ...
Setting up libxfixes-dev (1:4.0.3-2) ...
Setting up libxcursor-dev (1:1.1.9-1) ...
Setting up libxext-dev (2:1.0.3-2build1) ...
Setting up libexpat1-dev (2.0.1-0ubuntu1) ...

Setting up zlib1g-dev (1:1.2.3.3.dfsg-7ubuntu1) ...
Setting up libfreetype6-dev (2.3.5-1ubuntu4) ...

Setting up libfontconfig1-dev (2.5.0-2ubuntu3) ...

Setting up libxft-dev (2.1.12-2ubuntu5) ...
Setting up libxi-dev (2:1.1.3-1) ...
Setting up x11proto-xinerama-dev (1.1.2-4ubuntu1) ...
Setting up libxinerama-dev (2:1.0.2-1build1) ...
Setting up libxmu-headers (2:1.0.4-1) ...
Setting up x11proto-randr-dev (1.2.1-2) ...
Setting up libxrandr-dev (2:1.2.2-1) ...
Setting up libxt-dev (1:1.0.5-3) ...
Setting up m4 (1.4.10-1) ...

Setting up autoconf (2.61-4) ...

Setting up autotools-dev (20070725.1) ...
Setting up automake1.7 (1.7.9-9) ...

Setting up fdupes (1.40-4build1) ...
Setting up intltool (0.37.1-1ubuntu1) ...
Setting up cdbs (0.4.51ubuntu1) ...

Setting up libglib2.0-dev (2.16.4-0ubuntu3) ...
Setting up mesa-common-dev (7.0.3~rc2-1ubuntu3) ...
Setting up libgl1-mesa-dev (7.0.3~rc2-1ubuntu3) ...
Setting up libglu1-mesa-dev (7.0.3~rc2-1ubuntu3) ...
Setting up libglu1-xorg-dev (1:7.3+10ubuntu10.2) ...
Setting up libjpeg62-dev (6b-14) ...
Setting up libkadm55 (1.6.dfsg.3~beta1-2ubuntu1) ...

Setting up liblcms1-dev (1.16-7ubuntu1) ...
Setting up libmng-dev (1.0.9-1) ...
Setting up mysql-common (5.0.51a-3ubuntu5.1) ...
Setting up libmysqlclient15off (5.0.51a-3ubuntu5.1) ...

Setting up libpng12-dev (1.2.15~beta5-3) ...
Setting up comerr-dev (2.1-1.40.8-2ubuntu2) ...

Setting up libkrb5-dev (1.6.dfsg.3~beta1-2ubuntu1) ...
Setting up libpq5 (8.3.3-0ubuntu0.8.04) ...

Setting up libssl-dev (0.9.8g-4ubuntu3.3) ...
Setting up libpq-dev (8.3.3-0ubuntu0.8.04) ...
Setting up libaudio-dev (1.9.1-1) ...
Setting up libqt4-sql (4.3.4-0ubuntu3) ...

Setting up libqt4-qt3support (4.3.4-0ubuntu3) ...

Setting up libsqlite0-dev (2.8.17-4build1) ...
Setting up libxmu-dev (2:1.0.4-1) ...
Setting up libqt4-dev (4.3.4-0ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
skenmon@skenmon:~/mypackages$ apt-get source mobloquer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'mobloquer' packaging is maintained in the 'Svn' version control system at:
https://mobloquer.svn.sourceforge.net/svnroot/mobloquer/
Need to get 132kB of source archives.
Get:1 http://moblock-deb.sourceforge.net hardy/main mobloquer 0.5-2+hardy (dsc) [883B]
Get:2 http://moblock-deb.sourceforge.net hardy/main mobloquer 0.5-2+hardy (tar) [127kB]
Get:3 http://moblock-deb.sourceforge.net hardy/main mobloquer 0.5-2+hardy (diff) [4090B]
Fetched 132kB in 0s (207kB/s)   
dpkg-source: extracting mobloquer in mobloquer-0.5
dpkg-source: unpacking mobloquer_0.5.orig.tar.gz
dpkg-source: applying ./mobloquer_0.5-2+hardy.diff.gz
skenmon@skenmon:~/mypackages$ cd mobloquer-0.5
skenmon@skenmon:~/mypackages/mobloquer-0.5$ dpkg-buildpackage -uc -us -rfakeroot
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package mobloquer
dpkg-buildpackage: source version 0.5-2+hardy
dpkg-buildpackage: source changed by jre <jre-phoenix@users.sourceforge.net>
dpkg-buildpackage: host architecture lpia
 fakeroot debian/rules clean
test -x debian/rules
test "`id -u`" = 0
/usr/bin/make -C . -k clean
make[1]: Entering directory `/home/skenmon/mypackages/mobloquer-0.5'
make[1]: *** No rule to make target `clean'.
make[1]: Leaving directory `/home/skenmon/mypackages/mobloquer-0.5'
make: [makefile-clean] Error 2 (ignored)
rm -f debian/stamp-makefile-build
rm -f ./Makefile ./.qmake.internal.cache
dh_clean 
/usr/bin/make -f debian/rules reverse-config
make[1]: Entering directory `/home/skenmon/mypackages/mobloquer-0.5'
make[1]: Nothing to be done for `reverse-config'.
make[1]: Leaving directory `/home/skenmon/mypackages/mobloquer-0.5'
dpatch deapply-all
10_mobloquer.pro not applied to ./ .
rm -rf debian/patched
rm -f debian/stamp-patched
 dpkg-source -b mobloquer-0.5
dpkg-source: building mobloquer using existing mobloquer_0.5.orig.tar.gz
dpkg-source: building mobloquer in mobloquer_0.5-2+hardy.diff.gz
dpkg-source: warning: executable mode 0755 of 'debian/patches/10_mobloquer.pro.dpatch' will not be represented in diff
dpkg-source: building mobloquer in mobloquer_0.5-2+hardy.dsc
 debian/rules build
test -x debian/rules
mkdir -p "."
/usr/bin/make -f debian/rules reverse-config
make[1]: Entering directory `/home/skenmon/mypackages/mobloquer-0.5'
make[1]: Nothing to be done for `reverse-config'.
make[1]: Leaving directory `/home/skenmon/mypackages/mobloquer-0.5'
dpatch apply-all
applying patch 10_mobloquer.pro to ./ ... ok.
/usr/bin/make -f debian/rules update-config
make[1]: Entering directory `/home/skenmon/mypackages/mobloquer-0.5'
make[1]: Nothing to be done for `update-config'.
make[1]: Leaving directory `/home/skenmon/mypackages/mobloquer-0.5'
touch debian/stamp-patched
cd . && qmake-qt4   'QMAKE_CC = cc' 'QMAKE_CXX = g++' 'QMAKE_CFLAGS_RELEASE =  -g -O2 -g -Wall -O2' 'QMAKE_CXXFLAGS_RELEASE =  -g -O2 -g -Wall -O2'
/usr/bin/make -C . all
make[1]: Entering directory `/home/skenmon/mypackages/mobloquer-0.5'
/usr/bin/uic-qt4 ui/mobloquer.ui -o ui/ui_mobloquer.h
/usr/bin/uic-qt4 ui/settings.ui -o ui/ui_settings.h
/usr/bin/uic-qt4 ui/whois.ui -o ui/ui_whois.h
/usr/bin/uic-qt4 ui/list_add.ui -o ui/ui_list_add.h
/usr/bin/uic-qt4 ui/status_dialog.ui -o ui/ui_status_dialog.h
/usr/bin/uic-qt4 ui/ip_whitelist.ui -o ui/ui_ip_whitelist.h
/usr/bin/uic-qt4 ui/ip_remove.ui -o ui/ui_ip_remove.h
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/file_transactions.o src/file_transactions.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/main.o src/main.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moblock_info.o src/moblock_info.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moblock_lists.o src/moblock_lists.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moblock_log.o src/moblock_log.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moblock_settings.o src/moblock_settings.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/mobloquer.o src/mobloquer.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/super_user.o src/super_user.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moblock_control.o src/moblock_control.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/settings.o src/settings.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/whois.o src/whois.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/list_add.o src/list_add.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/settings_manager.o src/settings_manager.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/status_dialog.o src/status_dialog.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/ip_whitelist.o src/ip_whitelist.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/ip_remove.o src/ip_remove.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/proc_thread.o src/proc_thread.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/moblock_control.h -o build/moc/moc_moblock_control.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_moblock_control.o build/moc/moc_moblock_control.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/moblock_info.h -o build/moc/moc_moblock_info.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_moblock_info.o build/moc/moc_moblock_info.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/moblock_log.h -o build/moc/moc_moblock_log.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_moblock_log.o build/moc/moc_moblock_log.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/mobloquer.h -o build/moc/moc_mobloquer.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_mobloquer.o build/moc/moc_mobloquer.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/super_user.h -o build/moc/moc_super_user.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_super_user.o build/moc/moc_super_user.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/settings.h -o build/moc/moc_settings.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_settings.o build/moc/moc_settings.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/whois.h -o build/moc/moc_whois.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_whois.o build/moc/moc_whois.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/list_add.h -o build/moc/moc_list_add.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_list_add.o build/moc/moc_list_add.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/settings_manager.h -o build/moc/moc_settings_manager.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_settings_manager.o build/moc/moc_settings_manager.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/status_dialog.h -o build/moc/moc_status_dialog.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_status_dialog.o build/moc/moc_status_dialog.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/ip_whitelist.h -o build/moc/moc_ip_whitelist.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_ip_whitelist.o build/moc/moc_ip_whitelist.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/ip_remove.h -o build/moc/moc_ip_remove.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_ip_remove.o build/moc/moc_ip_remove.cpp
/usr/bin/moc-qt4 -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui src/proc_thread.h -o build/moc/moc_proc_thread.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/moc_proc_thread.o build/moc/moc_proc_thread.cpp
/usr/bin/rcc -name images images/images.qrc -o qrc_images.cpp
g++ -c -pipe -fpermissive -g -Wall -W -D_REENTRANT -DQT_SHARED -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Ibuild/moc -Iui -o build/obj/qrc_images.o qrc_images.cpp
g++ -Wl,--no-undefined -o mobloquer build/obj/file_transactions.o build/obj/main.o build/obj/moblock_info.o build/obj/moblock_lists.o build/obj/moblock_log.o build/obj/moblock_settings.o build/obj/mobloquer.o build/obj/super_user.o build/obj/moblock_control.o build/obj/settings.o build/obj/whois.o build/obj/list_add.o build/obj/settings_manager.o build/obj/status_dialog.o build/obj/ip_whitelist.o build/obj/ip_remove.o build/obj/proc_thread.o build/obj/moc_moblock_control.o build/obj/moc_moblock_info.o build/obj/moc_moblock_log.o build/obj/moc_mobloquer.o build/obj/moc_super_user.o build/obj/moc_settings.o build/obj/moc_whois.o build/obj/moc_list_add.o build/obj/moc_settings_manager.o build/obj/moc_status_dialog.o build/obj/moc_ip_whitelist.o build/obj/moc_ip_remove.o build/obj/moc_proc_thread.o build/obj/qrc_images.o    -L/usr/lib -lQtGui -lQtCore -lpthread
make[1]: Leaving directory `/home/skenmon/mypackages/mobloquer-0.5'
touch debian/stamp-makefile-build
DEB_MAKE_CHECK_TARGET unset, not running checks
 fakeroot debian/rules binary
test -x debian/rules
test "`id -u`" = 0
dh_clean -k 
dh_installdirs -A 
mkdir -p "."
DEB_MAKE_CHECK_TARGET unset, not running checks
/usr/bin/make -C . install DESTDIR=/home/skenmon/mypackages/mobloquer-0.5/debian/tmp/
make[1]: Entering directory `/home/skenmon/mypackages/mobloquer-0.5'
install -m 755 -p /home/skenmon/mypackages/mobloquer-0.5/images/mobloquer.png /home/skenmon/mypackages/mobloquer-0.5//home/skenmon/mypackages/mobloquer-0.5/debian/tmp//usr/share/pixmaps/
install -m 644 -p /home/skenmon/mypackages/mobloquer-0.5/other/Mobloquer.desktop /home/skenmon/mypackages/mobloquer-0.5//home/skenmon/mypackages/mobloquer-0.5/debian/tmp//usr/share/applications/
install -m 755 -p "mobloquer" "/home/skenmon/mypackages/mobloquer-0.5//home/skenmon/mypackages/mobloquer-0.5/debian/tmp//usr/bin/mobloquer"
make[1]: Leaving directory `/home/skenmon/mypackages/mobloquer-0.5'
dh_installdirs -pmobloquer 
dh_installdocs -pmobloquer ./README  
dh_installexamples -pmobloquer 
dh_installman -pmobloquer  
dh_installinfo -pmobloquer  
dh_installmenu -pmobloquer 
dh_installcron -pmobloquer 
dh_installinit -pmobloquer   
dh_installdebconf -pmobloquer 
dh_installemacsen -pmobloquer   
dh_installcatalogs -pmobloquer 
dh_installpam -pmobloquer 
dh_installlogrotate -pmobloquer 
dh_installlogcheck -pmobloquer 
dh_installmime -pmobloquer 
dh_installchangelogs -pmobloquer   
dh_installudev -pmobloquer 
dh_install -pmobloquer  
dh_link -pmobloquer  
dh_strip -pmobloquer  
dh_compress -pmobloquer  
dh_fixperms -pmobloquer  
dh_makeshlibs -pmobloquer  
dh_installdeb -pmobloquer 
dh_perl -pmobloquer 
dh_shlibdeps -pmobloquer    
dpkg-shlibdeps: warning: debian/mobloquer/usr/bin/mobloquer shouldn't be linked with libpthread.so.0 (it uses none of its symbols).
dh_gencontrol -pmobloquer 
# symlink identical documentation to depending packages
[ -n "$CDBS_NO_DOC_SYMLINKING" ] || \
	[ -h debian/mobloquer/usr/share/doc ] || \
	[ ! -d debian/mobloquer/usr/share/doc ] || \
	for dep in `perl -ne 'if (/^(Pre-)?Depends:/) {s/^\w+://; foreach (split /,/) { split; print($_[0], "\n"); } }' debian/mobloquer/DEBIAN/control`; do \
	    if [ -d debian/$dep/usr/share/doc ]; then \
                echo "Searching for duplicated docs in dependency $dep..."; \
                rootdir=`pwd`; \
                (cd debian/mobloquer/usr/share/doc/mobloquer; find -type f ! -name copyright | while read f; do \
                    thisfile="$rootdir/debian/mobloquer/usr/share/doc/mobloquer/$f"; \
                    depfile="$rootdir/debian/$dep/usr/share/doc/$dep/$f"; \
                    if [ -f $depfile -o -L $depfile ] && zcmp $thisfile $depfile >/dev/null; then \
                        echo "  symlinking $f in mobloquer to file in $dep"; \
                        rm $thisfile; ln -s /usr/share/doc/$dep/$f $thisfile; \
                    fi; \
                done ); \
            fi; \
	done
# symlink identical Gnome help files within packages
if [ -z "$CDBS_NO_GNOME_HELP_SYMLINKING" ] && [ -d debian/mobloquer/usr/share/gnome/help ]; then \
            cd debian/mobloquer && LC_ALL=C fdupes -r1nq usr/share/gnome/help | while read s; do \
                set -- $(echo $s | tr ' ' '\n' | sort); \
                f=$1; shift; \
                for d; do \
                    echo "symlinking duplicate Gnome help file $d to $f"; \
                    rm $d; ln -s /$f $d; \
                done; \
            done; \
	fi
dh_link -p mobloquer
dh_md5sums -pmobloquer 
dh_builddeb -pmobloquer 
dpkg-deb: building package `mobloquer' in `../mobloquer_0.5-2+hardy_lpia.deb'.
 dpkg-genchanges  >../mobloquer_0.5-2+hardy_lpia.changes
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
skenmon@skenmon:~/mypackages/mobloquer-0.5$ sudo dpkg -i ../mobloquer_0.5-*.deb
[sudo] password for skenmon: 
Selecting previously deselected package mobloquer.
(Reading database ... 114726 files and directories currently installed.)
Unpacking mobloquer (from .../mobloquer_0.5-2+hardy_lpia.deb) ...
Setting up mobloquer (0.5-2+hardy) ...
skenmon@skenmon:~/mypackages/mobloquer-0.5$ 
```

---

### Post by jre on 2009-01-29
Hey, that were just 6 weeks ;-) I'm glad you finally managed it and didn't give up.

mobloquer is just a graphical interface. You can use it, put it to the tray, close it, whatever you do: the moblock daemon will keep running. Of course you can use mobloquer to manually stop moblock.

(Unless you have configured it otherwise) moblock-control starts the moblock daemon automatically at system boot and updates the blocklists daily. So, no, no further actions are needed by you - you get the fully working moblock automatically.
Test it with "moblock-control test" and "moblock-control status".

If its working too good you may have to allow (whitelist) certain traffic. But this is a whole new toppic and discussed here, on the [Moblock wiki]("https://help.ubuntu.com/community/MoBlock"), moblock-deb.sourceforge.net and the documentation.

---

### Post by jre on 2009-04-30
Just an update:

Beginning with Ubuntu Jaunty I'm using the ppa at launchpad. This includes packages for lpia.

So you can go with this apt sources.list entry now:
```
deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) jaunty main
```

---

### Post by shiningkenmonster on 2009-05-20
oh, thanks. I was just curious. the method you gave me that got the install work. What is that called? I never got the term down.

---

### Post by jre on 2009-05-20
The old? Something like "building your own packages from a Debian source package".

---

### Post by shiningkenmonster on 2009-09-03
hey, i have been using the Ubuntu 9.04 netbook remix from Canonical.
I opened this:
```
gksudo gedit /etc/apt/sources.list
```

and added source packages
```

deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu jaunty main
deb http://archive.ubuntu.com/ubuntu jaunty main universe

```
and saved it.

I got the GPG key with this:
```
gpg --keyserver keyserver.ubuntu.com --recv 9C0042C8
gpg --export --armor 9C0042C8 | sudo apt-key add -

```

did an update
```
sudo aptitude update

```

did this command:
```
sudo aptitude install moblock blockcontrol mobloquer

```

everything was installing, but than i got into the config blockcontrol part. 


the terminal turns into a blue screen with this input:
```

Package configuration
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring blockcontrol &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474; Configuration variable: WHITE_TCP_OUT                                                                                &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Whitelist ports by port number or with the associated service name. Port ranges are specified in the format          &#9474; 
  &#9474; "port:port". Up to 15 ports can be specified. A port range (port:port) counts as two ports.                          &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Common ports:                                                                                                        &#9474; 
  &#9474;   80 - http                                                                                                          &#9474; 
  &#9474;  443 - https                                                                                                         &#9474; 
  &#9474;   22 - ssh                                                                                                           &#9474; 
  &#9474;  993 - SSL IMAP                                                                                                      &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Seperate multiple entries with whitespace (" "). Do not use surrounding "quotes". Be careful: senseless values are   &#9474; 
  &#9474; also accepted.                                                                                                       &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Whitelist outgoing TCP ports:                                                                                        &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; http https__________________________________________________________________________________________________________ &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474;                                  <Ok>                                      <Cancel>                                  &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                                                                           





```

```
Package configuration







  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring blockcontrol &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474; Configuration variable: WHITE_UDP_OUT                                                                                &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Whitelist ports by port number or with the associated service name. Port ranges are specified in the format          &#9474; 
  &#9474; "port:port". Up to 15 ports can be specified. A port range (port:port) counts as two ports.                          &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Seperate multiple entries with whitespace (" "). Do not use surrounding "quotes". Be careful: senseless values are   &#9474; 
  &#9474; also accepted.                                                                                                       &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Whitelist outgoing UDP ports:                                                                                        &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; ____________________________________________________________________________________________________________________ &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474;                                  <Ok>                                      <Cancel>                                  &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                                                                           


```

```
Package configuration







  &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring blockcontrol &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
  &#9474; Configuration variable: WHITE_TCP_FORWARD                                                                            &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Whitelist ports by port number or with the associated service name. Port ranges are specified in the format          &#9474; 
  &#9474; "port:port". Up to 15 ports can be specified. A port range (port:port) counts as two ports.                          &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Seperate multiple entries with whitespace (" "). Do not use surrounding "quotes". Be careful: senseless values are   &#9474; 
  &#9474; also accepted.                                                                                                       &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; Whitelist forwarded TCP ports:                                                                                       &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474; ____________________________________________________________________________________________________________________ &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9474;                                  <Ok>                                      <Cancel>                                  &#9474; 
  &#9474;                                                                                                                      &#9474; 
  &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                        
```

I did TAB and enter OK a couple of times. and Cancel. I have to put something in the input so it would work. There is no other way to get around it.

What do i put in the input for those screens?

---

### Post by jre on 2009-09-05
You don´t have to insert anything. Just leave these questions blank, unless you really want to add something, and then press **ok**. Don´t press **cancel** if you want to finish the installation!

Note that there are 6 nearly identical questions. And if you are asked even low-priority questions there are 31 questions :-) !

You can change debconf to use a nice graphical interface instead of the text console one. Simply type
```
sudo dpkg-reconfigure debconf
```
and choose for Interface to use: **Gnome**
You may also raise the priority for questions to be asked to at least **medium**.

---

