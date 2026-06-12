---
title: "Help with setting up Tripwire?"
date: 2011-12-09
forum: Security
---

### Post by dareys on 2011-12-09
Greetings,

I am in the process of installing UBUNTU because hacking of my XP System prevents me from connecting it to the Network, in either wireless or wired fashion. I know the hardware is sound because if I boot with Ubuntu, everything works. Since it is free, more secure, and I can re-install at will, inot a difficult decision.

So I have install Gufw, ClamTk, and now, I am trying to configure Tripwire, so I can find out if the system flies have been tampered with as with an embedded keylogger or the like.

However, I am very inexperienced with this and would preffer, the executable help is not very intuitive and I would appreciate it if you could provide me with some examples of a basic setup.

Thank you.

Jean-Pierre

---

### Post by Dangertux on 2011-12-09
> **dareys said:**
> Greetings,

I am in the process of installing UBUNTU because hacking of my XP System prevents me from connecting it to the Network, in either wireless or wired fashion. I know the hardware is sound because if I boot with Ubuntu, everything works. Since it is free, more secure, and I can re-install at will, inot a difficult decision.

So I have install Gufw, ClamTk, and now, I am trying to configure Tripwire, so I can find out if the system flies have been tampered with as with an embedded keylogger or the like.

However, I am very inexperienced with this and would preffer, the executable help is not very intuitive and I would appreciate it if you could provide me with some examples of a basic setup.

Thank you.

Jean-Pierre

Have you considered something along the lines of Suricatta or OSSec as a host based IDS system. Trip wire is pretty far reaching and usually also requires an additional network interface in promiscuous mode to function at its full potential. 

Also at this stage of the game if you are new to security principles an IDS may cause more alarm than it's worth. You may wish to learn more about basic security principles first before journeying into this endeavor. That's just my opinion.

Here are some references that may help you.

