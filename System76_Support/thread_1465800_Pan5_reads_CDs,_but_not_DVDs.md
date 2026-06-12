---
title: "Pan5 reads CDs, but not DVDs"
date: 2010-04-29
forum: System76 Support
---

### Post by Iteria on 2010-04-29
I have Pangolin Performance (Pan 5) and recently my cd/dvd drive stopped reading DVDs. It still reads CDs, but not DVDs.

I don't know what to do. It just suddenly stopped. It happened sometime after it burned a DVD if that helps. The computer is about 9 months old, so I don't think that wear and tear is the problem, especially since I don't use my optical drive very often.

---

### Post by thomasaaron on 2010-04-30
What happens when you put a DVD in? Does it throw an error? Does it spin up? Does it put an icon on your desktop?

---

### Post by Iteria on 2010-04-30
It spins up, but then does nothing. There's no error message. The disk icon doesn't appear on the desktop and the system doesn't in general acknowledge that I placed anything in the drive. 

I will note that I just noticed that the ... face plate, I guess I would call it, of the cd drive is loose. It sees like the clasp or whatever holding it has come loose from me tugging the drive open completely when I eject something. I don't know if this would have an effect since the drive still acknowledges and plays CDs and ejects properly when the eject button on the drive is pressed.

---

### Post by msrinath80 on 2010-04-30
I would be very interested in finding out how this situation pans out. Recently, I encountered the *exact* same problem on a friend's Sony Vaio VGN FE870E. The unit refused to read any DVDs both in Windows and GNU/Linux. Our solution was to remove the base Matshita optical unit and replace it with a SONY from an otherwise toasted Dell Inspiron 600M.

---

### Post by msrinath80 on 2010-04-30
I did some searching:

What follows are excerpts from a google search:

"... A DVD drive has one lens, but to read a DVD or a CD its laser focus are different.

According to how stuff works, when a drive is reading a CD its laser light will have a larger wave length of 780nm as compared to 640nm when reading a DVD.

As for Blu-Ray drives it has 2 lens, one red and the other violet.
Red is for CD and DVDs and the violet is for Blu-Ray as it can achieve a even shorter wave length of 405nm (from wiki) thus compacting more data on a single disc.

Also you could be right as your DVD may not be compatible with certain DVD-R disc..."


And in addition, the following posts seem to suggest that cleaning the lens or updating the firmware solves the problem. You may however want to wait for Tom (from System76) to chime in before you do anything!

