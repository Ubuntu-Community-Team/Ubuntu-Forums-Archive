---
title: "Why is my Bandwidth Usage so High?"
date: 2008-12-17
forum: The Cafe
---

### Post by PRGUY85 on 2008-12-17
Hey:

I don't know where to post this so I hope the trusty Ubuntu community pulls through.  Recently, I received a letter from my internet cable company stating that I exceeded the new download bandwidth use of the servie, 40 GB.  Supposedly I used 100GB on download...which as you can see is pretty excessive.  Now, that was on a month where I only used the computer 2-3 hours a day, didn't download much music (2-3 CDs at the most) and downloaded 2-3 linux distros plus upgrades.  THe only other thing I did was watch 3 full Lost seasons on ABC.com with HD streaming.  My connection is shared with my family but they are not power users, just browse and check emails.  

So, I want to know what is giving me these elevated traffic numbers considering I am limiting my usage.  Is it streaming video?  Is it something else?

---

### Post by Icehuck on 2008-12-17
>  3 full Lost seasons

This right here was your usage.

---

### Post by PRGUY85 on 2008-12-17
> **Icehuck said:**
> This right here was your usage.


Was that an issue even if it was streaming?  I also thought that could be the culprit but the tech guys (which know ****) told me video streaming doesn't take that much bandwidth.

I watched 3 full seasons and my sister watched 1 1/2 .  Also, during the months where I started to do this, the bandwidth download rate went up the roof.

---

### Post by Tom--d on 2008-12-17
A HD 1 hour video is around 1GB? or more.

---

### Post by |{urse on 2008-12-17
2 questions.
1.Are you using wireless?
2.Is it unencrypted?

If you answered yes to these questions then someone is obviously using your connection (perfectly legal for them to do if you dont encrypt it). To confirm this install bmon

```
sudo apt-get install bmon
```

run it by typing 

```
bmon
```

if someone else is using your connection it would be prudent to type

```
who
```

just to make sure noone else is logged in your box (not likely, but just to be safe)

If this doesn't immediately answer your concerns try openin a second terminal and run 

```
top
```

watch and compare the terminal running bmon vs. the term running top, If you see a process that seems to be spiking your bandwidth try killing it with

```
sudo killall processname
```

happy hunting.

---

### Post by howefield on 2008-12-17
Definately the video streaming, especially at HD.

Try it, open your system monitor, and start streaming your video, on the resources tab, run it for some time and the the network history will tell you how much data you are transmitting and receiving, (usually isps count both ways, up and down towards your limit).

Run it for an hour (or whatever) and you can roughly work out what bandwidth your Lost epsiodes are taking.

---

### Post by howefield on 2008-12-17
> **|{urse said:**
> If you answered yes to these questions then someone is obviously using your connection (perfectly legal for them to do if you dont encrypt it).

Where would that be legal ?

---

### Post by PRGUY85 on 2008-12-17
Well, I am currently on a Mac and only my laptop uses Ubuntu so I can't use Linux instructions.  My network has wireless as well and has a password which I believe to be pretty secure and people around me are old folks which I seriously doubt know much about cracking codes.

I can try the tip about monitoring how much a Lost episode can take.  The download rate went up the roof when I began watching so much LEGAL internet episodes of Lost and The Office so that could be it.  Currently I have used so far 36GB of download bandwidth.  I have watched 8-13 Lost episodes at the beginning of the month plus some episodes my sister also watched on her own.  

I now don't dare to download any PS3 demos...

---

### Post by Dr Small on 2008-12-17
> **howefield said:**
> Where would that be legal ?
As he said, any place that does not encrypt their connection.

---

### Post by PRGUY85 on 2008-12-17
Encryption doesn't mean putting a password to the wireless network right?

---

### Post by howefield on 2008-12-17
> **Dr Small said:**
> As he said, any place that does not encrypt their connection.

FUD

:lolflag::lolflag:

Let's see what |{urse meant.

---

### Post by gletob on 2008-12-17
> **howefield said:**
> Where would that be legal ?

Not where I live.  It's one of those things that's illegal but unenforced.

---

### Post by blazercist on 2008-12-17
Yea HD video are you enemy, that and a crappy bandwidth limit.  Depending on the format HD video can eat as much as 4GB per hour or possibly more.

---

### Post by Icehuck on 2008-12-17
> **PRGUY85 said:**
> Encryption doesn't mean putting a password to the wireless network right?

If you are using a password you have either WPA/WEP setup , and you are encrypting your wireless traffic.

---

### Post by |{urse on 2008-12-17
the "password" is a hash key to an algorythm that encrypts the wireless signal/transmissions, and yes, if your wireless isnt encrypted then it's free for all to use (not illegal)

---

### Post by |{urse on 2008-12-17
> **gletob said:**
> Not where I live.  It's one of those things that's illegal but unenforced.

You live in the US, yes it's legal.

---

### Post by PRGUY85 on 2008-12-17
My main video streaming sites are:

1) Youtube
2) Hulu
3) ABc.com player with HD streaming (my connection allows for max settings)

---

### Post by smartboyathome on 2008-12-17
You better turn off HD streaming and lower quality on ABC (if you can) if you want your 40GBs to last. It uses a ton of bandwidth (as others have said).

---

### Post by PRGUY85 on 2008-12-17
Well no more Internet Lost streaming for me then.  On September, when I did not watch Lost, my download rate was 36GB.  It's still high but I am more controlled now based on this.  

I only have 4GB to last me and my family the remainder of the month, suggestions? haha.

---

### Post by ajcham on 2008-12-17
> **PRGUY85 said:**
> 
I only have 4GB to last me and my family the remainder of the month, suggestions?

Board games?

---

