---
title: "Secure Browsing via Live CD"
date: 2010-03-02
forum: Security
---

### Post by TRG1 on 2010-03-02
I have a home network with 4 computers all windows.  Two are used primarily for browsing.  Keeping up with security issues is a bit of a hassle; it uses up computer capacity and they must be updated all the time. So, I'm intrigued by the possibility of converting one or two of my computers to just run off the CD. I have booted one up on ubuntu right now and it seems find for just looking around and reading stuff, but what are the limitations and how does one deal with them? Email could be all done with browser based mail which we do mostly anyway. One concern I have is not being able to view movies, etc. Information which needs to be downloaded can be download to a network drive where it can be checked before use.

I'm just interested in hearing more about this from people who have some experience and know how.

Thanks in advance.

Tom

---

### Post by Ghost|BTFH on 2010-03-02
> **TRG1 said:**
> I have booted one up on ubuntu right now and it seems find for just looking around and reading stuff, but what are the limitations and how does one deal with them? Email could be all done with browser based mail which we do mostly anyway. One concern I have is not being able to view movies, etc. Information which needs to be downloaded can be download to a network drive where it can be checked before use.

I'm just interested in hearing more about this from people who have some experience and know how.

Thanks in advance.

Tom

Nothing can be saved to the CD.  That's your biggest limitation right there.

Second - nothing could be installed for more than a session.

A better solution would be running it off a flash drive - more room, you can create a partition for storage, save settings, etc.

The best solution is the one I'm wondering why you're not doing anyhow - if Windows is such a pain on the ones used for surfing the net and email, why not just install Ubuntu and be done with it?

It would be far more logical to do it that way, or at the very least use WUBI and install it from Windows, thus giving you dual boot without the hassle of dual booting/partitioning.

Just a few thoughts on the matter.

Cheers,
Ghost|BTFH

---

### Post by OpSecShellshock on 2010-03-02
The primary point of booting from a live CD for browsing is to conduct the more sensitive business in those sessions (things of a private, medical, or financial nature). Other, more casual browsing would still be done under a regular setup. Ideally, you wouldn't check webmail or view videos or do casual surfing from the same session as that during which sensitive business is conducted. It's about separating web-based activities so that the riskier (but more fun!) parts don't interfere with or even touch the systems used for the important stuff.

---

### Post by bodhi.zazen on 2010-03-03
Just curious why you feel a live CD is necessary for secure browsing ?

---

### Post by uRock on 2010-03-03
I agree that the thumb drive install would be the way to go, but if you are trying to do something where you just don't want a trail, then yes the LiveCD is the way to go.

---

### Post by Ghost|BTFH on 2010-03-03
My bet is he just wants to use it for browsing pr0n.

>.>

Cheers,
Ghost|BTFH

---

### Post by cdenley on 2010-03-03
Using a livecd is NOT secure. You won't be able to keep your browser current with security updates. Instead, use a guest session. The guest user's home directory will only be written in memory, which should be the only place any sensitive data gets stored.

---

### Post by TRG1 on 2010-03-03
Thank you all for your replies.  Perhaps I should elaborate a little more.  First, I have a pathological aversion to updates so if I'm just running off a cd, it will still have to be updated, but that would only be done as often as needed to maintain reasonable browser performance.  The idea that I don't have the latest flash animation or whatever doesn't concern me too much.  If I need to save something to disk, I can put it on a network drive where it will be inspected by antivirus before use. Some things just cannot be avoided.  Part of the problem is just the hard drive, irrespective of the OS.  They accumulate stuff and need some regular maintenance, plus this is where malware goes to roost. Without the HDD + OS if your computer gets a bug or hangs, you just reboot and all the bad stuff is gone. 

Some of my security concerns stem from recent credit card problems. I use the CC a lot on line and never had any problems until a couple of months ago.  An online company I do business with had their CC files stolen and my number was among them so the CC company was informed and immediately issued me a new number.  A hassle.  Now, almost immediately upon getting the new number, there was an attempt at fraudulent use so I'm getting yet another number... more hassle.  This is not likely to cost me anything, but it's a real nuisance. I don't know if any of this was due to lack of security on my home network, but I don't think so.  I did get a bug a couple of months ago, but it was while traveling. 

Someone suggested I just install ubuntu. What is the general practice among linux users re anti-virus software.  Necessary or not?

I would imagine that you could still create security problems running from a cd but you would have to be extremely negligent for that to occur.

