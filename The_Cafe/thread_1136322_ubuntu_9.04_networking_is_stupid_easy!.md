---
title: "ubuntu 9.04 networking is stupid easy!"
date: 2009-04-24
forum: The Cafe
---

### Post by wildman4god on 2009-04-24
One of the problems I had with 8.10 is it was complicated to create your own wireless network that others could easily connect to for file sharing or internet sharing, but they fixed that in 9.04 and it is awesome, even file sharing is easier in ubuntu now than xp (have you ever tried to connect to computers together wirelessly in xp, it takes about 10 mins of messing around with the settings and praying to God to make it work). In ubuntu I was able to share my eathernet connection to an apple ipod touch over wifi in less than 10 seconds. My teacher says its hard to do this in windows because it is "special"

Anywho just wanted to highlight one of my favortie features in this awesome release of ubuntu.

---

### Post by lovinglinux on 2009-04-25
[When Teachers Are Obstacles To Linux In Education](http://linux.slashdot.org/article.pl?sid=08/12/10/001236).

My favorite feature is that I can watch TV now, without HDD interference.

---

### Post by Saint Angeles on 2009-04-25
you messed up the punctuation and the order of the words in the title... it should read:
"ubuntu 9.04 networking is easy, stupid!"

---

### Post by Sashin on 2009-04-25
Can you explain to me how to setup a wired network between two ubuntu computers? As in how I can transfer files etc.

---

### Post by inobe on 2009-04-25
it was easy enough for 8.10



howto 8.10 [https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

steps 1 to 11 under **"Sharing folders via the Shared Folders application'**

and to secure shares, steps 1 to 6 under **"Accessing shared folders via Windows"**

that roughly took 5 minutes to setup to share over a network.

---

### Post by Sashin on 2009-04-25
Well I'm using the newly released Jaunty on both but I'll try the guide anyway.

---

### Post by lisati on 2009-04-25
> **Saint Angeles said:**
> you messed up the punctuation and the order of the words in the title... it should read:
"ubuntu 9.04 networking is easy, stupid!"

- or -
"ubuntu 9.04 networking is stupidly easy"

Getting my Ubuntu installations hook up to my wirdless routers has been fairly painless with each of the flavours of Ubuntu I've used.

I've successfully used the file-sharing tutorial (with only minor modifications) at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) on 7.04, 8.10 and 9.04

---

### Post by inobe on 2009-04-25
> **Sashin said:**
> Well I'm using the newly released Jaunty on both but I'll try the guide anyway.

it may be a slight difference in procedure with **Karmic Koala**, that's the next alpha after jaunty so your good.

---

### Post by crl0901 on 2009-04-25
I feel stupid.  I first installed 9.04 on my laptop and of course, out of the box, wireless didn't work....kind of.  After snooping around, I realized I had to activate the proprietary Broadcom wireless drivers.  After that, it works perfectly, so yes, it's stupid easy.

---

### Post by inobe on 2009-04-25
what the heck, to anger the kubuntu haters it will be a bit more complicated to setup samba in kubuntu' but works well....

1) we need to install samba if it's not already installed, open konsole and do 

```
sudo apt-get install samba
```

2) we need to create a samba user name and password replacing username with actual user name, don't forget this !

```
sudo smbpasswd -a username
```

3) creating the shared folder, shares can be replaced with anything you wish

```
mkdir /home/username/shares
```

4) lets backup your current smb.conf encase your destroy something you can fix it.

```
sudo cp /etc/samba/smb.conf ~
```

5) lets edit your smb.conf

```
sudo kate /etc/samba/smb.conf
```

6) when kate opens the smb.conf scroll down and paste

```
[shares]
path = /home/username/shares
available = yes
valid users = username
read only = no
browsable = yes
public = yes
writable = yes
```


remember the shares, you can name the folder anything, also don't screw it up and forget to add your actual user name.

click save and close kate.

7) restart samba.

```
sudo /etc/init.d/samba restart
```

you will be informed via terminal when samba is started back up.

now lets run the smb test

```
testparm
```

if your output says **loaded services file ok** your good.

someone using kubuntu would find this very useful even in the cafe.

enjoy

---

### Post by winjeel on 2009-04-25
> **lovinglinux said:**
> [When Teachers Are Obstacles To Linux In Education]("http://linux.slashdot.org/article.pl?sid=08/12/10/001236").

My favorite feature is that I can watch TV now, without HDD interference.

As a teacher, I can tell you a little of what I know of these "obstacles". I've deliberately have chosen not to work in the UK, Australia or other western education system, as parents can create obstacles, the older generation of teachers are concerned about getting the basics right, rather than exploring the future. I've met an Australian teacher who wants to use mobile phones in class, but the education system prevents him, and he's the principle of a high school!

