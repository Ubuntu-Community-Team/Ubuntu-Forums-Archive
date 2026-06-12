---
title: "Wife wants to keep Windows but I want Ubuntu for her"
date: 2014-03-13
forum: Virtualisation
---

### Post by Joe_Johnston on 2014-03-13
Hello All,

I have been wanting to make my wife's desktop an Ubuntu machine but she really likes her Windows and wants to stick with it. What I want to know is, is it possible to put Ubuntu on the machine and run her Windows 8 in Virtualbox so we can have the best of both worlds? We have a 1TB drive with 16gigs RAM so my thinking was giving her VB 8gigs and then she would be happy.

I have backed up her system already with Redo and was going to try and restore it to VB under Ubuntu and then have her run it full screen when she needs it. Do you think this will work and can you give me any advice for/against it?

Thank you all for the input.

Joe

---

### Post by QIII on 2014-03-13
Better choice:  Don't take the chance on sleeping in the dog house.  Leave her Windows alone and run Ubuntu in a VM.

---

### Post by Joe_Johnston on 2014-03-13
There may be some wisdom in what you say. I mainly wanted to get feedback on the possibilities, i.e. performance and viability.

---

### Post by QIII on 2014-03-13
Running Windows in a VM is viable. But if your wife likes to watch YouTube or Netflix on Windows, she will beat you about the head and shoulders.  Video in a VM is typically terrible.  You are limited to the video "card" provided by the VM software's hardware abstraction layer -- which is well nigh useless in VirtualBox.  Streaming is a No Go.

---

### Post by Lars Noodén on 2014-03-13
Running Ubuntu as the host and putting the legacy system as a guest allows snapshots which can help with maintenance, especially if the system can be in the VM and the user's home directory on a physical partition.

---

### Post by Joe_Johnston on 2014-03-13
> **QIII said:**
> Running Windows in a VM is viable. But if your wife likes to watch YouTube or Netflix on Windows, she will beat you about the head and shoulders.  Video in a VM is typically terrible.  You are limited to the video "card" provided by the VM software's hardware abstraction layer -- which is well nigh useless in VirtualBox.  Streaming is a No Go.

This is something I was not aware of and would be a deal breaker if it is that bad. Thank you for the tip!

---

### Post by Joe_Johnston on 2014-03-13
> **Lars Noodén said:**
> Running Ubuntu as the host and putting the legacy system as a guest allows snapshots which can help with maintenance, especially if the system can be in the VM and the user's home directory on a physical partition.

I will need to look into this as I am not sure exactly what you mean as I am new to Ubuntu but it sounds intriguing. Thank you.

---

### Post by Lars Noodén on 2014-03-13
Here is a little about snapshots, 

[https://www.virtualbox.org/manual/ch01.html#snapshots](https://www.virtualbox.org/manual/ch01.html#snapshots)

They are one of the main advantages of virtualization.  However, the disadvantage with the video cards may outweigh it.

---

### Post by bapoumba on 2014-03-13
Why not a dual boot ?

---

### Post by QIII on 2014-03-13
Snapshots can also be made of a guest on a Windows host.  Not being a naysayer, of course, Lars!  ;)  You are quite right.  That is one of the beauties of virtualization.  But "domestic tranquility" is an important factor here.  Having a squabble about OSes would be silly.  I maintain that the two most important words in the English language for a married man are "Yes, dear!"

I think that having the VM's virtual disk on a completely different hard drive is actually preferable if possible.  Host and guest on the same drive can lead to performance bottlenecks due to read/write conflicts.  When possible, say with a desktop machine, having the guest's virtual disk on a separate physical drive from the host is a good way to go.  Moving the virtual disk to a completely different machine works well in the enterprise, but at home I think the inherent latency due to transmission across the network would be frustrating.

If this is a desktop, it might be worth getting another small drive ... but then that means spending some money.

---

### Post by QIII on 2014-03-13
> **bapoumba said:**
> Why not a dual boot ?

We have a winner here!

Of course, that is a more advanced level approach.

---

### Post by bapoumba on 2014-03-13
> **QIII said:**
> We have a winner here!

Of course, that is a more advanced level approach.

Yes dear :p

And I have to say, giving her 8G when there is a 1T hard drive is a little, well, .. :)

---

