---
title: "A couple of questions"
date: 2011-12-24
forum: Security
---

### Post by rima on 2011-12-24
Hello! I've got a couple of questions to ask regarding security for Ubuntu. First of all, I would like to introduce myself.  I'm your average computer user, I mainly use computers for computer graphics and occasional word processing and browsing. I never play any computer games, I rarely/not very often check on my emails. For Firefox I use NoScript, Ghostery, AdBlock, and myWOT. I'm a very cautious surfer and if I find the website suspicious, I never really click on it or I check the reputation of it. I never do internet banking or store very important files.  What safety measures could I use? I read the Security Sticky and Other guides but I got throughly confused and still don't know what to do. (I only got Ubuntu 2 days ago, plus I used Windows for ages, so I know it's not the same.)   1. Do I need an antivirus? (I know there isn't a lot of viruses, but I still like to be extra cautious). 2. Do I really, really need a firewall?  3. Should I use any other anti-malware programs?  4. Should I do anything with Terminal? (to be honest, I'm very scared of using it, as I'm afraid of messing anything up 5. What else should I do?  I would appreciate any sort of tips or tricks.

---

### Post by BC59 on 2011-12-24
All your questions are answered here
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by oldos2er on 2011-12-24
Moved to Security Discussions.

---

### Post by Ms. Daisy on 2011-12-24
The wiki in my signature was created specifically for people like you. Hope it helps.

---

### Post by HermanAB on 2011-12-25
Dude, just relax and enjoy your Ubuntu system.  It will work perfectly fine without you having to do anything special.  Yes, I know that sounds incredible to a Windows refugee, but with Linux, you can blissfully enjoy your machine the way the computer gods intended.

---

### Post by Ms. Daisy on 2011-12-25
> **rima said:**
>  4. Should I do anything with Terminal? (to be honest, I'm very scared of using it, as I'm afraid of messing anything up 
In regards to this little bit, I had similar concerns.  I decided to install ubuntu in a virtual box and that allows me to mess around in bash without worrying.  If I break it, I can just revert to a snapshot.

---

### Post by saneearth on 2011-12-25
> **HermanAB said:**
> Dude, just relax and enjoy your Ubuntu system.  It will work perfectly fine without you having to do anything special.  Yes, I know that sounds incredible to a Windows refugee, but with Linux, you can blissfully enjoy your machine the way the computer gods intended.

I agree with HermanAB. If and when you decide to start using terminal just begin with cutting and pasting know commands for installs or to change directories that are available from Ubuntu sites. Start slowly and you will learn. The biggest things are that if you have a good admin password there are few if any security concerns. In over six years of using linux I have never been infected or compromised in any way and I am not especially careful. You sound as if you use more precautions than the general public, so you shouldn't have a thing to worry about other than doing the things you like and need to do.

---

### Post by Gentoo64 on 2011-12-26
The thing is, Windows users all go on this massive security craze, because viruses/malware are the norm, everyone keeps recommending security software, and security apps for Windows are advertised everywhere online saying you _need_ them.
So you have a load of stuff running like antivirus, antispyware, etc etc that you have to constantly monitor and update.

Then you move to Linux, and you see you have none of this 3rd party stuff running, and nothing to do. Naturally that can make you feel a bit paranoid, but for the average user you really don't have to do anything at all on Linux. Just get on with whatever it is you need to do :)

---

### Post by Ms. Daisy on 2011-12-27
[QUOTE=saneearth]...The biggest things are that if you have a good admin  password there are few if any security concerns...[/QUOTE]
[QUOTE=Gentoo64]...but for the average user you really don't have to do anything at all on Linux...[/QUOTE]
[QUOTE=HermanAB]It will work perfectly fine without you having to do anything special.  [/QUOTE]

The Windows mindset is definitely very different than the *nix mindset, I'll agree with that much.

It's pretty easy to do a few basic things to make your Ubuntu a lot more  secure, all outlined in the wiki (staff advised me to put it in the body of the post instead of  only in my sig, so here it is again: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)).

And it's true, you don't HAVE to do anything on Linux.  No one's holding  a gun to anyone's head to run a basic firewall or install all security  updates.  But it's ill-advised to do nothing.  It seems like a big  hurdle for people to understand that one of the biggest threats to  security on Ubuntu is in the browser (be it firefox, opera, chrome...).  And it can  be completely out of your control.  I can visit  MyFavoriteSite.com  every single day with no problems.  Then one day Billy BlackHat  compromises MyFavoriteSite.com. When I visit it, a malicious code executes in my  browser and gives him access to my machine. Fact: it happens.  So why chance it when it's so easy to set up a basic defense?

---

### Post by haqking on 2011-12-27
Viruses and malware are a very small percentage in security attack vectors, Linux is no more secure than windows or any other OS.

Yes it is more immune to viruses but that could easily change very quickly and we dont have any current good AV solutions with heaurisitics that could be of much help if this happened, actually it is not even that it is more immune per se, it just has no major virus threat currently

However as i said Viruses are very little to do with security overall as the payloads are often nuisance based.

As for any other compromise Linux is as susceptible as any other OS.

It is upto you to make sure your browsing habits remain intelligent, use things like NOScript etc, enforce tight outbound and inbound firewall rules, maybe use things like Apparmor etc

Cheers

---

### Post by Dangertux on 2011-12-27
I agree with haqking. Viruses are a small percentage of threats even on windows (yeah I said that). At the very minimum I would suggest doing what you do with your browser. In addition to that a well configured firewall never hurt anyone (can someone link my thread? I'm stuck at work yay on call!). If you're feeling particulary adventurous (doesn't sound like you are) you can try using an apparmor profile for your browser. Te default profile for firefox works pretty well so that should be easier. Easier still and more often overlooked: are you using strong passwords? You should be, for everything and make sure you're not re using them. Also what about updates you need to make sure you're keeping up with them. 

Hope this helps.

---

### Post by Ms. Daisy on 2011-12-27
> **Dangertux said:**
>  In addition to that a well configured firewall never hurt anyone (can someone link my thread? I'm stuck at work yay on call!). 
Dangertux's threads on firewalls:

_Do I need a firewall?_  [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

_Creating a firewall_  [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

---