Thanks again for the feedback.

---

### Post by cdenley on 2010-03-03
While using the guest account, any changes made will be lost after logging out. The home direcory is not located on the hard disk, but in memory. The guest user will not be able to write anything malicious to the hard drive, except maybe in /tmp, but you can easily mount that with tmpfs as well. The guest account is a great compromise between a regular install and a livecd.

Keeping updates installed is not to give you "the latest flash animation or whatever", but to protect you from known vulnerabilities which could compromise your session or profile.

Virus scanners will not look for linux viruses, only windows viruses, since there aren't really any linux viruses to look for. There can still be malicious software, though, so don't install anything from outside the ubuntu repo's. You can use tools which check for rootkits, but I don't think it is necessary on a typical desktop system if you follow common sense.

A livecd has the same security as a regular install (maybe a little less since sudo doesn't require a password). The only difference is anything bad will not persist after a reboot.

---

### Post by tubbygweilo on 2010-03-03
cdenley, I like the idea of using the guest account as up to now this had not occurred to me and I would have selected a live CD as the way to go. 

Thanks for your insight.

---

### Post by bodhi.zazen on 2010-03-03
> **TRG1 said:**
> Thank you all for your replies.  Perhaps I should elaborate a little more.  First, I have a pathological aversion to updates so if I'm just running off a cd, it will still have to be updated, but that would only be done as often as needed to maintain reasonable browser performance.  The idea that I don't have the latest flash animation or whatever doesn't concern me too much.  If I need to save something to disk, I can put it on a network drive where it will be inspected by antivirus before use. Some things just cannot be avoided.  Part of the problem is just the hard drive, irrespective of the OS.  They accumulate stuff and need some regular maintenance, plus this is where malware goes to roost. Without the HDD + OS if your computer gets a bug or hangs, you just reboot and all the bad stuff is gone. 

Linux is not windows and much of this is a non-issue on Linux.

> Some of my security concerns stem from recent credit card problems. I use the CC a lot on line and never had any problems until a couple of months ago.  An online company I do business with had their CC files stolen and my number was among them so the CC company was informed and immediately issued me a new number.  A hassle.  Now, almost immediately upon getting the new number, there was an attempt at fraudulent use so I'm getting yet another number... more hassle.  This is not likely to cost me anything, but it's a real nuisance. I don't know if any of this was due to lack of security on my home network, but I don't think so.  I did get a bug a couple of months ago, but it was while traveling. 

I hope you understand that this has nothing to do with if you are running from a live CD or hard drive install ?

When performing online transactions you need to use ssl (https) and be care ful of Phishing.

If your financial institution is cracked, it does not matter what OS you are running.

In terms of security updates, again this is not windows and IMO updates are critical. As indicated by cdenley you are actually less secure.

> Someone suggested I just install ubuntu. What is the general practice among linux users re anti-virus software.  Necessary or not?

I would imagine that you could still create security problems running from a cd but you would have to be extremely negligent for that to occur.

Thanks again for the feedback.

I understand your concerns, but this is not Windows ...

The good news, the vast majority of these things are essentially a non-issue (no need for antivirus, no need for anti-spyware, no need for defragmentation, updates go much much smoother and actually fix problems, more frequent security updates, and there is really not much a need to "clean" system files of "junk").

I suggest you perform a HD install and perform automatic "security only" updates.

I highly suggest you read the following threads:

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

[Ubuntu Forums - View Single Post - General Security ?]("http://ubuntuforums.org/showpost.php?p=8620985&postcount=236") 

You can enable your firefox apparmor profile with 2 commands :

```
sudo apt-get install apparmor-profiles
sudo aa-enforce firefox
```

You may wish to:

```
sudo aa-enforce /etc/apparmor.d/*
```

---

### Post by uRock on 2010-03-03
I prefer just having a full install and utilizing the Private Browsing option in Firefox.

---

### Post by Ijan on 2010-03-03
As ponited out before regular updates are essential as unpatched security flaws would be the most common way for malware to attack your system.

From that point of view choosing a well maintainded but not too commonly used browser might bear additional advantages.

Another way to combine the necessary security of regular updates and the reboot-all-gone apporach is provided by virtualisation software that let's you choose to revert to the state you booted your virtual machine in or to update permanently.

Another alternative was using a thumbdrive with hardware wirte protection.

Then keeping the system you use for online shopping lean with only few an trusted pieces of software installed and using another system for experimentig and trying out stuff might add to your security as well.

---

### Post by TRG1 on 2010-03-03
The guest session does look like it should be the thing.  Thanks for pointing that out.

tom

---

### Post by rookcifer on 2010-03-03
OP,

Just install VirtualBox on your Windows machine and then install Ubuntu as a guest OS.  That way, you will have all the benefits of a LiveCD without the slow speed or lack of updates.

---

### Post by mihalisla on 2010-03-03
Please , could someone tell me how to make a guest account under ubuntu?
How a guest account can be more secure?

---

### Post by cdenley on 2010-03-03
> **mihalisla said:**
> Please , could someone tell me how to make a guest account under ubuntu?
How a guest account can be more secure?

1. Make sure you have the "Indicator Applet Session" at the top of your desktop. Recent installs have it by default.

2. Click the applet, select "Guest Session".

It is more secure because any changes (possibly malicious) will not be persistent. It is probably more about protecting privacy.

---

### Post by Objekt on 2010-03-03
> **TRG1 said:**
> Some of my security concerns stem from recent credit card problems. I use the CC a lot on line and never had any problems until a couple of months ago.  An online company I do business with had their CC files stolen and my number was among them so the CC company was informed and immediately issued me a new number.  A hassle.  Now, almost immediately upon getting the new number, there was an attempt at fraudulent use so I'm getting yet another number... more hassle.  This is not likely to cost me anything, but it's a real nuisance. **I don't know if any of this was due to lack of security on my home network, but I don't think so.** 

I don't think so either.  You see, the real problem is twofold:

1) we have a stupid financial system, where the information necessary to commit fraud (CC number) must be protected, yet must also be shared to do business.  That leads us to...

