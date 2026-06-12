---
title: "New to Ubuntu ~ Debit Card Hacked"
date: 2011-05-07
forum: Security
---

### Post by Mesquiter on 2011-05-07
I'm new to Ubuntu and in my seventh decade.  Had several Amigas years ago and took a couple of courses in C programing so know a little about the Linux-Unix structure.  I'm pretty satisfied with Ubuntu and hope I've found a home; however, yesterday I ordered some software on the Net.   Early this morning, I got a call from my bank someone else tried to charge to my debit card.

I called the company I ordered from to alert them and they assured me it had to be my computer security because theirs was checked, upgraded regularly and above reproach.  Fortunately, the bank caught it in time and my account wasn't debited.  After I assured them I didn't order anything from Bed, Bath and Beyond, the bank shut down my card and I had to apply for another.

I was shocked.  You hear about it but never imagine it will happen to you.  I began to wonder and worry if it was because I was using Linux and it wasn't as secure as Microsoft.  I'm isolated in a very small town in West Texas so I order some things on the Net. 

I loaded the full version of Ubuntu "Lucid Lynx" 10.04 from a 4 disk set and downloaded all the upgrades; almost five hundred and set everything up the way I wanted.  My question is: Are there programs running among the Ubuntu build to assure a secure transaction on the net or do I have to load others and a fire wall like Windows?  That's one of the reasons I left Microsoft behind was the "Auntie-viral" programs took over and almost became a competing system. 

Any thoughts or suggestions would be greatly appreciated.

Mesquiter

---

### Post by kerry_s on 2011-05-07
4 disk set ?

ubuntu is 1 disk, where did you get yours from ?

you need to get straight from ubuntu:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by Maheriano on 2011-05-07
Why is Windows always used as a control group?
The operating system is irrelevant, your wireless connection and the encryption on your browser is more likely to blame. There are too many variables to try and figure it out, just move on and save yourself the trouble.

---

### Post by SparTacux on 2011-05-07
That's got to come as a shock.

First - you don't really know if you've been hacked over the internet. Second - you don't know if the company you were dealing with were as secure as they say they are. Take a look at the latest news from the huge Sony internet hack in the news. 

I like to see what's going on when I'm on the internet & have full logging on all traffic in and out of my system. some people just log the blocked traffic but that doesn't help in working out when things go wrong. A simple temporary solution is to type netstat -ntuc to list connections out of your computer when making transactions. You should be seeing https connections for a secure connection Run terminal & do a whois on those ip addresses to see if they are legitimate or not. 

I'd be checking out those disk you downloaded too. Were did you get them and did you do an Md5sum check on them before installation?

Did you browse the web with your main account or did you create a standard desktop user account and browse with that?

A good idea is to clear your internet browsing history, cookies, cache etc after making transactions.

You might want to download NOSCRIPT to block all scripts running on your computer. Linux can be hacked from the browser and your local directory compromised if it's not set up properly. Run scripts at your own risk !!! 

I'm sure the rest of the guys on the forum will add more info on this subject.

---

### Post by Mesquiter on 2011-05-07
Thanks for your compassionate and intelligent reply.  I purchased the disks last year from Amazon.com.  It contained a 64 bit disk and a 32 bit disk and two Linux training disks packaged by UnixAcademy.com  I know Ubuntu is free but I just saw the offer and responded.  I thought it might be a more thorough guide and provide a bit more info for the novice.  I use Firefox for a browser and connect to the Net through a broadband cable.

---

### Post by lavinog on 2011-05-07
Did you happen to ever use your card with a sony service?
Sony was recently hacked and all stored credit card info has been stolen.

Edit: just noticed spartacux made a ref to the sony issue.

---

### Post by SparTacux on 2011-05-07
No problem Mesquiter

I've been hacked myself in the past - it's a rather unpleasant feeling. Hope you didn't lose too much sleep over it. One tends to get the jitters about going back on the internet after an episode like that.

It's possible you didn't get hacked and the problem lies elsewhere but it's better to be safe than sorry. I'd backup all the log files using sudo nautilus in the <var<log directory and backup your home directory to usb stick or DVD and then do a re-install. Install GUFW  ( Firewall )  and allow logging. Do an update. Then create your standard desktop user account.  Turn off scripts in Firefox and download NOSCRIPT. Then turn scripts back on in Firefox to allow noscript to work. I'm sure someone will mention get used to working with apparmour here ;-). 

One more point - make sure your modem is password protected with a very good password and not using the default password and also make sure no remote administration of the modem is enabled.

Get used to using netstat -ntuc  & the whois tool for checking out the IP addresses.

That should be ok for starters

---

### Post by jramshu on 2011-05-07
Darn it, I hit the wrong button and lost my post. Too many windows open!!

---

### Post by Zewbie on 2011-05-07
> **Mesquiter said:**
> Thanks for your compassionate and intelligent reply.  I purchased the disks last year from Amazon.com.  It contained a 64 bit disk and a 32 bit disk and two Linux training disks packaged by UnixAcademy.com  I know Ubuntu is free but I just saw the offer and responded.  I thought it might be a more thorough guide and provide a bit more info for the novice.  I use Firefox for a browser and connect to the Net through a broadband cable.


This guy may have order from a unsecured location such as Fedex Kinkos or a public library.
  


just a thought

---

### Post by Mesquiter on 2011-05-07
SparTacux ~ Thanks again for your considerate and encouraging responses.  Your suggestions are excellent and I will certainly follow through with them.

---

