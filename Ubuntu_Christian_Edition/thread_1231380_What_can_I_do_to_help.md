---
title: "What can I do to help?"
date: 2009-08-04
forum: Ubuntu Christian Edition
---

### Post by oneinch on 2009-08-04
Greetings everyone!

Now this is a project I can get into! I am both a Christian and a lover of the *nix. What can I and others do to contribute to this project?

---

### Post by oneinch on 2009-08-04
I have been trying to get the torrent of UbuntuCE 5.0 for a while now but there is no seeders :( I will seed for you guys. I don't have the fastest connection in the world, just a cable connection but I usually get 1.5 - 2.0mbit downstream never really tested my upstream. None the less! I will seed for you guys :D

---

### Post by stlsaint on 2009-08-04
glad to see another sharing the faith and loving ubuntu!

---

### Post by Viva on 2009-08-04
You can burn a few Ubuntu CE CDs and distribute them to your friends at a Church or a gathering.

---

### Post by oneinch on 2009-08-04
Well, I have the torrent now. The problem was not with the seeders the problem is with Monsoon.  Tried it in a different bittorrent client and the download went smoothly and is seeding smoothly. Yet monsoon is doing nothing and I don't know why just yet either.

---

### Post by david_kt on 2009-08-04
> **oneinch said:**
> Greetings everyone!

Now this is a project I can get into! I am both a Christian and a lover of the *nix. What can I and others do to contribute to this project?

First, you could help us to test the release/deb package and feedback any difficulties you have.

Now I am preparing the server version. For server version, I plan to have:

1. Church administration software preconfigured
2. Church website ready for deployment.
3. Prayer request web blog for church member to put up their request.

On top of that, I will also include the applications available on ubuntu ce desktop version (OpenSong, dansguardian, linbread, trivia, encfs-gui, e-Sword installer).

DK

---

### Post by oneinch on 2009-08-04
sounds like a plan, and good one :D

Any thoughts on presentation and video software for churches to make use of?

---

### Post by stlsaint on 2009-08-06
> **david_kt said:**
> first, you could help us to test the release/deb package and feedback any difficulties you have.

Now i am preparing the server version. For server version, i plan to have:

1. Church administration software preconfigured
2. Church website ready for deployment.
3. Prayer request web blog for church member to put up their request.

On top of that, i will also include the applications available on ubuntu ce desktop version (opensong, dansguardian, linbread, trivia, encfs-gui, e-sword installer).

Dk



i will surely test that for you!!

---

### Post by stlsaint on 2009-08-06
i have never put server software on a laptop before so im asking what will be the limitations if any on using server version with a laptop?

---

### Post by oneinch on 2009-08-06
Any coding or anything else, writing a man page, formatting something. GIVE US ASSIGNMENTS@!@!! 

:P

---

### Post by stlsaint on 2009-08-06
> **oneinch said:**
> Any coding or anything else, writing a man page, formatting something. GIVE US ASSIGNMENTS@!@!! 

:P

lol...well ubuntu coding may be a little above my level!!

---

### Post by oneinch on 2009-08-06
> **stlsaint said:**
> lol...well ubuntu coding may be a little above my level!!

still scripting or something :D I tried to look for the source for the dansguardian gui but could not find it. Not saying that I could do anything with it but still was courious enough to give it a peek. :D

---

### Post by david_kt on 2009-08-07
> **stlsaint said:**
> i have never put server software on a laptop before so im asking what will be the limitations if any on using server version with a laptop?

There is no problem to put it on laptop. The only different I see now is Raid software. For server, normally we would use raid software to make sure we have robust data storage.

But if you only have one harddisk, there is no Raid required. Furthermore, for ubuntu ce server version, I do not use raid.

DK

---

### Post by david_kt on 2009-08-07
> **oneinch said:**
> still scripting or something :D I tried to look for the source for the dansguardian gui but could not find it. Not saying that I could do anything with it but still was courious enough to give it a peek. :D

It is just normal scripting and is not compiled. You could see the script easily, open terminal and:

```
gedit /usr/bin/dansguardian_gui
```

It is very simple and ugly script, but it works!

DK

---

### Post by oneinch on 2009-08-07
> **david_kt said:**
> It is just normal scripting and is not compiled. You could see the script easily, open terminal and:

```
gedit /usr/bin/dansguardian_gui
```It is very simple and ugly script, but it works!

DK


Awesome, Thank you. I am gonna snoop around and If I can do anything I will.

---

### Post by stlsaint on 2009-08-07
> **david_kt said:**
> There is no problem to put it on laptop. The only different I see now is Raid software. For server, normally we would use raid software to make sure we have robust data storage.

But if you only have one harddisk, there is no Raid required. Furthermore, for ubuntu ce server version, I do not use raid.

DK


so theoretically i should be able to run server edition and hopefully my church website from my laptop right?

---

### Post by oneinch on 2009-08-07
> **stlsaint said:**
> so theoretically i should be able to run server edition and hopefully my church website from my laptop right?

Well, there is no reason that you couldn't run a web site from the laptop. But I would advise against it because if you want to host your own site it is better to put it on a box that is going to be dedicated to just that or just running servers. In other words, its going to be on a box that is going to sit there and rarely ever get used. So unless you plan to hook that laptop up, leave it on and never move it around or do anything else with it, then you could. But if you plan on carrying that lap top around then I say no because you are going to end up with a lot of angry people who find it is hit and miss trying to get on the site.

Now there is no reason what so ever that you can't do presentations, editing and everything else from the laptop. Its just if you want to run a server you want to have a dedicated machine for hosing the server(s)

---

### Post by stlsaint on 2009-08-07
yea i have a custom built desktop that i was thinking of using for it but its def. in need of an upgrade...but i will prolly use another laptop but put a bigger hdd in it a leave it up and alone!

---

### Post by david_kt on 2009-08-07
> **stlsaint said:**
> yea i have a custom built desktop that i was thinking of using for it but its def. in need of an upgrade...but i will prolly use another laptop but put a bigger hdd in it a leave it up and alone!

You could use a laptop but you must announce when it is up and when it is down to your church member. Because if you on the laptop 24 hours, I guess it would shorten the live span of your laptop.

I think Ubuntu ce server edition should be on desktop, it could be use for desktop purposes as well just in case you only have one desktop at home.

DK

---

### Post by stlsaint on 2009-08-07
what if i used server edition on a laptop as well as a desktop and just use one at a time on and off per week??

---

### Post by oneinch on 2009-08-07
> **stlsaint said:**
> what if i used server edition on a laptop as well as a desktop and just use one at a time on and off per week??


Do you mean keep the desktop up for a week running the http server then switch out the desktop with the laptop for a week then switch out the laptop with the desktop for another week and so on? That _could_ work and would work, but here is the thing: It would be double the work for you. Because if you change it on one then you are going to have to change it on the other and any databases would have to be moved back and forth, etc, etc. I think in the long run it will prove to be a big ol pain in the butt doing it this way. 


You could always build a cheap lower end desktop with stuff bought bought from ebay, just be sure to give it gobs of hdd space and lots of ram. Don't really need a fancy sound card or vid card, and don't really need the greatest monitor in the world either. And you really don'ty need the fanciest keyboard around nor the best mouse. After all, It will just be used as an http server. Hook it up, turn it on, configure it and let it run. Just do some routine maintenance every now and then :D

---

### Post by david_kt on 2009-08-07
> **stlsaint said:**
> what if i used server edition on a laptop as well as a desktop and just use one at a time on and off per week??

The problem is on the ip address assignment I guess. In order to run server on internet, you have to have public domain name, and set up port forward.

But if you use it on LAN only that would be easier.

DK

---

### Post by stlsaint on 2009-08-08
thanks for the response guys...yea its my first time getting a website up so im new to web design but i know a little coding so it cant be too hard! oneinch ill prolly just do what you adivse, i already have a case, hdd, cd-rom, i may get a new mobo and process and grapchis card but thats all i need!! thanks again...now to look up how to buy a domain!!

---

### Post by david_kt on 2009-08-08
> **stlsaint said:**
> thanks for the response guys...yea its my first time getting a website up so im new to web design but i know a little coding so it cant be too hard! oneinch ill prolly just do what you adivse, i already have a case, hdd, cd-rom, i may get a new mobo and process and grapchis card but thats all i need!! thanks again...now to look up how to buy a domain!!

You could use Free Dynamic DNS

[http://www.dyndns.com/](http://www.dyndns.com/)

You do not need to buy a domain.

DK

---

### Post by stlsaint on 2009-08-08
wow...DK does it again!
thanks!!

---

