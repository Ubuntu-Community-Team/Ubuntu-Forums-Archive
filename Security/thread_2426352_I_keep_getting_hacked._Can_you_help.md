---
title: "I keep getting hacked. Can you help?"
date: 2019-09-07
forum: Security
---

### Post by linux-user-0987 on 2019-09-07
I mostly use my computer for surfing the internet and I have become a target of some hacker (probably paid). I understand the basics of hacking and I know the hacker has to exploit some vulnerability but I cannot understand what he is exploiting. I mostly visit trusted sites and I also have noscript addon installed. I keep reinstalling my OS and updating, using ufw but I get hacked again. Clam scanner does NOT find anything once I get hacked. Can you explain why this is? In windows I once installed a spyware and it got picked up by the antivirus.     

So the questions are : 
1)What vulnerability could the hacker be exploting?
 2) Most recently when I got hacked I had connected to a public wifi. Is it easier to hack on a public wifi?  
3) Why does clam not detect anything? How can I tell I have been hacked? What software can I use? I only know about hacking by his actions on my laptop.  
4) Could my laptop be physically 'infected'. If so how can I find out? 
 5) What could be the solution? I tried installing virtualbox and started surfing on a standard account but he hacked that also and he was able to get to the administrator account of the main OS. When I reset using a snapshot the next time he hacked me was very soon. Very quick. I live in a hostel, and just in case some one accesses my laptop I have it installed on a usb. But I still keep getting hacked.

---

### Post by #&amp;thj^% on 2019-09-07
> Is it easier to hack on a public wifi? 
This just takes seconds to achieve.
The rest I'll leave to others to advise.

---

### Post by crip720 on 2019-09-07
Can you explain what happens after you get hacked, and have you changed password?  Saying hack can mean almost anything.  Can also install a VPN, better if a paid one(some paid ones have a free limited option) if you are using public wifi.  You might even have a rootkit that you need a rootkit hunter to find.

---

### Post by QIII on 2019-09-07
What makes you think you were hacked?

Hard to say what to do without knowing the observed behavior.

---

### Post by sevendogs1337 on 2019-09-07
Exactly.  Why do you believe you have been hacked. What is being hacked, your Ubuntu PC, or an  online account? Please provide details. Typically,  hackers (script kiddies, black hats) could care less about individuals, unless your machine is being infected with something to make a part of a botnet.

---

### Post by rbmorse on 2019-09-07
Could also be a malicious prank by a co-worker, roommate, or so-called friend.  Does anyone else have physical access to the machine besides you?

And yes, it would be most helpful if you could describe specific symptoms.

---

### Post by Skaperen on 2019-09-07
i was going to ask that same question.  what are you seeing or experiencing that makes you think you were hacked.

FYI, i was a gray-hat hacker in the 1970s.  that means i hacked in (mainframes in those days) where no permission was obtained in advance, but never did damage or stole data.  except, a hack into a friend's account, every time he logged in, it would say "big brother is watching".  but after 20 logins it changed and said "big brother is taking over", cleared all evidence of existence, and logged off.  he finally came to me about it after that last event. he didn't think that first message was a problem but he should have.

---

### Post by linux-user-0987 on 2019-09-08
The hacker has so far done things which make the laptop stop working. Like closing the browser when I am using it, corrupting the hard drive , opening things randomly, and overloading the laptop. I have visual proof.

---

### Post by Rubi1200 on 2019-09-08
I am going to ask a few questions but you also need to answer what others have asked if you expect us to help:

1. Does the person have physical access to the laptop?

2. Is there only one user account on the machine, if not how many users are there?

3. Have you checked the logs for signs of access? >  /var/log/auth.log

The more information you provide, the better.

---

### Post by coffeecat on 2019-09-08
> **linux-user-0987 said:**
> The hacker has so far done things which make the laptop stop working. Like closing the browser when I am using it, corrupting the hard drive , opening things randomly, and overloading the laptop. I have visual proof.

Several people have asked you what makes you believe you have been hacked. The above is not an adequate answer. A laptop ceasing to work, browsers closing unexpectedly, corrupted hard drives, and overload of the hardware could be down to faulty hardware or bugs in applications, or some other perfectly innocent explanation. You need to give details. What evidence do you have that leads you to believe that you have been hacked, rather than what you see is being caused by hardware or software problems?

---

### Post by linux-user-0987 on 2019-09-08
> **Rubi1200 said:**
> I am going to ask a few questions but you also need to answer what others have asked if you expect us to help:

1. Does the person have physical access to the laptop?

2. Is there only one user account on the machine, if not how many users are there?

3. Have you checked the logs for signs of access? 