Me, I find excuses to have my students use their phones in class. The problem is that students know more about how to use their phones, than they do using a computer. Many of my students don't even have computers, and don't know how to use MS Word even.

I haven't tried yet, but can iPhones connect via wifi to a regular computer directly?

---

### Post by wildman4god on 2009-04-25
No I didn't mess up the title, "stupid easy" is my favorite funny phrase to discribe something that is easy enough for stupid people to do. as far as a wired connection is concerned, get a crossover cable and before you connect the ethernet jacks of the two computers together, configure each nic with a static ip address that are both in the same subnet but not the same address (e.g. nic 1 = 192.168.0.1 nic 2 = 192.168.0.2) also remember to configure the subnet mask (255.255.255.0 for both nics in this case). then connect your cable and in a few seconds they should connect and off you go, just be sure to setup file sharing on both computers. if you want to share one of the computers internet connection, then go enable internet connection sharing on the nic that access the internet.

---

### Post by 3rdalbum on 2009-04-25
I found the file sharing in Ubuntu 8.10 to be "stupid easy" too - what has changed?

The procedure for file sharing in Ubuntu 8.10 is actually exactly the same as file sharing in System 7; how's that for a spin-out? I'm not complaining!

---

### Post by wildman4god on 2009-04-25
> **3rdalbum said:**
> I found the file sharing in Ubuntu 8.10 to be "stupid easy" too - what has changed?

The procedure for file sharing in Ubuntu 8.10 is actually exactly the same as file sharing in System 7; how's that for a spin-out? I'm not complaining!

not file sharing, creating a wireless network is stupid easy, it didn't work in 8.10 unless you did a certain trick in the configuration of it, you don't need the trick anymore.

---

### Post by billgoldberg on 2009-04-25
> **Sashin said:**
> Can you explain to me how to setup a wired network between two ubuntu computers? As in how I can transfer files etc.

```
sudo apt-get install ssh
```

Now on both computers, go to Places -> Connect to Server.

Give in the ip adress of the machine you are connecting to (you can see it in Network Manager if you don't know) and use the username and password for that machine.

Done.

You will be able to browse the other pc from within Nautilus and copy/paste stuff from machine to machine as you please.

---

### Post by Saint Angeles on 2009-04-25
> **wildman4god said:**
> No I didn't mess up the title, "stupid easy" is my favorite funny phrase to discribe something that is easy enough for stupid people to do...
i know... it was a joke

---

### Post by inobe on 2009-04-25
> **billgoldberg said:**
> ```
sudo apt-get install ssh
```

Now on both computers, go to Places -> Connect to Server.

Give in the ip adress of the machine you are connecting to (you can see it in Network Manager if you don't know) and use the username and password for that machine.

Done.

You will be able to browse the other pc from within Nautilus and copy/paste stuff from machine to machine as you please.

what security methods do you use for that.

---

### Post by Giant Speck on 2009-04-25
Ubuntu 9.04 seems to have also extended support for more mobile broadband companies, allowing you to easily tether Sprint and Verizon phones.  With Intrepid, there were only options for AT&T and T-Mobile.

Sigh... if only Anchorage had 3G.

---

### Post by inobe on 2009-04-25
> **Giant Speck said:**
> Ubuntu 9.04 seems to have also extended support for more mobile broadband companies, allowing you to easily tether Sprint and Verizon phones.  With Intrepid, there were only options for AT&T and T-Mobile.

Sigh... if only Anchorage had 3G.

i noticed that too, all the countries and 3g providers.


i think the supported devices are only evdo cards.

---

### Post by Giant Speck on 2009-04-25
> **inobe said:**
> i noticed that too, all the countries and 3g providers.

i think the supported devices are only evdo cards.

When I was running Intrepid, I was able to tether my Blackjack II and use it for internet.  I didn't even need an additional tethering plan for it to work.

---

### Post by 3rdalbum on 2009-04-25
> **wildman4god said:**
> not file sharing, creating a wireless network is stupid easy, it didn't work in 8.10 unless you did a certain trick in the configuration of it, you don't need the trick anymore.

Oh okay... you're talking about using your computer as a wireless AP? Sorry! I'll have to take your word for it being stupid easy, I've never tried :-)

But there are still people complaining that Samba is too difficult to set up...

---

### Post by wildman4god on 2009-04-25
> **3rdalbum said:**
> Oh okay... you're talking about using your computer as a wireless AP? Sorry! I'll have to take your word for it being stupid easy, I've never tried :-)

But there are still people complaining that Samba is too difficult to set up...


well the trick to samba is you need you manually setup a username and password, when enabling file sharing it does not prompt you for that info.

---

