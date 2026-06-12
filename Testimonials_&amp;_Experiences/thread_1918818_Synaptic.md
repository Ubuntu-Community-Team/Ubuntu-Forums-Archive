---
title: "Synaptic"
date: 2012-02-01
forum: Testimonials &amp; Experiences
---

### Post by tbresson on 2012-02-01
With the new release of Ubuntu and the Synaptic removed I kind of felt lost.

I tried to install a webserver with database etc. (LAMP-ish) but couldn't.

The software center keep telling me something was wrong but I could go right ahead if I wanted to. That's not user-friendly, that's just saying to the user "he/she did something wrong".

I agree the software center is more user-friendly-LOOKING than the Synaptic interface. Perhaps that's the reason why if you search for a guide to setup a webserver it will ask you to use a terminal. 

That doesn't help new users when they search for help does it?

I tried to install apache, php and mysql and the phpmyadmin but my install of the ladder just gave me an error - something like I didn't have a database installed (I google the error response). But I did. Perhaps I didn't restartm, close the software center or rebooted but I had installed everything as supposed to. Yet, I felt like a noob user. I still think that attracting new users to Ubuntu is the goal and my experience does not count in that favor hence my thread.

After rebooting I went and tried installing again and it worked. I don't know if it ever made the changes to the database which it wanted to or if it picked up where it left off the last try I made but it works.

Now I can only imagine what kind of components are a part of that installation. mySQL only, or mySQL Cli - and what other components are in the default install, ImagePick? I feel like I should know this when installing a development tool but the user-friendliness may be taking over.

Even though I had trouble I still believe Linux and Ubuntu is a great system and more should use it and I hope they will. 

Tnx.

---

### Post by Claus7 on 2012-02-01
Hello,

synaptic is gone? I feel like a prehistoric man! Thanks for the info!

Hmmm, my humble opinion is that sticking with the latest and greatest sometimes you start anew. Sometimes this is not bad, as you evolve through it. If you need something more stable, you stick with older releases I guess.

Regards!

---

### Post by Myrddin Emrys on 2012-02-01
Synaptic doesn't come on the CD any more, but it's still available in the repositories (though now in Universe rather than Main). Only takes a minute to install.

---

### Post by mörgæs on 2012-02-02
Agree, Software Centre is not suitable for complicated tasks. 

When I install Buntu for a friend I always wonder if I should recommend SC or Synaptic. Only if I am convinced he is never going to try anything advanced I show him SC; if he likes experimenting best is to learn Synaptic from day one.

As for the LAMP stack, even better than Synaptic are the two comamnds
```
sudo apt-get install tasksel
sudo tasksel install lamp-server

```

---

### Post by mastablasta on 2012-02-02
server is normally not ment to be run with desktop. 
 
but if you insist on GUI for server stack install tasksel indeed does the job of installing well.

---

### Post by satanselbow on 2012-02-02
[QUOTE=mastablasta;11658359
but if you insist on GUI for server stack install tasksel indeed does the job of installing well.[/QUOTE]

Anyone is doing any sort of webdev is gonna need a development LAMP stack... unless you're into google caching every mistake you make :D

Synaptic is the 1st thing back on my machines... rapidly followed by the tasksel installed LAMP ;)

---