The more information you provide, the better.

1. Possibly. But I have set a bios password.
2.There is only one administrator account.
3. I did and once they were deleted.

---

### Post by linux-user-0987 on 2019-09-08
> **coffeecat said:**
> Several people have asked you what makes you believe you have been hacked. The above is not an adequate answer. A laptop ceasing to work, browsers closing unexpectedly, corrupted hard drives, and overload of the hardware could be down to faulty hardware or bugs in applications, or some other perfectly innocent explanation. You need to give details. What evidence do you have that leads you to believe that you have been hacked, rather than what you see is being caused by hardware or software problems?

He also does things like opening applications and once a page got bookmarked by itself. Once I also got locked out of my account. I could not access it with my password. Thats enough evidence. And the RAM does not go to full capacity by itself. And hard drives don't become corrupt as well. Its very rare for a partition to suddenly become unreadable.

---

### Post by QIII on 2019-09-08
> **linux-user-0987 said:**
> He also does things like opening applications
Which applications?  Does this happen when you are at the machine?  While you are away?  If away, how do you know they were opened?

> and once a page got bookmarked by itself.
Once? Might it not have been a stray keystroke of your own?

> Once I also got locked out of my account. I could not access it with my password.
Again, just once?  Please see all of the questions on the Forums where others have encountered this -- without having been hacked.


> Thats enough evidence.
No, it's not.


> And the RAM does not go to full capacity by itself.
What do you mean here?

> And hard drives don't become corrupt as well.
Actually, they do.  There are plenty of questions here on the forums where people encounter this.  This is one of the reasons we highly recommend frequent backups.

> Its very rare for a partition to suddenly become unreadable.
More common than you seem to think.  Operator error can make it happen in an eyeblink.  Again, backups.

When you said you had checked logs, which ones did you check specifically?

Does anyone have physical access to your machine?

Have you installed any random software from outside of the repos or trusted/respected PPAs?

Do you practice good web surfing hygiene?

Do you allow remote desktop access?

Have you used conferencing software?

Do you allow SSH over port 22 with root login allowed?  Do you allow passwords?

Jumping to the conclusion that you have been hacked just because you machine does something unexpected is not constructive.  Giving those who have offered help partial, vague, and frankly evasive information is not either.  Please provide detail rather than waiting for members to pull your teeth.

---

### Post by linux-user-0987 on 2019-09-08
> **QIII said:**
> Which applications?  Does this happen when you are at the machine?  While you are away?  If away, how do you know they were opened?


Once? Might it not have been a stray keystroke of your own?


Again, just once?  Please see all of the questions on the Forums where others have encountered this -- without having been hacked.



No, it's not.



What do you mean here?


Actually, they do.  There are plenty of questions here on the forums where people encounter this.  This is one of the reasons we highly recommend frequent backups.


More common than you seem to think.  Operator error can make it happen in an eyeblink.  Again, backups.

When you said you had checked logs, which ones did you check specifically?

Does anyone have physical access to your machine?

Have you installed any random software from outside of the repos or trusted/respected PPAs?

Do you practice good web surfing hygiene?

Do you allow remote desktop access?

Have you used conferencing software?

Do you allow SSH over port 22 with root login allowed?  Do you allow passwords?

Jumping to the conclusion that you have been hacked just because you machine does something unexpected is not constructive.  Giving those who have offered help partial, vague, and frankly evasive information is not either.  Please provide detail rather than waiting for members to pull your teeth.



I do not understand why you are trying to convince me that I have not been hacked. I know that I have been hacked. Thats not the thing to discuss and even if the other problems can happen by themselves, applications do not open by themselves. I saw the amazon app open in front of me and bookmarking a page requires two keys. I did not do that accidentally. It is clear to me that someone is trying to disturb me.

To answer your questions:
I checked all the logs but the auth.log was deleted once. Once in enough.

I already told you that it is possible some one could access my laptop without me knowing. But I have set up a bios password. And right now I am using a usb.

I have not installed untrusted software many times I have been hacked. As I said I keep reinstalling. I have not used my laptop for banking because of being hacked although nothing has happened to other accounts.

I don't know what you mean by good surfing hygiene but many times after installing the OS, I have used only trusted websites mostly and still got hacked. 

I don't allow remote access . I used zoom once and port 22 is always closed.

**Can anyone tell me of a scan or something else I can do to detect an intrusion?** **Is there some sure way of knowing that you have been hacked?** As I said I once tried installing spyware on windows and the antivirus picked it up.

---

### Post by linux-user-0987 on 2019-09-08
Apart from the things that I mentioned that make it clear that I have become a target of some hacker, like the auth.log being deleted. So many other things happening in a short period of time is very suspicious.