[1] [http://www.computing.net/answers/hardware/drive-reads-cd-but-not-dvd/59126.html](http://www.computing.net/answers/hardware/drive-reads-cd-but-not-dvd/59126.html)

[2] [http://forums.techguy.org/hardware/633141-dvd-player-not-working-plays.html](http://forums.techguy.org/hardware/633141-dvd-player-not-working-plays.html)

This post on the other hand suggests that a firmware update resolves the issue:

[3] [http://www.techspot.com/vb/topic32758.html](http://www.techspot.com/vb/topic32758.html)

---

### Post by Iteria on 2010-04-30
I know the drive is compatible with the DVDs I bought, because it has read those type DVDs before. I'm wary about trying to clean the lens, mostly because I don't know if it will involve me removing the drive to do so and I hate taking laptops apart. I saw the firmware one, but... my computer is running Ubuntu, so I'm not really sure how to go about doing that, nor do I understand why that would suddenly become an issue, but my knowledge about such things is a bit lacking, so firmware could be  possibility.

I guess I will wait for a System 76 representative's opinion on the matter.

---

### Post by miniyak on 2010-05-02
this is probably unrelated because my panp5 will still recognizes the dvd 

A couple of weeks ago I tried to play Monty Python and the Holy Grail for a group of friends. Couldn't get any decent video...even after booting from Mint, just a bunch of garble... Try explaining why a dvd wont play in a dvd player to a bunch of non technical friends then try to reinstall all the relevant packages at the same time.... it was embarrassing really, not to mention the disappointment of missing out on crude quotes such as "bring out your dead" and "your mother was a hamster"    

brasaro is also only recognizing cds as being only 5 or 6mbs if anyone knows anything about that. (will still write 700mb iso though)

---

### Post by miniyak on 2010-05-02
> **Iteria said:**
> I know the drive is compatible with the DVDs I bought, because it has read those type DVDs before. I'm wary about trying to clean the lens, mostly because I don't know if it will involve me removing the drive to do so and I hate taking laptops apart. I saw the firmware one, but... my computer is running Ubuntu, so I'm not really sure how to go about doing that, nor do I understand why that would suddenly become an issue, but my knowledge about such things is a bit lacking, so firmware could be  possibility.

I guess I will wait for a System 76 representative's opinion on the matter.

Which version of ubuntu are you using itiria?

I have and external usb dvd drive which makes trouble shooting a little more easy, allowing me to narrow my issue to being a software one, but you can see if your having a hardware issue by trying a different OS. Now to do this you only need to use a live cd distro that can run from ram such as puppy linux, the next task would be to find a version of puppy that is capable of play dvds right of the bat (there are many versions of puppy) Once puppy is loaded up you can pop the live cd out without ever having to install to disk.

now thats just one thing i would do off the top of my head, im sure there is a bash command or something that with tell you if there are errors in communicating with drive. im just unaware of them.

---

### Post by Iteria on 2010-05-02
I'm running Ubuntu 9.10. I haven't upgraded to 10.04 yet because of the wireless issues.

I don't think the problem is software based because I can't get my computer to boot from DVD, but it boots from CD happily. It was a terrible thing to learn after I cleared all my partitions in preparation for reinstalls (I had borked my Windows install accidentally and I was going to give opensuse a try since ubuntu 10.04 wasn't looking viable and I was doing a reinstall anyway).

I still think it's incredibly strange that it stopped since I had put in a DVD, Ubuntu acknowledged it in the normal way, then burned a perfectly good opensuse install disk (I checked it in another computer). Then right after I rebooted cleared the partitions using gparted on a CD, I popped in my windows 7 DVD and it wouldn't boot. I popped in my Opensuse DVD, same thing. I popped in my Ubuntu 9.10 DVD, same thing. My only saving grace is I had a friend with 9.10 on a CD I could use.

To me, it doesn't make sense it that it's a software problem, since it isn't just contained within the OS. On that same note... I'm not sure how a hardware problem this severe could occur with no warnings on such a new machine.

I'm not really familiar with Puppy Linux, but I could give it a shot. It will be a few days because I don't own any blank CDs and my finals start this monday.

---

### Post by miniyak on 2010-05-02
i had just suggested puppy as one way of narrowing down to either a hardware or software issue. It seems things have been narrowed down to hardware though. 

Puppy is sorta a novel lightweight linux disto worth trying out for fun particularly on older computers. Its incredibly fast/responsive once you booted in. The downside is that its difficult to set things up, plus puppy uses very basic applications(in the official release at least).

 Odd that it could write to dvd but now its unable to read them. I wonder if something happen between now and the time you wrote the opensuse disc, can it still write?

---

### Post by Iteria on 2010-05-02
Huh... Here's the fascinating part. It acknowledges blank DVDs. After that I popped in the movie I watched before and it acknowledges that. I thought it might be that it just doesn't like OSs, so I tried a data DVD I burned a long time ago, but that wasn't acknowledged. The data was burned by a different computer, so I know it's not just that it doesn't like the DVDs that it itself creates.

So... I guess I need to ask: What's the difference between a blank or commercial movie DVD and a burned data or ISO DVD?

EDIT: sorry I realized I didn't answer you question. Yes it can still burn DVDs

---

### Post by thomasaaron on 2010-05-03
If you can burn *data* to a DVD, but then you can't read it, you have a bad DVD drive. Please contact me at support...at...system76...dot...com for a resolution.

---

