---
title: "backdoor/keylogger program"
date: 2009-02-01
forum: Security
---

### Post by vze57gc8 on 2009-02-01
I've been interested in security penetration and have successfully done some wifi exploits via bt. Now im getting bored and want to try something new. I've been researching creating a backdoor for remote access and also installing a keylogger. Thus far a virtual machine has been set up and im in the process of acquiring a low end box (dont rly want to mess with my system). 
Problems are idk how to acquire a malware (im not an author) and how to get past security scan by email and the target machine its self?

---

### Post by Kinstonian on 2009-02-01
You could go to [http://packetstormsecurity.org/](http://packetstormsecurity.org/) and find something that interests you there.  I'm not sure exactly how trustworthy the code from that site is, but I think most of it (if not all) is open source letting you modify the source code to evade detection from AV software.  You could also pack/encrypt the malware with something like UPX to help get past AV software.

Some other things that are common is compressing the malware in a .zip file with a password.  The email/virus scanner won't be able to decrypt the zip file so it can't scan it.  In the email you can use social engineering to trick the end user into extracting it with the password, and then running it.  Another thing you could do is social engineer them into downloading a "patch" from a web site, that way the malware never goes through the email scrubber.

---

### Post by RaiCoss on 2009-02-02
> **vze57gc8 said:**
> I've been interested in security penetration and have successfully done some wifi exploits via bt. Now im getting bored and want to try something new. I've been researching creating a backdoor for remote access and also installing a keylogger. Thus far a virtual machine has been set up and im in the process of acquiring a low end box (dont rly want to mess with my system). 
Problems are idk how to acquire a malware (im not an author) and how to get past security scan by email and the target machine its self?

Grow up.

---

### Post by tubbygweilo on 2009-02-02
vze57gc8,
research or not, I expect that you have now been added to a few watch lists.

---

### Post by vze57gc8 on 2009-02-02
i believe ignorance is far more dangerous than knowledge. all i wanna do is learn.

---

### Post by glotz on 2009-02-03
I'm also interested in penetration!

---

### Post by vze57gc8 on 2009-02-04
i forgot to thank you for your response. many thanks

---

### Post by The Tronyx on 2009-02-05
> **vze57gc8 said:**
> i forgot to thank you for your response. many thanks

Greetings vze57gc8.  If you are looking for malware, you might want to check [http://offensivecomputing.net](http://offensivecomputing.net).  Most of the stuff you find is going to be Win32 but it is still good learning.  If you want to learn a valuable skill, don't spend time trying to write it because that will be justification for the guy who told you to grow up earlier.  Instead, download a copy of Immunity Debugger and OllyDBG, create a virtual install of Windows (I use XP for this purpose) and install the debuggers and disassemblers and spend time analysing malware and seeing how it works.

As you get more and more into this you will acquire a bigger toolkit so you might want to get ahead of the game and find a good hex editor, LordPE, ASPackDie, Reflector for .NET, etc.  Lastly, find a reverse code engineering forum and start reading and looking at tutorials.  Lastly, if you want to learn about malware on linux, I would simply google for Linux rootkit downloads and download them, unpack them, and look at the code.

The above is a major undertaking but so is learning to write malware.  It is my opinion that leaning how malware works and being more familiar with it will teach you far more than simply learning to write malware.  Good luck!

---

### Post by Kinstonian on 2009-02-05
> **2point0 said:**
> Greetings vze57gc8.  If you are looking for malware, you might want to check [http://offensivecomputing.net](http://offensivecomputing.net).  Most of the stuff you find is going to be Win32 but it is still good learning.  If you want to learn a valuable skill, don't spend time trying to write it because that will be justification for the guy who told you to grow up earlier.  Instead, download a copy of Immunity Debugger and OllyDBG, create a virtual install of Windows (I use XP for this purpose) and install the debuggers and disassemblers and spend time analysing malware and seeing how it works.

As you get more and more into this you will acquire a bigger toolkit so you might want to get ahead of the game and find a good hex editor, LordPE, ASPackDie, Reflector for .NET, etc.  Lastly, find a reverse code engineering forum and start reading and looking at tutorials.  Lastly, if you want to learn about malware on linux, I would simply google for Linux rootkit downloads and download them, unpack them, and look at the code.

The above is a major undertaking but so is learning to write malware.  It is my opinion that leaning how malware works and being more familiar with it will teach you far more than simply learning to write malware.  Good luck!

Hey 2point0, do you know of any good beginner tutorials for OllyDBG?

---

### Post by The Tronyx on 2009-02-05
> **Kinstonian said:**
> Hey 2point0, do you know of any good beginner tutorials for OllyDBG?

I am sure you could find a few things [here]("http://www.tuts4you.com/")

There are some nice tutorials with video guides, programs designed for reversing, etc. and that is likely the best place to get started

---

### Post by Kinstonian on 2009-02-06
> **2point0 said:**
> I am sure you could find a few things [here]("http://www.tuts4you.com/")

There are some nice tutorials with video guides, programs designed for reversing, etc. and that is likely the best place to get started

Looks good, thanks!

---

### Post by zerofool2005 on 2009-02-09
If you want to learn penetration. Start basic. Basic IM network social engineering spreading.

E.G "HEY Look its you" >> File.exe
But a nix variant.
Then start looking over remote buffer overrun. And that sort of exploits.

But you just sound like a skiddie. Wanting to write nix backdoors. *perl cough*

---

### Post by The Tronyx on 2009-02-10
> **zerofool2005 said:**
> If you want to learn penetration. Start basic. Basic IM network social engineering spreading.

E.G "HEY Look its you" >> File.exe
But a nix variant.
Then start looking over remote buffer overrun. And that sort of exploits.

But you just sound like a skiddie. Wanting to write nix backdoors. *perl cough*

Arguably some of the worst advice I have ever heard.  It kind of sounds like you just read some cyber crime novel and now you feel that you have a solid grasp on what "it" is all about.

> 
E.G "HEY Look its you" >> File.exe


Kind of made me LOL irl

---

### Post by JoshuaRL on 2009-02-11
> **2point0 said:**
> Kind of made me LOL irl

Nah, this is the best part:

> **zerofool2005 said:**
> Wanting to write nix backdoors. *perl cough*

It's like if the Onion wrote tech advice.

---

### Post by koenn on 2009-02-11
> **vze57gc8 said:**
> i believe ignorance is far more dangerous than knowledge. all i wanna do is learn.

first step in learning, especially in compter related matters, is learning how to find the information you need. 

Simply asking to be fed info on a forum isn't the way. And you picked the wrong forum to begin with.

And yes, you sound like a script kiddie. Why anyone would teach you or help you to create malware is beyond me. I use a computer daily, so I don't want *more* malware out there ....

---

### Post by UbuKunubi on 2009-02-11
Oddly enough, but a very quick Google search for vze57gc8

yeilds the results:

MyPornBucket Free Amateur Teen Porn TOS'd Videos and Pictures ...
vze57gc8 · mpbthis · dinnerroll. Public Videos: 596 | Private Videos: 35 | Watched Videos

---

### Post by Kinstonian on 2009-02-11
> **UbuKunubi said:**
> Oddly enough, but a very quick Google search for vze57gc8

yeilds the results:

MyPornBucket Free Amateur Teen Porn TOS'd Videos and Pictures ...
vze57gc8 · mpbthis · dinnerroll. Public Videos: 596 | Private Videos: 35 | Watched Videos

Looks like someone's interested in more than computer security! :)

It appears after a little googling that he really does plan on getting a job in security and isn't doing anything malicious.

> so i learned alot today. hopefully if i keep up the pace i could get an IT job somewhere. network security is something that interests me specifically. thx

I guess we can stop giving him a hard time now.  Although, koenn brought up a good poing about learning how to find information.

---