### Post by QIII on 2014-03-13
I suspect the OP was referring to 8GB of RAM.  ;)  If not, perhaps you should offer some friendly "retraining"?

---

### Post by Joe_Johnston on 2014-03-13
Thank you all for the info and I am presently dual booting but was hoping for the ability to have Ubuntu up all the time and have her Windows when she needs it. I figure that investigating my options is a good thing before making a big mistake.

---

### Post by bapoumba on 2014-03-13
> **QIII said:**
> I suspect the OP was referring to 8GB of RAM.  ;)  If not, perhaps you should offer some friendly "retraining"?
Eheh, OK, in the virtualized environment /o\
My bad. But anyway, I'd say 50/50 on the HD :)

---

### Post by Joe_Johnston on 2014-03-13
> **QIII said:**
> I suspect the OP was referring to 8GB of RAM.  ;)  If not, perhaps you should offer some friendly "retraining"?

LOL, yes, 8 gigs RAM! That would be hilarious to have 8gigs HD space..her profile alone is around 50gigs. :)

---

### Post by bapoumba on 2014-03-13
> **Joe_Johnston said:**
> Thank you all for the info and I am presently dual booting but was hoping for the ability to have Ubuntu up all the time and have her Windows when she needs it. I figure that investigating my options is a good thing before making a big mistake.

> **Joe_Johnston said:**
> LOL, yes, 8 gigs RAM! That would be hilarious to have 8gigs HD space..her profile alone is around 50gigs. :)

Yeah, sorry :)
If you are already dual booting, and using Ubuntu has not convinced her, I'd say give her more time, or use whatever suits her best. Habits are very hard to break, whether male of female, nothing related to gender here. My very old parents are happy with Windows, their machine goes for maintenance on a regular basis as it gets stuffed with crapware. So be it.

---

### Post by Joe_Johnston on 2014-03-13
> **bapoumba said:**
> Yeah, sorry :)
If you are already dual booting, and using Ubuntu has not convinced her, I'd say give her more time, or use whatever suits her best. Habits are very hard to break, whether male of female, nothing related to gender here. My very old parents are happy with Windows, their machine goes for maintenance on a regular basis as it gets stuffed with crapware. So be it.

Yes, I am trying to convince all users to switch to Ubuntu but many are set-in-their-ways and will take time to come around. I will stick with dual boot as my wife stated she may be more willing down the road after I use it more and get better with Ubuntu.

Thank you all for the great input!

---

### Post by monkeybrain20122 on 2014-03-13
> **QIII said:**
> Running Windows in a VM is viable. But if your wife likes to watch YouTube or Netflix on Windows, she will beat you about the head and shoulders.  Video in a VM is typically terrible.  You are limited to the video "card" provided by the VM software's hardware abstraction layer -- which is well nigh useless in VirtualBox.  Streaming is a No Go.

Why? You can watch Youtube and Netflix on Ubuntu.

---

### Post by QIII on 2014-03-13
Wife wants to use Windows is the point.  VM + guest = bad graphics performance.

---

### Post by Joe_Johnston on 2014-03-13
Well, I have been talking with her about it and apparently she is willing after a few months of testing by me so it is inevitable for her to get Ubuntu on her system in the next few months. :)

---

### Post by KillerKelvUK on 2014-03-14
Ha a little chuckle at this thread...have you considered skinning Ubuntu to look like Windows...maybe wifey won't notice...

[http://www.howtogeek.com/55985/how-to-make-ubuntu-linux-look-like-windows-7/](http://www.howtogeek.com/55985/how-to-make-ubuntu-linux-look-like-windows-7/)

Good luck ](*,)

---

### Post by Thee on 2014-03-14
So what's stopping her from using Ubuntu? The looks or the software?

---

### Post by Rich.T. on 2014-03-15
> **Thee said:**
> So what's stopping her from using Ubuntu? The looks or the software?

The learning curve. (Even if it is *easier*, it wil still be there!) Believe me.

Try changing your TV set . ](*,)

---

### Post by Rich.T. on 2014-03-15
> **Joe_Johnston said:**
> "apparently" she is willing after a few months of testing by me so it is "inevitable" for her to get Ubuntu on her system in the next few months. :)

You may get her around to your way of thinking eventually, but I'd recommend that if you have kids; tutor them along with your Mrs and she will come along for the ride, too. :-?