### Post by ssam on 2008-12-17
i am not a lawyer but i've met law students :-)

it would be very interesting to see a proper testing in court of using an unencrypted wireless network. in the UK the law that you might be breaking is about unauthorised use of computer or network. so i think in court you would need to prove that you were given permission.

one could argue that the access point was advertising a service, by broadcasting its SSID. you computer then sends a message asking for details of the network. the access point then goes, 'here you are, here is all the information you need to connect to the internet'. if you could argue that this is permission to use the network, then i dont know what law you are breaking.

---

### Post by |{urse on 2008-12-17
If the internet is deemed an unauthorized computer network then i'd say you may have something there.

---

### Post by smartboyathome on 2008-12-17
> **PRGUY85 said:**
> I only have 4GB to last me and my family the remainder of the month, suggestions? haha.

I know they're ancient but... Video rental stores? ;)

---

### Post by PRGUY85 on 2008-12-17
Don't worry I'm not planning on watching any video streaming for the remainder of the month.  I wanted to download a PS3 demo but I guess that's out of the question...

---

### Post by PRGUY85 on 2008-12-17
Is there any way to limit the bandwidth use to a set number per week or something?

---

### Post by Dr Small on 2008-12-17
> **howefield said:**
> FUD

:lolflag::lolflag:

Let's see what |{urse meant.
Excuse me?
Where I live, connecting to an unencrypted wireless network is not illegal, so long as the owner does not forbid you. I can sit on his back porch and use his wireless internet unless he says otherwise, since his connection is not encrypted.

Breaching an encrypted connection is considered illegal, because you are circumventing a form of authentication to the network.

If sending and receiving unencrypted frequencies is illegal, than we all are guilty of violating laws, as we speak and hear on a regular basis. (Speech and noise *are* in the frequency spectrum.)

---

### Post by |{urse on 2008-12-17
>  Originally Posted by PRGUY85  View Post
I only have 4GB to last me and my family the remainder of the month, suggestions? haha.

Lol! You could see if anyone around you has unencrypted wireless.:-\"

---

### Post by Azatos on 2008-12-17
> **PRGUY85 said:**
> I only have 4GB to last me and my family the remainder of the month, suggestions? haha.
I use **4GB** in around a ~2-4hours god bless America and there unlimited bandwith :)

---

### Post by |{urse on 2008-12-17
Bandwidth limitation is generally decided by isp/service plan not US government.

---

### Post by PRGUY85 on 2008-12-17
> **|{urse said:**
> Bandwidth limitation is generally decided by isp/service plan not US government.

Exactly.

---

### Post by Dr Small on 2008-12-17
> **Azatos said:**
> I use **4GB** in around a ~2-4hours god bless America and there unlimited bandwith :)
Unfortunately,  not every ISP is so generous...

---

### Post by Azatos on 2008-12-17
> **Dr Small said:**
> Unfortunately,  not every ISP is so generous...

Yeah, Frontier another I.S.P in my town had a 5GB monthly limit not sure if they still have it as it was 6 months ago.

---

### Post by |{urse on 2008-12-17
Lol @ this thread.

---

### Post by Grant A. on 2008-12-17
> **|{urse said:**
> 2 questions.
If you answered yes to these questions then someone is obviously using your connection (perfectly legal for them to do if you dont encrypt it). 

A law was passed in the United States recently making it illegal to use someone else's internet without permission. They consider it akin to cable siphoning. I would recommend using a WEP code.

[http://blogs.pcworld.com/techlog/archives/000767.html]("http://blogs.pcworld.com/techlog/archives/000767.html")
[http://www.geekwithlaptop.com/man-arrested-for-using-free-wi-fi/]("http://www.geekwithlaptop.com/man-arrested-for-using-free-wi-fi/")

---

### Post by ajcham on 2008-12-18
> **Grant A. said:**
> I would recommend using a WEP code.

NO! While this may detract a few (maybe even most) potential leeches, it is easily broken by someone with a little more know-how. Please use WPA2.

---

### Post by madverb on 2008-12-18
Just wondering why this post has gone into a thread about wireless security and the legalities of accessing insecure wireless network considering it is about a guy that doesn't understand what downloading is?
How do people not understand that watching VIDEO over the internet is going to use a lot of their download quota? It's video sent via bits! There is a lot of bits in video and audio to send for high quality video.
Many people also can't seem to grasp that accessing anything that isn't actually locally on their computer (like this forum for example) IS DOWNLOADING.
Thank you for your time.
RANT OVER AND OUT

---

### Post by |{urse on 2008-12-18
> **Grant A. said:**
> A law was passed in the United States recently making it illegal to use someone else's internet without permission. They consider it akin to cable siphoning. I would recommend using a WEP code.

[http://blogs.pcworld.com/techlog/archives/000767.html]("http://blogs.pcworld.com/techlog/archives/000767.html")
[http://www.geekwithlaptop.com/man-arrested-for-using-free-wi-fi/]("http://www.geekwithlaptop.com/man-arrested-for-using-free-wi-fi/")

I am speechless. Does this mean a wifi signal strength indicator is contraband now?

---

### Post by |{urse on 2008-12-18
> **madverb said:**
> Just wondering why this post has gone into a thread about wireless security and the legalities of accessing insecure wireless network considering it is about a guy that doesn't understand what downloading is?
How do people not understand that watching VIDEO over the internet is going to use a lot of their download quota? It's video sent via bits! There is a lot of bits in video and audio to send for high quality video.
Many people also can't seem to grasp that accessing anything that isn't actually locally on their computer (like this forum for example) IS DOWNLOADING.
Thank you for your time.
RANT OVER AND OUT

Probably no-one read this. I know I didn't.

---

