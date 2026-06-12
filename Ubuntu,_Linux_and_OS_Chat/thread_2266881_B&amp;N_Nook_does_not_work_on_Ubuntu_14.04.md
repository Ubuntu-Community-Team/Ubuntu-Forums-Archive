---
title: "B&amp;N Nook does not work on Ubuntu 14.04"
date: 2015-02-25
forum: Ubuntu, Linux and OS Chat
---

### Post by fwrun2011 on 2015-02-25
Hi all;
I spent at least 4 hours today trying to get Nook for PC to run on Ubuntu 14.04 with Wine. I know that I could have purchased the book on Amazon Kindle, and if I couldn't get the Kindle PC app to run on Ubuntu, I could always use their Cloud Reader. But I found the book for $11 less than it was on Amazon at B&N Nook. 
I was able to install the Nook for Windows PC app, and at first it looked as though it was working. I started the app using the option to launch it immediately after the install had finished.
I was apparently able to log into my newly created Nook account. But after I went and purchased a book - "A Practical Guide to Ubuntu 4th Edition" by Mark Sobell, I was plunged into a 4-hour long fight with the app, Wine, and Ubuntu but came out a loser. I was unable to download the book. When I hit the sync button, it said that sync was complete after only a second, but nothing happened.

I tried everything - two versions of Wine (the stable version, and the 1.7 beta) but was unable to log into my account (always got the login error 1025) or download the book I had purchased.
I went on live chat with B&N, but got nowhere - in the end, the guy I chatted with told me that the app probably required the Windows OS.
I have a dual-boot system, so I booted into Windows 7 and was successful in installing Nook PC, logged into my account, and downloaded the book. But what good was that going to do me? I needed this book for Ubuntu - not Windows.

I tried one more thing: I have another box that runs Windows XP-SP3. I have a second monitor - an older 15" LCD that I could use to read the book on while I worked with Ubuntu on the main monitor.
I installed the app onto that system, but still received a login error - it wasn't the same one I got on Ubuntu, but the same effect.
That's when I came back to Ubuntu and upgraded the version of Wine I was running. I also installed the Wine tricks, but that didn't help either.
Finally, I opened another chat session with B&N and requested a refund for the book. They gave me no problem. I should be receiving my refund even before my credit card bill is due.

I'm sure you can guess my next step: Right. I went to Amazon and downloaded Kindle PC for Windows. Then I installed it on Ubuntu 14.04 with Wine 7.1 and wine tricks. Everything went smoothly - I logged into my Amazon Kindle account, and immediately saw all of my other Kindle books in my library. I was able to download all of them without a glitch. So I went to the Kindle store and purchased the book.

You might ask me why I would go through all that trouble for $11, when I already have several Kindle books and 0 Nook books. Well, money is very tight right now. $11 means one more book in the Kindle store, two cold heros at my favorite deli, or bus and subway fare to get home from a long run through New York City. And besides that, I was learning about Ubuntu all the while - using Google to search for possible solutions.

After all this, I read in a blog or forum post that B&N has discontinued support for Nook PC and Mac.
So I lived and I learned. And I love Ubuntu Linux!

FW

---

### Post by tgalati4 on 2015-02-26
I put Cyanogenmod (Android) on my Nook.  I can move books back and forth between my PC with Calibre, but only books without DRM.  There are plenty of free resources to learn Ubuntu.  Read some of the topics in Popular Pages in my signature.  Just pick a few that you are interested.  Hands-on is a good way to learn.  Roll your sleeves up and start breaking things.  Everything is fixable.  Patience is key.

---

### Post by Bucky Ball on 2015-02-26
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Thanks for sharing, but not a support thread. ;)

---

