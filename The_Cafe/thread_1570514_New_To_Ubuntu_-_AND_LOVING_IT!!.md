---
title: "New To Ubuntu - AND LOVING IT!!"
date: 2010-09-08
forum: The Cafe
---

### Post by tenfly on 2010-09-08
Just wanted to say hi to the community!
 
I've been running Windows Vista on an HP Pavillion DV6000 laptop.  Blue screens started creeping up on me.  Startups would take 4-5 minutes.  Delays in everything you do.  I just couldn't stand it anymore.  Meanwhile, I was taking a liking to learning Python.
 
I have looked in to Ubuntu some time ago, but it seemed very daunting, and I also had issues with partitioning my drive.  With the new release of Ubuntu out, I found out it came with WUBI, and it made it SO easy to install. 
 
That being said, there were issues.  All my internet is via wireless, and that gave some challenges.  Thanks to Google, and these forums, I was able to get that up and running.  I ended up buying a USB wireless card to go with my N protocol router.  That was another challenge, but I got that working as well.
 
Added Compix and wowed some people with the crazy stuff you can do.  
 
I do have a question though: Can anyone recommend some good resources for **understanding** the Ubuntu system?  The Terminal isn't too crazy for me as I was pretty familiar with DOS, but a lot of times with the things I'm doing in Terminal, I have no idea WHY I'm doing them - other than someone is posting instructions..Some good resources on that end would be great.
 
Other than that, Ubuntu is treating me very well.  My laptop feels as if it's brand new again.  I plan on getting deeper in Python, working with Conky, and trying another project of setting up a 6PC cluster run on Ubuntu.
 
Anyhow..
 
Just saying hi, and giving my story :D):P

---

### Post by LowSky on 2010-09-08
here is one of the best out there
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

oh and welcome to the forums!

---

### Post by Calash on 2010-09-08
Google can be your friend to understanding commands :).  

Linux also has a very nice internal document system called man.

For example, say you want to learn more about the dd command.  Type the following in the terminal

```

man dd

```

Press Q to exit out when you are done.

For a brief help you can usually get information by typing a --help after the command.

```

dd --help

```

Other variants of that switch are -? and sometimes /?

The Ubuntu Community Wiki is also a great resource.

[https://help.ubuntu.com/](https://help.ubuntu.com/)



Welcome to the world of Linux :)

---

### Post by undecim on 2010-09-08
We careful when using a Wubi install. It's prone to breaking after updates (or at least it was. I don't know what it's like now), and if you wipe your Windows install, you will also wipe ubuntu.

I usually recommend Wubi for people who want to try out Ubuntu before doing a standard install.

---

### Post by Naitsirhc Hsem on 2010-09-08
I like the ubuntu pocket guide, It helped me alot.  it is written for an older version of ubuntu , but most of the information is still acurate

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by praveenthivari on 2010-09-08
[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

---

### Post by Rasa1111 on 2010-09-08
Welcome. :)

Here is a good book for beginners ~ [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

 Also, Ubuntu Kung Fu is a good one.
 and [**here**]("http://thepiratebay.org/torrent/4826505/Ubuntu_eBooks#filelistContainer") is 11 pdf's, all books on Ubuntu, if you like.

The titles are~
/Beginning Ubuntu Linux - From Novice To Professional (2006)	
/Curso de Ubuntu.pdf	
/Hacking Ubuntu Serious Hacks Mods and Customizations
/Linux in a Nutshell 3rd Ed.
/Pocketubuntu Ubuntu shortcuts
/The Official Ubuntu Book.
/Ubuntu Linux - Bible [2007]
/Ubuntu Unleashed.chm	
/Ubuntu for Non-Geeks (2nd Ed).
/Ubuntu--Introdución y configuración.
/ubuntupocketguide-v1-1.pdf

 I also have a few more that I think are not there, If you need more let me know. 

Glad you loving Ubuntu,
Ive been loving it for about 9 months, and love it more all the time!
Congrats on a real OS coming into your life!
it's a beautiful thing! lol :) <3

---

### Post by Rasa1111 on 2010-09-08
ok, the others i have are~

 Ubuntu Hacks-Tips and Tools
Ubuntu Linux Toolbox- 1000+ Commands for Ubuntu and Debian Power Users
and 
Ubuntu, The Absolute Beginners Guide.

 if you want any of those, and can't find them, or can't find them for free, let me know and you can have them.
peace

---

### Post by tenfly on 2010-09-08
Wow - thanks so much for all the info all!! Ubuntu Forums is my new best friend :p

---

### Post by chriswyatt on 2010-09-08
Partitioning isn't too hard, it sounds scary but it's easy to do. GParted I find a breeze to use, you just shrink the block with your mouse until there's some space left, click OK and wait, then you install Ubuntu and tell it to fill the space.  If you try it just remember to be careful, and backing up is definitely advised.  Ubuntu setup can partition the drive for you as well.

When I first tried Ubuntu I reserved a bit of space for it, and gradually grew the partition until I abandoned XP altogether.  It's an inherently risky operation though, backing up is definitely advised.

---

### Post by tenfly on 2010-09-09
> **chriswyatt said:**
> Partitioning isn't too hard, it sounds scary but it's easy to do. GParted I find a breeze to use, you just shrink the block with your mouse until there's some space left, click OK and wait, then you install Ubuntu and tell it to fill the space.  If you try it just remember to be careful, and backing up is definitely advised.  Ubuntu setup can partition the drive for you as well.

When I first tried Ubuntu I reserved a bit of space for it, and gradually grew the partition until I abandoned XP altogether.  It's an inherently risky operation though, backing up is definitely advised.

I saw some info on GParted before installing Ubuntu, but I assumed you needed Ubuntu first in order to run it.  Would GParted work on Windows?  Is it on the LiveCD?

On top of that..Considering I used Wubi and my Ubuntu installation is part of the Windows system currently, could I still partition and bring it to it's own location, or would that mess up my Ubuntu installation?

So far I'm aiming towards getting rid of Vista altogether, but I'm still apprehensive. I figure a good 3 months of no going back, and the system will be 100% Ubuntu :D

---

