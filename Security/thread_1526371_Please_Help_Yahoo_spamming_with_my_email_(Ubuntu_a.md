---
title: "Please Help: Yahoo spamming with my email (Ubuntu and Vista)"
date: 2010-07-07
forum: Security
---

### Post by UbuNoob001 on 2010-07-07
Hey all, please help me. I am new to Linux.  I dual boot 10.04_64 and Vista

Problem: My Email Address is spamming 


[SIZE="3"]Situation Chronology[/SIZE]: 
**1.**  I received an email (spam) on Yahoo Mail from someone who was not intending to send it.  (While it did go to spam folder, I did 'open' the email (since it came from a trusted sender) but it only contained a link (which because of WOT) I assumed was spam.)** I did NOT click the link. **

**2.** I then informed him that his email addy was spamming.

**3** Shortly thereafter, i noticed in Ubuntu (firefox) whenever I clicked "reply" to email back to someone,  there was a quick flash of letters/numbers in the slot where I would normally write. This instantly disappears and goes blank so I can write something, so I just figured it was a bug. *This is happening on BOTH windows and Ubuntu.*

**4** Now MY EMAIL is spamming people the people I write to.

So far: I have 1. Changed my Yahoo password 2. Deleted firefox 3.  In windows Ran Spybot/Search-Destory AVG  (turns up nothing) What else can I do? Anything I should do with Linux? Please help.

---

### Post by uRock on 2010-07-08
I would have the account closed and open a new one. It sounds like the account has been hijacked. A friend of mine recently had this happen with her Hotmail account and no matter what she does I still get an email linking me to a Canadian pharmaceutical site.

---

### Post by UbuNoob001 on 2010-07-08
> **uRock said:**
> I would have the account closed and open a new one. It sounds like the account has been hijacked. A friend of mine recently had this happen with her Hotmail account and no matter what she does I still get an email linking me to a Canadian pharmaceutical site.

uRock, ugh, thats a pain. Do you think that this "code"/text that shows up in the reply box instantaneously is nothing or do you think there could be something software oriented that is going on? Just curious given the situation with my friend. Note that his spam that was sent to me said "Yahoo! Auto Reply" as its subject.

---

### Post by uRock on 2010-07-08
Have you actually clicked to sign out of Yahoo, then clearing the cookies? In Firefox click on Tools,   then clear clear recent history and clear all. This may help, but I am not very positive about it.

---

### Post by UbuNoob001 on 2010-07-08
> **uRock said:**
> Have you actually clicked to sign out of Yahoo, then clearing the cookies? In Firefox click on Tools,   then clear clear recent history and clear all. This may help, but I am not very positive about it.

uRock, Thanks for your help so far. Yeah, I have -perhaps paranoid- deleted firefox and I plan to reinstall. I am currently, on the windows side, running virus scan. 


The issue (of me sending out the email) happened while using my Ubuntu 0S, however the guy's email that accidently spammed me today (I suppose I am now in his situation) was opened in Vista.

---

### Post by lookitseman on 2010-07-08
You can use an extension like NoScript or adblock to see what's running on the page, and block what doesn't look familiar.

---

### Post by lisati on 2010-07-08
As well as checking the Yahoo auto response (it should be listed under "mail options" on the Yahoo webmail page) there are other options.

Whatever you do, don't trust the "From" address in junk email - it's quite easily forged.

There are services like [Spamcop]("http://spamcop.net") which can help you trace suspicious emails, and figure out who to report them to. You might want to use such a service to double check that the "spam" really is from your friend.

---

### Post by UbuNoob001 on 2010-07-08
> **lisati said:**
> As well as checking the Yahoo auto response (it should be listed under "mail options" on the Yahoo webmail page) there are other options.

Whatever you do, don't trust the "From" address in junk email - it's quite easily forged.

There are services like [Spamcop]("http://spamcop.net") which can help you trace suspicious emails, and figure out who to report them to. You might want to use such a service to double check that the "spam" really is from your friend.


Lisati, I will look into that service. Does the text in the reply box that I see, just for an instant when i click "reply" seem to imply some sort of code? How would this be running both in Firefox Ubuntu and Firefox for Vista? Perhaps this has always been there but I kindof doubt it in that I just noticed it today, and today started the email issues.

---

### Post by Chris1274 on 2010-07-08
You might also do a GMER scan to see if you've been rootkit-ed

---

### Post by UbuNoob001 on 2010-07-08
> **Chris1274 said:**
> You might also do a GMER scan to see if you've been rootkit-ed


Is this something I should do in both Windows AND Linux? I have Rkhunter.  Note that the "spam" email that my friend sent I am *pretty sure* was opened on my Vista. I am positive however that the email sent from me was sent while I was logged into Ubuntu. (and I saw that odd text in the reply box (as listed above) in both Firefoxes (Vista and Ubuntu).

---

### Post by wacky_sung on 2010-07-08
I believe it can be the spammer mail come along with an auto script injection once you view into that email,create a cookie and infested your system.It will tag along your email account once every mail you have sent it out followby auto send through your contact list.I have seem such malwares going on in my friend account which affected system is Microsoft system but immune to Linux system.I believe you could be using dual boot system which prompting Ubuntu is affected.Otherwise i will very much appreciated if you can send the mail to me and i doubtful it will affect me.

---

### Post by OpSecShellshock on 2010-07-08
I doubt that the issue is on your local machine. It's probably in the Yahoo webmail interface somewhere. Someone I know had a similar issue a while back where she had these spam links showing up in the signature area after her real messages. What I ended up doing was going into the page where people can set up signatures for their messages and highlighting everything in that text field (even though to all appearances it was blank), then deleting everything I'd highlighted. For whatever reason it had to be done that way; if I just put the cursor there and tried to use backspace on individual characters nothing happened. Not sure how or why, but it worked.

---

### Post by UbuNoob001 on 2010-07-08
> **wacky_sung said:**
> .I believe you could be using dual boot system which prompting Ubuntu is affected.Otherwise i will very much appreciated if you can send the mail to me and i doubtful it will affect me.

I just want to make sure you dont get affected: you say that "which prompting Ubuntu is affected", but also ask that i send it to you "doubful it will affect me". Could you explain this? Thanks for your help 


> **OpSecShellshock said:**
> I doubt that the issue is on your local machine. It's probably in the Yahoo webmail interface somewhere. Someone I know had a similar issue a while back where she had these spam links showing up in the signature area after her real messages. What I ended up doing was going into the page where people can set up signatures for their messages and highlighting everything in that text field (even though to all appearances it was blank), then deleting everything I'd highlighted. For whatever reason it had to be done that way; if I just put the cursor there and tried to use backspace on individual characters nothing happened. Not sure how or why, but it worked.

Op, I have tried this and all signatures are still disabled. So currently this isnt the problem. Thanks for the continued assistance!

---

### Post by UbuNoob001 on 2010-07-08
Just an update: Malwarbytes (Win) turns up nothing. Rkhunter (10.04) only says one warning related to "Sudo" (might this be from when I changed my sudo timeout from 15 to 5 min? )

---

### Post by wacky_sung on 2010-07-08
> I just want to make sure you dont get affected: you say that "which  prompting Ubuntu is affected", but also ask that i send it to you  "doubful it will affect me". Could you explain this? Thanks for your  help The reason is that linux will not be so easily get infested with a virus/malware when you just opened out your email.In order for the script injection into your system and it must be vulnerable to it.Action like you have clicked on the link / you using wine/samba in Ubuntu which contributed to Window software /system.If so, only the window system are vulnerability without even the user intervention for the script to get executed.Most malware / virus writer will only write for window system because they know that linux is totally immune to it.

In order for the script to work,their victim is targeted for window user.First is auto injected their script into window system when they victim opened their email.Next,their victim unknowingly click on the link / delete the mail without realising that their mail cookie is being compromised.They continue to use their mail to send mail to their friends.Next the script will capture all the contact list and auto execute the spam.This type of spamming is similar to a worm.Apart from that,if you are using pop3,then your system may be a target of getting compromise.

Note: Pardon me for my english if i do not explain it well.

Much appreciated if you can send it to <snip/email].I just like to test it because i being testing on my system(Window / Linux) with all kinda virus so that i can improved myself in hardening or make it better.

---

### Post by UbuNoob001 on 2010-07-10
I am no longer being informed that my email is spamming. I have done a fresh install of Firefox on both Ubuntu and Vista as well as password changes. 
   
     Oddly, the instantaneous text flickering (in the reply box- see above) has started again. Very odd. I will try and upload a video of this phenomenon. 

    Because I am no longer having the spam issue, I will mark this thread as solved. 

   Many thanks to everyone.

---

### Post by lisati on 2010-07-10
> **UbuNoob001 said:**
> Lisati, I will look into that service. Does the text in the reply box that I see, just for an instant when i click "reply" seem to imply some sort of code? How would this be running both in Firefox Ubuntu and Firefox for Vista? Perhaps this has always been there but I kindof doubt it in that I just noticed it today, and today started the email issues.

I don't know how current the spamcop FAQ are, but they have a section on checking the email header information with Yahoo - I rarely use Yahoo's webmail. Have a look here: [http://www.spamcop.net/fom-serve/cache/23.html](http://www.spamcop.net/fom-serve/cache/23.html)

---

### Post by wacky_sung on 2010-07-11
> **UbuNoob001 said:**
> I am no longer being informed that my email is spamming. I have done a fresh install of Firefox on both Ubuntu and Vista as well as password changes. 
   
     Oddly, the instantaneous text flickering (in the reply box- see above) has started again. Very odd. I will try and upload a video of this phenomenon. 

    Because I am no longer having the spam issue, I will mark this thread as solved. 

   Many thanks to everyone.

Take my word,it is the window issue but not Linux.Try to refrain using dual boot otherwise it is tough to narrow down the issue.

---