### Post by Mesquiter on 2011-05-07
jramshu ~  I agree the banks in Texas take a more personal approach and seem genuinely more interested in their customers.  I realize the chances of when, where and how my card was hijacked are many a varied; however, one has a tendency to panic when it happens.  Thanks for your words of empathy and concern.  After a good nights sleep and some excellent suggestions, I'm feeling more like fighting back.

---

### Post by rookcifer on 2011-05-07
You didn't provide enough information for anyone to make any determination of what happened.  I will say the chances of it being Linux's fault are next to none.  As others have pointed out, do you use a wireless connection?  Do you ever connect to free Wifi hotspots?  Are you sure you didn't fall victim to a MITM SSL attack?  

As for the company itself, they say they're secure, but why should you take their word?  Many companies in the past have kept serious breaches secret.  It's also very possible a rogue employee at the company steals CC numbers from time to time in order to go on shopping sprees.  I would say this is the most likely scenario.  The truth is, whenever you give your credit card number to anyone, they can use it just as you can.  This is why some identify fraud experts say to always use a CC on the Internet and *never* a bank card.  Using a credit card puts the onus on the CC company -- they are responsible for cleaning up the mess if someone steals the number.

---

### Post by wilee-nilee on 2011-05-07
Linux has a good password generator called pwgen, I use it on occasion and string together the out put to make passwords that would be impossible to crack. But there are other ways if you use a wireless setup when using the card. Although a wpa password is quite safe, the packets containing data can be picked up from wireless sniffing, and without actually knowing the password can be used to hack in. 

Don't know the drill on doing this but it is widely known and there are actually applications in the Ubuntu and linux repos to do just this. And a lot of youtube videos showing how.

Never use a wireless setup when doing work you need to ultimately protect.

Hope this is accurate and helps.;)

Some people use a live cd do do their business it has no memory of the transactions.

---

### Post by Mesquiter on 2011-05-07
Rookcifer & Wilee-nilee ~ Thanks for your input. I don't use a wireless unit.  I have a direct broadband cable hookup.  After reading yours and other comments I'm more inclined to believe there might be an employee passing on people's card info to others, but that's only speculation.  Or, as you pointed out I have no way of knowing how secure the company's computers are.  I'm taking it as a wakeup call and will spend the next several days working on security measures.

---

### Post by bodhi.zazen on 2011-05-07
> **Mesquiter said:**
> I'm new to Ubuntu and in my seventh decade.  Had several Amigas years ago and took a couple of courses in C programing so know a little about the Linux-Unix structure.  I'm pretty satisfied with Ubuntu and hope I've found a home; however, yesterday I ordered some software on the Net.   Early this morning, I got a call from my bank someone else tried to charge to my debit card.

I called the company I ordered from to alert them and they assured me it had to be my computer security because theirs was checked, upgraded regularly and above reproach.  Fortunately, the bank caught it in time and my account wasn't debited.  After I assured them I didn't order anything from Bed, Bath and Beyond, the bank shut down my card and I had to apply for another.

I was shocked.  You hear about it but never imagine it will happen to you.  I began to wonder and worry if it was because I was using Linux and it wasn't as secure as Microsoft.  I'm isolated in a very small town in West Texas so I order some things on the Net. 

I loaded the full version of Ubuntu "Lucid Lynx" 10.04 from a 4 disk set and downloaded all the upgrades; almost five hundred and set everything up the way I wanted.  My question is: Are there programs running among the Ubuntu build to assure a secure transaction on the net or do I have to load others and a fire wall like Windows?  That's one of the reasons I left Microsoft behind was the "Auntie-viral" programs took over and almost became a competing system. 

Any thoughts or suggestions would be greatly appreciated.

Mesquiter

This may be a bit off topic, and I am sorry you had this problem, but it seems to me you really do not know how your financial information was compromised.

There are many potential ways you could have been compromised and in my experience cracking a Linux (Ubuntu) box would not be even close to the top of my list of possibilities.

With that in mind, yes there are several tools available to investigate, the general term for such tools would be penetration testing.

Penetration testing is a complex topic, however, and it would require a lot of time and effort on your part to learn.

I suggest you start with the security sticky. There are links in the sticky to detailed documentation of penetration testing.

There are tools such as chkrootkit, tiger, and rkhunter, but you need to know how to interpret the results (means reading the documentation) and you can not trust the output from those apps on a compromised system.

IMO a live CD is not more secure then an installed an up to date system. Learn to secure your browser (NoScript) =)

---

### Post by amanchesterman on 2011-05-08
I hope this isn't off topic. I just want to commiserate with you and offer a couple of thoughts from my own experience.

First, I don't think it's likely that your card details were stolen by hi-tech hacking: it's much more probable that they were copied by a person in the company you dealt with, or in another company on a previous occasion. I'm not a computer expert but your system sounds pretty secure to me. By all means add firewalls etc. as the experts here recommend, but none of that will stop your card being hijacked by crooks.

In my case, I have had my card hijacked twice, and in neither case was my computer at fault: I simply used the card to make purchases in shops. Both times (three years apart) it happened around Christmas, when stores are busy and temporary staff are employed.

The other point is to encourage you, as a previous poster has done, to consider getting a credit card that you use solely for online purchases. The reason is that when your card is compromised, the bank or credit card company immediately blocks it -- and if that's your only card, then you are sunk until they issue another. Maybe in Texas that happens really quickly, but over here in England I have had to wait 4-5 days if it falls over a weekend. So having more than one card gives you a backup that minimises the inconvenience to you.

Good wishes

John

---

