---
title: "Is this enough for securing my laptop?"
date: 2011-04-21
forum: Security
---

### Post by FrostBlue on 2011-04-21
Hi,
A few days ago , I suspect my data was stolen from my laptop.I had my screen locked and went away from for about 20 mins. When I came back everything was as I left it,the screen locked,the same folder opened ,etc.
But now I have reason to believe that some personal data , such as my diary and some written stuff is known by others. I had backups in an encrypted container on an external disk so I just reinstalled Kubuntu and set up everything again with a crazy strong password.

Now I am going to do the following to test things before Natty arrives so I can set it up in a more secure way,

*Set up a bios password
*Disable cd boot
*Set up GRUB password
*Install firestarter and configure it
*Look into AppArmour
*Disable remote login
*Have a crypted container for all data and backup everyday in another container on an external disk ,both containers hidden truecrypt volumes 
*Change passwords frequently
*Keep checking logs-logins and network traffic as well

Now , is this enough to lock down a laptop or do I need more. What else should I look into or be aware of ? 
Do I need a hardened kernel , is Bastille still useful on Ubuntu?
Also, could you point me to a guide on how to find rootkits and get rid of them.

I am still learning about security and just wanted to know if I am heading in the right direction and what more should I research about.

Thanks for reading this.

---

### Post by cipherboy_loc on 2011-04-21
Is this a company laptop? Where were you when you suspected a break in of some kind? Home, work, or a public place? What type of break in do you suspect? Physical access, or remote? What was your security situation like before the break in (open ports, extra users, weak passwords, etc)?

As for your list, while I am by no means a security expert, I would expect that to be enough. When you say you will disable remote access, what type of remote access did you have before? Also, do you think anything outside of your ~/ was taken?

Cipherboy

---

### Post by FrostBlue on 2011-04-21
This is a Home laptop and I was at my home. I don't really know what kind of break in it was but I suspect it happened and am taking precautions just in case. Is it easy to bypass  a lock screen ? 
I didn't really set up any open ports after the default Kubuntu installation and don't have any other users. My password was long but didn't have any special characters as I lock screen often. But now I don't mind remembering a long complicated password for security.
I don't know if Kubuntu by default allows any remote access so I was just going to look into and disable it if it was present,so I put it on my list.
I have found about rootkits from this [[COLOR="DarkRed"]sticky[/COLOR]]("http://ubuntuforums.org/showthread.php?t=510812") and am picking up more stuff as I read.

Right now I am wondering about hardened kernels and Bastille as that sounds very secure.

---

### Post by brian_p on 2011-04-22
> **FrostBlue said:**
> 

I am still learning about security and just wanted to know if I am heading in the right direction and what more should I research about.

You don't really have any direction to take if your only motivation is a suspicion. Coming up with a long list of security measures, some of which are of dubious value, to combat data being stolen may get you nowhere unless you are able to pinpoint the area of concern.

I'd stick with changing your password and move on.

---

### Post by FrostBlue on 2011-04-22
I get your point Brian , if we put aside the question of whether my suspicions are founded or not , could you please point out which things on the list did you think were dubious and why.

I know the BIOS password is useless if you remove some battery or something.

I am just trying to learn a few things,data stolen or not. I have already reinstalled Kubuntu anyway.

---

### Post by CharlesA on 2011-04-22
Why do you think that someone accessed your machine without your knowledge?

If you use a strong password and lock the screen, there really isn't anything that can be done without powering off the machine - unless someone knows your password.

---

### Post by FrostBlue on 2011-04-22
> **CharlesA said:**
> If you use a strong password and lock the screen, there really isn't anything that can be done without powering off the machine - unless someone knows your password.

Cool thanks for clearing that CharlesA , I just have a strong suspicion so I am doing as much I can to learn about security now. I kind of knew Ubuntu was relatively secure out of the box but after going through this forum for only one day I have picked up so many things.

Probably wont be messing around with hardened kernels and even AppArmor actually , but a few easy to setup roadblocks in the path of an intruder don't really hurt , I guess.

---

### Post by brian_p on 2011-04-22
> **FrostBlue said:**
> I get your point Brian , if we put aside the question of whether my suspicions are founded or not , could you please point out which things on the list did you think were dubious and why.

Why change passwords at all, nevermind frequently. Starting with a strong one known only to you is sufficient. Also, ufw is usually recommended instead of firestarter, which is no longer actively maintained. I use neither, nor do I filter any packets coming in. No ill effects so far.

Make your starting point the intention to understand the security state of your default installation before being tempted to alter it. Keep it updated from the official archives and it will serve you well. By all means read up on security but critically examine whether any particular advice suits your situation.

---

### Post by FrostBlue on 2011-04-22
> **brian_p said:**
> By all means read up on security but critically examine whether any particular advice suits your situation.

I agree with that.
I will look into ufw , BTW what about GuardDog ?

---

### Post by mr-woof on 2011-04-22
Why do you think someone has managed to get into the laptop and take some data?

---

### Post by brian_p on 2011-04-22
> **FrostBlue said:**
> I agree with that.
I will look into ufw , BTW what about GuardDog ?

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=619736](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=619736)

---

### Post by FrostBlue on 2011-04-22
@ mr-woof - I don't really want to share that , I am not sure of the data loss 100% , but I have a few reasons to believe it could be possible so I am just using this to look into security a little , otherwise I wont really bother with it. Kubuntu has never given me security worries at all and even this may be nothing. Although my password wasn't really the strongest. Now I know how to make better ones and remember them too !! Besides forensics is not an issue right now I am taking precautions for future thats all.

@ brian_p - thanks man , ufw it is then.Cheers.

---

