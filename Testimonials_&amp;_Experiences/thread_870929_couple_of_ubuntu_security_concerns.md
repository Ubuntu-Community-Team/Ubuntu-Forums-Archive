---
title: "couple of ubuntu security concerns"
date: 2008-07-26
forum: Testimonials &amp; Experiences
---

### Post by dingorunner on 2008-07-26
Hello, I've been using ubuntu for more than a year now and I've come to realise a couple of 'actions' that ubuntu 'allow' and may not be very safe.

First is the Live CD thing. This Live CD it's pretty safe when you don't have ubuntu installed on your computer, you can test ubuntu without installing it and that's a great option; but in my opinion, Live CD is a 'threat' to the privacy of any ubuntu user and I'll tell you why: Every time you run ubuntu, you are asked for a login password and this password will be repeatedly ask when your about to perform 'administrator' tasks however, when you boot ubuntu from a LiveCD you won't be required a password and admin rights will be granted immediately opening the door to every single file on your filesystem. In other words anyone with a Live CD can access all private files (including your private stuff. 
Is there a way to LOCK files from being accessed that way I'll be happy to hear it.

The second issue I was talking about is Wine. Someday I was testing some VOIP client for Windows on Wine, when I was finished I closed everything and now I had to get some work done and I needed a file that was on my USB Memory (which of course was infected since I had used it in a windows PC on campus) and for my surprise there was an AUTORUN which I repeatedly tried to delete with sudo rights but this file was copying itself over an over again; I didn't know what to do until I remembered I had use Wine before and of course once I finished a wineclient and some .exe processes I was able to completely delete that file. So, Wine acted as a Virus simulator too. 


Any feedback regarding how right or who wrong I am is much welcome.

---