Basic Ubuntu Desktop Security stuff - [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
More Desktop/Server Security stuff (more in depth than the last) - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Host based IDS (this is what you likely want) - [http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)
Network IDS (you might be interested in this as well) - [http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)

Hopefully this is helpful. Also another disadvantage of Tripwire with Ubuntu is that it is designed to profile a more traditional Linux filesystem (like RHEL) , it's not as effective on Debian based distros like Ubuntu.

---

### Post by dareys on 2011-12-09
Dangertux,

Thank you for the response. A mouthful!

In my life, I have been lousy at, and in that order, philosophy and sales. I excell at them now, even though the subject matter is really not my speed. Now, I am getting hammered on security issues. So. not my topic, but it looks like I am going to have to become an expert to protect myself.

I have good refference material. Everythihng I know from UBUNTU comes from a  book called "Ubuntu Unleashed". The information you sent me is great. I represents hours of study and experimentation. Fine, I reallly can't afford it, but, if that is what it is going to take to defeat hackers. So be it.

However, what I was looking for was a "hit the ground running" safety net. I get hacked left, right and center. Please somebody help? Ok, I can hit the books and figure it out. But I have lost three computers to hacking and I am getting tired of it. Gee, even MACs are hackable. They tell you not. I have proof.

So, if you can send me the quick refference gjuide, I would greatly appreciate it. Otheriwise, I greatly appreciate the answer, and I will hit. The  books.

Thank you.

Jean-Pierre

---

### Post by Dangertux on 2011-12-09
> **dareys said:**
> Dangertux,

Thank you for the response. A mouthful!

In my life, I have been lousy at, and in that order, philosophy and sales. I excell at them now, even though the subject matter is really not my speed. Now, I am getting hammered on security issues. So. not my topic, but it looks like I am going to have to become an expert to protect myself.

I have good refference material. Everythihng I know from UBUNTU comes from a  book called "Ubuntu Unleashed". The information you sent me is great. I represents hours of study and experimentation. Fine, I reallly can't afford it, but, if that is what it is going to take to defeat hackers. So be it.

However, what I was looking for was a "hit the ground running" safety net. I get hacked left, right and center. Please somebody help? Ok, I can hit the books and figure it out. But I have lost three computers to hacking and I am getting tired of it. Gee, even MACs are hackable. They tell you not. I have proof.

So, if you can send me the quick refference gjuide, I would greatly appreciate it. Otheriwise, I greatly appreciate the answer, and I will hit. The  books.

Thank you.

Jean-Pierre

Well a couple of things here. One NOTHING is impenetrable, not windows, not mac, no Ubuntu, not RHEL, not IRIX or AIX. That's just how it goes.

That being said, I'm not really sure there is a "quick setup safety net" for tripwire. An Intrusion detection system or prevention system is only as effective as its configuration. Additionally either OSSec or Suricatta can be configured as a host based IDS similar to tripwire, and they can be updated with the latest emerging threats rules, which give you a pretty decent configuration out of the gate. 

Now what I'm trying to explain here is -- I think you may be exaggerating the threat to your systems. I'm not discrediting your loss and though I stated nothing is inherently secure. The risk level in using Ubuntu as opposed to using Windows XP is considerably lower. I think that if you follow decent computing practices and take some basic measures (Firewall, NoScript, Appamor [this is more difficult], and strong credentials) you should be more than fine without configuring and complicated IDS solution.

Hope this helps.

---

### Post by larrypg on 2011-12-10
Hello,

Just a thought...you might want to step back a minute and think about why you are getting hacked left,right,and center.  Even with a firewall, and noscript if you are constantly doing things such as warez or downloading files from unknown sources it might not help.

---

### Post by dareys on 2011-12-19
Dangertux and Larrypg,

Thank you for the responses. 

1. I don't know who or why I am being hacked. People don't receive my messages. I don't get messages.
    It can happen from my own computer, or from an internet join. I can open nothing but the standard.
    Email, twitter, facebook, microsoft, ubuntu, etc. 

2. I only need to setup Tripwire to verify that my Ubuntu system files have not been hacked with a 
    keylogger or something like that. 

3. Thank you for confirming that EVERYTHING can be hacked.

The question is, how can I achieve 2.

Jean-Pierre

---

### Post by Dangertux on 2011-12-19
> **dareys said:**
> Dangertux and Larrypg,

Thank you for the responses. 

1. I don't know who or why I am being hacked. People don't receive my messages. I don't get messages.
    It can happen from my own computer, or from an internet join. I can open nothing but the standard.
    Email, twitter, facebook, microsoft, ubuntu, etc. 

2. I only need to setup Tripwire to verify that my Ubuntu system files have not been hacked with a 
    keylogger or something like that. 

3. Thank you for confirming that EVERYTHING can be hacked.

The question is, how can I achieve 2.

Jean-Pierre

In order of appearance.

1 - What exactly is happening? Are you being redirected to another site when you try to visit something else? Or is it just not loading (connection reset/refused by target machine). This is not necessarily an indicator you've been hacked. In fact it's more than likely a bad configuration or quirky internet connection.

2 - Tripwire is one of many IDS solutions. It is more difficult to set up than others and is not necessarily more thorough than any of the other solutions I mentioned earlier (Snort, OSSec, Suricata). It's also important to understand that IDS and forensics tools that determine if a system has been tampered with rely on a "known good configuration". There for if you are installing it on a compromised system the initial fingerprint for the "known good config" will be that of a compromised system. So if you do go this route, you need to wipe everything first, and before anything else configure your forensics software/HIDS.

3 - You're welcome.

Extra info, a keylogger may not necessarily be detected by an application that is looking for tampered files. For instance, rkhunter or chkrootkit are going to look for certain files, and their hash sums. If they are there and checksum correctly then there will be no warning giving. However if the keylogger is not bound to one of the programs that is checked, and the keylogger's binary is not signatured it will likely pass right under most forensics applications radar.

So I ask again, why is it you're so sure you were compromised? This really doesn't appear to be the case from what I've seen here.

Hope this helps.

---

### Post by dareys on 2011-12-19
Dangertux,

Thank you for the response. My list of problems follows. In any order. I have been observing them for close to five years, and they have prompted me to start learning about networks and security to protect myself. I hope you have time to read my entire list and that you can make a recommendation.

- Yes, I have been re-directed to other sites. Frequently. It just happened a minute ago.
- I can't get access to a particular web site. This morning I could not enter [www.lenovo.com]("http://www.lenovo.com") to download
  the apparently damaged communication drivers of my XP installation.
- Sometimes the font, size and color of the text I am typing changes while I am writting an email.
  I have been a Yahoo mail user for thirteen years, and these issues only started four years ago.
- People don't get my email.
- I don't get people's email. For example, even when I sign up to follow a thread I have posted, and
  people respond to it, I don't get the notification. I have to log in to find that people replied. It has happened
  with the UBUNTU and Microsoft forums.
- My passwords change spontaneously. For UBUNTU, I practically have to request a new password  
  everytime I try to log in to post a quesion on the UBUNTU forums or connect to UBUNTU ONE to
  backup my machine to the cloud.

  I keep using the same one over and over and make it really simple and unsecure so I won't
  forget it...

  This is ironic because I did technical support for JPMChase and had to remember
  dozens of passwords. Even when they woke me up at 3:00 AM, I only forgot a couple in two years.

- I share internet with only one other person, and even when they are not around throughput of the
  network connection sometimes degrades drastically and unexpectedly during activities that
  I engage in daily without any problem at other times.
- The phone company has provided me with the admin user and password for the
   modem gateway (and they don't work). I need them to change the same, enable the
   hardware firewall, and restrict access to sites, games, and certain ports, as well as change
   the wireless WEP hexadecimal password. Sure I could reset the modem but I would be affecting
   the other user who has no complaints. A hard sell because it might take me hours to configure and
   we both can't afford the downtime.
- Invisible characters are introduced into what I type. And then, sometimes, after proof reading
   an email, the copy I routinely send myself is riddled with typos I did not see at mailing time.
- The text of my messages changes. Sometimes, the copy I send myself does not contain the
   text that I remember writting.It is not what I sent. Missing words, added words.
- The speed at which I can type decreases dramatically at times, as if the text was being
   buffered.
- Emails I am typing suddenly get wiped out. I have to retype them two or three times.

As you can see, all of this makes me very frustrated. I waste hours trying to solve problems I never
experienced before, leading to decreased productivity and affecting my ability to communicate in a very bad way.

Jean-Pierre

---

### Post by needhelppeeps on 2011-12-19
You could try aide. Basically when you initializethe database it takesahash of the files and lets you knowif they changed but easier to setup. The database is storedon write protected media like an sdcard. After updates are applied, you unlockthe card, update the database, and resume monitoring. Worth doing for a server's system files but you obviously need to exclude dataareas or you will quickly grow tired of it. On a desktop, likely you will grow tired of it and thus it will not be effective anyway.

---

### Post by Dangertux on 2011-12-20
Well to be honest, and I really don't mean to say that you are being paranoid but I think there are quite a few different issues going on here. Compromised security may or may not be one of them.

Alot of what you are describing sounds like a combination of poorly configured or failing hardware and bad password management. The characters being inserted or removed from text documents is almost certainly attributed to poorly configured hardware. I've had the same issue on a laptop with a poorly configured synaptics touchpad driver. It was remedied by configuring the hardware properly.

The changing passwords thing...They may not be changing at all, human minds are fragile things, we forget a lot of stuff. After all we're very busy people it's natural. I would suggest either using a password management system like keep pass OR considering changing your password construct model to something easily memorable yet still strong.

As far as users not receiving your emails, that could be a poorly configured mail client, inproperly typed receipient address or a handful of other things.

Ultimately I really don't think your security has been breached. Furthermore this is enforced by the fact you said this has been going on for 5 or so years. In all that time that an attacker could have had access to your computer, have you noticed any sign of identity theft or someone attempting to access your financial information? If the answer is no, I can almost certainly guarantee this system is not compromised. Remember most cracks are smash and grab. They get in take what they want (or place the computer in a botnet) and leave. There isn't some long drawn out espionage-like process.

I hope this doesn't come off as me being too judgemental, however in my opinion with the information provided I really don't think your system is compromised.

---

### Post by dareys on 2011-12-21
needhelppeeps,

Thank you for the response. Too technical or vague for me. Elaborate. Please.

Jean-Pierre

---

### Post by dareys on 2011-12-21
Dangertux

Judgemental? No worries.I have no issues with honest opinions. Every one has to be taken into account. In the end, you associate yourself with winners, and build a good team. It is your two cents.I am an expert at that kind of advice as well.

However, all I can say is that, I subscribed to my post, and I did not get the email alerting me to the fact that you had responded to it today. The French would say. CQFD. "Ce qu' il fallait demontrer". In other words, proof.

I did not get your response. I had to log in to find out that you responded.... So, proof I am not receiving emails from UBUNTU, Microsoft and God know who else.Much more worrisome...

Whoever is hacking me is not after money. They are after destroying my ability to communicate, my ability to make a living, make friends, find a mate and get laid. My step father once said,"I find out you are messing with my ***** and you are toast". Graphic, but the truth. The Navy man rules. My best friend.

And as far as being paranoid, well, onlly the paranoid succeed in IT and life, and in life. Please check:
[http://blogs.hbr.org/cs/2011/12/what_it_takes_to_win_extreme_l.html](http://blogs.hbr.org/cs/2011/12/what_it_takes_to_win_extreme_l.html)
An excerpt:
Andy Grove of Intel went around "looking for the black cloud in the silver lining." He even titled his book Only the Paranoid Survive. Leaders need to draw up a list of all the bad things that can happen, build cash reserves, hedge, and acquire options, to prepare for the worst. This requires fanatic discipline.
Ok?

Jean-Pierre


Re: Help with setting up Tripwire?
Well to be honest, and I really don't mean to say that you are being paranoid but I think there are quite a few different issues going on here. Compromised security may or may not be one of them.

Alot of what you are describing sounds like a combination of poorly configured or failing hardware and bad password management. The characters being inserted or removed from text documents is almost certainly attributed to poorly configured hardware. I've had the same issue on a laptop with a poorly configured synaptics touchpad driver. It was remedied by configuring the hardware properly.

The changing passwords thing...They may not be changing at all, human minds are fragile things, we forget a lot of stuff. After all we're very busy people it's natural. I would suggest either using a password management system like keep pass OR considering changing your password construct model to something easily memorable yet still strong.

As far as users not receiving your emails, that could be a poorly configured mail client, inproperly typed receipient address or a handful of other things.

Ultimately I really don't think your security has been breached. Furthermore this is enforced by the fact you said this has been going on for 5 or so years. In all that time that an attacker could have had access to your computer, have you noticed any sign of identity theft or someone attempting to access your financial information? If the answer is no, I can almost certainly guarantee this system is not compromised. Remember most cracks are smash and grab. They get in take what they want (or place the computer in a botnet) and leave. There isn't some long drawn out espionage-like process.

I hope this doesn't come off as me being too judgemental, however in my opinion with the information provided I really don't think your system is compromised.

---

### Post by dareys on 2011-12-21
Dangertux

Judgemental? No worries.I have no issues with honest opinions. Every one has to be taken into account. In the end, you associate yourself with winners, and build a good team. It is your two cents.I am an expert at that kind of advice as well.

However, all I can say is that, I subscribed to my post, and I did not get the email alerting me to the fact that you had responded to it today. The French would say. CQFD. "Ce qu' il fallait demontrer". In other words, proof.

I did not get your response. I had to log in to find out that you responded.... So, proof I am not receiving emails from UBUNTU, Microsoft and God know who else.Much more worrisome...

Whoever is hacking me is not after money. They are after destroying my ability to communicate, my ability to make a living, make friends, find a mate and get laid. My step father once said,"I find out you are messing with my ***** and you are toast". Graphic, but the truth. The Navy man rules. My best friend.

And as far as being paranoid, well, onlly the paranoid succeed in IT and life, and in life. Please check:
[http://blogs.hbr.org/cs/2011/12/what_it_takes_to_win_extreme_l.html](http://blogs.hbr.org/cs/2011/12/what_it_takes_to_win_extreme_l.html)
An excerpt:
Andy Grove of Intel went around "looking for the black cloud in the silver lining." He even titled his book Only the Paranoid Survive. Leaders need to draw up a list of all the bad things that can happen, build cash reserves, hedge, and acquire options, to prepare for the worst. This requires fanatic discipline.
Ok?

Jean-Pierre


Re: Help with setting up Tripwire?
Well to be honest, and I really don't mean to say that you are being paranoid but I think there are quite a few different issues going on here. Compromised security may or may not be one of them.

Alot of what you are describing sounds like a combination of poorly configured or failing hardware and bad password management. The characters being inserted or removed from text documents is almost certainly attributed to poorly configured hardware. I've had the same issue on a laptop with a poorly configured synaptics touchpad driver. It was remedied by configuring the hardware properly.

The changing passwords thing...They may not be changing at all, human minds are fragile things, we forget a lot of stuff. After all we're very busy people it's natural. I would suggest either using a password management system like keep pass OR considering changing your password construct model to something easily memorable yet still strong.

As far as users not receiving your emails, that could be a poorly configured mail client, inproperly typed receipient address or a handful of other things.

Ultimately I really don't think your security has been breached. Furthermore this is enforced by the fact you said this has been going on for 5 or so years. In all that time that an attacker could have had access to your computer, have you noticed any sign of identity theft or someone attempting to access your financial information? If the answer is no, I can almost certainly guarantee this system is not compromised. Remember most cracks are smash and grab. They get in take what they want (or place the computer in a botnet) and leave. There isn't some long drawn out espionage-like process.

I hope this doesn't come off as me being too judgemental, however in my opinion with the information provided I really don't think your system is compromised.

---

### Post by Ms. Daisy on 2011-12-21
> **Dangertux said:**
> Alot of what you are describing sounds like a combination of poorly configured or failing hardware and bad password management. The characters being inserted or removed from text documents is almost certainly attributed to poorly configured hardware. I've had the same issue on a laptop with a poorly configured synaptics touchpad driver. It was remedied by configuring the hardware properly.

[QUOTE=dareys] However, all I can say is that, I subscribed to my post, and I did not  get the email alerting me to the fact that you had responded to it  today. The French would say. CQFD. "Ce qu' il fallait demontrer". In  other words, proof.[/QUOTE]

Hello Jean-Pierre.  What I am reading in your post is that you take your quote above as proof of hacking.  Although I would never presume to speak for him, what I think Dangertux is suggesting is that first you rule out hardware failure/misconfiguration before you decide it is caused by hacking. It's more likely that the former is the cause of your problems, so you need to rule it out.

Just so we all understand, have you specifically ruled out hardware? Are any of your connections loose or damaged? What about connecting cords, are they frayed or damaged? How old are the computer, router & modem?  Have you run the memory test in BIOS?  Ubuntu has a utility in the software center called "System Testing". It takes a lot of time to run it and it requires your constant attention, but it will go through each piece of hardware on your computer.  If you haven't specifically ruled out hardware, then I'm not sure that you will get much better advice from the forum.

---

### Post by dareys on 2011-12-21
Ms. Daisy,

Thank you for the response. 

1. The modem is an old model, but the other ruser has no complaints. My only issues with it are that
     I have not reconfigured the admin password, WEP password, and firewall, for reasons I 
     explained earlier in the thread.

2. As far as the hardware, I have dismantled 2/3 of the laptop. But, I made sure I put back the screws in
    tightly. It took me hours. I installed 4GB of memory and ran the BIOS memory test. No problem.
    And, yes, I am aware of  the Ubuntu software center called "System Testing". I ran all the tests 
    shortly after discovering UBUNTU. Everything was fine at the time. 

So, I will run the tests again. But this is not a hardware problem. It is a software problem, or a hacking
problem. Anyway, I am about to buy a Thinkpad just so I can communicate without these problems, 
but trying to fix this machine. It is a good machine and still viable.

Anyway, I just remembered two other issues I did not mention before in my long list of grievances which I hope you posted. They are as follows:

- When I am logged in to my Yahoo mail client, sometimes after closing a tab, and reading an email in  
   particular folder, I find other tabs open, for folders containing mail I have not accessed in months.

- I bought software to track emails I sent, because I was paranoid that they were not being received. It 
  reports on the IP address of the recipient, the browser that opened it, how many times it was opened, on 
  how many different computers, and similar statistics regarding any computers that the message might    
  have been forwarded to. And, so everytime the reader re-opens a message I sent them, no matter how   
  old, I get another report. At some point I was negotiating for a job in Geneva, and had sent mail to people 
  there. The deal fell through, I forgot about it, and a year or more passed, and then, suddenly, I get a 
  report that the recipient had re-opening the message. I found it odd. So I looked carefully. Well, the
  message was being opened in my current city,... not in Geneva. Hence, I  believe somebody has
  access to my email account as well. Ok, so I keep changing the passwords. A keylogger, or a sniffer
  on the network takes care of that in a jiffy! See my point? 

Regards,

Jean-Pierre

---

### Post by dareys on 2011-12-27
Greetings,

Perhaps it is because of the holidays, but I received no response to my last post. To those that have responded and put up with my paranoia, many thanks. I hope you are having a wonderful holiday season and I wish you a healthy and prosperous 2012. 

Since I wrote my last update, i logged int to my FaceBook account, only to find that I had family I never knew I had .... Really, my settings, totally messed up. You could speculate i did this while sleep walking, but really, not a possibility.

In any case, I thank you for your help. Even though I have downloaded the drivers I think my patch my XP installation, I really like Ubuntu, its offereing and the community. I look forward to years of positive, communicative, and constructive interaction.

Jean-Pierre

---

### Post by Dangertux on 2011-12-27
> **dareys said:**
> Greetings,

Perhaps it is because of the holidays, but I received no response to my last post. To those that have responded and put up with my paranoia, many thanks. I hope you are having a wonderful holiday season and I wish you a healthy and prosperous 2012. 

Since I wrote my last update, i logged int to my FaceBook account, only to find that I had family I never knew I had .... Really, my settings, totally messed up. You could speculate i did this while sleep walking, but really, not a possibility.

In any case, I thank you for your help. Even though I have downloaded the drivers I think my patch my XP installation, I really like Ubuntu, its offereing and the community. I look forward to years of positive, communicative, and constructive interaction.

Jean-Pierre

Hey sorry, I've been busy with the holidays and I didn't see your reply until today. Since you seem dead set on this, despite advice to the contrary the best I can do to help you is this. I put together the following quickie one shot guide for installing / configuring Tripwire on Ubuntu. Following it step by step should get you set up, make sure it's a clean OR trusted installation. Meaning a fresh install may be in your future.

[http://dangertux.wordpress.com/2011/12/28/installing-tripwire-on-ubuntu/](http://dangertux.wordpress.com/2011/12/28/installing-tripwire-on-ubuntu/)

Hopefully this helps. Though I still think checking your human interface devices might better serve you. :-)

Hope you're having a wonderful holiday season despite the computer issues.

---

### Post by emiller12345 on 2011-12-27
If your computer is completely patched up and your LAN is compromised, then you still have massive problems.  Lots of things can still be done even if your computer is okay.  One thing that comes to mind is Cookie theft.  If you login and someone sniffs your authentication cookies, they don't need your password to login as you.  They could change your password and change all of your settings, just like your seeing.  I would strongly recommend securing your network.  If you can't afford the down time, buy a new up-to-date router and configure it before you install it.  Do not use WEP. It is not only easily cracked, but is also a target for hackers.  WPA2 is very good and should be available on all modern routers.  You should change the default admin password of the router as well, as soon as you get it to help protect your settings.

---

### Post by dareys on 2011-12-27
emiller12345,

Thank you for the response. I know that my network is compromised. Yes, it is a week WEP key protection, and I have been trying to reset the modem, configure the firewall, shut down access to certain sites and ports, as well as change the WEP key. And yes, I have not been able to afford the downtime...

So, as soon as I can I wiill do what you indicate. Thank you and happy holidays.

Jean-Pierre

---

### Post by dareys on 2011-12-28
Dangertux,

My goal is to patch up my XP installation, which once I resolve the communication problem will be quite well protected, as I have learned, painfully the lessons of hacking and have progressively learned how to protect the machine.

 I have just not bitten the bullet, and installed the drivers, because I have not had the time and don't wan't to suddenly be incomunicado.I am a very deliberate person and like to make sure I have learned enough to take the risk.

As far as Ubuntu, well, it will be an environment for another installation (an IT guy and only one computer? LOL), and I am learning how to secure that one slowly but surely... Thank you for the information. I will read it and proceed with care.

Thank you for your help.

Happy holidays.

Jean-Pierre

> **Dangertux said:**
> Hey sorry, I've been busy with the holidays and I didn't see your reply until today. Since you seem dead set on this, despite advice to the contrary the best I can do to help you is this. I put together the following quickie one shot guide for installing / configuring Tripwire on Ubuntu. Following it step by step should get you set up, make sure it's a clean OR trusted installation. Meaning a fresh install may be in your future.

[http://dangertux.wordpress.com/2011/12/28/installing-tripwire-on-ubuntu/](http://dangertux.wordpress.com/2011/12/28/installing-tripwire-on-ubuntu/)

Hopefully this helps. Though I still think checking your human interface devices might better serve you. :-)

Hope you're having a wonderful holiday season despite the computer issues.

---

### Post by dareys on 2011-12-28
emiller12345,

Just as a footnote. I did get a message in my inbox indicating that someone else had replied to the thread, namely DangerTux. 

However, I did not receive an email indicating that you had responded. I almost missed it. And that would have been a shame. See what I mean? I am positively convinced of hacking, and I have documented conclusively in this thread.

And yes, my network is totally hacked. I know it. I leave BS files around for the hackers. I will try to secure it ASAP. New years eve sounds like a good time to try it. LOL.

In the meantime, I have enouch information to continue setting up Tripwire, thanks to DangerTux. If it works.Last night, it failed at the very last step. I suspect a disk space issue, but will investigate and try again.

Many thanks for your support. I wish you and our colleauges a healthy and prosperous 2012.

Jean-Pierre

> **dareys said:**
> emiller12345,

Thank you for the response. I know that my network is compromised. Yes, it is a week WEP key protection, and I have been trying to reset the modem, configure the firewall, shut down access to certain sites and ports, as well as change the WEP key. And yes, I have not been able to afford the downtime...

So, as soon as I can I wiill do what you indicate. Thank you and happy holidays.

Jean-Pierre

---

### Post by Dangertux on 2011-12-28
> **dareys said:**
> emiller12345,

Just as a footnote. I did get a message in my inbox indicating that someone else had replied to the thread, namely DangerTux. 

However, I did not receive an email indicating that you had responded. I almost missed it. And that would have been a shame. See what I mean? I am positively convinced of hacking, and I have documented conclusively in this thread.

And yes, my network is totally hacked. I know it. I leave BS files around for the hackers. I will try to secure it ASAP. New years eve sounds like a good time to try it. LOL.

In the meantime, I have enouch information to continue setting up Tripwire, thanks to DangerTux. If it works.Last night, it failed at the very last step. I suspect a disk space issue, but will investigate and try again.

Many thanks for your support. I wish you and our colleauges a healthy and prosperous 2012.

Jean-Pierre

Jean-Pierre what was the error message given in the last step?

---

### Post by dareys on 2011-12-28
DangerTux,

There was no error. The following command failed on the next to last step, in other words the following command:

sudo tripwire --init

I had several issues.

Initially, I typed in an incorrect password. The ironic thing is that I was prompted to create passwords twice during the previous installation steps, that I entered each one twice as usual to make sure that I got things right, and that I made them both the same, because I figured I was just testing.

So, no possibility that I might be typing the wrong password... I learned to always use the same one when installing and learning a new product, to avoid exactly this kind of problem... 

Then on the next to last step, which I indicate above, the error was:

$ sudo tripwire --init
### Error: Config file site key mismatch.
### The config file "/etc/tripwire/tw.cfg" is not encrypted with the current
### keyfile "/etc/tripwire/site.key".
### Exiting...

What is the issue, I don't know. Like I complained earlier in this thread password issues plague me, in spite that in my support role at JPMChase I had to remember dozens of them, and that in the two years I was there, never forgot one. The issues I had at 3:00 AM where when they expired!

Also, I have indicated that characters are inserted into what I type, and that the text of my emails when I send them is not the same as what I get back when I copy myself.... Anyway, enough rambling. Thank you for your help.

Jean-Pierre

---

### Post by Dangertux on 2011-12-28
> **dareys said:**
> DangerTux,

There was no error. The following command failed on the next to last step, in other words the following command:

sudo tripwire --init

I had several issues.

Initially, I typed in an incorrect password. The ironic thing is that I was prompted to create passwords twice during the previous installation steps, that I entered each one twice as usual to make sure that I got things right, and that I made them both the same, because I figured I was just testing.

So, no possibility that I might be typing the wrong password... I learned to always use the same one when installing and learning a new product, to avoid exactly this kind of problem... 

Then on the next to last step, which I indicate above, the error was:

$ sudo tripwire --init
### Error: Config file site key mismatch.
### The config file "/etc/tripwire/tw.cfg" is not encrypted with the current
### keyfile "/etc/tripwire/site.key".
### Exiting...

What is the issue, I don't know. Like I complained earlier in this thread password issues plague me, in spite that in my support role at JPMChase I had to remember dozens of them, and that in the two years I was there, never forgot one. The issues I had at 3:00 AM where when they expired!

Also, I have indicated that characters are inserted into what I type, and that the text of my emails when I send them is not the same as what I get back when I copy myself.... Anyway, enough rambling. Thank you for your help.

Jean-Pierre

That error means you encrypted your cfg files wrong, not at all or with the wrong keys. In my opinion slow down, take it easy and read carefully what you're doing each step of the way. Or go fast and copy paste, I ran it through a VM as I was doing it and copy/pasta'd verbatim so it should work in it's default state.

---

### Post by dareys on 2011-12-28
DangerTux,

I tried the procedure you outlined yesterday as soon as I read the message, went fast, using cut and paste, and got the described results. I will try it again the same way, but more slowly. As you stated, it should work verbatim. 

Doing it slower, is what I should do once I am protected and want to understand exactly what is going on and learn about it. 

BTW, I am still running the installation with the security that is configured by default, hence not a lot. With Tripwire, I want to make sure that the system files have not been tampered with. Because that was the most difficult problem to track on Windows XP.

Anyway, I just tried it again, and this time the installation fails at a different point. E.g.

sudo twadmin --create-cfgfile -S site.key /etc/tripwire/twcfg.txt

sudo twadmin --create-cfgfile -S site.key /etc/tripwire/twcfg.txt
### Error: File could not be opened.
### Filename: /etc/tripwire/twcfg.txt
### No such file or directory
### Exiting...

Jean-Pierre

> **Dangertux said:**
> That error means you encrypted your cfg files wrong, not at all or with the wrong keys. In my opinion slow down, take it easy and read carefully what you're doing each step of the way. Or go fast and copy paste, I ran it through a VM as I was doing it and copy/pasta'd verbatim so it should work in it's default state.

---

### Post by Dangertux on 2011-12-28
> **dareys said:**
> DangerTux,

I tried the procedure you outlined yesterday as soon as I read the message, went fast, using cut and paste, and got the described results. I will try it again the same way, but more slowly. As you stated, it should work verbatim. 

Doing it slower, is what I should do once I am protected and want to understand exactly what is going on and learn about it. 

BTW, I am still running the installation with the security that is configured by default, hence not a lot. With Tripwire, I want to make sure that the system files have not been tampered with. Because that was the most difficult problem to track on Windows XP.

Anyway, I just tried it again, and this time the installation fails at a different point. E.g.

sudo twadmin --create-cfgfile -S site.key /etc/tripwire/twcfg.txt

sudo twadmin --create-cfgfile -S site.key /etc/tripwire/twcfg.txt
### Error: File could not be opened.
### Filename: /etc/tripwire/twcfg.txt
### No such file or directory
### Exiting...

Jean-Pierre

If you're going to restart the install you need to 

```

sudo apt-get remove --purge tripwire
sudo apt-get install tripwire

```

Remember in step 4 you deleted those txt  files. So they will not be there if you just repeat the steps, they are generated at install time. I would recommend choosing yes to allow automatic generation of site/db key at install time if you're having trouble. That's why I put the last part as optional.

Hope this helps.

---

### Post by dareys on 2012-03-21
> **Dangertux said:**
> If you're going to restart the install you need to 

```

sudo apt-get remove --purge tripwire
sudo apt-get install tripwire

```

Remember in step 4 you deleted those txt  files. So they will not be there if you just repeat the steps, they are generated at install time. I would recommend choosing yes to allow automatic generation of site/db key at install time if you're having trouble. That's why I put the last part as optional.

Hope this helps.
Dangertux,

It has been a while since my last communication. I hope that you will get this response. In the end, I have been using Gufw as a firewall, and I have not had time to configure Tripwire. Too distracted by other things. However, I can tell you this. The hacking, well documented above, has been pervasive and relentless for years.Firewall or not... 

Since my last communication, I have absolute and overwhelming proof. For the record, Google, "Beini". A program written in China, but I am sure there are many others like it.  It allows you to break the WEP, WPA, and WPA2 encryption of any WiFi connection within reach. Available for dowload for free, or on the streets of Mexico for about $5.00 USD.

A great article about this was published in the Reforma newspaper in Mexico on January 17th 2012, written by Rodolfo Gonzalez blowing the lid on the story. I reasearched it, and tested things out. I was able to crack my WEP encryption in five minutes flat. I tried another couple of WEP networks, owned by friends, just to verify it, and sure enough, it works.

The issue is, over 90% of all networks here are WEP encrypted even if the moden allows for WPA2-PSK encryption. Go figure why. And people here steal everything... Anyway, I am not into stealing anyone's internet, I just want my communications and privacy back.

I am now trying to change the encryption of my connection, enable firewall on it and on my machine, and hope that I don't already have a keylogger embedded in my kernel. 

Thank you for the help.

Jean-PIerre

P.S. As far as Tripwire, I will give it the time it deserves ASAP, and will probably come back to this forum with more 
        questions.

---

### Post by cryptotheslow on 2012-03-21
Hi,

Just a couple of ideas that sprang to mind reading through this.

1. Even if just as a temporary experiment - why not disable the wireless ability of your router entirely and connect using Cat5 ethernet cable? That would preclude anyone outside your physical environment snooping on your LAN traffic.

2. You mention "another user" using your router. Do you absolutely trust this person? Maybe they are snooping your cookies off the LAN and messing with your various accounts as a "joke".

3. Always use secure https pages for any site that requires any kind of login.

4. If funds allow - consider subscribing to a VPN provider and use that to route all your internet traffic.

5. I haven't used it in a long while, but when I did, I regularly had problems with Yahoo mail black-holing mail as spam and random non (or much delayed) delivery of mail both in and outbound. I didn't use it for long so no idea if those were just temporary problems at the time or actually indicative of how the service is.

---

### Post by dareys on 2012-03-21
> **cryptotheslow said:**
> Hi,

Just a couple of ideas that sprang to mind reading through this.

1. Even if just as a temporary experiment - why not disable the wireless ability of your router entirely and connect using Cat5 ethernet cable? That would preclude anyone outside your physical environment snooping on your LAN traffic.

2. You mention "another user" using your router. Do you absolutely trust this person? Maybe they are snooping your cookies off the LAN and messing with your various accounts as a "joke".

3. Always use secure https pages for any site that requires any kind of login.

4. If funds allow - consider subscribing to a VPN provider and use that to route all your internet traffic.

5. I haven't used it in a long while, but when I did, I regularly had problems with Yahoo mail black-holing mail as spam and random non (or much delayed) delivery of mail both in and outbound. I didn't use it for long so no idea if those were just temporary problems at the time or actually indicative of how the service is.
cryptotheslow,

Thank you for the response. 

1. My landlady is an independent Lawyer, and very unpredictable. Your suggestion is great, but following it might create 
     a disruption of her network  "access" you know what I mean? Murphy might strike at any time and 
    I don't need trouble.I just have to plan it for when she is away for a few days and we negotiate it. Thanks for the tip.

2. My landlady is the? other user. Do you absolutely trust anybody? For certain things yes. Otherwise, she seems 
    innocent enough, being a lawyer and not very computer savy. But I really don't know her, or her motivations, or 
    what she or any of the people being able to hack the ridiculous WEP key might want to do to pre-empt me or why.

    But yes, you are right. Somebody might be doing what you say, just for fun. or just to make my life miserable. Well, it 
    is not fun to me, and has been disrupting my communications, jobs and relationships for years.

3. Of course. Including access to my own router, when I can configure it successfully in this daisy chain mode.

4. Funds are an issue because of the fact that contracts have to be signed for a period of time longer than I am willing
    to garantee or without having the proper backing. I am not a local here.  This is an issue that I am aware is bitting me
    and one I foresaw long ago when I moved into the area. The inability to secure my own space has been my downfall.

5. Yes, sometimes I find things in my SPAM folder that are there randomly. I also believe that emails are hugely
    delayed sometimes. I sometimes respond to invitation declinations by saying, I never got the invitation, only to 
    find it in my inbox later.

Thank you very much for your feedback.

Jean-Pierre

---