2) it's other people whose screwups expose you to fraud.  Either using your info fraudulently themselves, or protecting it poorly, so that third parties are able to get your info.

Changing how you use your computers won't address either problem.  Although it is good to keep systems patched & use a firewall, the vast majority of CC fraud does not happen by a clever cracker breaking into your computer by remote control.  The effort to do so would be large, and the reward limited, for the would-be fraudster.  Rather, criminal organizations target banks and businesses, which aggregate large amounts of CC info and do a lousy job protecting it (maybe that's problem #3).

Trying to do everything in a Live CD or guest account is only going to be a lot of bother for little benefit.  About the only positive will be absence of a data trail on your computer.  But do you really plan to not store ANY sensitive info at home?  That just means you are trusting someone else to protect it - which, as discussed above, is the weak spot.

On that note, have you ever used TrueCrypt?  It is possible to store your sensitive information in such a way that someone else won't even know it's there, let alone get at it.

---

### Post by mihalisla on 2010-03-03
Sorry not mentioning that I use kubuntu.
I cannot find the indicator...
Is there any other way around it?

---

### Post by cdenley on 2010-03-04
> **mihalisla said:**
> Sorry not mentioning that I use kubuntu.
I cannot find the indicator...
Is there any other way around it?

It is an applet with your username on it in the panel at the top. If it is missing, right-click the panel, select "Add to Panel", add "Indicator Applet Session". At least that is for gnome. Don't know about KDE.

---

### Post by uRock on 2010-03-04
Is it not easier to just use the Private Browsing option in Chrome or Firefox like mentioned in PCWorld Magazine?

---

### Post by cdenley on 2010-03-04
> **iRock said:**
> Is it not easier to just use the Private Browsing option in Chrome or Firefox like mentioned in PCWorld Magazine?

I'm not very familiar with the technical details, but I'm guessing the "Private Browsing" option writes data to disk as usual, but deletes it after the session ends. For the very paranoid, this may be unacceptable since that data can still be recovered after deletion. I guess as it relates to this thread, though, the data would be safe from remote attackers or malware, since usually physical access is needed to recover deleted files.

---

### Post by bodhi.zazen on 2010-03-04
> **cdenley said:**
> I'm not very familiar with the technical details, but I'm guessing the "Private Browsing" option writes data to disk as usual, but deletes it after the session ends. For the very paranoid, this may be unacceptable since that data can still be recovered after deletion. I guess as it relates to this thread, though, the data would be safe from remote attackers or malware, since usually physical access is needed to recover deleted files.

To add a little to your post,

I would have to look under the hood, but from this page :

