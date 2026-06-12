---
title: "Protecting computer in police state"
date: 2011-04-10
forum: Security
---

### Post by Kivrin on 2011-04-10
(Please pardon me in advance for asking what may be a beginner question.)

I'm going back to Syria in a few weeks to visit (I'm American, but studied there for a while). With the recent unrest, they've been checking laptops at the border for evidence of disreputable websites and content.

I double boot my computer with Windows and Ubuntu (Lucid), and I'd like to temporarily disable my Grub so that if they look in my computer, it will just boot into Windows, which I barely use. How can I do this? 

Or, are there any other suggestions for protecting my computer?

Thanks in advance.

---

### Post by bodhi.zazen on 2011-04-10
Well, I would simply wipe the entire HD and re-install windows. Tell them you experienced a virus and did a fresh install.

I would re-install Linux after the trip.

IMO no OS is worth the consequences of getting caught at the border with a hidden OS or anything else.

If you must, image your Ubuntu install and restore it when you get home again.

If you do not trust the network, don't use it. I'm sure you can live without it for a few weeks or days.

Relax, enjoy the trip, and use the internet when you are safe at home.

---

### Post by HermanAB on 2011-04-11
Howdy,

I currently live in the Middle East. It is quite nice here actually, provided that you toe the line.

If I were you, I would remove the hard disk and leave it at home.  Then boot off a Linux Live CDROM and use that while traveling.  Leave the CD in the drive and if Customs want to look at the machine, just turn it on and let it boot up.  

It simply isn't worth taking any chances in the current situation.

---

### Post by Kivrin on 2011-04-13
Thanks for the advice. Normally I would leave my computer at home, but this time I need to take it to do work with some people while I'm there, and I really need to have my own machine. 

How does one remove the hard drive?

---

### Post by NFblaze on 2011-04-13
To remove the hard drive you will have to refer to the manufacturers manual. It may be as simple as 1 or 2 screws or if it was anything like my last computer an HP Pavillion, it will be complex and you will have the potential to break things. In either case, if you continue on that route consult the technical manual for that info.


Secondly, if you decide to keep the hard drive in. Depending on how much far security investigates. You can create a separate partition, and install Windows on it. Configure GRUB to be hidden/low-timeout and default load Windows unless Left Shift (or it might be a diff key but consult Grub manual) is pressed. That way the system will automatically boot into Windows, on poweron. Where you can keep your unimportant and chill browsing on there.

---

### Post by wilee-nilee on 2011-04-13
I would take bodhi.zazen's advice, but clone the whole HD or the partitions, then remove it, use clonezilla you can then slip them back in when needed. This is a great method anyway to having full images.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by HermanAB on 2011-04-14
Howdy, 

On a laptop computer, there are usually two little panels on the bottom secured with little screws.  Get a jeweller's screwdriver set and remove the panels.  One panel hides the RAM (one or two green circuit boards clipped into a connector - leave it lone) and the other hides the HDD (a rectangular shiny metal box), which usually kind of slides and lifts out.

So it is quite easy to remove the HDD and leave it at home, then use the machine with a CDROM and USB sticks instead of a HDD, or you can replace it with a brand new HDD.

---

### Post by Learning Linux 2011 on 2011-04-14
Can you store the files/bookmarks you need on the web somewhere?

Seems like you could upload the files to a web server somewhere, format the HD, get through inspection, and then download the files from the web once you get where you are going.

Of course if you think they might be monitoring downloads, that could be risky too.

Also, maybe you could transfer the stuff to a USB flash drive and then send the drive to the hotel before you get there so it would be separate from you.

---

### Post by tubbygweilo on 2011-04-15
With that part of the globe being in a state of flux I suggest it may well be unwise to do something that in your eyes is OK but in their eyes may not be. So if you do the crime in their eyes then you may well have to do the time.

---

### Post by Megaptera on 2011-04-15
Why not go in with a fresh install of Windows or Ubuntu (having used Clonezilla) to backup at home.
Use Xmarks to sync your bookmarks and something like DropBox or GoogleDocs so you can access all you need without having it all physically with you?
Much safer & less likely to cause problems with the host nation.

---

### Post by Learning Linux 2011 on 2011-04-15
I think another question here is how intelligent are the people who would potentially search your hard drive?  Would they really go through your entire hard drive and every single bookmark in your browser?  That doesn't seem realistic.

