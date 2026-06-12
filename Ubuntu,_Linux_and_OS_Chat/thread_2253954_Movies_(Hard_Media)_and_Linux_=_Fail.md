---
title: "Movies (Hard Media) and Linux = Fail?"
date: 2014-11-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Kurt_Alan on 2014-11-23
Now that I've converted my friend to Ubuntu, he wants to jump back to Windows for one reason only: He cannot play movies (hard copy) on Ubuntu. Other than this, he STRONGLY prefers Linux.

Which would be the path of least resistance to follow:

1. Configure Linux to play movies (in spite of DRM).
2. Dual Boot Windows and Ubuntu
3. Run a movie in Windows, virtually, in Ubuntu ?

I'm guessing 2 as best because I don't know if 3 is possible. I think that #1 would be the best solution but the most complicated. What's your opinion?

---

### Post by leclerc65 on 2014-11-23
Tell him to try LinuxMint (I recommend Mint 17.1 Mate, version containing codecs).

---

### Post by deadflowr on 2014-11-23
or 4) Buy the fluendo dvd player from the software center.
It ain't cheap, but I believe it is 100% legal, and not in a gray area like libdvdcss.

---

### Post by kevdog on 2014-11-23
I'd just install the libdvdcss packages.  Honestly that's my opinion.  I'm not sure the legality of it all.  It's always worked for me.

---

### Post by cariboo on 2014-11-23
I think one of the reason many people use Ubuntu, is because it is free. as kevdog suggested, libdvdcss is free, and depending on where live legal. I've used it almost from it's release, and so far I haven't found a dvd it won't play. I also recently found a way to play Blu-ray using VLC and makemkv.

---

### Post by craig10x on 2014-11-24
With libdvdcss installed, you can play any encrypted movie with vlc player...I assume we aren't talking about blurays, though...not sure about those as i never played one on the computer...

---

### Post by coldraven on 2014-11-24
I would go for Option 1
I always thought that the region locking of DVDs was stupid. If i want to buy a DVD from another country why should I have to jump through hoops in order to watch it.
The global corporations want to be able to do business everywhere but they do not want us to have the same rights :(

---

### Post by /ADM on 2014-11-24
It depends where you are living.

If you are living in USA, South-Korea, Japan then using libdvdcss is illegal due to these countries allowing patents to apply to software.

If you live in Latin America, the European Union or other Asian countries then libdvdcss is legal due to these countries/areas not allowing patents to apply to software.

It's why Linux Mint is legally allowed to offer the codec version, it's based in Ireland and patents don't apply to software (it's in the EU).

---

### Post by SagaciousKJB on 2014-11-24
> **/ADM said:**
> It depends where you are living.

If you are living in USA, South-Korea, Japan then using libdvdcss is illegal due to these countries allowing patents to apply to software.

If you live in Latin America, the European Union or other Asian countries then libdvdcss is legal due to these countries/areas not allowing patents to apply to software.

It's why Linux Mint is legally allowed to offer the codec version, it's based in Ireland and patents don't apply to software (it's in the EU).

And THEN it depends on if you care about it being illegal.  I'm an American, and I use libdvdcss.  Come and and get me MPAA

But if the legality concerns you, you COULD run Windows in a "virtual machine" using VirtualBox or VMWare.

---

### Post by mc4man on 2014-11-24
There has never been a challenge in the US to libdvdcss (there was to decss in NY state supreme court). Technically it does fall under dmca but no one cares about it's use for end users, not before, now or ever.
If one has some personal moral issues here then by all means use a licensed player, if not then don't  & nothing to be concerned about at all.

---

### Post by SeijiSensei on 2014-11-24
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Dragonbite on 2014-11-25
Did you try the instructions here? [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")?

I was trying to play a DVD on my desktop the other night, it didn't work, followed these instructions and viola! I spent the next couple hours watching the movie!  This was on Ubuntu 12.04.

Otherwise, there is nothing wrong with using Fluendo.

---

### Post by monkeybrain20122 on 2014-11-25
+ 1 to libdvdcss2. I have not had any problem playing dvd with it. However, I think there is one brand of DVD drive which enforces DRM at the hardware level so with that you may be out of luck.

---

### Post by monkeybrain20122 on 2014-11-25
> **leclerc65 said:**
> Tell him to try LinuxMint (I recommend Mint 17.1 Mate, version containing codecs).

Yeah what magic is in Mint that you cannot get in Ubuntu with 
```
sudo apt-get install ubuntu-restricted-extras
```?

And what does Mate have to do with whether you can play multimedia?

---

### Post by mc4man on 2014-11-25
> **monkeybrain20122 said:**
>  However, I think there is one brand of DVD drive which enforces DRM at the hardware level so with that you may be out of luck.
You may be referring to Matshita drives (usually their laptop dvices.
They enforce region coding so one can't play dvd's from any region other than the one the drive is set to,

---

### Post by leclerc65 on 2014-11-25
> **monkeybrain20122 said:**
> Yeah what magic is in Mint that you cannot get in Ubuntu with 
```
sudo apt-get install ubuntu-restricted-extras
```?

And what does Mate have to do with whether you can play multimedia?
Nothing, but I like Mint Mate !

---

### Post by Kurt_Alan on 2014-12-22
I just installed Linux Mint, 17.1 MATE.  After no configuration, my machine played "out of the box" a DVD movie I had bought in Viet Nam.  I played it via the pre-installed VLC media player.  I also noticed during my first update that Adobe Flash was installed.

So my buddy will be happy about this and now stay with Linux.

Marked "SOLVED" by OP.

---

