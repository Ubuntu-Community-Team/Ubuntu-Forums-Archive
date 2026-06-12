---
title: "Internet DJ console doesnt' have mp3 encode and SErver Shoucast doesn't conect"
date: 2008-09-13
forum: Ubuntu Studio
---

### Post by rockstar1 on 2008-09-13
Hello. I have and old pc with Xubuntu. I read about Internet DJ console because I have to use this computer for streaming my radio.
I download and install. But I can conect the IDJC to the server streaming. And the Encode is only OGG.
So how can I put mp3 and server to shoutcast?

PD: Saludos. Sorry for my English

---

### Post by wowbuts5 on 2008-09-14
It helps to be reminded of positive thoughts and positive attitudes. Get a small book of positive, inspirational thoughts and keep it by your desk. Read one or two thoughts each day. Cheap [world of warcraft gold](http://veryge.com/) presents many different monsters to challenge you in battle. The[http://veryge.com](http://veryge.com) is one of the most experiences MMORPG-Secondary market service (like wow gold) provider on the web. We found in year 2004 . Our missions are serving our customer with all our hearts and provide qualified service with attractive price.You can buy [wow gold](http://veryge.com/) and [ffxi gil](http://veryge.com/) here,we supply [wow power leveling](http://only4game.com/) for you.enjoy it!

---

### Post by Dave-ie on 2008-09-14
did you make sure mp3 is selected in the server window and the right details are correct, also is shotcast configured right?

---

### Post by Steveway on 2008-09-14
I told you before what to do:
> You need to compile it yourself with support for restricted formats like mp3.
Check the official site of IDJC for informations: [http://www.onlymeok.nildram.co.uk](http://www.onlymeok.nildram.co.uk)

---

### Post by rockstar1 on 2008-09-14
Well I can't put mp3 the only option that I can put is ogg.
And when I put Shoucast The bottom "Server connect" not works.

PD: Saludos. Sorry for my English

---

### Post by rockstar1 on 2008-09-14
Well. Before I compile IDJC. I search all of package that the program need. But when I found libshout in repositories. The description is this:

> MP3/Ogg Vorbis broadcast streaming library 
A library for communicating with and sending data to Icecast and Icecast 2
streaming audio servers.  It handles the socket connection, the timing of
the data transmission, and prevents bad data from getting to the server.

But never say **sending data to Shoutcast library for communicating**. That could be the problem?

---

### Post by Stochastic on 2008-09-14
Shoutcast is a trademark and can't be used in the description of a GPL'ed library.  In general, if someone with as much experience as Steveway suggests you'll need to do action x and he backs it up with official documentation then you shouldn't have to be told three times (be weary of executing commands you don't understand though - there are malicious people out there).

Edit: wait, rockstar1 only has 3 posts to his name right now and all three are in this thread; how could Steveway have "told [him] before"?  *-- Stochastic scratches his head on this one*

Edit #2: ahh, I see you've both been visiting each other's public profile, now I see.

---

### Post by rockstar1 on 2008-09-15
Yes, I use ubuntu for 3 years. But I allways posted in Spanish Forums. 
But now I can't found the information in my native language.

PD: Saludos

---

### Post by Steveway on 2008-09-15
A little correction:
As Stephen Fairchild told me the official site of IDJC is now avaiable under this adress: [http://web.bethere.co.uk/idjc](http://web.bethere.co.uk/idjc)
Thanks Stephen.

---

### Post by rockstar1 on 2008-09-22
Well. I finally install IDJC with mp3 and shoutcast.
But now when I put mp3 this message appers:
" Mp3 streaming is unavaliable and as a consequence Shoutcast is also disableb".
I was read in other forums. The problem happend when I compile and install.

> ./configure --enable-tooltips=yes

make

sudo make install

How can I avaliable mp3 streaming?

PD: Saludos, sorry for my english

---

### Post by rockstar1 on 2008-09-22
Well, Finally I install IDJC with shoutcast and mp3.
But now I have another problem!!
I put and connect idjc to my private server. 
[http://64.56.65.43:8110/]("http://64.56.65.43:8110/")

My server is on-line. But I can't heart any music. If you try to listen my radio station, you will can't.

¿Anybody have any idea?:confused:

PD: Saludos :([-o<:???:

---

### Post by StephenF on 2008-09-22
> **rockstar1 said:**
> My server is on-line. But I can't heart any music. If you try to listen my radio station, you will can't.

¿Anybody have any idea?:confused:

Is this a freeformat stream? I'm getting garbled audio with xine. Please post a screenshot of the server window (fully expanded) so we can see what you are doing wrong.

Edit: Still waiting.

---

### Post by mackay12 on 2008-09-24
I have same problem and compiling the way it says doesn't work. I type make and nothing happens same with make install. Also when I download throgh console or add remove apps, it installs but the Connect Server button is un pressable when on shoutcast. And I have all needed things for mp3 thing, it says to edit a file in it to alow for mp3 but I can't edit says premission denied.

---

### Post by StephenF on 2008-09-24
> **mackay12 said:**
> I have same problem and compiling the way it says doesn't work. I type make and nothing happens same with make install.
This link provides Ubuntu specific instructions.
[http://ubuntuforums.org/showthread.php?p=5200135&highlight=idjc#post5200135](http://ubuntuforums.org/showthread.php?p=5200135&highlight=idjc#post5200135)

---

