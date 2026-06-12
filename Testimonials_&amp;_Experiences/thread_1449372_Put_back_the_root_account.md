---
title: "Put back the root account"
date: 2010-04-07
forum: Testimonials &amp; Experiences
---

### Post by Aurien on 2010-04-07
This is ridiculous. Trying to give ubuntu/linux another go as a game server OS, but removing access to root makes working with ubuntu a pain. Oh you want to setup SNMP? Well too bad those files are owned by root. So you can forget editing them with anything but VI, the most unfriendly editing software ever. Wanna create a new directory right on the c:\ drive so that directory structure is setup the way you want. Screw that root owns all that and your account isn't special enough to have those kind of privileges. Login to the root account? We can't have you actually using your computer the way you want or make anything easy for you.

And linux users wonder why it still can't make it mainstream.

---

### Post by VCoolio on 2010-04-07
Is this a question or just ranting to get rid of some frustration? There is a reasoning behind all this, like explained [here](https://help.ubuntu.com/community/RootSudo). Permissions in linux can be annoying, especially if things differ between distros and you did some hopping. But if you do distrohopping and get to a point where you complain about root stuff you should be able to make the next move and learn the next step. Stay happy.

---

### Post by sisco311 on 2010-04-07
I can't decide if you are looking for help or jsut want to share your experience with Ubuntu.

---

### Post by CharlesA on 2010-04-07
Smells like a rant to me.

sudo is yer friend.

---

### Post by VeeDubb on 2010-04-07
okay, let's learn 3 commands today, and go from there, shall we?


1.```
sudo
```
This will allow you to enter any one command at the terminal as the root user.  

2.```
sudo -i
``` 
This will switch you to being the root user.  Of course, if you need to be told this, you probably have no business running as root because your ignorance is too great and you'll mess up your system.  (I'm not using ignorance as in insult, but in the literal sense of "lack of knowledge")


