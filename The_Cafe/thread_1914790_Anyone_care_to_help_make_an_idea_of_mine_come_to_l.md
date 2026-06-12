---
title: "Anyone care to help make an idea of mine come to life?"
date: 2012-01-25
forum: The Cafe
---

### Post by spliffinz on 2012-01-25
Hi everyone! Sorry if this is the wrong place to post this, I wasnt quite sure where to.
This is my first post about Linux ever so youll have to excuse my lack of knowledge. What i dont have in terminology i more than make up for in enthusiasm for Linux (especially ubuntu) and all its delicious possibilities. Ive been compiling texts about topics from linux, ssh, vpns, etc etc etc but havent had time to fully read them :/


What i want to do is create a self sufficient linux kernel on my external hard drive thats capable of being run from any computer via usb but still contained within the hard drive (it has over 100gigs if thats enough). is this possible? how so how would i go about prepping the hard drive to run linux w/o any permanent formatting? 

With that I hope to be able to remotely access my Home pc to turn it on whenever and have it torrent me files and such.  
Ideally said connection would be totally secure, private and easy to use. Ive looked into SSH a little and it looks like the right way to go.  Maybe? is a linux remote desktop program the answer? and does the home pc even need linux for this to be possible?

Sorry if ive not made any sense, but Ive been mulling this idea around for a while after seeing hardcore Linux users in action and what they are capable of. Im finally at a point when i have both a reason and a desire to look into the world of Linux and such so these are exciting times :D

That being said thanks in advance for any help, feel free to ask for clarification, point me in the right direction or what have you, cheers!:popcorn:

---

### Post by mips on 2012-01-25
Well you can resize existing partitions on your HDD, create a new partition and then install a linux distro of your choice on it.

---

### Post by stefangr1 on 2012-01-25
You can always configure your home computer as a server that you can connect to from computers running any other operating system, and have it run any software you want. However, then it needs to stay on all the time because otherwise you won't be able to connect. Though, maybe you could use wake up on lan to turn it on remotely.

---

### Post by nothingspecial on 2012-01-25
Closed.

---

### Post by nothingspecial on 2012-01-26
Reopened.

---

### Post by earthpigg on 2012-01-26
Refinanced.

---

### Post by llua+ on 2012-01-26
Renegotiated.

---

### Post by satanselbow on 2012-01-26
retired?

---

### Post by aeiah on 2012-01-26
are you wanting to access files from home, or set torrent downloads going remotely or what?

---

### Post by spliffinz on 2012-01-26
Thanks for re-opening and re-negotiating! \\:D/
> **aeiah said:**
> are you wanting to access files from home, or set torrent downloads going remotely or what?

I want to be able to control what my home computer torrents, downloads, uploads, etc from my remote laptop and, then be able to rapidly and securely transfer those files.

The home PC has over a terabyte of memory so Id like to be able to swap different chunks of files back and forth as i need/use them.

Furthermore, id like to build (if possible, and forgive me if my terminology is incorrect) an ssh built vpn of sorts with the Home PC acting as an archive (not really wanting a constantly running server) that can transfer data to any computer that has my external hard drive plugged into it.

i hope this helps clear things up :P
ive just begun reading linux for dummies 8th ed which focuses on Fedora. as far as i have gotten is creating a new 10gig partition. I plan to run linux (hopefully Ubuntu with all its shinyness :D) on one half and keep the other as storage
--is 200gigs too much memory for a linux partition? what is a good number? i want to maximize pure storage space

---

### Post by Supermouse on 2012-01-26
Take a look at this software

[http://www.teamviewer.com](http://www.teamviewer.com)


It has versions for Linux and Windows, and can be installed on the machine (I.E. the "server" machine at home) or can be run "stand-alone", in a pen drive.

It does exactly what you want, you can create an account and link several machines to it, so you can remotely connect to them anywhere, and you don't even need to configure your router. Also, it's free for domestic use.

The only problem is that you have no ways to remotely start the machine, it needs to be on when you try to connect to it, but besides that, it's an amazing piece of software, I use it extensively to provide support to some clients of mine.

---

