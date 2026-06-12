---
title: "can someone tell me what kiluxso.cn is?"
date: 2009-11-21
forum: Security
---

### Post by Gatorade on 2009-11-21
I installed Ubuntu 9.04 on a friends pc , today he told me that it was infected with some trojans .

I went to his house and started the computer. everything seemed like it was booting up ok. When it got done and I tried to open up firefox there were some popups saying the security had bee breached or something like that.

I wanted to take a screenshot but it was unresponsive. the update manager also came up , so I told it to download the updates.

after that I rebooted the system and it seems to be working fine now.

I wrote down some of the stuff I saw.

one popup said something about kiluxso.cn

and inside another popup there were 3 things 

trojan im.win32.faker.a
virus win32.faker.a
trojan psw.Bat.Cunter

what are these? 
As I mentioned, the computer seems to be ok,and I restarted it a few times to see if the messages would come back. but it never it.

so, how should I go about checking if there's going to be a problem down the line? I don't want to tell him its ok just to find out later there was something lying dormant just waiting for the right time to take over his computer.

a search on yahoo for kiluxso.cn only turned up some stuff in spanish or portugese or something.

---

### Post by jacobs444 on 2009-11-21
the ones that have w32 in the name are windows only viruses/trojans. The other probably will have no effect, but tell your friend to use a safe search through yahoo or the like as there are always 0-day flaws in every OS

---

### Post by Gatorade on 2009-11-21
ok, this is what I just found [http://www.2-spyware.com/remove-trojan-im-win32-faker-a.html]("http://www.2-spyware.com/remove-trojan-im-win32-faker-a.html")

but,from reading that article, it says it was designed to steal passwords form MSN messenger users.

how does this affect Ubuntu users?

---

### Post by Gatorade on 2009-11-21
hi , 

thanks for the reply.

> **jacobsbollocks said:**
>  but tell your friend to use a safe search through yahoo or the like as there are always 0-day flaws in every OS


can you clarify this please. what does safe search mean?

so, he doesn't need to worry about the win32 ones, but how did this thing install itself on his pc in the first place if its designed for windows?

---

### Post by Logan1985 on 2009-11-21
It could have been "scareware" or just a popup telling him he had somehing but didn't. I've never seen this in Linux mind so I'm not really sure. 

How about installing a free anti virus client and doing a full scan? A personal firewall may also be worth looking into also

As for safe search, it will show safe pages, check they are not redirected to dodgy sites, etc. 

Also in Firefox check for any dodgy proxy setting in Edit > Preferences > Advanced > Network and then look at the Proxy bit and see nothing is dodgy in there. May also be worth looking at /etc/resolv.conf to see if there are any dodgy DNS server entries that may be poisoning search results.

Again though...this is all stuff I've came accross in Windows, not Linux...but it's worth checking I guess.

---

### Post by movieman on 2009-11-21
If it's popups from the web browser it's almost certainly a scam: people try to convince Windows users that they have a virus and should pay them $50 to download some magic software to fix it... but it's just opening a popup window that looks like a Windows anti-virus warning, there's nothing actually on the system.

---

### Post by scottuss on 2009-11-21
Don't panic, it's just a website that uses scare tactics. The other day I was on a site with a banner that told me it had detected my registry needed cleaning. I was sat on a Linux box. You can work the rest out.

---

### Post by sgosnell on 2009-11-21
I agree, it's a website that is trying to scare people into buying their worthless software.  They assume everyone is using Windows, so they tell you that you have an infection by Windows malware without even checking to see what OS you're running.  Preventing popups will stop a lot of this, and just ignoring the rest will work.  Many of those sites will try to install some malware so they can sell a fix for it.  It's best to stay away from those sites, but if you're running Linux you don't really need to worry about them.

---

### Post by Gatorade on 2009-11-21
if it was a popup that came up when he went to a certain site I wouldn't have been concerned. 

but this happened as soon as he opened up firefox. and he said it kept coming back each time he started it. 

The only time I've seen something like this, coming back persistently, was with windows, and the computer was indeed infected with spyware. I had to go through a bunch of crap to get rid of it.

I've been using Ubuntu for close to a year now and haven't had any problems. Thats why I was shocked when he told me there was a popup saying there was a trojan on his pc.

I just told him to keep using it for a while and see if it shows up again, if it does then I'll know there's something more to it, but the more I think about it , its probably nothing.

thanks for the replies , everyone.

---

### Post by sgosnell on 2009-11-21
A quick Google search shows that kiluxso.cn is a website.  [Norton Safe Web](http://safeweb.norton.com/report/show?name=kiluxso.cn) shows that it may have a trojan on it.  It's Windows only, though, so don't worry about it.

[Safe Browsing](http://safebrowsing.clients.google.com/safebrowsing/diagnostic?client=Firefox-3.5&hl=en-US&site=http://kiluxso.cn/) has more information.

---

### Post by scottuss on 2009-11-22
> **Gatorade said:**
> if it was a popup that came up when he went to a certain site I wouldn't have been concerned. 

but this happened as soon as he opened up firefox. and he said it kept coming back each time he started it. 

The only time I've seen something like this, coming back persistently, was with windows, and the computer was indeed infected with spyware. I had to go through a bunch of crap to get rid of it.

I've been using Ubuntu for close to a year now and haven't had any problems. Thats why I was shocked when he told me there was a popup saying there was a trojan on his pc.

I just told him to keep using it for a while and see if it shows up again, if it does then I'll know there's something more to it, but the more I think about it , its probably nothing.

thanks for the replies , everyone.


You did check he didn't have this site set as his homepage didn't you?

---

### Post by Gatorade on 2009-11-22
yes , his homepage is set to yahoo.

As I said , it seems to be fine now. I'll post an update if it comes back .

---

