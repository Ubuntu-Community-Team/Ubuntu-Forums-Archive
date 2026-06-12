---
title: "Help me install Cinelerra"
date: 2009-06-28
forum: Ubuntu Studio
---

### Post by Vostrocity on 2009-06-28
I just spent half an hour trying to figure out how to install Cinelerra and I'm still clueless. The instructions are [right here]("http://cinelerra.org/getting_cinelerra.php#jaunty") but I don't understand it at all. If they just gave me a link to a deb or tar then it would've been easy.

---

### Post by Grishka on 2009-06-29
> **Vostrocity said:**
> I just spent half an hour trying to figure out how to install Cinelerra and I'm still clueless. The instructions are [right here]("http://cinelerra.org/getting_cinelerra.php#jaunty") but I don't understand it at all. If they just gave me a link to a deb or tar then it would've been easy.

install [this](http://akirad.cinelerra.org/pool/addakirad.deb), then click [here](apt://cinelerracv). :)

---

### Post by Vostrocity on 2009-06-29
Awesome! Easiest thing ever. :guitar:

---

### Post by projectbronco on 2009-09-22
> **Grishka said:**
> install [this](http://akirad.cinelerra.org/pool/addakirad.deb), then click [here](apt://cinelerracv). :)


Wow, thanks. I was having the same problem and this really helped!

---

### Post by Gliderfm on 2009-10-06
Thanx so much. I'm so new to linux so far all I've done is boot it up and read.

---

### Post by a2z on 2009-10-08
> **Grishka said:**
> install [this](http://akirad.cinelerra.org/pool/addakirad.deb), then click [here](apt://cinelerracv). :)

I did this. But I can't find it! Neither can "search>filesystem"....
The package manager says it is installed though.
Where could it be hiding?

Thanks

a2z


Ubuntu Jaunty 
ASUS P5N-D
intel Core 2 quad Q6700
Corsair 4G RAM
Maxtor 40G

---

### Post by modorf on 2009-10-13
```

wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add -
sudo echo 'deb http://repository.akirad.net akirad-jaunty main' >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install  cinelerracv-smp

```

---

### Post by corncob on 2009-10-14
> **modorf said:**
> ```

wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add -
sudo echo 'deb http://repository.akirad.net akirad-jaunty main' >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install  cinelerracv-smp

```

It worked!  Left me with a question though.  I have 2 Cinelerra's listed in my applications -- with and without xcb.  What is xcb?

---

### Post by modorf on 2009-10-15
> **corncob said:**
> It worked!  Left me with a question though.  I have 2 Cinelerra's listed in my applications -- with and without xcb.  What is xcb?

I think this is what XCB is:
[http://en.wikipedia.org/wiki/XCB]("http://en.wikipedia.org/wiki/XCB")

In computing, XCB (X C Binding) is a C language binding for the X Window System. It is implemented as free software and aims to replace Xlib. The project was started in 2001 by Bart Massey.

Xlib/XCB provides application binary interface compatibility with both Xlib and XCB, providing an incremental porting path. Xlib/XCB uses the protocol layer of Xlib, but replaces the Xlib transport layer with XCB, and provides access to the underlying XCB connection for direct use of XCB. Most distributions nowadays use Xlib/XCB for their libX11[citation needed], because by opening a single connection to the X server this allows to mix usage of XCB and Xlib in an application and the libraries it uses[2][3].

---

### Post by shantiq on 2010-05-28
[B][COLOR="Blue"]well i too had problems with the site's instructions using addakirad


and then somewhere else i saw this

the very simple

```
sudo apt-get install cinelerra
```

the obvious is sometimes elusive but hey worked first time[/COLOR][/B]

---

### Post by drkitty on 2010-06-24
the apt-get install cinelerra isn't working for me (Ubuntu 9.10). 

cinelerra: Depends: liblame0 (>= 3.97) but it is not installable
           Depends: libmjpegtools0c2a (>= 1:1.8.0) but it is not installable
           Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
           Depends: libquicktimehv (= 1:2.1.0-2svn20082807ubuntuubuntu1) but it is not going to be installed
           Depends: libraw1394-8 but it is not installable
E: Broken packages

---

### Post by Fidelio on 2010-07-19
> **drkitty said:**
> the apt-get install cinelerra isn't working for me (Ubuntu 9.10). 

cinelerra: Depends: liblame0 (>= 3.97) but it is not installable
           Depends: libmjpegtools0c2a (>= 1:1.8.0) but it is not installable
           Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
           Depends: libquicktimehv (= 1:2.1.0-2svn20082807ubuntuubuntu1) but it is not going to be installed
           Depends: libraw1394-8 but it is not installable
E: Broken packages

I get this error with 10.04 too. Can anyone help?

---

### Post by spaceshipguy on 2010-08-31
I've been trying to install Cinelerra for over an hour.

Giving up... NOW!

I switched to Ubuntu to avoid having to mess about for hours when I wanted to install something. Grrr.

---

### Post by MrVas on 2010-11-12
I can totally see why people would pull their hair out after reading the [install instructions for Ubuntu from Cinelerra site]("http://cinelerra.org/getting_cinelerra.php"):

What worked for me (Ubuntu 10.04 64-bit) was the following:

```
wget -q http://akirad.cinelerra.org/pool/addakirad.deb && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
```
Followed by:
```
sudo apt-get install cinelerra-xt
```You should leave out "-xt" if your CPU doesn't support [Supplemental Streaming SIMD Extensions 3 (SSSE3)]("http://en.wikipedia.org/wiki/SSSE3") (AMD for example). To find out, check /proc/cpuinfo for SSSE3:
```
cat /proc/cpuinfo | grep "ssse3"
```
In the output you should see a ssse3 flag. If not, your CPU doesn't support SSSE3.

Vas

---

### Post by dancomic on 2010-12-23
That's what I did to install cinelerra.

I opened software sources from system --> administration --> software sources

Then I went to "other software" tab and I clicked "add"
there I pasted the ppa address given on the cinelerra website. (Here [https://launchpad.net/~cinelerra-ppa/+archive/ppa](https://launchpad.net/~cinelerra-ppa/+archive/ppa))

I selected my ubuntu version (maverick) and I copied and pasted the sources in the add source window

```
deb http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu maverick main 
deb-src http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu maverick main 
```

[I]Note:
Here there's instructions about how to do that
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)[/I]

Then I closed the "software sources" window and I opened "synaptic package manager"

System --> Administration --> Synaptic Package Manager

I searched for cinellera, it appeared among other software, I just marked "cinellerra" for installation.

Click on "Apply" and the installation began.

When it finished I got cinellera in Applications --> sound and video

Hope this helps, there's a lot of different ways to do this, It is possible to do that on the command line too, or editing a text file that has all the info about repositories, I don't remember exactly the name, I'm a newbie too...
:-)

---

### Post by olligobber on 2011-01-14
> **Grishka said:**
> install [this](http://akirad.cinelerra.org/pool/addakirad.deb), then click [here](apt://cinelerracv). :)

I tried the first link to install and got this:
> Oops! Google Chrome could not connect to akirad.cinelerra.org

Anyone got a solution? Another location for this deb file?

---

### Post by beccatoria on 2011-01-20
Yeah, the akirad repository appears to be offline right now, but there's a new ppa available - 
 
[https://launchpad.net/~cinelerra-ppa/+archive/ppa](https://launchpad.net/~cinelerra-ppa/+archive/ppa)
 
which hosts Cinelerra CV 2.1.5 - the version that was released in November 2010.  It's effectively the same as 2.1 but with better support for a number of media types and a bunch of bugfixes, etc.  
 
Add **ppa:cinelerra-ppa/ppa **to your sources in synaptic, reload, and it should show up in the software centre if you search for it.  
 
I'm quite excited by the activity here - especially if it means potentially getting Cinelerra HV in the future since I've never had enough code-fu to compile that from source, but I dream of one day being able to make use of nested sequences...

---

### Post by beccatoria on 2011-01-20
apologies - computer glitch led to triple post.

---

### Post by beccatoria on 2011-01-20
apologies - computer glitch led to triple post.

---

### Post by mikeyrobertson on 2011-05-16
Ok, so i know this is a really old topic. But I had a little bit of trouble setting this up and figured I'd give it a try explaining it.
I dont ever use Linux, and was able to figure it out within a hour or so.

First add the "signing key": do this by opening your terminal and typing 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 72D340A3 
```
(replace 72D340A3 with whatever your key is).

Then Add cinellera to software sources:
in terminal type 
```
sudo software-properties-gtk 
```
(this starts software sorces)

Then in the other software tab, add the ppa source. in my case it was: deb [http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu](http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu) natty main (natty main should be replaced with whatever ubuntu version your using, in my case it was natty, which is version 10.04)

Next, exit software sources, it will ask you if you want to reload your stuff, click on reload.

then, just open up synaptic package manager. Once its open click on reload. then search for cinelerra, if its not your top hit, exit synaptic and reopen. Once you see it, just check it and click apply.

DONE, now just look for it in your applications

---

### Post by jejeman on 2011-05-16
For launchpad ppas you dont need to separetly add key and sources, just type
```
sudo apt-add-repository ppa:cinelerra-ppa/ppa
```
and you will automaticly add key, and sources.

---

### Post by arisepeter on 2011-10-14
I have wasted hours in searching installation instructions for  Cinelerra. I have also downloaded the latest version from Cinelerra  website, but that too failed to work.Also  the instructions in most of  the website found not suitable for my Ubutu version.Atlast  the  following instruction in a website found working for my Ubuntu 10.04  Lucid. They claim it will work for the following also.
Ubuntu Maverick 10.10 , Lucid 10.04, Karmic 9.10:
Here are the instruction.
Open a terminal by typing trl+ Alt+ T then paste the following commends one by one. Wait for each instruction to execute.
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra
for details see the website:
[http://www.g-raffa.eu/Cinelerra/HOWTO/installation.html](http://www.g-raffa.eu/Cinelerra/HOWTO/installation.html)

If that dosent work try adding ppa by issuing the following command in a command line by pressing Crrl+Alt+T
sudo add-apt-repository ppa:gwibber-daily/ppa
it will fetch the ppa, then issue the command
sudo apt-get update
 now try the following commands
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra

---

### Post by jejeman on 2011-10-14
> **arisepeter said:**
> Atlast  the  following instruction in a website found working for my Ubuntu 10.04  Lucid.
Which version do you use?

---

### Post by marer13 on 2011-10-19
The first link doesn't work....

---

### Post by marer13 on 2011-10-19
It doesn't work on my Kubuntu.....

Here's the output I'm getting:

> marer13@marer13-Studio:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cinelerra

What shall I do?

---

### Post by jejeman on 2011-10-19
Which version do you use?

---

### Post by marer13 on 2011-10-19
I have just updated to the latest version

---

### Post by jejeman on 2011-10-19
The oneiric version failed to build in PPA.
You can try to install Natty packages.

---

### Post by marer13 on 2011-10-19
How?

---

### Post by jejeman on 2011-10-19
I've tried my self, and ended up with broken package system. Well, maybe I wasn't careful, but if you don't have experience, I would not recommend.

---

### Post by timsdeepsky on 2011-10-19
This is the first time Cinelerra has failed from the PPA for me....Seems the package for 11.10 has some issues still....[https://launchpad.net/~cinelerra-ppa/+archive/ppa/+packages]("https://launchpad.net/~cinelerra-ppa/+archive/ppa/+packages")

---

### Post by timsdeepsky on 2011-11-08
This appears to be fixed now....

---

### Post by timsdeepsky on 2011-11-10
Appears to work in 11.10 (32 bit)...Seems 64 bit install of Cinelerra in 11.10 is still a problem for now....

---

### Post by mjhouska on 2011-11-12
> **modorf said:**
> I think this is what XCB is:
[http://en.wikipedia.org/wiki/XCB](http://en.wikipedia.org/wiki/XCB)

In computing, XCB (X C Binding) is a C language binding for the X Window System. It is implemented as free software and aims to replace Xlib. The project was started in 2001 by Bart Massey.

Xlib/XCB provides application binary interface compatibility with both Xlib and XCB, providing an incremental porting path. Xlib/XCB uses the protocol layer of Xlib, but replaces the Xlib transport layer with XCB, and provides access to the underlying XCB connection for direct use of XCB. Most distributions nowadays use Xlib/XCB for their libX11[citation needed], because by opening a single connection to the X server this allows to mix usage of XCB and Xlib in an application and the libraries it uses[2][3].

thanks for trying to explain.:popcorn:

---

### Post by NoDeity on 2012-03-29
> **arisepeter said:**
> Open a terminal by typing trl+ Alt+ T then paste the following commends one by one. Wait for each instruction to execute.
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra
Thanks.  This worked for me and ended my frustration.  :-)

---

### Post by NoDeity on 2012-03-29
> **arisepeter said:**
> Open a terminal by typing trl+ Alt+ T then paste the following commends one by one. Wait for each instruction to execute.
sudo add-apt-repository ppa:cinelerra-ppa/ppa
sudo apt-get update
sudo apt-get install cinelerra
Thanks.  This worked for me and ended my frustration.  :-)

---

### Post by wildmanne39 on 2013-03-08
Old thread closed!

---

