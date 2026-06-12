---
title: "Jargon in the Movie &quot;Breach&quot;"
date: 2008-04-02
forum: The Cafe
---

### Post by aysiu on 2008-04-02
Yesterday, I saw the movie *Breach*, which is about the capture of the FBI double agent Robert Hanssen, who happened to be one of the most knowledgeable in the FBI regarding internet security.

There's one part where he goes on a long rant about all the things they should be replacing, and he mentions ditching WAN for some other three-letter thing and making sure they get Linux Red Hat servers and stuff. Naturally, most viewers would have no idea what the hell he's talking about, but I'm just curious if anyone here does.

If you're a pretty knowledgeable network person, and you've seen *Breach*, was that all just mumbo-jumbo that sounds "smart" but really means nothing, or had they actually consulted a network administrator when writing the script?

P.S. My dad's a mathematician, and he almost laughed out loud when he saw the problems Matt Damon was solving in *Good Will Hunting*. He said they should have just written gibberish on the chalkboards instead of easy math problems.

---

### Post by LaRoza on 2008-04-02
Perhaps there is a transcript of this?

---

### Post by Kingsley on 2008-04-02
Here's the movie script: [http://awards.universalpictures.com/pdf/breach.pdf](http://awards.universalpictures.com/pdf/breach.pdf)
[IMG]http://i37.photobucket.com/albums/e57/demasterk/Screenshot-5.png[/IMG]

I also had no clue what he was talking about in quite a few parts of the movie. He sure did sound knowledgeable though.

---

### Post by LaRoza on 2008-04-02
I am not familiar with some of those abbreviations, and Wikipedia didn't help.

The part about dynamic IP address to hide the network is stupid, not a security practice.

For a security LAN, you don't have any outside connections, especially for this subject.

It sounds like he is just trying to sound good. I envision him speaking quickly and confidently and somewhat smug, to hide the fact it is not really good information.

---

### Post by Calash on 2008-04-02
The abreviations are right, but it just does not fit together very well.  At least it seems they did some research.


Some reference of the terms

[http://www.ittc.ku.edu/workshops/spartan/1998/lyon.pdf](http://www.ittc.ku.edu/workshops/spartan/1998/lyon.pdf)
[http://en.wikipedia.org/wiki/Asynchronous_Transfer_Mode](http://en.wikipedia.org/wiki/Asynchronous_Transfer_Mode)

---

### Post by init1 on 2008-04-02
Yeah I remember red hat in that conversation.

---

### Post by DoorGunner on 2008-04-02
[http://networking.ittoolbox.com/groups/technical-functional/networkadmin-l/atm-vs-ethernet-386770](http://networking.ittoolbox.com/groups/technical-functional/networkadmin-l/atm-vs-ethernet-386770)

> There are many differences between ethernet and ATM. Ethernet is frame-based, ATM is cell-based with isochronous transmission. ATM is generally utilized in a WAN as opposed to a LAN. ATM is a more robust and powerful protocol used for backbones. ATM is connection-oriented setting up a PVC before data transmission which usually runs over fiber. ATM equipment is much more expensive. Many other differences as well. 

I have only had one bad experience with static addressing from cable. "Some one hacked into my windows box when i first got a computer. My hard drive started to spin out one day". So someone got in and i needed to do something about it. Hence a router. 

The way it was explained to me was is static addressing is on all the time. So its like having your porch lite on.  Dynamic addressing is only on when you dial in or actually use the computer to search out. That way it makes it that much harder for a cracker to know your there or even if an address is active or not. At least, I think thats what they are getting at. There is a lot i havent really looked into so take it with a grain of salt.

---

### Post by p_quarles on 2008-04-02
> **DoorGunner said:**
> The way it was explained to me was is static addressing is on all the time. So its like having your porch lite on.  Dynamic addressing is only on when you dial in or actually use the computer to search out. That way it makes it that much harder for a cracker to know your there or even if an address is active or not. At least, I think thats what they are getting at. There is a lot i havent really looked into so take it with a grain of salt.
That makes sense, and would mean that "dynamic" means something different than the way in which commercial ISPs use the term. In the sense you are describing, a dynamic IP address from your ISP would actually be a static address which has an expiring lease. A true dynamic address would acquire a new DHCP lease each and every time the connection was invoked. The network gateway itself, that is, would be working in a more interactice fashion. 

I only have experience with home networking, so this is very interesting to me.

---

### Post by koenn on 2008-04-02
> **Calash said:**
> The abreviations are right, but it just does not fit together very well.  At least it seems they did some research.


Some reference of the terms

[http://www.ittc.ku.edu/workshops/spartan/1998/lyon.pdf](http://www.ittc.ku.edu/workshops/spartan/1998/lyon.pdf)
[http://en.wikipedia.org/wiki/Asynchronous_Transfer_Mode](http://en.wikipedia.org/wiki/Asynchronous_Transfer_Mode)

ACS could possibly refer to Automated Cartreidge System, [http://www.webopedia.com/TERM/A/Automated_Cartridge_System.html](http://www.webopedia.com/TERM/A/Automated_Cartridge_System.html)
and of "low bandwith" is IT speak for "it takes forever to get your data", it kinda makes sense in the context. 

WAN is Wide Area Network, just like LAN is Local Area network. WANs used to be made up out of of leased copper peairs with modems at each end : slow and expensive. Moving to a "modern" data transmission / network protocol sounds sensible. 

"Ip routers troughout the building" sounds like he wants IP for his LAN. Everybody  does that these days. He doesn't need routers unless he's thinking separate networks / segments, not a bad idea.

It doesn't sound too stupid to me if you read it as a list of things you want changed, not implying that ACS has enything to do with IP routers or so. 
I've never heard of megabips (megabits ?) and I don't know what  A-B servers are, unleass the mean what is known in marketing as an "A" Brand. 

IMy guess: They consulted a network administrator / consultant, but they didn't understand all of it.

---

### Post by DoorGunner on 2008-04-02
I think incorporating multiple Ip routers throughout the building is refering to Battlestar Galactica when Lt Gaita created the multiple firewalls to keep the Cylon Virus from penatrating the network.... ;)

Dam those cylons



ok now ive gone to far..LOL

---