3.```
gksudo
```
This will allow you to run any application as root, just like sudo, except that it's intended to be used with graphical applications.  For example, if you wanted to edit a text file that's owned by root, say, /etc/fstab, and you're not comfortable doing it with vi, you just enter ```
gksudo gedit /etc/fstab
``` and there you are with an idiot proof graphical text editor.


On a related note, the root account has always been there, it just doesn't have a password that will allow you to log into it directly.  Changing that is so easy as to be trivial.  It's just not a good idea.  10 seconds searching on google would have provided you with step by step directions if you really feel like typing "sudo -i" is too much work.

---

### Post by Aurien on 2010-04-07
Oh don't worry it is a rant. The link to the graphical sudo was helpful, I think Windows is going back on the box. It works and SNMP works. I feel like I'm about to re-engineer the wheel here to just turn on SNMP. Take a cue from microsoft simple is better.

[Couldn't direct link images]("http://www.mydigitallife.info/2007/11/01/install-and-enable-snmp-service-in-windows-xp-vista-and-2003/")

Look at that. Easily layed out format that's intuitive. Trudging through a text file that's 99% examples isn't easy or intuitive. I've changed what needed to be changed and it should work, but it doesn't.

And it's not the fact that the different levels of linux user/admin privileges are confusing, it's that I can't just switch to root make the changes and switch back. That would be the logical and easy way to do it. Searching the web to figure out how to deal with files owned by root isn't.

---

### Post by doas777 on 2010-04-07
you have the power in your hands to enable it yourself if you so choose, though I strongly recomend against it. VeeDub mentioned most everything you need to know to  administer ubuntu safely.
I am not allowed to tell you exactly how to enable the account, but I will give you a hint: the root account is "locked" and has a random password

---

### Post by wirelessmonkey on 2010-04-07
Aurien, if 
```
sudo apt-get install net-snmp 
```
isn't at least as easy as installing and starting the service in MS, I don't know what is...

But, on the other hand, you should use what works best for you.  Best of Luck.

---

### Post by marshmallow1304 on 2010-04-07
Sometimes we must make a choice between security and convenience.  It's clear which you desire.  Farewell.

---

### Post by Jazzy_Jeff on 2010-04-08
> **Aurien said:**
> Take a cue from microsoft simple is better.


People who make virus' and hackers would agree with ya. Use what ever floats your boat. Just don't complain when you are hacked.

---

### Post by shazbut on 2010-04-08
> **Aurien said:**
> [SNIP] Wanna create a new directory right on the c:\ drive so that directory structure is setup the way you want.[SNIP]

What's a c:\ drive?
;)

---

### Post by WinterRain on 2010-04-08
> **shazbut said:**
> What's a c:\ drive?
;)

With a name like shazbut, I take it you're not a young person. Ahhhh, 70's TV. Nanu-Nanu!

---

### Post by shazbut on 2010-04-08
> **WinterRain said:**
> With a name like shazbut, I take it you're not a young person. Ahhhh, 70's TV. Nanu-Nanu!
Actually, I stole it from a simpsons [episode.]("http://www.snpp.com/episodes/3F04.html")   And misspelled it too, apparently.

But no, I don't consider myself young.

---

### Post by kenweill on 2010-04-08
@TS
You might want to read the following links why root has been disabled by default in ubuntu. And another link on how to enable it in case you really need it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html](http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html)

Sometimes, i really need to run some apps with root privilege but i don't actually enable root. I just run "sudo -i" to do the trick.

---

### Post by lisati on 2010-04-08
> **shazbut said:**
> What's a c:\ drive?
;)
Good question! :) 
Joking aside, it's how MS-DOS & Windows refer to the primary disk drive or partition.
> **shazbut said:**
> Actually, I stole it from a simpsons [episode.]("http://www.snpp.com/episodes/3F04.html")   And misspelled it too, apparently.

But no, I don't consider myself young.
See [here]("http://www.imdb.com/title/tt0077053/")
> **kenweill said:**
> @TS
You might want to read the following links why root has been disabled by default in ubuntu. And another link on how to enable it in case you really need it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html](http://www.ubuntugeek.com/enable-and-disable-ubuntu-root-password.html)

Sometimes, i really need to run some apps with root privilege but i don't actually enable root. I just run "sudo -i" to do the trick.

+1

Edit: I notice the OP hasn't been back since post 6 of this thread.

---

### Post by uRock on 2010-04-08
> **Aurien said:**
> Oh don't worry it is a rant. The link to the graphical sudo was helpful, I think Windows is going back on the box. It works and SNMP works. I feel like I'm about to re-engineer the wheel here to just turn on SNMP. Take a cue from microsoft simple is better.

[Couldn't direct link images]("http://www.mydigitallife.info/2007/11/01/install-and-enable-snmp-service-in-windows-xp-vista-and-2003/")

Look at that. Easily layed out format that's intuitive. Trudging through a text file that's 99% examples isn't easy or intuitive. I've changed what needed to be changed and it should work, but it doesn't.

And it's not the fact that the different levels of linux user/admin privileges are confusing, it's that I can't just switch to root make the changes and switch back. That would be the logical and easy way to do it. Searching the web to figure out how to deal with files owned by root isn't.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Go down the page until you see the bright yellow warnings. That is here the explanation is to create the root account. Save your ranting for when you go back to that other OS and they don't give free security software for you to protect your server.

Cheers & beers,
Ronnie

---

### Post by WinterRain on 2010-04-08
[QUOTE=lisati;9096290]Good question! :) 
Joking aside, it's how MS-DOS & Windows refer to the primary disk drive or partition.
QUOTE]
As a side note, your primary disk drive or partition can be other drive letters also. Mine is D:

But most of the time, it is C:

---

### Post by uRock on 2010-04-08
> **WinterRain said:**
> <snip>

I used to have them up through M:, then I got rid of all but one NTFS partition and made a bunch of EXT4 partitions.

---

