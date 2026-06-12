---
title: "Opinions on this laptop."
date: 2006-10-17
forum: The Cafe
---

### Post by theturtlemoves on 2006-10-17
So I'm thinking of buying a new laptop, and I've had friends who have this laptop and really like it.

[http://www.newegg.com/Product/Product.asp?Item=N82E16834115246](http://www.newegg.com/Product/Product.asp?Item=N82E16834115246)

However, it has one crucial flaw: It has an ATI Mobility x1800 video card. Now, I don't intend to do a lot of heavy gaming under linux (I'll dual boot for most of my gaming) but I would like to be able to play things like Enemy Territory and stuff with decent graphical quality and speed, and also use AIGLX/XGL. 

I've heard a lot of mixed reviews about the ATI frglx driver, and I was wondering what the consensus is. I've heard that "the drivers are improving all the time, and you won't have any problems", to "the ATI drivers suck and will not work."

What do you guys think? Especially people with recent experience on this card or other ATI cards.

Thanks!

---

### Post by chaosgeisterchen on 2006-10-17
I would suggest you go for a notebook with Intel integrated graphics as you won't do gaming on it.

pros are the open source driver, longer lasting batteries and lower overall price.

---

### Post by John.Michael.Kane on 2006-10-17
The ati gpu might be a pain to get going,however.It can be done. The cardreader may also be an issue if the chip that runs it is not supported. 

Can any of your friends let you use an ubuntu live cd to see what works,and what does not work?

---

### Post by theturtlemoves on 2006-10-17
> **SD-Plissken said:**
> The ati gpu might be a pain to get going,however.It can be done. The cardreader may also be an issue if the chip that runs it is not supported. 

Can any of your friends let you use an ubuntu live cd to see what works,and what does not work?

Will the live-cd let me test the 3D driver? I thought I would have to do an install for that. Also, the card-reader is not too much of an issue.

> **chaosgeisterchen said:**
> I would suggest you go for a notebook with Intel integrated graphics as you won't do gaming on it.

pros are the open source driver, longer lasting batteries and lower overall price.


I will be gaming, just not a lot under Linux. I intend to game under Windows.

---

### Post by matthew on 2006-10-17
I think the laptop looks great. I don't have that particular ATI card, mine is about 2 years old now. The one in my laptop is an ATI Mobility Radeon 9700 (128Mb), so my experience shouldn't be used as an absolute statement on whether the card in the laptop you are looking at will work or not, but I can give you my experiences.

With Hoary (5.04) I got the fglrx driver to install after a lot of work. It was adequate, but not great.

With Breezy (5.10) the fglrx installation was much easier and the edition from the repos worked pretty well.

With Dapper (6.04) the fglrx driver from the repos installed easily and works great. I can play all the 3D games I want with excellent results (eg. Scorched3D, Tremulous, etc.). I used to hesitate to recommend ATI's stuff due to driver quality. Their drivers still aren't perfect, but they work well enough now that I am willing to tell people (who aren't concerned about the openness issue) that the proprietary, binary fglrx drivers work quite well and I'm satisfied with them.

This wiki page is one you will want to read: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I have used the first method it recommends for driver installation with great success.

---

### Post by chaosgeisterchen on 2006-10-17
Okay, if you're gaming GMA950 could be a bit lousy, I agree.

The graphics card will certainly work, but AIGLX is not supported yet AFAIK.

---

### Post by John.Michael.Kane on 2006-10-17
theturtlemoves the ati card should work. what you would use the live cd to check is that the network/wifi sound bluetooth modem IEEE 1394 are supported.

---

### Post by chaosgeisterchen on 2006-10-17
I can only second that.. live CDs are always a good thing. Never ever buy hardware you haven't tested and proved working.

---

### Post by theturtlemoves on 2006-10-17
I used a 6.06 live CD on it, and everything seemed to work. The only kicker left is the graphics card, but I'm leaning towards getting it right now. 

Anyone else? ATI Mobility x1800 experiences?

---

### Post by John.Michael.Kane on 2006-10-17
theturtlemoves the ati card should work. what most user's here have been saying is that setting  up ati cards can be a pain sometimes.

---

