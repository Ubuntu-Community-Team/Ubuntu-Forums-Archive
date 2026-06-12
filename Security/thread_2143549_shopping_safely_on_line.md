---
title: "shopping safely on line"
date: 2013-05-09
forum: Security
---

### Post by Kojak Peg on 2013-05-09
Hi everyone
I've had my credit card cloned, will I was still a microsoft user, I have to say. The bank said it could have been randomly generated, since I'm always so careful. So me question is, how can I make internet shopping even safer. 

When I was on windows I used a program called Rapport from trusteer.com, which is recommended by the banks. Is there a similar program for linux. And although I know I don't need antivirals, firewalls, anti malware, software. are there any you would recommend. At the moment I've got 
clam tk 
firestarter (although I really don't know if I'm using it properly)
and firewall (which is inactive because I don't know how to use it)

Many thanks

---

### Post by Bucky Ball on 2013-05-09
*Thread moved to** Security Discussions***

---

### Post by Kojak Peg on 2013-05-09
Thanks Bucky Ball. Sorry about putting it in the wrong section

cheers

---

### Post by kurt18947 on 2013-05-09
Disclaimer:  I'm no security expert, just another user.  It never hurts to be careful but are you certain your card was cloned as a result of your online activities?  I ran into this with a debit card but it had NEVER been used online, thank goodness the perps were greedy.    I suspect the issuing bank had been compromised due to a phone call a bank officer made while I was in their office to the effect of "I've got another one of those cards".  I have the impression that more compromises are a result of either cracking a bank or retailer's system or something like a skimmer or clerk swiping your card twice.  A TV news piece about some n'er-do-well in a poorly lit room intercepting online transactions makes for much better drama though, doesn't it?

I did create a separate Ubuntu install just for online financial transactions.  My thinking is that only going to financial institutions in that install lessens the risk of downloading some sort of malware.  I also don't have flash or java on that install and limit the sites that are allowed to set persistent cookies.  I can't see ads but I can suffer that deficiency;).   I don't know if that'll help or not but figure it can't hurt.

---

### Post by Bucky Ball on 2013-05-09
S'alright. You might have more luck here is all. ;)

Yea, I would be (and am) more worried about what's happening at the bank's end. They are a much bigger target and more chance of compromise. Pretty hard to get in at your end, with or without firewall (UFW I think is the one you want to look at) especially if you are behind a router, too. 

There is a Ubuntu security sticky floating round somewhere, though, if you have a dig on the forums.

* The link to it is on the front page of the ***Security Discussions*** sub-forum, second down:

[https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall)

---

### Post by pqwoerituytrueiwoq on 2013-05-09
[gufw](apt:gufw) if you are not behind a router, gufw is the gui for ufw, a router is a firewall since you have to allow the ports on it
dont use the same password in more than one place, don't use weak passwords, if you use firefox's saved password feature use the master password feature
be more worries about banks using XP after support is ended, only use cash in person

---

### Post by Kojak Peg on 2013-05-09
Thanks Guys
Yeah, like you say it probably was the bank or retailer. The fraud officer, said it was probably a randomly generated number, because they tried and failed to purchase lots of things, and were successful once. I've also hear a lot about the security of linux distros, but being a newbie I just wanted to make sure I was doing everything I could. I did know about the jave thing but didn't know about flash. So that's something to think about. And I'll definitely have a look for the UFW thing, but I'm used to windows firewalls which created rule based on your usage so I'm not sure if I'll know how to make a rule, but will look into it 

So maybe I'll get rid of window all together and dual boot with two distros. A user freindly one for everyday use and an uber secure one. Any suggestions about uber secure distros

---

### Post by pqwoerituytrueiwoq on 2013-05-09
personally i use xubuntu, nice n stable, fast, not too bla in the effects, user frendly
if you stay on the bleeding edge it is unlikely you will be targeted by anything, it is not worth the effort to make something to infiltrate something that will probably get a update soon that could break you hack before you can release it
if you like that approach you can use the dev version of Ubuntu or a variant, dev versions can be prone to breaking as they are intended for testers
here is the dev version for xubuntu
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/")

but if you want to go to extremes, here
[http://www.makeuseof.com/tag/linux-distros-paranoid-secure-distros-si/](http://www.makeuseof.com/tag/linux-distros-paranoid-secure-distros-si/)

---

### Post by Kojak Peg on 2013-05-09
thanks pqwoerituytrueiwoq
[COLOR=#000000][/COLOR]it's the gufw firewall I've got inactive at the moment because I don't understand how to create a rule. So I'm using firestarter because it's got a wizard, which make it easier for me. I always thought of myself as being reasonably compliant with computers, until now, lol, but I'll figure it out in the end with lots of help, lol

Thanks

---

### Post by Kojak Peg on 2013-05-09
I dipped my toe in with xubuntu so if it's secure I'll definitely go back to it. Is it a rolling release or do you need to download the latest version and the up date to keep on the bleeding edge. As for dev versions I'm a little to new to linux , but thanks for the tip 

Cheers

---

### Post by Bucky Ball on 2013-05-09
Xubuntu 12.04 LTS has three years support, everything else apart from LTS releases, at this point, has eighteen months. Not rolling release. While the advice might be good for security, it is a strange way of going about it and expect (regular) breakages if you are living on the bleeding edge. If you want something stable use an LTS and tweak security settings as needed (as I say, behind a router is pretty safe). And read the link I posted earlier. ;)

---

### Post by pqwoerituytrueiwoq on 2013-05-09
> **Kojak Peg said:**
> I dipped my toe in with xubuntu so if it's secure I'll definitely go back to it. Is it a rolling release or do you need to download the latest version and the up date to keep on the bleeding edge. As for dev versions I'm a little to new to linux , but thanks for the tip 

Cheers
Ubuntu/xubuntu/kubuntu/ubuntu-gnome/lubuntu saucy (13.10) will be rolling release 13.10 is in its 1st month of development the version will be 13.7 13.8 13.9 changing every month

---

### Post by Stef700 on 2013-05-11
fwiw I have *one* credit card only dedicated to Internet purchases (I *only* use it for Internet purchases and I have a special *low* limit on it) 

(I got this card connected to Paypal + Amazon + Google etc for example)

:)

---

### Post by BigCityCat on 2013-05-11
one of the best things you can do is pick up keepassx and learn how to use it. Go through all your important passwords and use keepassx to generate new passwords for all of them, using a different password for each. Make sure you use the most complicated passwords allowed by each institutions password criteria. Some will allow more characters and some won't allow special characters. Keepassx password generator allows you to modify the password criteria so that you can fit within the institutions password rules. Make sure the master password for your keepassx file is complicated and secure. Remember it and don't lose it. Backup your password file on a usb key in case you have to reinstall.

---

### Post by BigCityCat on 2013-05-11
the nice thing is that you can also use keepassx for windows as well.

---

### Post by Irihapeti on 2013-05-11
+1 for keepassx

There's even a J2ME version for older "smartphones".

---

### Post by BigCityCat on 2013-05-11
> **Irihapeti said:**
> +1 for keepassx

There's even a J2ME version for older "smartphones".

forgot to mention that windows has a portable version of keepassx that you can put on a usb key so you can take your passwords anywhere. as long as you use a good master password you shouldn't have to worry.

---

### Post by Kojak Peg on 2013-05-13
Thanks Guys for all your replies. I'll have a look into keepassx and the one credit card idea is good

Many thanks

---

