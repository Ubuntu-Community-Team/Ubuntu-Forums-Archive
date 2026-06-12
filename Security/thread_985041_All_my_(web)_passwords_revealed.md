---
title: "All my (web) passwords revealed"
date: 2008-11-17
forum: Security
---

### Post by kwaanens on 2008-11-17
I'm a little concerned.

I today found some weirdness going on in my Facebook account, and I realised I had been hacked.

In my Gmail inbox there is an e-mail from the hacker (sent from my e-mail adress) telling me:
"YOUR PASSWORDS ARE HACKED
PLEASE CHANGE YOUR PASSWORD EVERYWHERE, I AM A GOOD HACKER AND DID NOT DELETE STUFF - OTHERS WILL DO 
CHANGE THEM"

"Proof" is a png of a list of usernames and passwords on, from what I can tell, only web based services. No system passwords.

So, hopefully the "good hacker" part is true. What I'm wondering is, how did this happen? There are numerous alternatives. 

- There is a possibility that this is someone who got into the computer itself, but that's hopefully unlikely. (All updated Ubuntu 8.10, no extra security used. I'm behind a standard router from my ISP, which has some sort of firewall.)

- It could be related to Firefox.
---- I use Mozilla Weave. It keeps my passwords in the "cloud", and could be a liability. (I unistalled it right away, but I need to find out how to delete *all* the online stuff
---- Extensions: Adblock +, CustomizeGoogle, DownloadHelper, DownThemAll!, Fasterfox, FireFTP, FireGPG, Flashblock, Google Gears, Google Icon, I heart Miro, Image Zoom, Signature, Tab Mix Plus, Ubuntu Firefox Pack, Greasemonkey (with Facebook Autologin, Facebook Fixer, Last.fm Mutual Groups, Gmail Addons, Google Reader + Gmail Addons, NYTimes ad jumper, New Facebook Layout Ad Killer, Facebook thumbnail enlarger, Userscripts Updater, Google Reader: Show Feed Favicons, Last.fm - Polish the profile)

It could be online:
- I don't give Facebook a lot of access to much
- I use Mugshot, which gets some stuff
- I use Twitter which does not get much
- I use Last.fm, which does not get much.

Now, the problem is not huge. No banking is compromised, etc. But I need to get some input into this. Are some of these known vulnerabilities?

Please help me!

---

### Post by cb951303 on 2008-11-17
it's probably a **weak** mail password. once he got to your mailbox he can get the other sites' password easily (i.e: facebook)

---

### Post by hyper_ch on 2008-11-17
are those your usernames and your passwords?

Did you use everywhere the same password?
What services was it? Do you always have the same username?
Is that actually your username?
Do you use those services listed?
...
...
...

Do you have noscript extension in firefox?
Do you have your password stored somewhere else?

---

### Post by kwaanens on 2008-11-17
I really hope so. I'm now using apg to generate new passwords for myself.

But however, wouldn't that be very time consuming for the hacker?
It's not like I keep much old mail linking me to online services on my Gmail account, so he would have to manually surf around. And some of the web areas compromised are not international services, but stuff you would need to really look for.

Come to think of it, I very much doubt this. One of the sites are really, really obscure for anyone to link me to. I didn't even remember it myself.

Please reply if anyone knows anything.

---

### Post by Kinstonian on 2008-11-17
All of the passwords probably share something in common.  Whether they were mentioned in an email when you registered an account, or your browser was configured to remember them, or you saved them to a file on your computer, or they were sniffed, etc.  However, if I were in your shoes, I would ask the the so called "good hacker" responsible for it rather than guess.

---

### Post by kwaanens on 2008-11-17
> **hyper_ch said:**
> are those your usernames and your passwords?

Did you use everywhere the same password?
What services was it? Do you always have the same username?
Is that actually your username?
Do you use those services listed?
...
...
...

Do you have noscript extension in firefox?
Do you have your password stored somewhere else?

No, I dont use noscript.
I have made backups earlier, and have not really destroyed them fully, but this needs to be at the most 1 year old.

I use 3-4 usernames. They check out.
Some passwords are the same. Things that are important have other passwords
The services are Gmail, Facebook, some work related, my local router (not the new one though). It looks as just part of a long list, so there might be others.

---

### Post by kwaanens on 2008-11-17
> **Kinstonian said:**
> All of the passwords probably share something in common.  Whether they were mentioned in an email when you registered an account, or your browser was configured to remember them, or you saved them to a file on your computer, or they were sniffed, etc.  However, if I were in your shoes, I would ask the the so called "good hacker" responsible for it rather than guess.

Yes, I have had  Firefox remember my passwords, etc. So I'm could def. have been more secure.
I would ask the hacker, but he sent the mail from my own account. If he was so good, he should have posted how he got in in the first place.

---

### Post by Kinstonian on 2008-11-17
> **kwaanens said:**
> Yes, I have had  Firefox remember my passwords, etc. So I'm could def. have been more secure.
I would ask the hacker, but he sent the mail from my own account. If he was so good, he should have posted how he got in in the first place.

He will probably check your email again either to see if you've changed your password, or looking for a response.

---

### Post by kwaanens on 2008-11-17
> **Kinstonian said:**
> He will probably check your email again either to see if you've changed your password, or looking for a response.

Probably.
Of course the first thing I did was get rid of some suspects (or extensions i really don't need, or now, trust completely), and changed the most important stuff.

---

### Post by buyyourall4 on 2008-11-17
[size=5][color=black]it is a windows operation system  [/color][/size][[size=5][color=black]chinese mobile phone[/color][/size]](http://www.buyyourall.com/)[size=5][color=black] , it makes people think of S1 of dopoda, just as the picture. Yes  the out-look is like dopoda S1 exactly, but the function is over S1 since it has wifi function. yet what amazy you is it`s low price, not over than 200USD, can you believe?  it is trueth.[/color][/size][size=5]now the request is over the offer, lots of orders from worldwide keep the factory busy in the manufacture without stop day and night.would you like the details? click the picture please.[/size][[img]http://www.buyyourall.com/syssite/home/shop/1/pictures/productsimg/big/1042.jpg[/img][size=5][color=sandybrown][/color][/size]](http://www.buyyourall.com)

---

### Post by Kinstonian on 2008-11-17
> **kwaanens said:**
> Probably.
Of course the first thing I did was get rid of some suspects (or extensions i really don't need, or now, trust completely), and changed the most important stuff.

Yeah, that's a good idea.  Since you can't really rule out that the so called hacker has access to your computer, you should look for some signs you've been compromised.  A pretty good checklist is the [CERT's Intruder Detection Checklist](http://www.cert.org/tech_tips/intruder_detection_checklist.html)

---

### Post by kwaanens on 2008-11-17
Actually, I googled myself and found the source to all this hazzle.

A couple of weeks ago, I helped debug some software, and openpasted the output. It looked as if the passwords were encrypted, but they were in fact easy to decode. The authors of the software were not aware of this either, but have been notified.

So, I now know the extent of the problem, and was able to change all passwords.

Let this be a lesson to anyone who reads this: Even though sensitive info is obfuscated, it might be reversible, and pose a security risk.

Thanks for all your help!

---

### Post by Sarmacid on 2008-11-18
Next time, remember you can see from which ip is your gmail account being accessed. This might not provide a lot of help since the hacker will probably be behind a proxy or some service to make him anonymous but it might give you an idea where he's from.

---