---

### Post by Tom_ZeCat on 2014-03-17
> **QIII said:**
> Running Windows in a VM is viable. But if your wife likes to watch YouTube or Netflix on Windows, she will beat you about the head and shoulders.  Video in a VM is typically terrible.  You are limited to the video "card" provided by the VM software's hardware abstraction layer -- which is well nigh useless in VirtualBox.  Streaming is a No Go.

^^^ This.  If she's going to be doing much in the way of videos, go with a dual boot.  I have my laptop set up with with a dual boot and with Windows under VirtualBox.  VB is great if I want to run Quicken 2012 (which runs poorly under WINE) or Final Draft (which doesn't run at all under WINE).  However, if I want to do video editing in ConvertXtoDVD, I reboot into Windows.

---

### Post by bojo on 2014-03-19
Actually my wife does use ubuntu and I am using win 7 in virtual box. Win 7 in virtual box ... sucks (it is not "that" great even out of a VM... just OK). Since we have only 1 computer she got used to it little by little. And I am actually impressed that she is mostly OK with nautilus and navigating to the shared folder for windows files (don't lough here - documents prepared in windows, converted to PDF for printing, moved to Linux and printed from there - is not fun). There are so many programs that work just fine on ubuntu - including you tube is OK and music is very good. Win 7 is limited to the office suite (she is using it not me - and it is because she has to know it too). I am using it for VPN - Aventail (because there is no deb package and I got burned with it before). I don't really think we can reject one system or another (all of them have good and weak points...). With all the strugles that I had with Linux (started back then in the days of Mandrake 7) however - it is still my favorite system and it is because I like it. And my wife respects it. So it is worth it to try. You can always back up your hard drive to an image - clonezilla for example. If you have only 1 machine well... one of you will have to compromize (and live in the VM environment). I've run ubuntu in VM too - on a mac machine. And it is also a good approach. It is more like - who is using the computer for what - what is more critical to be available. Then just talk and if you both agree to give it a try one way or another - then go for it.

---

### Post by 1clue on 2014-03-19
I have some really good advice for you: 

Don't try to make your wife like Ubuntu.  It won't work.  It can't work.  All she will see is you trying to pressure her into doing something she doesn't want to do.

Instead, use it yourself.  Don't be ostentatious about it, just use it to get your work done.

I use a Mac for my workstation for work, and I have a Linux box that I use for my personal workstation.  My wife (then my girlfriend) had Windows Vista and had viruses every few days, it would get so bad that the system was unusable.  I'd boot off the antivirus CD and clean it off, it would take hours and then she had a computer again for a few days.

Meanwhile I made an account for her on my Linux box, and let her use it if she wanted.  She is a native Es_CO speaker, and I'm a native En_US speaker.  We needed different settings.  Anyway, I set up her email and facebook and all that, and just left it there.

When her Vista laptop became unusable, she would get on while I was at work and use Linux.  I originally noticed only because she would still be logged in when I sat down.  I said nothing.  She started asking questions and I answered them, and the antivirus sessions got further and further apart.  Finally, she just wanted me to install Ubuntu on her laptop.

People don't need or necessarily even WANT Linux to look like Windows.  In doing it that way, you tell the world that you consider Windows to be the thing to beat.  Meaning YOU think it's better.  And by that measure, Linux can NEVER beat Windows because Windows is automatically the thing to beat, and you can't be better at Windows because Windows is a moving target.

People are smart.  They don't have trouble learning iPhone or Android, or Mac vs Windows.  Or Ford vs Chevy vs Toyota.  It's all got common features to do the things that everyone needs to do, just the controls are a bit different.

So don't do anything but use your Ubuntu box.  Don't be ostentatious (Hey, look at me!  I'm using Ubuntu!!!!) or people will think you're corny or trying to sell you something.  Just use it, people will notice and after awhile they'll start asking questions if they're interested.  Answer the questions, DON'T POUNCE ON THEM but make it clear that you don't mind helping.

The best way to sell something is to show people how it's used in everyday situations, no fuss, and in ways the person might want to use it.  It doesn't hurt to show a little bling, but don't get outrageous about it or it gets annoying.  People like to change it up sometimes.  Let them sell it to themselves.

---

