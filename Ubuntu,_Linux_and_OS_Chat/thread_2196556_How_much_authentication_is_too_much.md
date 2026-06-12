---
title: "How much authentication is too much?"
date: 2013-12-30
forum: Ubuntu, Linux and OS Chat
---

### Post by jgestiot on 2013-12-30
Hi,

I have just replaced my windows 8.1 with Ubuntu 13.10. In the process I had to install quite a lot of bits and it took me over a day to customise the environment. Most of it works pretty well except netbeans which dies while loading modules. I will look into it tomorrow...

My issue is this... I had to authenticate over 50 times during the process. What makes Ubuntu believe that I am not the same person that authenticated 20 seconds ago for something else? I get asked via sudo, even though it is the same terminal window open that is opened from a previous authentication. I get asked when dealing with the software center, canonical, when changing system settings. 

To add insult to injury, I get asked to authenticate while "buying" free software.

This remind me of a simple optimization we put into a chess program about 25 years ago.  Rather than going through alpha-beta pruning at a ridiculous depth, if it is the only move, MAKE IT! do not calculate at any depth. Here is pretty much the same philosophy. If a guy authenticated 20 seconds or 3 minutes ago, it is the same freaking guy at the computer. 

And what's up with having to go through the buying process for free software? There seems to be a self-centered attitude at Ubuntu with developers so preciously looking at their belly button, they fail to see the logical and natural world around themselves.

The operating system needs to work for me. Today, I worked for the operating system. I am sure there is a setting somewhere or a workaround to deal with this rubbish but it must be reserved for the inner sanctum...

Next time I might post something about the nightmare of finding a setting in the dconf editor.

---

### Post by Elfy on 2013-12-30
mmm - if you have to supply the password 50 times I'd guess you did so in seperate apps

I did a clean install yesterday - installed those applications and edited those system files I wanted to and authenticated 3 or 4 times. 

Not sure what you did to need 50 off them - perhaps because you're learning to use linux.

So - if you don't like the way it works - don't - use windows if it suits you.

>  Next time I might post something about the nightmare of finding a setting in the dconf editor. 

If you do - perhaps you'll do people the favour of finding where to posts it. Top tip - read forum descriptions - might work wonders.

I have no idea how posting a thread about not understanding an OS authentication method should be posted in a forum who's description is 

> Report technical problems with the website here (i.e. broken features), or ask questions pertaining to forum features.

Thread moved.

---

### Post by buzzingrobot on 2013-12-30
In Unix/Linux/OS X, software installation requires modifications of files and directories that only root has the privilege of changing, or, sometimes, just accessing. That's why you're prompted to authenticate. It can be annoying early on while setting up a system.  Once that's done, you won't be prompted to authenticate very often at all.

The essential "free" in FOSS has to do with freely available source code, not the zero-cost kind of free. Nothing is wrong with selling free software; licensing does not require FOSS products to be gratis.  For that matter, Canonical is free to sell closed- source products if it wants to, and you are free to buy or not buy.

Dconf, like Window's Registry editor, is an admin tool not really intended for end user manipulation. It allows changes to various schemas, the same ones that are typically changed by the intended-for-users GUI-fied System Settings that don't require knowing where, in the hierachical scheme of things, a value is located. dconf assumes you do.

---

### Post by vasa1 on 2013-12-30
> **jgestiot said:**
>  ...
My issue is this... I had to authenticate over 50 times during the process. What makes Ubuntu believe that I am not the same person that authenticated 20 seconds ago for something else? I get asked via sudo, even though it is the same terminal window open that is opened from a previous authentication. ...
Hard to believe. Sorry.

---

### Post by 3rdalbum on 2013-12-30
I also can't understand why you'd need to authenticate fifty times in a day. A number that makes more sense is "less than ten", for someone just starting up with installing their system. Of course, once you've settled down and are merely using your system instead of learning and setting up, you'll probably only type your password twice a day.

In any case, the authentication prompt is not so much to prove that you are the same person who was in front of the computer twenty seconds ago, but more of a way to ensure a piece of malware can't just invisibly make changes to your system. Access to modify system files and certain "privileged" operations is only available through 'sudo', 'gksudo' or Policykit, and all three of these require you to prove your humanity by typing your password. That's something a piece of malware can't guess, and there are systems in-place to ensure that malware can't actually overhear your password as you type it.

---

### Post by buzzingrobot on 2013-12-30
Sudo in Ubuntu times out in, I think, 15 minutes, requiring re- authentication. If it was actually timing out every 20 seconds, something was wrong.

OP might also look at "sudo -i", the inherent risks, etc.

---

### Post by grahammechanical on 2013-12-31
> [COLOR=#000000]If a guy authenticated 20 seconds or 3 minutes ago, it is the same freaking guy at the computer. [/COLOR]

That would be a most stupid assumption for a OS developer to make. I can use the Ubuntu Software Centre to queue several applications that I select to install. So that the installation of them takes place in one operation with one authentication. If I use the terminal to install applications, then once I have entered my password as requested then I can run command after command without needing to put in my password. But if I stop entering commands I will lose that administrator's privilege after about 15 minutes. This is called "security." If I can do this, why can't you? 

What we cannot do in Ubuntu is install closed source, proprietary software that is under a licence without accepting the terms of the licence agreement. Or install software that it might be illegal to install in some countries without our taking personal responsibility for the action. Perhaps you were installing that kind of software.

I do not believe that you are genuine. Your complaints do not match the reality of Ubuntu.

Good Bye.

---

### Post by buzzingrobot on 2013-12-31
> **grahammechanical said:**
> That would be a most stupid assumption for a OS developer to make. 


Yeppers.  Software isn't clairvoyant.  It has no way of knowing who is at the keyboard.

(My Evil Twin might notice that the OP had opened a root terminal to avoid all the inconvenience of authentication, issued a time-consuming command and walked out for coffee.  I walk in and notice this, suspend the command and use rm to wipe his disk. Ta-da.)

---

### Post by Dave_L on 2014-01-01
If I'm doing a long sequence of actions that require root privileges, I'll open a root shell with "sudo -i".  That helps even with GUI applications, I think, if they're launched from the command line.

---

### Post by t0p on 2014-01-02
> **buzzingrobot said:**
> 
(My Evil Twin might notice that the OP had opened a root terminal to avoid all the inconvenience of authentication, issued a time-consuming command and walked out for coffee.  I walk in and notice this, suspend the command and use rm to wipe his disk. Ta-da.)

Why would you want to do that?  I think it's *you* who is the evil twin!  Leave his computer alone, you evil twin you!

---