[http://support.mozilla.com/en-US/kb/Private+browsing](http://support.mozilla.com/en-US/kb/Private+browsing)

> 
Firefox 3.5 and later provide "Private Browsing," which allows you to  browse the Internet without Firefox saving any data about which sites  and pages you have visited. 
  **Note**: Private Browsing prevents  information from being recorded on your computer. It does not make you  anonymous on the Internet.

Lower in the page is a list of things which are not retained, including cached pages, cookies, passwords, downloads, etc

Again , if they are in RAM or "somewhere" on the Hard drive, I do not know.

---

### Post by ray33 on 2010-03-05
Thanks for this discussion. I am using Vista + Firefox for my usual browsing, and Ubuntu 9.10 Live CD for my banking.

1) from the above I gather that it is very important to keep OS and browser updated, which obviously is difficult from live CD. Why is it that important, if I only go to my bank's website with the live CD? If the bank's website is compromised enough to install malware to my system or track my keystrokes etc., I would expect my account within the bank would be compromised as well, no matter how up-to-date my OS and browser are.

2) I would like to install Ubuntu to my hard drive, at first as a dual boot with vista and hopefully later get rid of Windows altogether. Would having Ubuntu all the time on my hard drive actually make me less secure using my live CD for banking? My concern here is that malware in Ubuntu on the hard drive could keylog etc. on my live CD banking sessions.

Your comments will be greatly appreciated, as always.

---

### Post by Ijan on 2010-03-05
ray33: Keeping in mind that there is no 100% secure way to use homebanking, only more or less secure ways, what you do is a pretty secure practice but it still has the possible drawback of an unpatched browser or system you mentioned yourself.

1 - Your Bank account/the banks server is probably protected, kept up to date and monitored by professionals. Your personal PC and Browser isn't so it's probably easier to compromise than your bank's system. Sometimes it is enough to inject a short line of code into a website which could be done by modifing third party ad banners placed there or misusing user comments on your bank's site. Another way could be attacking the line of communication e. g. at a public hot spot. In all those cases the attacker does not have to gain priviledged access to the bank's servers. He probably just legally bought some advertising space or posted "I love this bank ="€²3~{3>[[[" into some shoutbox. After compromising the victim's system he transfers money in the ordinary way, using the victim's credentials. That's why keeping your browers and OS patched is so important.

2 - No, when you boot up an ordinary live CD, your HD should not be touched unless you configure your live system to share data with it. Any possible keylogger - anyway an uncommon thing on linux systems - would sleep idly on your hard drive as long as your live system is used.

Judging from my imperfect knowledge of online fraud statistics I'd say that malware resinding on an installed linux system is the less likely thing to an attack on an unpatched browser. Not that linux distributions were perfectly safe. AFAIK criminals merely ignore them an attack more widespread platforms ATM. This means I'd consider an up to date an well configured system installed to your hd more safe than a out of date live CD.

---

### Post by ray33 on 2010-03-06
Thanks for good insights Ijan. 
I am still trying to get my head around the actual attack, which would need to happen from a third party ad or a discuccion forum:

1) I boot my live CD, always on my own computer only

2) I only go to my bank's website

3) my greatest fear is the log in, but at the time of the log in the third party attacker is not yet in my system

4) I encounter a third party ad or discussion site inside my bank's website? I have never yet noticed anything like that on a bank's website, the ads are strictly their own. It sounds to me like a massive security breach on the bank's side if there is an attacker waiting to pounce inside their own webpages. On a stockbroking site this might be feasible for the attacker, but even then he would need to compromise one of the stock market sites

5) I am just doing the regular banking stuff, but clicking on something like transfer money -button would allow the attacker to find a security breach on my unupdated OS or browser and inject a 
malicious code. Where does he inject it? It cannot go to the CD itself, so it goes to RAM memory? Can the attacker utilise the RAM memory to get relevant info to access my accounts? 

6) What about all the encryption that the bank is no doubt doing, how will the attacker get around that?

Thanks again for your answer. If you can help me with the above, it will be greatly appreciated

---

### Post by cdenley on 2010-03-06
> **ray33 said:**
> 
5) I am just doing the regular banking stuff, but clicking on something like transfer money -button would allow the attacker to find a security breach on my unupdated OS or browser and inject a 
malicious code. Where does he inject it? It cannot go to the CD itself, so it goes to RAM memory? Can the attacker utilise the RAM memory to get relevant info to access my accounts? 

6) What about all the encryption that the bank is no doubt doing, how will the attacker get around that?

