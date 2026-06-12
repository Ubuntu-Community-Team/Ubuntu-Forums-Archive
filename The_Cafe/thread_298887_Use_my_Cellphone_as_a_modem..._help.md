---
title: "Use my Cellphone as a modem... help?"
date: 2006-11-13
forum: The Cafe
---

### Post by schurtek on 2006-11-13
I have a Nokia 6020 with GPRS. Prevoiusly I used it when I ran Windows... as a modem. I connected it to my PC with the USB cable CA-42 and then created a Dialup Connection to use USB Phone Device as the modem and used the number my Service Provider gave me.

Now in Ubuntu, when I connect it, my Device Manager sees that I connected a USB device... but it won't let me create a dial up connection using it... it's not listed as a modem... is there any way I can get Ubuntu to see it as a modem?

Thanx...

---

### Post by mips on 2006-11-13
This topic has been covered a few times in the Networking forum, do a search for Vodafone, GPRS & 3G.

There are also guides in the [www.mybroadband.co.za](www.mybroadband.co.za) linux section.

---

### Post by schurtek on 2006-11-14
I could only find two topics... and they were relating to 3G data cards.... my problem is with a USB cable and a Nokia 6020 for GPRS... secondly... I check MyBroadband.co.za and they don't have a linux section...

Ta...

Have also posted in the Network section... didn't realise... sorry about that... this post can be closed now and we can discuss this in that section...

---

### Post by ed_agamemnon on 2006-11-14
there are some programs in the repos that i used for my nokia 3210 (or 3215, i forget the version numbers) - i can't remember their names either: try searching synaptic for 'nokia'.

---

### Post by schurtek on 2006-11-15
AAARRRRGGGGHHHH!!!

Will have to wait till next week until I get home... can't access internet with here in Joburg with out my phone... and no internet cafe will let me plug my Laptop in... I've tried...

Well I hope that it will work... thanks...

If anyone else has any ideas... please let me know...

When I do get it working... I will post a full TUT so others can get it right first time...

---

### Post by mips on 2006-11-15
> **schurtek said:**
> I check MyBroadband.co.za and they don't have a linux section...


Apologies, have a look under forum for your Service Provider. Maybe also ask there, someone might be in the know and provide you a link or something. Just ensure You use the word Linux & Phone model in the title.

---

### Post by schurtek on 2006-11-16
ha... mips you need to come to sa for a holiday so you can empathise with my frustration. My service providor doesn't have a forum on their website... their technical call centre doesn't even know what edge is... they told me to take out a three year contract for 3G as this is the only way you can connect to the internet via the GSM network (and apparantly, according to Vodacom here in South Africa - there is no way under gods sun you can access the internet with Linux - the guy was very upset when I burst out laughing - I told him that there is no way under gods sun you should access the internet with Windows and then I hung up - at least I got a laugh out of this ordeal)... my attitude towards SA service providers is very cynical... which is why my company get's most of it's services from India, US, HK, UK and EU.

I was playing with it again this morning...

I noticed that serial modems come up as ttyS0 for COM1 and ttyS1 for COM2. I tried to get my phone dialing through IR on COM2, no luck... but the cable is the better option as if I move my laptop or phone I am still connected. So I did a modprobe for USB and that is when my Laptop started picking up the USB cable as a USB UART ADAPTER. So I got that far... but I still can't get my Network Tool to let me see it as a port (ttyUSB0). It's actually connected to Etc/Device/USB/2/2

Once I can see it as a port, then according to nokia I just use it as a standard modem. Dial *99# and if opens a tunnel to my Service Providers Internet Backbone. This has so far worked in Windows 2000, XP and MacOS X... but I want to use Ubuntu... 

Haha... I know we gonna get this one... I know we gonna win... cos we don't have to spend four hours on the phone to Microsnot talking to sum ignot in France who can't speak english and has never head of GSM... this happened to me once...

I get to talk to normal human beings who use linus for human beings....


UBUNTU ROCKS!!!

---

### Post by mips on 2006-11-16
Hey, I am sitting in this shitehole called SA.

I'm sorry my message was not that well written. I meant the Vodacom forum on the MyBroadband site, apologies for the confusion.
[http://mybroadband.co.za/vb/forumdisplay.php?f=103](http://mybroadband.co.za/vb/forumdisplay.php?f=103)

Tech support in general is a joke, the people answering the phones know jack **** to say the least. They have procedural guides for windows & mac, nothing for Linux or any other os for that matter. Monkey see, monkey do...

> **schurtek said:**
> ha... mips you need to come to sa for a holiday so you can empathise with my frustration. My service providor doesn't have a forum on their website... their technical call centre doesn't even know what edge is... they told me to take out a three year contract for 3G as this is the only way you can connect to the internet via the GSM network (and apparantly, according to Vodacom here in South Africa - there is no way under gods sun you can access the internet with Linux - the guy was very upset when I burst out laughing - I told him that there is no way under gods sun you should access the internet with Windows and then I hung up - at least I got a laugh out of this ordeal)... my attitude towards SA service providers is very cynical... which is why my company get's most of it's services from India, US, HK, UK and EU.

I was playing with it again this morning...

I noticed that serial modems come up as ttyS0 for COM1 and ttyS1 for COM2. I tried to get my phone dialing through IR on COM2, no luck... but the cable is the better option as if I move my laptop or phone I am still connected. So I did a modprobe for USB and that is when my Laptop started picking up the USB cable as a USB UART ADAPTER. So I got that far... but I still can't get my Network Tool to let me see it as a port (ttyUSB0). It's actually connected to Etc/Device/USB/2/2

Once I can see it as a port, then according to nokia I just use it as a standard modem. Dial *99# and if opens a tunnel to my Service Providers Internet Backbone. This has so far worked in Windows 2000, XP and MacOS X... but I want to use Ubuntu... 

Haha... I know we gonna get this one... I know we gonna win... cos we don't have to spend four hours on the phone to Microsnot talking to sum ignot in France who can't speak english and has never head of GSM... this happened to me once...

I get to talk to normal human beings who use linus for human beings....


UBUNTU ROCKS!!!

---

### Post by lisati on 2009-11-28
> **mips said:**
> 
Tech support in general is a joke, the people answering the phones know jack **** to say the least. They have procedural guides for windows & mac, nothing for Linux or any other os for that matter. Monkey see, monkey do...

My sister was telling me about some of the hassles she and her husband were having setting up a new modem using a laptop running Windows 98 in a rural part of New Zealand. After a rather long and frustrating time they were on the point of giving up and asked for help reverting the settings back to how they were before. The person at the call centre made some comment about not supporting Windows 98. Why couldn't the help desk say so at the beginning, before their system was effectively in an unusable state? I think they finally got things figured out.

---

### Post by cariboo on 2009-11-28
There are plenty of threads in [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") that answer the question. Technology has changed quite a bit since this thread was started. Closed.

---