Border agents aren't usually known for being computer nerds and I wouldn't think they would even have the time to search your entire computer given the number of people coming and going.

---

### Post by HermanAB on 2011-04-15
No, the intelligence of the border agents are not the thing to question.  The question is, how comfortable are the jails and would you like to risk paying an extended visit to one?

---

### Post by bodhi.zazen on 2011-04-15
> **HermanAB said:**
> The question is, how comfortable are the jails and would you like to risk paying an extended visit to one?

Or worse.

---

### Post by doctortonic on 2011-04-15
I am a human, and usually I have curiosity, so no I am wondering what do you wish to hide? I have some thought's in my mind but, uhm anyway I would do like this:

This would be my personal and time consuming way, I assume no responsabiliy for potential of data loss.
 
1.  Get all the files I need to hide, or if it is the all os, then make an encrypted image of that ''dirty'' partition. 

2. (go to 6) I would use Acronis for making images(backup). There is a trial version that you could use, and they have some 256 bit encrypt system or maybe better.

3. (go to 6) Then I would compress another time the foo-file-image.tib image again with an archiver as 7z.  in foo-file-imag.7z format that archiver have an option to put the password on the archive and encrypt it too.

4. (go to 6) I used that once, but I saw that windows have some encrypting options, with certificates, I am sure there are another best programs for encrypt.

5. Compress the file&encrypt once again this time with Ace archiver

6. I after .7z, .tib where created I would change the extension like .xvid or .exe

7. Archive&encrypt the file once more

8. Archive&encrypt the file once more

9. A: Save the Archive on DVD/blueray or another hardisk 
   B: Upload to a website like transfer.ro there are many of them for online transfer but check if they are accesibile from the country you travel, some sites are banned.

10. Wipe the hardisk minimum 7 steps with ccleaner or dd from windows / ubcd has Darik's Boot And Nuke or any other method you prefer.

Good luck!:popcorn:

Epilogue: then download the file from syria/usa etc unarchive, unencrypt. Get saved certification from previlousy saved email etc. :)

---

### Post by Learning Linux 2011 on 2011-04-16
> **HermanAB said:**
> No, the intelligence of the border agents are not the thing to question.  The question is, how comfortable are the jails and would you like to risk paying an extended visit to one?

Well, that's my point.  If the agents aren't too bright, which seems more realistic, how would you go to jail?  How would they have the time to check every bookmark and file on a person's computer?  The material would have to be really offensive.
And if he is a US citizen "caught" at the border, he would be extradited fairly quickly anyway.

---

### Post by Megaptera on 2011-04-16
> **Learning Linux 2011 said:**
> Well, that's my point.  If the agents aren't too bright, which seems more realistic, how would you go to jail?  How would they have the time to check every bookmark and file on a person's computer?  The material would have to be really offensive.
And if he is a US citizen "caught" at the border, he would be extradited fairly quickly anyway.

The Border Officers - if suspicious of your laptop- will detain it and _you_ for as long as it takes to get their computer forensics people to examine that machine and all its files. And if you sit in gaol for the weeks that that will take that's not going to worry them in the slightest.

US citizens are subject to the laws of the country they are visiting as are UK citizens and everyone else - US citizens don't have an automatic "get out of gaol free" card in their passport!! I know in the 19th century the British Government would "send a gunboat" to help their citizens but I don't think it works like that these days ;)

---

### Post by Learning Linux 2011 on 2011-04-16
> **Megaptera said:**
> I know in the 19th century the British Government would "send a gunboat" to help their citizens but I don't think it works like that these days ;)

I wouldn't put that past the US Military.  As you have probably seen they will invade anybody for any reason, legitimate or not.  I doubt Syria would give the US much of a fight over a person detained for porn.  The US Military is already over there.  I seriously doubt Syria wants to p1ss off the USA right now.

---

### Post by tubbygweilo on 2011-04-16
[538]("http://xkcd.com/538/") says it all!

---

### Post by rookcifer on 2011-04-17
I was going to provide my own ideas on how the OP could pass through with his data unmolested, but since this could literally be a life and death situation for him, I decided to remain quiet.  An American going to Syria at this point in time is, well, dangerous to say the least (these mid-east governments see "spies" everywhere right now and are extremely paranoid of outside influence).  I only wonder what business the OP has in Syria that can't wait until things calm down?

