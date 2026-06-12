---
title: "Downloading DVD ISO's with Bittorrent"
date: 2005-07-03
forum: The Cafe
---

### Post by jsimmons on 2005-07-03
This is a freakin' joke. I downloaded the CD ISO's in less than 15 minutes. With Bittorrent, it's taken me 1 hour 10 minutes just to get the first 90mb. This is no faster than freakin' dial-up.

Is there anyplace I can download the dvd iso without being forced to use this bittorrent garbage?

---

### Post by primeirocrime on 2005-07-03
as time unfolds the torrent get's faster, don't forget it is shared with other people and bennefits from the sharing. Downloadng from a sole ftp or http adress it's not only consumming your bandwith but also the servers bandwith. Torrents are slower agree but also a decent way of sharing data because it's generous.

---

### Post by UbuWu on 2005-07-03
Maybe you are behind a router of firewall? Without proper configuration that can have a major effect on download speed through bittorrent and p2p programs.

---

### Post by sapo on 2005-07-03
the thing that i hate most is people complaining about bittorrent.. i always download 10GB+ stuff and never had problems...

then people open bittorrent for 10 minutes and say "this is downloading at 10kbps, this thing sux"  ](*,) 

Think about it.. maybe you have 100 sources ... but you will NEVER connect to 100 sources when you open your bittorrent.. you will connect to usually 20..

then if you are lucky.. among this 20 sources you can have a guy with a 500kbps upload.. or you can have 20 sources with 12kbps upload...

but if you wait.. when you bt client update the tracker, more sources will be added to your download.. so its gonna be faster...

you have to be patient about it.. stop looking at the download.. just leave it open and find something to do..  ](*,)

---

### Post by jsimmons on 2005-07-03
[QUOTE=sapo]the thing that i hate most is people complaining about bittorrent.. i always download 10GB+ stuff and never had problems...

then people open bittorrent for 10 minutes and say "this is downloading at 10kbps, this thing sux"  ](*,) 

Think about it.. maybe you have 100 sources ... but you will NEVER connect to 100 sources when you open your bittorrent.. you will connect to usually 20..

then if you are lucky.. among this 20 sources you can have a guy with a 500kbps upload.. or you can have 20 sources with 12kbps upload...

but if you wait.. when you bt client update the tracker, more sources will be added to your download.. so its gonna be faster...

you have to be patient about it.. stop looking at the download.. just leave it open and find something to do..  ](*,)[/QUOTE]