### Post by scragar on 2008-07-26
The liveCD isn't a problem, since any liveCD can access any file on anyones computer for the most part, windows, linux, BSD or whatever. if you are truely concerned about your files in such a way of being accessed then use encryption, hardy supports it easily enough.
Wine is designed to emulate windows, unfortunatly, there are way's with a bit of playing around to get confirmation first, but that going out of your way, if you get a virus running use ```
pkill wine
``` to kill wine processes, easily enough.

---

### Post by Sef on 2008-07-26
> So, Wine acted as a Virus simulator too. 

Viruses can't replicate or do any harm to your GNU/Linux system.

---

### Post by Mr. Picklesworth on 2008-07-26
> **Sef said:**
> Viruses can't replicate or do any harm to your GNU/Linux system.

Not entirely true. A Wine program can happily access and delete files in one's home folder. (On that thought, though, I wonder if there's a way to lock them down?).
Most viruses don't do that, though, or at least won't understand the place...

---

### Post by Keyper7 on 2008-07-26
> **Mr. Picklesworth said:**
> Not entirely true. A Wine program can happily access and delete files in one's home folder. (On that thought, though, I wonder if there's a way to lock them down?).
Most viruses don't do that, though, or at least won't understand the place...

A malicious script can also destroy the home folder without sudo access, in any operational system. And a simple .bat script containing "deltree *" in Windows wouldn't be detected as a virus.

If your concerns go to that extent, then either never download anything or simply don't use your computer. :)

And for the OP: if a malicious user uses a LiveCD in your system, then he has physical access to it. If he has physical access, then it's game over regardless of the operational system you use.

---

### Post by Canis familiaris on 2008-07-26
> **Mr. Picklesworth said:**
> Not entirely true. A Wine program can happily access and delete files in one's home folder. (On that thought, though, I wonder if there's a way to lock them down?).
Most viruses don't do that, though, or at least won't understand the place...

But WINE isn't installed in the Live CD. :D

As for a regular system, I share your concern

---

### Post by Oldsoldier2003 on 2008-07-26
> **dingorunner said:**
> 

First is the Live CD thing. This Live CD it's pretty safe when you don't have ubuntu installed on your computer, you can test ubuntu without installing it and that's a great option; but in my opinion, Live CD is a 'threat' to the privacy of any ubuntu user and I'll tell you why: Every time you run ubuntu, you are asked for a login password and this password will be repeatedly ask when your about to perform 'administrator' tasks however, when you boot ubuntu from a LiveCD you won't be required a password and admin rights will be granted immediately opening the door to every single file on your filesystem. In other words anyone with a Live CD can access all private files (including your private stuff. 
Is there a way to LOCK files from being accessed that way I'll be happy to hear it.




As scragar said. Encryption will defeat live cds. you can go with gpg encryption of sensitive information and if you are extremely concerned you can encrypt the partition (via LUKS, truecrypt or whatever pleases you).

---

### Post by hyper_ch on 2008-07-26
> **Oldsoldier2003 said:**
> As scragar said. Encryption will defeat live cds. you can go with gpg encryption of sensitive information and if you are extremely concerned you can encrypt the partition (via LUKS, truecrypt or whatever pleases you).

I'd rather say encrpyting the whole system is way more confortable than knowing exactely where "important" files are that needed to be protected. With full disk encryption you don't have to worry about that.

---

### Post by shad0w_walker on 2008-07-26
I think you have missed the point here. The LiveCD isn't a security issue. Anyone with physical access to your system can have free reign over it. The only solution to that is to encrypt your files. 

Ever thought that I could go and install Windows on a system with windows already installed? Replace what's already there and give it my own password, then I have full access to the files and my own nice login. LiveCD isn't a problem, the fact you are worried about private data and not encrypting is the problem.

Wine is also not an issue to the whole system and as long as you don't download random virus ladden crap shouldn't be a danger to your personal files either. There are a million and one ways that things can be carried on. Did you consider that if you hadn't noticed the virus with Wine then you would have likely just carried that infected file around with you all over the place? It acted as a simulator, but it also alerted you to the fact there was something dodgy going on.

---

### Post by dingorunner on 2008-07-26
Ok, this Post got more feedback than I thought. Regarding the Live CD thing.. well it's not entirely true that anyone with physical access to your computer will be able to access all my info; most people won't be able to go much further from the login screen, unless they're really trying to SOME harm and they are a trained hacker, but that's not the case. What I was talking about it's more like a noisy brother or someone who doesn't like you at office.
About the Wine issue, I really felt powerless for the whole minute I was trying to delete that file and It was reappearing over and over again, it is true that it's not gonna affect my system but if I hadn't noticed it, it could have copy itself into another USB memory and infect another computer, let's say a friend's computer.
Anyways, I agree you guys, it's not such a big deal.

---

### Post by Oldsoldier2003 on 2008-07-26
> **hyper_ch said:**
> I'd rather say encrpyting the whole system is way more confortable than knowing exactely where "important" files are that needed to be protected. With full disk encryption you don't have to worry about that.

I agree. But a fully encrypted system is just a touch harder to set up. Most folks get along fine without one, but if they are more security conscious it's definitely worth the extra effort and time.

---

### Post by oneporter on 2008-07-26
You guys should give [this new feature]("https://wiki.ubuntu.com/EncryptedPrivateDirectory") coming to 8.10 a read.

Edit: This is in response to concerns about Live cds..

---

### Post by aysiu on 2008-07-26
> **dingorunner said:**
> Regarding the Live CD thing.. well it's not entirely true that anyone with physical access to your computer will be able to access all my info; most people won't be able to go much further from the login screen, unless they're really trying to SOME harm and they are a trained hacker, but that's not the case. What I was talking about it's more like a noisy brother or someone who doesn't like you at office. If someone is nosy or doesn't like you **and** knows how to boot a live CD, she has access to all the unencrypted files on your system. It doesn't matter what OS you're running. This has nothing to do with Ubuntu security.

---

### Post by Keyper7 on 2008-07-26
> **dingorunner said:**
> Ok, this Post got more feedback than I thought. Regarding the Live CD thing.. well it's not entirely true that anyone with physical access to your computer will be able to access all my info; most people won't be able to go much further from the login screen, unless they're really trying to SOME harm and they are a trained hacker, but that's not the case. What I was talking about it's more like a noisy brother or someone who doesn't like you at office.

Well, no one has to be a trained hacker to yank off your hard drive and give it to someone who is. Physical access is game over unless you encrypt your data, period.

Most systems are very vulnerable to physical access by default. The repair mode of the Windows install CD gives you full access to the hard drive. This is not a security issue, but an option for people who forgets their password, for example.

There are more people who forget passwords than people who have to worry about malicious people who have physical access to their computer. And for those people, that's what encryption is for.

> **dingorunner said:**
> About the Wine issue, I really felt powerless for the whole minute I was trying to delete that file and It was reappearing over and over again, it is true that it's not gonna affect my system but if I hadn't noticed it, it could have copy itself into another USB memory and infect another computer, let's say a friend's computer.
Anyways, I agree you guys, it's not such a big deal.

There's nothing that can be done. The whole point of Wine is emulating Windows' behavior and that unfortunately includes being vulnerable to viruses. It would be nearly impossible to restrict what a Windows virus can do without also restricting what actual programs can do. Viruses use the Windows API, Wine implements the Windows API, you do the math.

Wine behaves like Windows, so treat it like Windows: use an antivirus.

---

