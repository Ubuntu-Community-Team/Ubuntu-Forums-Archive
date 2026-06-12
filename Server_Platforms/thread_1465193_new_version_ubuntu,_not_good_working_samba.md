---
title: "new version ubuntu, not good working samba"
date: 2010-04-29
forum: Server Platforms
---

### Post by rainer169 on 2010-04-29
Hi to all,

installed the 9.10 Version of ubuntu. 

Now the situation is:

Four Computers are running under Windos XP-professional SP3
My computer, the fifth has ubuntu as os

After the upgrade to ubunto 9.10 (with the newest updates installed today) I`m unable to access the windows network. Shows me only windows network but when I click on it no list of workgroup is shown and therfore the network cannot be connected

Only with one "trick" get access: 
connect to server, then putting the ip's of th windows computers I've got connection to all allowed dir of all the four windows computers (location: smb://ip-adress)

To install a network printer is impossible neither with cups nor with system-> adaministration->print

At my computer is one printer which works fine. the other printer a Xerox Phaser 6110 is connectet to one XP computer and is configured as network printer under Windows.
The computer (IP-Adress is found but that is all) Printer is not connected.

Trying now for three days I'm really upset because there is one golden rule: Never touch running Systems! But you folks from ubuntu must bring ever second day some 
updates. Nothing against this, but configure your updates in that manner that the updates don't change all my settings.

When I boot my computer with windows-XP all network computers are there and usable.

My Samba config is ok too because otherwise I would not be able to connect to windows computer through the above mentioned trick.

Who can help me really? I do not need any blabla such as try this or try that as I googled for three days and all the answers where crap!

---

### Post by rainer169 on 2010-04-29
Oh Oh so much replies

---

### Post by ktmom on 2010-04-29
> **rainer169 said:**
> 
Who can help me really? I do not need any blabla such as try this or try that as I googled for three days and all the answers where crap!

That comment is going to deter all but the most stolid of people.

---

### Post by rainer169 on 2010-04-29
> **ktmom said:**
> That comment is going to deter all but the most stolid of people.


you see, that is the reply which is usal  googling ! I do not have to waste my time therfore 
pls answer only with a real problem solver:confused:

---

### Post by CharlesA on 2010-04-29
Do you have a working DNS server? If you can access the share from the IP but not the hostname, the windows clients are probably just doing netbios broadcasts to get the hostname/ip address instead of using DNS.

You could try adding the windows machines to the hosts file and see what happens.

As for the networked printer, how is it connected? I haven't had any problems connecting to either of my HP network printers while running 9.10.

---

### Post by rainer169 on 2010-04-30
The problem is resolved as I installed my former Ubuntu everything works fine now again. Do not touch running systems

Thank so lot

---

### Post by krodrigue on 2010-05-01
You need:

apt-get install gvfs-backends

It resolved the problem for me.

---

