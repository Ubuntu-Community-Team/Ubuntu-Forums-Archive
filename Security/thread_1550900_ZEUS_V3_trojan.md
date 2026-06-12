---
title: "ZEUS V3 trojan"
date: 2010-08-11
forum: Security
---

### Post by welshmike on 2010-08-11
**Are we Ubuntu users vulnerable to the recent ZEUS V3 trojan** that has infected PCs of some 3000 bank customers and stolen some £675,000 from a British bank, 
See 
[http://www.eweekeurope.co.uk/news/zeus-v3-trojan-steals-675000-from-uk-bank-8928](http://www.eweekeurope.co.uk/news/zeus-v3-trojan-steals-675000-from-uk-bank-8928)

---

### Post by HPD2 on 2010-08-11
Likely not, I haven't looked at the particulars yet, but most viruses are made for windows as that's the most popular OS.

---

### Post by welshmike on 2010-08-11
I've seen and fixed so many infected PCs of friends and neighbours who run MS Windows that I will not be continuing with dual boot Ubuntu / XP soon and will be removing Windows from my PCs.

---

### Post by OpSecShellshock on 2010-08-11
Zeus 3 is Windows-only. However, there does not appear to be anything that Windows users can do to protect against it. A colleague has shown me part of the installation guide (not sure how it was obtained, or whether my colleague's source has anything other than the guide, though the packing and encryption of the binaries makes them useless for static analysis even if someone could get hold of them). If it works as advertised, then it renders access controls irrelevant. Careful out there.

---

### Post by bodhi.zazen on 2010-08-11
> **HPD2 said:**
> Likely not, I haven't looked at the particulars yet, but most viruses are made for windows as that's the most [s]popular[/s] exploitable OS.

Fixed that for you :lolflag:

Writing code that acts as a "virus" is possible in Linux, but it is much more difficult.

---

### Post by wacky_sung on 2010-08-12
_**Interesting**_
[Zeus botnet raid on UK bank accounts under the spotlight]("http://www.theregister.co.uk/2010/08/11/zeus_cyberscam_analysis/")
```
Zeus botnet raid on UK bank accounts under the spotlight
Alert Print Post comment Retweet Facebook
More details of sophisticated cyber-blag emerge
By John Leyden • Get more from this author

Posted in Crime, 11th August 2010 12:35 GMT
Analysis More details have emerged of how security researchers tracked down a Zeus-based botnet that raided more than $1m from 3,000 compromised UK online banking accounts.

Bradley Anstis, vice president of technical strategy for M86 Security which discovered the attack, said hackers began the assault by loading compromised third-party sites with a battery of exploits designed to infect visiting PCs with variants of the Zeus banking Trojan.

Phase one of the attack used the Eleonore Exploit Kit and the Phoenix Exploit Kit to load Zeus onto compromised machines through a battery of browser and application-based vulnerabilities and drive-by download attacks. The main attack revolved around the use of version 3 of Zeus to steal money from online bank accounts.

Version 3 of Zeus is focused on stealing the login credentials of online bank accounts. Older versions also snaffled user names and passwords for social networking sites and online services as well as online banking credentials.
```

---

### Post by welshmike on 2010-08-12
More on how ZEUS V3 works **and much more** in [***_this M86 Security PDF_***]("http://www.m86security.com/documents/pdfs/security_labs/cybercriminals_target_online_banking.pdf")

"Administration Panel
**In addition to the included exploits**, the author of the toolkit enables his customers to review and analyze incoming traffic."

See Figure 3: Exploit statistics organized by the operating system of the incoming machines and amount of successful exploits divided by the exploit&#8217;s name.

of note is "Linux 359"

There does not appear to be very much you can do to stop being infected if you happen to visit infected websites. It may be that stopping your browser from running JavaScript will help protect you. Firefox has a NoScript add on to control this.

---

### Post by rookcifer on 2010-08-12
> **welshmike said:**
> More on how ZEUS V3 works **and much more** in [***_this M86 Security PDF_***]("http://www.m86security.com/documents/pdfs/security_labs/cybercriminals_target_online_banking.pdf")

"Administration Panel
**In addition to the included exploits**, the author of the toolkit enables his customers to review and analyze incoming traffic."

See Figure 3: Exploit statistics organized by the operating system of the incoming machines and amount of successful exploits divided by the exploit&#8217;s name.

of note is "Linux 359"

There does not appear to be very much you can do to stop being infected if you happen to visit infected websites. It may be that stopping your browser from running JavaScript will help protect you. Firefox has a NoScript add on to control this.

I'm skeptical.  I would like to see one example of a Linux box being infected with this trojan.  Just one.  There are millions of Linux users in the world, so it shouldn't be too hard to find one example.  And I would especially love to see an example of a Linux box being infected via a drive-by download.

Now, I don't doubt that the C&C servers are Linux boxes, but that is not the same thing.

---

### Post by wacky_sung on 2010-08-12
> **rookcifer said:**
> I'm skeptical.  I would like to see one example of a Linux box being infected with this trojan.  Just one.  There are millions of Linux users in the world, so it shouldn't be too hard to find one example.  And I would especially love to see an example of a Linux box being infected via a drive-by download.

Now, I don't doubt that the C&C servers are Linux boxes, but that is not the same thing.

I do not know what type of trojan you want from Linux box but there is one down [here]("http://vx.netlux.org/src_view.php?file=woolien.zip").Most credit card servers run on customize linux / Unix(hardened) and it depend on the infrastructural of the network connecting to it.


Don't be surprise that ATM machine is running on Window CE.

See [here]("http://www.fiercecio.com/techwatch/story/black-hat-atm-hack-has-implications-beyond-financial-sector/2010-07-30") for ATM OS.

Short video clip [link]("http://it.toolbox.com/blogs/securitymonkey/blackhat-2010-video-the-atm-hack-and-jackpot-40245") of the hack.

---

### Post by rookcifer on 2010-08-12
> **wacky_sung said:**
> I do not know what type of trojan you want from Linux box but there is one down [here]("http://vx.netlux.org/src_view.php?file=woolien.zip").Most credit card servers run on customize linux / Unix(hardened) and it depend on the infrastructural of the network connecting to it.

Those are trojans specifically designed for Linux.  What the PDF linked in the previous post says is that Zeus is able to target Windows, OSX, Linux, Sun OS, Nintendo Wii, Playstation 3, and others.  I somehow doubt that a single trojan is targeting all of these OS's.  They are all designed differently and require different access permissions, etc., in order for a keylogger to work.

The above linked PDF is the only source I have seen that claims any OS other than Windows is affected by Zeus.  Therefore, I think they are simply mistaken (or perhaps we are mistaken in our interpretation of what page 4 really means).


> Don't be surprise that ATM machine is running on Window CE.

Not quite sure what ATM's running on Windows have to do with this discussion.

---

### Post by cariboo on 2010-08-12
The ATM exploit depends on having access to the electronics, for most banks, at least here in Canada ATMs are kept in a securely locked room inside the bank. For the inexpensive stand-alone type, you still have to have access to the electronics, which is pretty hard to do if it is located in a busy location.  Like anything in security, you have to have physical access in order to use the exploit. 

I worked for NCR in the 90's, servicing ATMs, I remember the change-over from OS/2 to NT, if I remember correctly the install was on 12-15 floppies, and took a couple of hours to complete.

---

### Post by wacky_sung on 2010-08-12
> **cariboo907 said:**
> The ATM exploit depends on having access to the electronics, for most banks, at least here in Canada ATMs are kept in a securely locked room inside the bank. For the inexpensive stand-alone type, you still have to have access to the electronics, which is pretty hard to do if it is located in a busy location.  Like anything in security, you have to have physical access in order to use the exploit. 

I worked for NCR in the 90's, servicing ATMs, I remember the change-over from OS/2 to NT, if I remember correctly the install was on 12-15 floppies, and took a couple of hours to complete.

I believe each country has their own system of running ATM.

Look at the date prior before the demostration of ATM hack, Singapore bank has been affected.No sure if there is a link or leak of source of exploits to the public.

[http://sg.news.yahoo.com/afp/20100731/ttc-us-it-internet-bank-software-crime-d-0de2eff.html](http://sg.news.yahoo.com/afp/20100731/ttc-us-it-internet-bank-software-crime-d-0de2eff.html)

```
Jack proved his findings using two kinds of ATMs typically found in corner stores, bars or other "stand-alone" venues in the United States but said the flaw likely exists in machines at banks.

Banks use "remote management" software to monitor and control their ATMs, and Jack used a weakness in that kind of code to take control of machines by way of the Internet.

He found a way to bypass having to submit passwords and serial numbers to access ATMs remotely. Once in the machines, he could command them to spit out cash or transfer funds.

He could also capture account data from magnetic strips on credit or bank cards as well as passwords punched in by ATM users.

"When you think about ATM security you generally think about the hardware side; is it bolted down and are the cameras in position," Jack said.

"This is the first time anyone has taken the approach of trying to attack the underlying software. It is time to find software defenses rather than hardware defenses."
```

---

### Post by TNT1 on 2010-08-12
> **wacky_sung said:**
> I believe each country has their own system of running ATM.



Yeah, in South Africa, the common practice is to  use stolen mining explosives to attempt to gain entry to the ATM and thereby steal cash...

---

### Post by welshmike on 2010-08-12
> **wacky_sung said:**
> I do not know what type of trojan you want from Linux box but there is one down [here]("http://vx.netlux.org/src_view.php?file=woolien.zip").Most credit card servers run on customize linux / Unix(hardened) and it depend on the infrastructural of the network connecting to it.


Don't be surprise that ATM machine is running on Window CE.

See [here]("http://www.fiercecio.com/techwatch/story/black-hat-atm-hack-has-implications-beyond-financial-sector/2010-07-30") for ATM OS.

Short video clip [link]("http://it.toolbox.com/blogs/securitymonkey/blackhat-2010-video-the-atm-hack-and-jackpot-40245") of the hack.

wacky, why is your "here" link pointing to a zip file? Makes me think that it could be an exploit attempt. Also that video of the supposed ATM spewing out stuff is not at all convincing. What is it supposed to show about hacks.

Edit: Ah! I see from you later post what you meant.

---

### Post by cariboo on 2010-08-12
The machines I worked on had 4" hardened steel safes, bolted to concrete floors with 18" bolts. We had an incident at one of the banks where the only two people that had the combination to the safe were away for two weeks, so they had to get a locksmith in to drill out the lock, it took him well over an hour to drill it out.

---

### Post by wacky_sung on 2010-08-12
> **welshmike said:**
> wacky, why is your "here" link pointing to a zip file? Makes me think that it could be an exploit attempt. Also that video of the supposed ATM spewing out stuff is not at all convincing. What is it supposed to show about hacks.

Edit: Ah! I see from you later post what you meant.

Sorry the post about the ATM hack went offtrack.

Just that i wanna highlight that there is trojan (or exploits in which you wanna called it) written for Linux.

> **rookcifer said:**
> What the PDF linked in the previous post says is that Zeus is able to target Windows, OSX, Linux, Sun OS, Nintendo Wii, Playstation 3, and others.  I somehow doubt that a single trojan is targeting all of these OS's.  They are all designed differently and require different access permissions, etc., in order for a keylogger to work.

I fully agreed.

---

### Post by OpSecShellshock on 2010-08-12
Some of the exploit packs that are used to deliver the bot do include OSX exploit code as well, but I'm not sure that they have the capability of going beyond the exploit stage and actually installing malicious software. There are Mac-only botnets, but I've never heard of a mixed-platform botnet or trojan. Wouldn't surprise me, of course, due to the low cost of the software and the speed with which an entire exploit pack can hit a system.

Another important thing to consider is that the exploit packs have built-in metrics-gathering capability, and they will break their statistics down by things like the OS, the application exploited, and whether or not the installation succeeded. So if someone infiltrated the criminal network and took a peek at their metrics, they would likely see Linux machines on the list of targets hit by their exploit sites (because web browsers are cross-platform). However, that doesn't mean there was a successful deployment of the next stage attack.

---

### Post by rookcifer on 2010-08-12
> **OpSecShellshock said:**
> Another important thing to consider is that the exploit packs have built-in metrics-gathering capability, and they will break their statistics down by things like the OS, the application exploited, and whether or not the installation succeeded. So if someone infiltrated the criminal network and took a peek at their metrics, they would likely see Linux machines on the list of targets hit by their exploit sites (because web browsers are cross-platform). However, that doesn't mean there was a successful deployment of the next stage attack.

Yep.  Browser exploits typically work the same way no matter the OS, so one can target them all with one exploit.  **However**, the difference is in what happens with the payload -- it's going to have to be tailored for each OS.  Installing a keylogger on Linux is not the same as installing one on Windows or the Playstation.  (I contend it is not possible to install a keylogger on Linux without root access.  I could be wrong, but no one has ever shown me how, and I have asked a lot of people).

---

### Post by bodhi.zazen on 2010-08-12
> **rookcifer said:**
>   (I contend it is not possible to install a keylogger on Linux without root access.  I could be wrong, but no one has ever shown me how, and I have asked a lot of people).

I do not intend to come across as rude, but ...

You are wrong on this and have been told so by several experienced users ( I have seen you discuss this on another recent thread as well).

People will not show you how to do that on these forums, these forums are for Ubuntu support, not cracking or proof of concept.

google search for your question.

---

### Post by rookcifer on 2010-08-12
> **bodhi.zazen said:**
> I do not intend to come across as rude, but ...

You are wrong on this and have been told so by several experienced users ( I have seen you discuss this on another recent thread as well).

If I am wrong, you are welcome to send me a POC keylogger privately to my e-mail address or find someone who will.  Lots of people love to say I am wrong but never say *why*.

I have challenged people in the other thread you mentioned and had one guy PM me about it.  Unfortunately, he only showed how to install something to the user account, but installing something to a user account is not the issue (that's easy)-- installing a **keylogger** to the user account is.  No one, including him, has illustrated how to do this.

> google search for your question.

Oh, I have and all of the keyloggers I have ran across require root access to install themselves.

Again, it might be possible to do.  I have heard many theories on how to do it, ranging from using xinput to using a wrapper around Xorg, to messing around with .bashrc.  Still no one out there seems to have created a working version that I can find.  You would think someone somewhere would have done so if it were easy.  Again perhaps they have, but I can't find it.

---

### Post by wacky_sung on 2010-08-13
> **rookcifer said:**
> If I am wrong, you are welcome to send me a POC keylogger privately to my e-mail address or find someone who will.  Lots of people love to say I am wrong but never say *why*.

I have challenged people in the other thread you mentioned and had one guy PM me about it.  Unfortunately, he only showed how to install something to the user account, but installing something to a user account is not the issue (that's easy)-- installing a **keylogger** to the user account is.  No one, including him, has illustrated how to do this.



Oh, I have and all of the keyloggers I have ran across require root access to install themselves.

Again, it might be possible to do.  I have heard many theories on how to do it, ranging from using xinput to using a wrapper around Xorg, to messing around with .bashrc.  Still no one out there seems to have created a working version that I can find.  You would think someone somewhere would have done so if it were easy.  Again perhaps they have, but I can't find it.

When you define trojan in the eariler thread which may have similar function as a keylogger.In actual the implant of each trojan horse is depending on the OS being implemented.

_**[COLOR="DeepSkyBlue"][Definition of Trojan Horse]("http://en.wikipedia.org/wiki/Trojan_horse_(computing)") [/COLOR]**_
```
A Trojan horse, or Trojan, is malware that appears to perform a desirable function for the user prior to run or install but instead facilitates unauthorized access of the user's computer system. "It is a harmful piece of software that looks legitimate. Users are typically tricked into loading and executing it on their systems", as Cisco describes.
```

**_[Definition of Keylogger]("http://en.wikipedia.org/wiki/Keystroke_logging")_**
```
Keystroke logging (often called keylogging) is the action of tracking (or logging) the keys struck on a keyboard, typically in a covert manner so that the person using the keyboard is unaware that their actions are being monitored.
```

As what you trying to determine that a malware / virus has a tracking capability is usually implemented as a [COLOR="Red"]tracking cookie[/COLOR] in a browser.A tracking cookie can also be OS independent recording all logins and sent it back the information it owner.It act like a keylogger without even being installed into any system.

**_[HTTP cookie]("http://en.wikipedia.org/wiki/HTTP_cookie")_**
```
A cookie, also known as a web cookie, browser cookie, and HTTP cookie, is a piece of text stored by a user's web browser. A cookie can be used for authentication, storing site preferences, shopping cart contents, the identifier for a server-based session, or anything else that can be accomplished through storing text data.
```

---

### Post by cariboo on 2010-08-13
What is this fascination that ex-Windows users seem to have with keyloggers? In all my years making Windows work properly, I've never run into a keylogger installed on a home computer. I have installed hardware keyloggers for customers while working for NCR/ATT at the customers request.

---

### Post by bodhi.zazen on 2010-08-13
> **cariboo907 said:**
> What is this fascination that ex-Windows users seem to have with keyloggers? In all my years making Windows work properly, I've never run into a keylogger installed on a home computer. I have installed hardware keyloggers for customers while working for NCR/ATT at the customers request.

Because some people have had a malicious key logger installed on Windows. It is a disaster if you are then the victim of identity theft (I saw this on a close associate keylogger -> bank account drained, credit card maxed out. It was fixed, but it took some time).

Again, if you know what you are doing in Windows this is less likely, but, many "casual" windows users do not pay any attention to security.

---

### Post by wacky_sung on 2010-08-13
> **bodhi.zazen said:**
> Because some people have had a malicious key logger installed on Windows. It is a disaster if you are then the victim of identity theft (I saw this on a close associate keylogger -> bank account drained, credit card maxed out. It was fixed, but it took some time).

Again, if you know what you are doing in Windows this is less likely, but, many "casual" windows users do not pay any attention to security.

I think it is more than just a window user but any OS user need to have some simple understanding to distinguish the difference between a keylogger, phishing site, tracking cookie and trojan.They may have simple function to keylog but the way of applying it is difference.

---

### Post by bodhi.zazen on 2010-08-13
> **wacky_sung said:**
> I think it is more than just a window user but any OS user need to have some simple understanding to distinguish the difference between a keylogger, phishing site, tracking cookie and trojan.They may have simple function to keylog but the way of applying it is difference.

Not really.

Key logger on windows is much more trivial then installing a key logger on Linux.

Key loggers on Linux can be done, but it takes some effort.

Try it for yourself on both Windows and Linux and you will see. I have not use Windows in some time so perhaps they tightened up on this, but when I was using windows last installing a key logger was fairly trivial (as these things go that is , obviously grey/black hat stuff is not for new users).

---

### Post by wacky_sung on 2010-08-13
> **bodhi.zazen said:**
> Not really.

Key logger on windows is much more trivial then installing a key logger on Linux.

Key loggers on Linux can be done, but it takes some effort.

Try it for yourself on both Windows and Linux and you will see. I have not use Windows in some time so perhaps they tightened up on this, but when I was using windows last installing a key logger was fairly trivial (as these things go that is , obviously grey/black hat stuff is not for new users).

Yeah i do agree of what you mentioned as i did it countless times.The problem in which i have encountered is that people get all mixed up of keylogger with phishing site(commonly use by real cyber criminal to steal the data which often found through the credit card transaction online), tracking cookie commonly used by malware writer in which is silently steal your data without you realise it) and trojan(usually found window OS but most malicious hack now move toward website injecting trojan into their victim system by using script) as all of them have the keylogging ability

---

### Post by cariboo on 2010-08-13
If you are going to use coloured font for emphasis, please use colours that are readable by all users.

Most of us here are well aware of the differences between a keylogger and a phishing site. Most of what you are talking about affects Windows, but it very rarely happens when running a Linux variant.

If you want to protect your Windows users, give them all limited user accounts, that will go a long way to protecting the average user.

---

### Post by rookcifer on 2010-08-13
> **wacky_sung said:**
> 
As what you trying to determine that a malware / virus has a tracking capability is usually implemented as a [COLOR="Red"]tracking cookie[/COLOR] in a browser.A tracking cookie can also be OS independent recording all logins and sent it back the information it owner.It act like a keylogger without even being installed into any system.



Uh, a tracking cookie is not going to get you the root password.  That is what I am concerned with as I thought I made clear in previous posts.

---

### Post by wacky_sung on 2010-08-14
> **rookcifer said:**
> Uh, a tracking cookie is not going to get you the root password.  That is what I am concerned with as I thought I made clear in previous posts.

Indeed you are right.Those tracking cookie will not get the root but what it did is only capture login data within a browser.

---