---

### Post by #&amp;thj^% on 2019-09-08
We Keep asking because it's so very very rare.;)
See if any of this puts you at rest: [https://www.tecmint.com/scan-linux-for-malware-and-rootkits/](https://www.tecmint.com/scan-linux-for-malware-and-rootkits/)

---

### Post by linux-user-0987 on 2019-09-08
Also the screen brightness dropped once or twice while I was away and the audio stopped playing. Again this **might** not be proof but the other things are.

---

### Post by sevendogs1337 on 2019-09-08
None of the things you mentioned are evidence of being hacked. "Being hacked" means only 3 things: someone brute forced in remotely via an open port/service, or malware got installed that provides remote control services, or, the machine was physically compromised. There are no other ways.

I guarantee, unless you are the CEO of Google, Microsoft or another billion dollar corporation, that you and your data mean exactly squat to a malicious hacker.

---

### Post by linux-user-0987 on 2019-09-08
> **sevendogs1337 said:**
>  ...someone brute forced in remotely via an open port/service, 

Another user mentioned that hacking on a public wifi is very easy. Can you explain how this might happen? Perhaps give an example?

> **sevendogs1337 said:**
> ...the machine was physically compromised  

Is there some way a laptop can be compromised ? I read laptops are harder to modify. Is there some way I could check for sure?

---

### Post by sevendogs1337 on 2019-09-09
Public WiFi is dangerous because everyone on that WiFi network is on the same network and anyone on that network can see the traffic anyone else generates. Good example is if you were to invite everyone at a coffeeshop over to your home and give them your WiFi password: you would all be on the same network. Being on the same network with a bunch of untrusted people is not a safe thing to do, unless you take other precautions such as a VPN. My opinion anyway.

As for laptops, not sure what you mean by "modify". If someone you don't know or trust has physical access to any computer, they can do things they shouldn't, like boot Linux or Unix to single user mode, boot to a recovery disk and gain access to data, copy date, etc.

---

### Post by uRock on 2019-09-09
This all reminds me of an SSD I tried to install recently. Debian would install, but immediately start having issues. I ran a few tests and found that the drive was bad. I had Amazon send a replacement and the problems went away. Someone hacking a specific system multiple times is very unlikely.

Have you ran any tests on the HDD or SSD? If it is a laptop, then have you tried disabling the touchpad and using a mouse to see it the issue continues? Are you using a wireless keyboard and/or mouse? Is Bluetooth enabled? Are you installing/enabling any remote desktop applications?

---

### Post by sevendogs1337 on 2019-09-09
Completely agree - hackers with ill intentions rarely target a single individual, especially the average individual. A CEO of a major company, then yes, but Joe on the street, almost never. Maybe once to get data or to include the machine in a botnet, but Linux is a harder target for this than Windows. Windows is trivial to compromise so is a bigger target and more likely to be compromised.

Likely, as uRock stated, the problems OP is experiencing are related to hardware failure or some other issue.

---

### Post by linux-user-0987 on 2019-09-09
> **uRock said:**
> 
Have you ran any tests on the HDD or SSD? If it is a laptop, then have you tried disabling the touchpad and using a mouse to see it the issue continues? Are you using a wireless keyboard and/or mouse? Is Bluetooth enabled? Are you installing/enabling any remote desktop applications?

How do I run a test for HDD or SSD? No I have not used a mouse, bluetooth is disabled and I don't use any remote desktop applications.

If I have been hacked then will running the programs on this website show something?   [https://www.tecmint.com/scan-linux-for-malware-and-rootkits/](https://www.tecmint.com/scan-linux-for-malware-and-rootkits/)
 What does a hacker do once inside? If the results come back clean then that probably means I have nothing to worry about?

[https://ubuntuforums.org/showthread.php?t=2426424](https://ubuntuforums.org/showthread.php?t=2426424)

---

### Post by sevendogs1337 on 2019-09-09
Possibly - a malicious hacker will either use your machine in a botnet or will steal data. A single individual is rarely the target of a data theft simply because it's one person. Why target one person? Makes no sense. I would rather target a large organization and get data on a million users.

Running a rootkit scan or AV scan will help put your fears to rest. If nothing is returned, you can relax. ClamAV and rkhunter are both good tools.

---

### Post by (kyT%0) on 2019-09-09
> **linux-user-0987 said:**
> How do I run a test for HDD or SSD?

[https://www.hdsentinel.com/hard_disk_sentinel_linux_gui.php](https://www.hdsentinel.com/hard_disk_sentinel_linux_gui.php)

---

