---
title: "When running scripts in terminal is it possible to get virus/spyware?"
date: 2011-04-13
forum: Security
---

### Post by xic816 on 2011-04-13
Hi, I just got this USB dongle with TV capabilities but it wasent supported by linux, 
when looking at the review/questions about the item there was a big debate about how to make it work on linux. One of the methods was to run this script;

DVB with chip AF9015 and tuner TDA18218:

on Kubuntu 10.4:

sudo aptitude install mercurial linux-headers-$(uname -r) build-essential
hg clone -r 0f41fd7df85d [http://linuxtv.org/hg/~anttip/af9015/](http://linuxtv.org/hg/~anttip/af9015/)
wget [http://jusst.de/manu/fw/AFA/dvb-usb-af9015.fw_a-link](http://jusst.de/manu/fw/AFA/dvb-usb-af9015.fw_a-link)
sudo mv dvb-usb-af9015.fw_a-link /lib/firmware/dvb-usb-af9015.fw
cd af9015
wget [http://media.ubuntuusers.de/forum/attachments/2466878/af9015.patch](http://media.ubuntuusers.de/forum/attachments/2466878/af9015.patch)
patch -p1 <af9015.patch
make
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
make
sudo make install
sudo reboot


Then my question appears! Is it generally safe to run these scripts or can they include different types of virus/spyware? 

ANother Q; It there anyway of running scripts in terminal in reverse? (remove the previously scrips)

Thanks

R

---

### Post by Spyderkid on 2011-04-13
you can't get spyware on linux and there are very few viruses.

just go for it and you can remove it with synaptic if you need to.

---

### Post by Frogs Hair on 2011-04-13
With the use of scripts or packages from untrusted sources there is always the possibility of the addition of something harmful . that is why it is suggested to use supported packages. I use some PPA applications and have not had any problems . I have not used scripts from outside sources simply because I have not needed to . I find Ubuntu supplies me with what I need . The software center now has 3rd party repositories and it is up to the user to enable them.

---

### Post by SeijiSensei on 2011-04-13
It's certainly possible to so all sorts of bad things to your computer running scripts that aren't well-vetted if you don't know what they are doing.  However that's not the case here:

```

sudo aptitude install mercurial linux-headers-$(uname -r) build-essential
hg clone -r 0f41fd7df85d [http://linuxtv.org/hg/~anttip/af9015/](http://linuxtv.org/hg/~anttip/af9015/)
wget [http://jusst.de/manu/fw/AFA/dvb-usb-af9015.fw_a-link](http://jusst.de/manu/fw/AFA/dvb-usb-af9015.fw_a-link)
sudo mv dvb-usb-af9015.fw_a-link /lib/firmware/dvb-usb-af9015.fw
cd af9015
wget [http://media.ubuntuusers.de/forum/attachments/2466878/af9015.patch](http://media.ubuntuusers.de/forum/attachments/2466878/af9015.patch)
patch -p1 <af9015.patch
make
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
make
sudo make install
sudo reboot

```

The first line installs some basic packages to be able to compile a kernel module.  I don't know what "hg" does, though it looks related to the video card.  The next two lines download a piece of firmware for the card and places it in the proper location.  The rest patches the kernel module code, compiles and installs it.

> ANother Q; It there anyway of running scripts in terminal in reverse? (remove the previously scrips)
 
Not really.  If you're concerned about the changes a script will make, back up any of the files or directories it touches first.

---

### Post by uRock on 2011-04-13
Moved to the Security Discussions sub-forum.

---

### Post by lithopsian on 2011-04-13
> you can't get spyware on linux
What a silly comment!  Of course you can get spyware for Linux.  It is fortunately extremely rare for a number of reasons.  Partly technical because it is difficult to work round the security features that Linux has by default and all the different Linux flavours out there.  Partly lack of interest because there aren't enough Linux users to be bothered with this sort of attack.  Most such malware on Linux is probably running within browsers.

The answer to the original question is that running a script in a terminal window can do anything you could do by typing in that window, and that is a whole lot of stuff!  Since you probably can't do most really important things like installing system software without entering an additional password, such a script would tend to be limited in what damage it could do.  It could certainly install itself or other software as a regular user and, for example, have itself run every time you login.

There are rootkits for Linux and they can do just about anything they want, but again infections aren't widespread because they need root or sudo passwords to get themselves installed.  Your router is a useful level of additional security simply because it is completely separate from your computer and an exploit on one will leave the other unaffected.

---

### Post by xic816 on 2011-04-13
> **SeijiSensei said:**
> It's certainly possible to so all sorts of bad things to your computer running scripts that aren't well-vetted if you don't know what they are doing.  However that's not the case here:

```

sudo aptitude install mercurial linux-headers-$(uname -r) build-essential
hg clone -r 0f41fd7df85d [http://linuxtv.org/hg/~anttip/af9015/]("http://linuxtv.org/hg/%7Eanttip/af9015/")
wget [http://jusst.de/manu/fw/AFA/dvb-usb-af9015.fw_a-link](http://jusst.de/manu/fw/AFA/dvb-usb-af9015.fw_a-link)
sudo mv dvb-usb-af9015.fw_a-link /lib/firmware/dvb-usb-af9015.fw
cd af9015
wget [http://media.ubuntuusers.de/forum/attachments/2466878/af9015.patch](http://media.ubuntuusers.de/forum/attachments/2466878/af9015.patch)
patch -p1 <af9015.patch
make
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
make
sudo make install
sudo reboot

```The first line installs some basic packages to be able to compile a kernel module.  I don't know what "hg" does, though it looks related to the video card.  The next two lines download a piece of firmware for the card and places it in the proper location.  The rest patches the kernel module code, compiles and installs it.


 
Not really.  If you're concerned about the changes a script will make, back up any of the files or directories it touches first.

Thanks a lot for answering my question!

R

MSS90

---

### Post by bodhi.zazen on 2011-04-13
> **Spyderkid said:**
> you can't get spyware on linux and there are very few viruses.

> **lithopsian said:**
> What a silly comment!  Of course you can get spyware for Linux.  

I would not put it exactly as lithopsian did, but if you run a script as root (sudo) it has full access to your system files, including your home directory, and can do what it wants.

"spyware" is a non-specific term and subject to opinions, some people may feel "popularity contest" is spyware, lol.

There are no know active viruses in Linux, but certainly if you run a script as root from an untrusted source all sorts of problems can occur.

These problems can range from bugs / incompatibilities in binaries or libraries to rootkits to backdoors to rogue servers to spyware to who knows what.

---

### Post by xic816 on 2011-04-13
> **uRock said:**
> Moved to the Security Discussions sub-forum.

Yeah, sry bout that.

Dno how to move it tho? O.o

---

### Post by uRock on 2011-04-13
> **xic816 said:**
> Yeah, sry bout that.

Dno how to move it tho? O.o

No worries.:D I moved it there/here.

---

### Post by xic816 on 2011-04-13
> **bodhi.zazen said:**
> I would not put it exactly as lithopsian did, but if you run a script as root (sudo) it has full access to your system files, including your home directory, and can do what it wants.

"spyware" is a non-specific term and subject to opinions, some people may feel "popularity contest" is spyware, lol.

There are no know active viruses in Linux, but certainly if you run a script as root from an untrusted source all sorts of problems can occur.

These problems can range from bugs / incompatibilities in binaries or libraries to rootkits to backdoors to rogue servers to spyware to who knows what.

hmm, dont u need to run everything as sudo anyways (talking about installation)?
Is there any way of scanning my computer for any threats? O.o 

How can you know if a script is legit?

Zazen every day! ^^;

---

### Post by xic816 on 2011-04-13
> **bodhi.zazen said:**
> I would not put it exactly as lithopsian did, but if you run a script as root (sudo) it has full access to your system files, including your home directory, and can do what it wants.

"spyware" is a non-specific term and subject to opinions, some people may feel "popularity contest" is spyware, lol.

There are no know active viruses in Linux, but certainly if you run a script as root from an untrusted source all sorts of problems can occur.

These problems can range from bugs / incompatibilities in binaries or libraries to rootkits to backdoors to rogue servers to spyware to who knows what.

hmm, dont u need to run everything as sudo anyways (talking about installation)?
Is there any way of scanning my computer for any threats? O.o 

How can you know if a script is legit? And does this also include programs in software center and synaptic? O.o

Zazen every day! ^^;

---

### Post by bodhi.zazen on 2011-04-13
> **xic816 said:**
> hmm, dont u need to run everything as sudo anyways (talking about installation)?
Is there any way of scanning my computer for any threats? O.o 

How can you know if a script is legit? And does this also include programs in software center and synaptic? O.o

Zazen every day! ^^;

Depends on the package and to some extent the configuration of your system.

For example, firefox is distributed (by mozilla) as a binary, so you can "install" it by downloading the archive and extracting it to your home directory.

Now your sys admin can mount your home directory as noexec or use tools such as selinux or apparmor to lock your account down, so there is some variability.

"trusted" sources of software would be :

1. The Ubuntu repositories.
2. ppa 
3. Any major peer reviewed repository (the linux kernel, sourceforge).
4. Any distributor you trust (intel, nvidia, wireless drivers, some printer drivers, etc).
5. Any code you have personally reviewed.

If you do not trust the source, do not  install the package.

There are tools you can use in Linux to detect problems, but forensics are complex.

See the security sticky for links or google search "Linux forensics".

So by default LInux is secure, and any problem, such as a rootkit, is going to be complicated to detect.

---

### Post by xic816 on 2011-04-18
> **bodhi.zazen said:**
> Depends on the package and to some extent the configuration of your system.

For example, firefox is distributed (by mozilla) as a binary, so you can "install" it by downloading the archive and extracting it to your home directory.

Now your sys admin can mount your home directory as noexec or use tools such as selinux or apparmor to lock your account down, so there is some variability.

"trusted" sources of software would be :

1. The Ubuntu repositories.
2. ppa 
3. Any major peer reviewed repository (the linux kernel, sourceforge).
4. Any distributor you trust (intel, nvidia, wireless drivers, some printer drivers, etc).
5. Any code you have personally reviewed.

If you do not trust the source, do not  install the package.

There are tools you can use in Linux to detect problems, but forensics are complex.

See the security sticky for links or google search "Linux forensics".

So by default LInux is secure, and any problem, such as a rootkit, is going to be complicated to detect.

Hm, so does that mean everything I can find on sourceforge for example is safe? By "the linux kernel" did u mean this site [http://tldp.org/LDP/tlk/tlk.html?](http://tldp.org/LDP/tlk/tlk.html?)
  
I'll take a look at forensics ;)

Thanks

---

### Post by bodhi.zazen on 2011-04-18
> **xic816 said:**
> Hm, so does that mean everything I can find on sourceforge for example is safe? By "the linux kernel" did u mean this site [http://tldp.org/LDP/tlk/tlk.html?](http://tldp.org/LDP/tlk/tlk.html?)
  
I'll take a look at forensics ;)

Thanks

You will have to decide for yourself what sources of scripts you trust.

---

### Post by xic816 on 2011-04-18
> **bodhi.zazen said:**
> You will have to decide for yourself what sources of scripts you trust.

How can I do that?! O.o I thaught all programs in software manager and synaptic were safe(inc. source forge)...

Can u give me some guidelines?

Thanks for reply

---

### Post by uRock on 2011-04-18
> **xic816 said:**
> How can I do that?! O.o I thaught all programs in software manager and synaptic were safe(inc. source forge)...

Can u give me some guidelines?

Thanks for reply

Everything in the repos is tested safe. When you go to sourceforge you have to use common sense. If there is a software you need from an external site, then feel free to ask if others think it safe.

---

### Post by bodhi.zazen on 2011-04-18
> **xic816 said:**
> How can I do that?! O.o I thaught all programs in software manager and synaptic were safe(inc. source forge)...

Can u give me some guidelines?

Thanks for reply

You are asking :

> **xic816 said:**
> Hm, so does that mean everything I can find on sourceforge for example is safe?

Define "safe" ?

The only safe code you install would be code that you have personally reviewed, which used to be the standard in Linux.

So you either need to relax and trust someone else to review the code for you or learn to review the code yourself.

The repositories from most any major distro, the Launchpad ppa, and sourceforge are all "peer reviewed", so considered fairly reliable.

One advantage of Ubuntu, the repos are quite large, it is rare you would need anything outside the repos, what is it you want to install ?

---

### Post by xic816 on 2011-04-18
> **uRock said:**
> Everything in the repos is tested safe. When you go to sourceforge you have to use common sense. If there is a software you need from an external site, then feel free to ask if others think it safe.


Yeah okey, good to know. From now on I proceed with caution!

Salute

---

### Post by xic816 on 2011-04-18
> **bodhi.zazen said:**
> You are asking :



Define "safe" ?

The only safe code you install would be code that you have personally reviewed, which used to be the standard in Linux.

So you either need to relax and trust someone else to review the code for you or learn to review the code yourself.

The repositories from most any major distro, the Launchpad ppa, and sourceforge are all "peer reviewed", so considered fairly reliable.

One advantage of Ubuntu, the repos are quite large, it is rare you would need anything outside the repos, what is it you want to install ?

I define safe as my data being secure (only viewed by me).

But yeah I'm not going to go all paranoid on this, but be aware.

I't not like one program I'm talking about just general, but while ur at it
I have been looking at despotify as my open source spotifty client but 
seems like not many are using it so I'm a bit sceptical.

---

### Post by Jive Turkey on 2011-04-18
> **xic816 said:**
> Hi, I just got this USB dongle with TV capabilities but it wasent supported by linux, 
when looking at the review/questions about the item there was a big debate about how to make it work on linux. One of the methods was to run this script;

DVB with chip AF9015 and tuner TDA18218:

on Kubuntu 10.4:

sudo aptitude install mercurial linux-headers-$(uname -r) build-essential
hg clone -r 0f41fd7df85d [http://linuxtv.org/hg/~anttip/af9015/](http://linuxtv.org/hg/~anttip/af9015/)
wget [http://jusst.de/manu/fw/AFA/dvb-usb-af9015.fw_a-link](http://jusst.de/manu/fw/AFA/dvb-usb-af9015.fw_a-link)
sudo mv dvb-usb-af9015.fw_a-link /lib/firmware/dvb-usb-af9015.fw
cd af9015
wget [http://media.ubuntuusers.de/forum/attachments/2466878/af9015.patch](http://media.ubuntuusers.de/forum/attachments/2466878/af9015.patch)
patch -p1 <af9015.patch
make
sed -i 's/CONFIG_DVB_FIREDTV=m/CONFIG_DVB_FIREDTV=n/' ./v4l/.config
make
sudo make install
sudo reboot


Then my question appears! Is it generally safe to run these scripts or can they include different types of virus/spyware? 

ANother Q; It there anyway of running scripts in terminal in reverse? (remove the previously scrips)

Thanks

R
Yes there is some risk there could be malicious code there.  It is more likely however that there are bugs that could affect system stability and possibly security.  

One thing I sometimes do is test it in a VM first and run a packet sniffer like wireshark to find any suspicious network activity (i.e. phoning home to a command & control server).  You could also run before and after nmap scans on the test system to get some assurance that the code is safe.  Another benefit of this is that VM's can be rolled back to a previous state quickly and easily for testing other things.

EDIT: There is no substitute for understanding and reviewing the code yourself.

---

### Post by xic816 on 2011-04-19
> **Jive Turkey said:**
> Yes there is some risk there could be malicious code there.  It is more likely however that there are bugs that could affect system stability and possibly security.  

One thing I sometimes do is test it in a VM first and run a packet sniffer like wireshark to find any suspicious network activity (i.e. phoning home to a command & control server).  You could also run before and after nmap scans on the test system to get some assurance that the code is safe.  Another benefit of this is that VM's can be rolled back to a previous state quickly and easily for testing other things.

EDIT: There is no substitute for understanding and reviewing the code yourself.

aha, so thats what wireshark is for! 

Salute

---

### Post by rookcifer on 2011-04-19
1) Scripts are code and code can do malicious stuff.

2) If you run said script as root, it can take over the entire system and you may never get rid of it short of reinstalling.

3) If you run the script as a user, it can still take over the user account and possibly attach itself to your /~autostart directory to run each time you login.  It can also elevate to root the next time you type in your root password (that is unless you set your sudo timeout to 0 which will prevent this).  We had a thread a while back where some guy provided a simple bash script which will elevate to root even if it was ran by a normal user.

4) As others have noted, the term "virus" is nowadays ambiguous because people have perverted the term to mean something it wasn't originally defined as. Nowadays people equate "virus" with any form of malicious code.  In reality, a virus is a self-replicating piece of computer code which is usually malicious.  That's it.  A malicious script may not replicate, but this doesn't mean it's not bad news.

5) To avoid any such attack, simply don't run random scripts unless you have read the code and understand it.  You can also set your sudo timeout to 0 which will stop it from elevating to root by capturing your password in the terminal.

---

### Post by xic816 on 2011-04-19
> **rookcifer said:**
> 1) Scripts are code and code can do malicious stuff.

2) If you run said script as root, it can take over the entire system and you may never get rid of it short of reinstalling.

3) If you run the script as a user, it can still take over the user account and possibly attach itself to your /~autostart directory to run each time you login.  It can also elevate to root the next time you type in your root password (that is unless you set your sudo timeout to 0 which will prevent this).  We had a thread a while back where some guy provided a simple bash script which will elevate to root even if it was ran by a normal user.

4) As others have noted, the term "virus" is nowadays ambiguous because people have perverted the term to mean something it wasn't originally defined as. Nowadays people equate "virus" with any form of malicious code.  In reality, a virus is a self-replicating piece of computer code which is usually malicious.  That's it.  A malicious script may not replicate, but this doesn't mean it's not bad news.

5) To avoid any such attack, simply don't run random scripts unless you have read the code and understand it.  You can also set your sudo timeout to 0 which will stop it from elevating to root by capturing your password in the terminal.

Noted, quick Q; if you get one of these viruses can it decrypt my passwords written in firefox as my paypal pw f. example? I'm now aware more of threats thanks to u guys

Salute

---