There's no way, as an American, that I would travel to any of those countries going through the protests right now.  No freakin' way.  I prefer to keep my head attached to my shoulders and not have it sliced off with a dull knife and streamed on YouTube.

---

### Post by Megaptera on 2011-04-17
> **Learning Linux 2011 said:**
> I wouldn't put that past the US Military.  As you have probably seen they will invade anybody for any reason, legitimate or not.  I doubt Syria would give the US much of a fight over a person detained for porn.  The US Military is already over there.  I seriously doubt Syria wants to p1ss off the USA right now.

I admire your confidence but I'm sure you won't mind me saying .... after you and let me know how it goes  ):P :D

---

### Post by josephmills on 2011-04-17
I would not even bring my laptop with me. I say go on vacation and have a good time try not to think about it. Spend some time with friend, see if they have one before you go. keep your nose clean and tell us what happens. As I am interested what happens at the border. but there is always one place you could hide it :o ouch!!!

---

### Post by Sharang.d on 2011-04-17
1. Backup EVERYTHING
2. Format EVERYTHING
3. Wipe HDD > 7 times
4. Install Fresh Win/Linux
5. Restore when you're back

Better safe than sorry :)

---

### Post by sammiev on 2011-04-17
Use clonezilla to backup your HD and save it to a backup website so you can reinstall it well your over there. Wipe it out before you head over seas and do the same before you leave there. GL :)

---

### Post by Learning Linux 2011 on 2011-04-17
> **Megaptera said:**
> I admire your confidence but I'm sure you won't mind me saying .... after you and let me know how it goes  ):P :D

If someone buys me a ticket, provides hotel accommodations and a laptop, I'll go just to prove a point.  Middle Easterners admire confidence too, you just need to know how to manipulate them.  

Middle Eastern men are all about respect.  They want their way of life respected, something most Americans won't (or don't know how to) do.

---

### Post by spynappels on 2011-04-18
OK, I'll bite......

????????

"Respect" and "manipulation" in the same context creating an oxymoron, sweeping generalisations about ethnic characteristics, sounds like a pointless discussion to me. Can we either get back on topic or close the thread please?

There are 2 distinct sides to this thread:

1. Don't do it, it's not worth the hassle if you get caught.

2. Do it and here is how.

Both have been explained rather fully, this thread runs the risk of just going round in circles from here.

---

### Post by usatonycuba on 2011-04-18
> **Kivrin said:**
> ..they've been checking laptops at the border for evidence of disreputable websites and content.

> **bodhi.zazen said:**
> Well, I would simply wipe the entire HD and re-install windows. Tell them you experienced a virus and did a fresh install.

I would re-install Linux after the trip.

IMO no OS is worth the consequences of getting caught at the border with a hidden OS or anything else..

+1

> **HermanAB said:**
> Howdy,
If I were you, I would remove the hard disk and leave it at home.  Then boot off a Linux Live CDROM and use that while traveling.  Leave the CD in the drive and if Customs want to look at the machine, just turn it on and let it boot up.  

It simply isn't worth taking any chances in the current situation.

+1

**" With the recent unrest, they've been checking laptops at the border for evidence of disreputable websites and content. "**

That's the real concern?

does not make much sense to me .. but anyway the point is that you can make good cleaning all your browsers, records of internal cache system, its would help you out in all of your concern ...if you have nothing also to hide .. you'll be ok...

---

### Post by Megaptera on 2011-04-18
> **spynappels said:**
> ok, i'll bite......

????????

"respect" and "manipulation" in the same context creating an oxymoron, sweeping generalisations about ethnic characteristics, sounds like a pointless discussion to me. Can we either get back on topic or close the thread please?

There are 2 distinct sides to this thread:

1. Don't do it, it's not worth the hassle if you get caught.

2. Do it and here is how.

Both have been explained rather fully, this thread runs the risk of just going round in circles from here.

+1 !!

---

### Post by tubbygweilo on 2011-06-30
Kivrin, I trust you are well and have returned home without too much drama. I'd love to know which precautions you took to protect your computer whilst overseas.

---

### Post by Dry Lips on 2011-06-30
> **tubbygweilo said:**
> Kivrin, I trust you are well and have returned home without too much drama. I'd love to know which precautions you took to protect your computer whilst overseas.

From Kivrin's public profile:
Last Activity: April 19th, 2011

I also hope the OP is safe and all right!

---