### Post by coldraven on 2015-02-26
I bought a Nook simple touch when they dropped the price from £59 to £29. Then I discovered that I could borrow e-books from my local library. But only if you install Adobe Digital Editions which of course only runs on Windows or Mac :(
It's like they are forcing me to torrent! 
Project Gutenburg is good for free books and Calibre is great for converting formats.

[http://www.gutenberg.org/wiki/Main_Page](http://www.gutenberg.org/wiki/Main_Page)

[http://calibre-ebook.com/](http://calibre-ebook.com/)

---

### Post by fwrun2011 on 2015-02-27
I have tried many of the free books, and the various web pages, but I have always learned best from a structured lesson plan. The book I purchased is just that. There are questions at the end of each chapter to test my absorption of the material. Of course I will always have the Ubuntu up and running in front of me.
That said, I have been doing a lot of 'seat of the pants' learning for the past few days. I have used mostly the official Ubuntu.com site. It's great, because I can get info quickly from there. Matter of fact, there are links in the e-book I bought that open pages on ubuntu.com.

Today, I was having 'fun' with display drivers. I have a legacy NVidia card - GeForce 9800GTX+ 512MB. There aren't any new drivers for this card, and some of the older ones didn't work too well.  I ended up with version 331.113, which seem to be working fine.
I absolutely agree that you need to learn by doing. No way I would learn anything if I didn't 'roll my sleeves up' and get into terminal.
After getting through the video driver debacle tonight, I concluded that I have installed Ubuntu for two reasons: 1 - it's not Microsoft (although I did install Wine so I can run Windows apps), 2 - I needed something to distract me from everyday life. 

When I was mostly interested in doing things on the computer, rather than with it or to it, I would get anxious when something didn't go right. But today I was relaxed, and enjoyed the trial and error I experienced with the drivers. I have dual-boot with Windows 7, so even if I break Ubuntu, I can still get online or whatever I need from Windows. I can even read the Ubuntu text in Kindle on Windows.
Now all I have to do is download it to my Android phone.

---

### Post by Bucky Ball on 2015-02-27
Sounding good so far. Just a suggestion: why don't you install an LTS release (perhaps 14.04 LTS) on another partition which is your 'stable' install and have the install you're tweaking now as your 'breakable'? That way, you can spend as much time as you like breaking and fixing on one install and it doesn't matter as you have a stable release you can use for everyday computing. 

Might even be handy to reference how the stable release is configured when you break something on the 'plaything'. 

Just a suggestion (I have four *buntu installs, one of which is my 'main squeeze' solid for when I need things to 'just work', plus a Win7 install which I haven't used for about a year!).

Keep on keeping on and enjoy the learning curve. ;)

---

### Post by fwrun2011 on 2015-03-09
> **Bucky Ball said:**
> Sounding good so far. Just a suggestion: why don't you install an LTS release (perhaps 14.04 LTS) on another partition which is your 'stable' install and have the install you're tweaking now as your 'breakable'? That way, you can spend as much time as you like breaking and fixing on one install and it doesn't matter as you have a stable release you can use for everyday computing. 

Might even be handy to reference how the stable release is configured when you break something on the 'plaything'. 

Just a suggestion (I have four *buntu installs, one of which is my 'main squeeze' solid for when I need things to 'just work', plus a Win7 install which I haven't used for about a year!).

Keep on keeping on and enjoy the learning curve. ;)
That's a really good idea! I used to do that when I was strictly Windows. So far though, I haven't been able to "break" Ubuntu 14.04.1. I did get it frozen a few times - to the point where I couldn't even do anything in the terminal window - or get into the real terminal mode - but rebooting fixed that. It always seems to have something to do with my video drivers. I am running with a legacy NVidia GeForce 9800GTX+512. Planning to upgrade that soon though.

I think I will do the "sandbox" install though - so I can follow the book and try all sorts of things without worrying that I will mess up my main OS.
Of course, I do still have Windows 7 on another part - but I hate to go back into that now that I am getting really familiar with Ubuntu.


FW

---

### Post by Bucky Ball on 2015-03-09
Yea, you can do this with other distros, too, and use the same /home and /swap partitions (if you have a separate /home partition, or link to an allocated data partition) so all installs use the same files. 

Why not go for a challenge and try the [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") on a partition? You'll certainly learn something doing that. ;)

Good luck and have fun.

---

