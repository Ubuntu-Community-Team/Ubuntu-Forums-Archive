---
title: "Kids - Internet Access - Restrictions"
date: 2011-07-28
forum: Security
---

### Post by ChrisNZ on 2011-07-28
Hi - I'm running Natty and have made two logins on the system. One for myself and family and one for the kids (teens 14-15yr) to play in without Internet access via Admin "Users and Groups". I have hidden the Internet software icons on their screen amongst others i don't want them to see on the menus. On our screen I use a Firefox addon called "Web Of Trust" that can be configured easily for the kids and another addon called 'Blocksite' that I can selectively use for them and myself etc.

However... I have found out that they have still been able to get on to the net somehow under their login. Will have to observe again!! ;)

In the users settings for the kids the tick box for 'Internet'and 'use modem' access is un-ticked so I presumed that would be enough! Not so!!

Can someone here help with this "basic" problem?

---

### Post by bodhi.zazen on 2011-07-28
There is no substitute for parental oversight, however, I use this :

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

---

### Post by ChrisNZ on 2011-07-28
Thanks bodhi.zazen

I had used Dansguardian in the past- however had to remove it from the system because it was problematic and virtually "killed" internet access for anyone! DG has a place in "filtering" yet thats no the issue i need to resolve here - sorry. Yeh Adblock is used already and this is easy to config. 

The main problem is restricting access on a separate login. Why do I need to intsall anything else? Surely Ubu is configurable enough to prevent net access and admin issues for others who use the same PC at home??

Cheers

---

### Post by bodhi.zazen on 2011-07-28
> **ChrisNZ said:**
> Thanks bodhi.zazen

I had used Dansguardian in the past- however had to remove it from the system because it was problematic and virtually "killed" internet access for anyone! DG has a place in "filtering" yet thats no the issue i need to resolve here - sorry. Yeh Adblock is used already and this is easy to config. 

The main problem is restricting access on a separate login. Why do I need to intsall anything else? Surely Ubu is configurable enough to prevent net access and admin issues for others who use the same PC at home??

Cheers

You use iptables. Read the examples in my first link.

Here is another example 

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

Use the OUTPUT table and notice the match -m owner ;)

---

### Post by cariboo on 2011-07-29
If you are behind a router, most of them can be setup to restricted internet access by time of day, block by web site and both of my Linksys routers allow you to block sites using keywords.

---

### Post by lisati on 2011-07-29
My $0.02: Some routers (e.g. the one I use) allow you to redirect sites to "safe" ones.

---

### Post by Thewhistlingwind on 2011-07-29
Are you sure they're not just holding shift at bootup?

Physical access is root access, this applies doubly to kids.

---

### Post by bubba2 on 2011-07-30
To stop a user "bubba" from accessing the internet:
sudo iptables -A OUTPUT -m owner --uid-owner bubba -j DROP

---

### Post by ChrisNZ on 2011-07-31
Ok found the way the kids where getting on through their login, simple point to "Places" and click "Desktop" - that opens files to view in a HTML manner within the browser!?

Thanks for the other suggestions, I'm working on it! ;)

The main reason for the restriction is for the online gameing (the PC is in the family room so everyone sees whats happening)- 
"thats enough time (30mins a day- 1 hour on Holidays) on the PC kids you can come off now" - "Oh dad i have to get to the next level before I can quit"!! Heard it before? :)

Gaming would normally require our login and restrictions etc. I have to keep up with the "updates and the changes that occur on the other login as well" The menus just seem to add access by them selves (Me thinks?)

The other option would be to hook up a timer so that everything shuts down!:lol: 

Thanks again for some ideas.

---