If an attacker manages to execute arbitrary code, he can access your mounted filesystems. On a livecd or with a guest session, this includes any tmpfs filesystems which write to memory instead of your hard disk. It doesn't matter where your filesystem's changes are physically written until you restart. Until you restart, your browser's profile (cache, saved form data, saved passwords) can be accessed or your home directory modified just the same.

What encryption are you referring to? If you mean SSL encryption, then an attacker cannot intercept any data you send to the encrypted site unless they have local access to your system or the site's server, or they do a MITM attack which would result in your browser giving you a scary warning about the SSL certificate.

---

### Post by Jive Turkey on 2010-03-07
Another issue to be aware of with the livecd method is that you are not running the lates security updates.  If a major vulnerability is found in the released code, it is usually patched in short order and updates are pushed out to close the vulnerability.  Running updates on the live CD is doable, however the kernel (which gets security updates too) can only have updates applied after a reboot.  Rebooting the live cd will only revert you to square one, with no updates applied.

If your main complaint is that you don't like to update, you will find that less updating is needed on an actual install.  I would recommend you just dual boot one of your computers with ubuntu, (acually CENTOS if you are really that paranoid), and only use the linux OS for your sensitive work.

Lastly, identity thefts are a lot more likely to occur at the institution either by external intrusion, or internal theft of data.  There are lots of client malwares around that can steal your data but they aren't that hard to avoid IMHO.

---

### Post by ray33 on 2010-03-08
Thank you cdenley and Jive Turkey for your comments, I appreciate your input to this question that has been vexing me for quite awhile. I have been mulling this over in the context of my original dilemma.

Quote: "On a livecd or with a guest session, this includes any tmpfs filesystems which write to memory instead of your hard disk. It doesn't matter where your filesystem's changes are physically written until you restart. Until you restart, your browser's profile (cache, saved form data, saved passwords) can be accessed or your home directory modified just the same."

I'm just wondering what worthwhile information there would be on those files? The actual logging in has already happened before the attacker gets in. Obviously there are no saved passwords etc. I never save them, and what would be the point on livecd session anyhow. 
Whatever the malicious code is planning to do, it will be wiped out at the next reboot only a few minutes away. So is there any risk really from that intrusion on RAM memory? 

Quote: "If your main complaint is that you don't like to update, you will find that less updating is needed on an actual install. I would recommend you just dual boot one of your computers with ubuntu, (acually CENTOS if you are really that paranoid), and only use the linux OS for your sensitive work."

My concern here is that even linux OS installation is vulnerable to viruses of some sort. I have been thinking that using the live CD for the banking would get me around the problem of any malicious software residing in the hard disk.

Thanks again.

---

### Post by tubbygweilo on 2010-03-26
Can Ubuntu Save Online Banking?  As discussed via the  [Slashdot]("http://linux.slashdot.org/story/10/03/25/2350236/Can-Ubuntu-Save-Online-Banking") crowd. 

>  Recognizing that most consumers don't want to buy a separate computer for online banking, CNL is seriously considering making available free Ubuntu bootable 'live CD' discs in its branches and by mail. The discs would boot up Linux, run Firefox and be configured to go directly to CNL's Web site. 'Everything you need to do will be sandboxed within that CD,' [CNL CIO Jay McLaughlin] says. That should protect customers from increasingly common drive-by downloads and other vectors for malicious code that may infect and lurk on PCs, waiting to steal the user account names, passwords and challenge questions normally required to access online banking.

---

### Post by GFWofChinaAustraliaEtcEtc on 2010-06-27
[SIZE=3]Some possibly useful links:

[/SIZE]                                  **[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]Avoid Windows Malware: Bank on a Live CD[/SIZE][/FONT]**
 [SIZE=3][COLOR=#000080]_[FONT=Liberation Serif, Times New Roman, serif][http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html](http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html)[/FONT]_[/COLOR][/SIZE]
 [SIZE=3][FONT=Liberation Serif, Times New Roman, serif][/FONT][/SIZE]   	 	 	 	 	 	  [FONT=Liberation Serif, Times New Roman, serif]http://www.dailycupoftech.com/2007/02/06/protect-your-privacy-with-a-livecd/[/FONT]
 
[SIZE=3][FONT=Liberation Serif, Times New Roman, serif][/FONT][/SIZE][URL="http://ubuntuforums.org/member.php?u=1102691"]
 
[FONT=Liberation Serif, Times New Roman, serif][SIZE=3]
[/SIZE]

[/FONT]
 

 [/URL]

---

