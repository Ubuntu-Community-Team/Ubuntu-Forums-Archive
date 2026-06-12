---
title: "Easier Printer Setup Idea."
date: 2006-08-21
forum: The Cafe
---

### Post by tagra123 on 2006-08-21
I am a developer -- mostly for MS Windows -- I KNOW.

I'm sure someone more skilled than me is already working on this -- I hope?

Installing most printers, except for my HP Laserjets the printers were just too much extra effort. Most would give up rather than spend the time figuring it out.  See my post for installing a Lexmark X125

[http://www.ubuntuforums.org/showpost.php?p=1344545&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1344545&postcount=1)


It seems to me everyone loves CUPS and LPRNG but I see from reading many printers only have windows drivers.


Is it possible to have a winprinterwrapper similar to the ndis wrappers. You know something that could decipher the windows driver commands and execute them on the Linux machine.

I thought of this after installing a wireless modem the other day and realizing just how much easier it could be if printers could be done this way; and I dont mean installing the printer under wine.

I see a couple of advantages if this could be done. All of the Windows only printers would become Linux printers too.

It just seems to me to be a logical way to get more compatibility especially for the companies that do not support Linux.

My HP printers installed perfectly with no extra effort.

The Lexmark Z23 took some time and it really took some time to figure out how to get my X125 working.

---

### Post by rattlerviper on 2006-08-21
Good idea, it would be even more helpful if they would release drivers for use on Linux:(   I've got a Lexmark z816 and it wasn't the easiest setup in the world. Next time I'll just buy a printer that is supported in CUPS, and would recomend everyone stay away from ones that aren't.

---

### Post by matthew on 2006-08-21
Not a bad idea. This thread fits better in the cafe so I'll move it there.

---

### Post by slimdog360 on 2006-08-21
I really like that idea. I mean I really like that idea.

---

### Post by prizrak on 2006-08-21
It's a good idea from a usability POV but a bad one in the long run. We need to send the message to hardware manufacturers that if they don't release [good] Linux drivers we will not buy their hardware. Once they realize the amount of business they are losing they are likely to take that extra effort and create a Linux driver.

---

### Post by SeanHodges on 2006-08-21
I agree with Pizrak, although many people moving to Linux already have printers, and cannot afford to go out buying new printes that are compatible. By religiously holding back non-free solutions we alienate them from the using GNU/Linux, and it causes bad publicity because they often go about telling everyone that Linux doesn't work properly.

It's the age-old problem in Free software, but at least by having both alternatives we give the user the choice.

Good idea, i wonder how easy it would be to do technically? Anyone got much experience with printer drivers in Windows?

---

### Post by Donnut on 2006-08-21
I have an HP printer, PSC 1210, and it takes about an hour to set up in windoze, and about 2 secs to set up in Ubuntu, I may be just lucky, but windoze seems to have a problem with most printer drivers.

---

### Post by %hMa@?b&lt;C on 2006-08-21
that seems like a great idea! I just hope that it isnt necessary and all of the printer manufactureers release Linux drivers. I know my mom's printer had linux drivers on a cd!

---

### Post by mrgnash on 2006-08-21
It's difficult? :confused: Took me about 5 minutes to add every printer (three) on the network. Granted, I don't have a Lexmark though; are they really exotic or something?

---

### Post by rattlerviper on 2006-08-21
> **mrgnash said:**
> It's difficult? :confused: Took me about 5 minutes to add every printer (three) on the network. Granted, I don't have a Lexmark though; are they really exotic or something?

Most Lexmarks don't just work...In fact if you are able to get some of them to work you have a real feeling of accomplishment.  To get mine to work I not only had to download 1 driver but also a driver development package and a whole bunch of libcups-dev packages and then make the install...works for some of us with this printer although most people are getting really poor print quality.  Just stay away from the Lexmarks!  Put the cheap Lexmark down and buy a printer that's supposed to work with Linux out of the box;)

---

### Post by prizrak on 2006-08-21
Just get a networked Xerox or something. Set one up with my Ubuntu laptop at work and it was as easy as pointing CUPS at the printserver :)

---

### Post by tagra123 on 2006-08-22
> **matthew said:**
> Not a bad idea. This thread fits better in the cafe so I'll move it there.


Thanks for moving it -- I wasnt' sure where to put it.

---

### Post by tagra123 on 2006-08-22
> **prizrak said:**
> It's a good idea from a usability POV but a bad one in the long run. We need to send the message to hardware manufacturers that if they don't release [good] Linux drivers we will not buy their hardware. Once they realize the amount of business they are losing they are likely to take that extra effort and create a Linux driver.

I do agree with your point and I will not buy another Lexmark printer either. I shouldn't really say that. My Lexmark Z23 installed a little more easily and works fine but still pain to get it working. 


People say what you said about needing native support for ndiswrapper too. Only one of my wireless needed to use ndiswrapper -- and once working its just fine. I personally wouldn't care whether the driver was a Windows or a Linux driver as long as the printer works the way it was designed to work.

I agree with the theory that the hardware manufacturers should supply linux drivers but with the hundreds or models floating around -- well who's going to support that 2-3 year old model that still works but is discontinued.

Honestly, I don't think the manufacturers will hear our voice because we (Linux) is such a small portion of the market. In my opinion anything that makes hardware more compatible is good for Ubuntu and Linux in general.

---

### Post by tagra123 on 2006-08-22
> **mrgnash said:**
> It's difficult? :confused: Took me about 5 minutes to add every printer (three) on the network. Granted, I don't have a Lexmark though; are they really exotic or something?

My Hp was easier to setup on Linux than on Windows, but the Lexmark is terrible to get working.  I don't think it's just Lexmark either.


Lexmarks for the most part are  a dime a dozen anymore.  Many people buy them because they are usually less the $50.00 for printer only models.  

4 or 5 years ago I paid around $200 for my X125 multifunction.  Not the most expensive printer but too much to become a printer only or worse yet a paper weight.

From my reading Lexmark uses their own printer language.  

I think the real problem, especially on the cheaper models, is that many the printer manufacturers count on the operating system to do the "heavy lifting".

---