That's all well and good, but this thing's been cooking for over two hours.  I got the install iso in less than 15 minutes.  Right now, the shittorrent is speeding along at 4KB/s, and it bounces around from there to 40KB (spending the majority of it's time at 15KB/s) - I fail to see how anyone can think this is a good idea...

---

### Post by sapo on 2005-07-03
[QUOTE=jsimmons]That's all well and good, but this thing's been cooking for over two hours.  I got the install iso in less than 15 minutes.  Right now, the shittorrent is speeding along at 4KB/s, and it bounces around from there to 40KB (spending the majority of it's time at 15KB/s) - I fail to see how anyone can think this is a good idea...[/QUOTE]


are you behind a firewall? are you limiting the upload speed?

if you cant get a direct connection with the clients.. or if you limit you upload speed it is gonna stay at this rate forever...

i have 42kbps upload.. and i always download with speed > than 36kbs... i think you have some configuration mistake or some problem... i m used to download things that are bigger than 10GB and it works fine for me with azureus

---

### Post by jsimmons on 2005-07-03
[QUOTE=sapo]are you behind a firewall? are you limiting the upload speed?

if you cant get a direct connection with the clients.. or if you limit you upload speed it is gonna stay at this rate forever...

i have 42kbps upload.. and i always download with speed > than 36kbs... i think you have some configuration mistake or some problem... i m used to download things that are bigger than 10GB and it works fine for me with azureus[/QUOTE]


I'm behind a Linksys router with port 6881 forwarded to this box.

Upload speed is not capped.

Number of users is not capped.

I have a 5-7mb down/512k up connection.  

I'm using gnome-torrent to dowenload because that's what was installed with Ubuntu.

If there's a super-secret setting you'd like to share with me, then by all means, do so.

---

### Post by sapo on 2005-07-03
[QUOTE=jsimmons]I'm behind a Linksys router with port 6881 forwarded to this box.

Upload speed is not capped.

Number of users is not capped.

I have a 5-7mb down/512k up connection.  

I'm using gnome-torrent to dowenload because that's what was installed with Ubuntu.

If there's a super-secret setting you'd like to share with me, then by all means, do so.[/QUOTE]


Try installing azureus.. i think its in backports.. or download it at: [http://azureus.sf.net](http://azureus.sf.net)

azures have a "health" stuff.. if the health indicator of your torrent stays yellow all the time.. means that you have a nat problem, it downloads.. but at 5/10kbps.

it have to stay green, with gnome-bittorrent you cant be sure about it.. if you use azureus and it stays yellow, you can be sure that the problem is your connection  ](*,)

---

### Post by jsimmons on 2005-07-03
[QUOTE=sapo]Try installing azureus.. i think its in backports.. or download it at: [http://azureus.sf.net](http://azureus.sf.net)

azures have a "health" stuff.. if the health indicator of your torrent stays yellow all the time.. means that you have a nat problem, it downloads.. but at 5/10kbps.

it have to stay green, with gnome-bittorrent you cant be sure about it.. if you use azureus and it stays yellow, you can be sure that the problem is your connection  ](*,)[/QUOTE]

Okay, I have it installed, but my "health" is always yellow.  I passed the port 6881 test when i installed it.  What do I do to make it green?

---

### Post by sapo on 2005-07-03
[QUOTE=jsimmons]Okay, I have it installed, but my "health" is always yellow.  I passed the port 6881 test when i installed it.  What do I do to make it green?[/QUOTE]


as i tought.. you have a nat problem..

hm.. you have to allow azureus to have a DIRECT connection with you.. but i dont know how are you gonna config your router, i dont understand this kind of stuff  ](*,)

---

### Post by poofyhairguy on 2005-07-03
[QUOTE=jsimmons]
I'm using gnome-torrent to dowenload because that's what was installed with Ubuntu.[/QUOTE]


There is your problem. Go in synaptic and uninstall bittorrent. Then install bittornado from the backports. 

Using the "dsl/cable slow" setting, I download at the top speed on my connection in most cases- not at first though. Takes a while to build.

---

### Post by jsimmons on 2005-07-03
[QUOTE=poofyhairguy]There is your problem. Go in synaptic and uninstall bittorrent. Then install bittornado from the backports. 

Using the "dsl/cable slow" setting, I download at the top speed on my connection in most cases- not at first though. Takes a while to build.[/QUOTE]

I installed azureus before i saw this.  In any case, it still took 8 hours to download after restarting with azureus.  IMHO, performance of this torrent stuff really sucks.

---

### Post by sapo on 2005-07-03
[QUOTE=jsimmons]I installed azureus before i saw this.  In any case, it still took 8 hours to download after restarting with azureus.  IMHO, performance of this torrent stuff really sucks.[/QUOTE]

man.. i already said it.. the problem is YOUR NETWORK.. not bittorrent.. if you are unhappy with it just dont use it at all and stop complaining... here a screenshot i just took:

[[IMG]http://img112.imageshack.us/img112/5190/screenshot5iz.th.jpg[/IMG]](http://img112.imageshack.us/my.php?image=screenshot5iz.jpg)

look at the size of the files, the percentage and the download speed... i have ADSL 450kbps.. so my maximum download speed is 42k.

Am i nuts? how can i download a torrent with all those files.. that togeter are more than 10GB in size.. and you cant download a single dvd image with your 2mb connection?


yes.. bittorrent sux... its all its fault, maybe you should write to Bram Cohen and say that his software is a worthless piece of shit..  :roll: 

or you can solve your nat problem and use it as everybody do  ](*,) 

sorry.. i just got stressed out  ](*,)

---

### Post by timczer on 2005-07-03
I have tried azureus, and the test tells me I have a nat problem.  I have googled the problem, followed the trouble shooting guides and cannot get it to go away.  Even if I disable my firewall (firestarter) it doesn't stop showing a nat error.  I am not on a network, just a single user.  How do I fix this?

---

### Post by poofyhairguy on 2005-07-03
[QUOTE=jsimmons]I installed azureus before i saw this.  In any case, it still took 8 hours to download after restarting with azureus.  IMHO, performance of this torrent stuff really sucks.[/QUOTE]


Should have done what I said. I download torrents a 300+KB.

The default options of most torrent programs suck.

Torrents kick ass.

---

### Post by timczer on 2005-07-04
Update on my issue with azureus.  I am using a voip phone, with my internet cable modem running to the phone modem, then running to the computer.  The phone modem seems to be the issue.  When I run with the modem in place, I get Yellow light for health  and slow speeds.  When I removed the modem, I got green health the download was up over 200kbps and climbing.  

Now, I have had issues with the modem on other fronts and am having the provider send me a new one which will hopefully help.  So, for the original question in the thread, could this also be your problem?  For others, has anyone else faced this, and if so, what did you do to fix it?  I know I could connect directly to the cable modem for large downloads, but then I lose my phone service, plus it seems like I have to reboot Ubuntu for it to find the change in cable connection).

---

### Post by UbuWu on 2005-07-04
[QUOTE=timczer]plus it seems like I have to reboot Ubuntu for it to find the change in cable connection.[/QUOTE]

Try this:
Go to system - administration - networking and then deactivate and activate the connection again.

---

