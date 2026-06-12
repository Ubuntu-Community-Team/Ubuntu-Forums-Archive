---
title: "Does Ubuntu need antivirus?"
date: 2019-06-08
forum: Ubuntu, Linux and OS Chat
---

### Post by j2ee on 2019-06-08
It sounds silly but I know the old answer was NO many years ago, the answer is still NO now?

---

### Post by TheFu on 2019-06-08
> **j2ee said:**
> It sounds silly but I know the old answer was NO many years ago, the answer is still NO now?
I don't, unless a contract requires it, like professional E&O insurance.
There is a sticky post at the top of the "Security" sub-forum here with more.

---

### Post by Rubi1200 on 2019-06-08
Have been using Linux distros since 2005 and have never installed or used antivirus.

---

### Post by #&amp;thj^% on 2019-06-08
> **Rubi1200 said:**
> Have been using Linux distros since 2005 and have never installed or used antivirus.

+1 Same here.

---

### Post by j2ee on 2019-06-08
> **emre-atakuru08 said:**
> No because if you install something on linux system
you can read everything of code so hackers doesn't write virus :)
if you don't know programming language of code 
maybe you can install harmful things on your computer :)

How about if I visit some websites and somehow the site does something to my computer? You really read every single line of code when you visit a website!?

---

### Post by TheFu on 2019-06-08
> **emre-atakuru08 said:**
> No because if you install something on linux system
you can read everything of code so hackers doesn't write virus :)
if you don't know programming language of code 
maybe you can install harmful things on your computer :)

I disagree with the reasoning above.  

Not all source code is available.  There are viruses for Linux. There are worms, there are remote exploits, and it isn't that hard to trick a user into copy/pasting commands that could be used to take over a linux system.

Nobody has the time or the skill to review all the source code on their system.  Experts in programs have been known to miss issues in their own code, much less catch problems in other people's code.

There are viruses written for Linux, but generally those are used to attack Linux servers, not desktops. It is purely a numbers game.  Suppose over 50% of the servers on the internet are running Linux, while only 1% of the desktops do.  Where would you spend your time?  There are millions of Linux servers running right now which have been hacked and are doing something other than what their admin thinks they should be doing. [https://www.zdnet.com/article/wordpress-accounted-for-90-percent-of-all-hacked-cms-sites-in-2018/](https://www.zdnet.com/article/wordpress-accounted-for-90-percent-of-all-hacked-cms-sites-in-2018/) 
[https://www.wpwhitesecurity.com/statistics-70-percent-wordpress-installations-vulnerable/](https://www.wpwhitesecurity.com/statistics-70-percent-wordpress-installations-vulnerable/)
[https://www.linux.com/learn/myth-busting-linux-immune-viruses](https://www.linux.com/learn/myth-busting-linux-immune-viruses) 

But for typical end users, only installing software from the Canonical repositories, not running any services, always behind a currently patched router with a firewall enabled, the risks are tiny. Just don't go visiting bad parts of the internet, opening email attachments from unknown sources, or running code you download from untrusted places.

---

### Post by j2ee on 2019-06-11
> **TheFu said:**
> I disagree with the reasoning above.  

Not all source code is available.  There are viruses for Linux. There are worms, there are remote exploits, and it isn't that hard to trick a user into copy/pasting commands that could be used to take over a linux system.

Nobody has the time or the skill to review all the source code on their system.  Experts in programs have been known to miss issues in their own code, much less catch problems in other people's code.

There are viruses written for Linux, but generally those are used to attack Linux servers, not desktops. It is purely a numbers game.  Suppose over 50% of the servers on the internet are running Linux, while only 1% of the desktops do.  Where would you spend your time?  There are millions of Linux servers running right now which have been hacked and are doing something other than what their admin thinks they should be doing. [https://www.zdnet.com/article/wordpress-accounted-for-90-percent-of-all-hacked-cms-sites-in-2018/](https://www.zdnet.com/article/wordpress-accounted-for-90-percent-of-all-hacked-cms-sites-in-2018/) 
[https://www.wpwhitesecurity.com/statistics-70-percent-wordpress-installations-vulnerable/](https://www.wpwhitesecurity.com/statistics-70-percent-wordpress-installations-vulnerable/)
[https://www.linux.com/learn/myth-busting-linux-immune-viruses](https://www.linux.com/learn/myth-busting-linux-immune-viruses) 

But for typical end users, only installing software from the Canonical repositories, not running any services, always behind a currently patched router with a firewall enabled, the risks are tiny. Just don't go visiting bad parts of the internet, opening email attachments from unknown sources, or running code you download from untrusted places.

How about the ads on popular sites got hacked?

---

### Post by kevdog on 2019-06-12
Twist on the scenario -- I Ubuntu shares a partition or stores files obtained from Windows -- does it need an Antivirus? Perhaps the answer in this scenario should be possibly?

---

### Post by j2ee on 2019-06-15
> **kevdog said:**
> Twist on the scenario -- I Ubuntu shares a partition or stores files obtained from Windows -- does it need an Antivirus? Perhaps the answer in this scenario should be possibly?

This is an interesting question...

---

### Post by kpatz on 2019-06-15
If you store Windows files on your Ubuntu system (via samba, or a mounted NTFS partition, etc). any malware won't infect the Ubuntu system since it can't/won't run Windows executables.  The only exceptions here is if you use WINE, or if the malware is in a script language that an interpreter is available for like Perl or Python, and even in these cases, someone would have to explicitly run the script.

If you're using Ubuntu as a file server/NAS storing files accessed by Windows systems, chances are the Windows systems will have antivirus on them anyway, so it's not really the responsibility of the NAS to scan/clean files.  But, you could install an antivirus and use it to scan the Windows share folders if you like.

Another case where you may want a virus scanner in Ubuntu is if you're running an email server, especially one that Windows clients will use, and you want to scan incoming attachments, or a website that allows files to be uploaded and stored and you want them scanned.

---

### Post by cruzer001 on 2019-06-15
> **j2ee said:**
> This is an interesting question...
I then would let windows antivirus/malware kick in and scan any or all files.

I think let windows do windows and linux do linux.

---

### Post by j2ee on 2019-06-19
> **j2ee said:**
> How about the ads on popular sites got hacked?

Anyone has idea? Just believe in Linux with faith is good enough?

---

### Post by DuckHook on 2019-06-21
> **j2ee said:**
> Anyone has idea? Just believe in Linux with faith is good enough?

Depends what you mean by "believe" and "faith". This is often used as a passive-aggressive sneer by Linux detractors (I'm not accusing you of doing so&#8212;but it's a common ploy used against the Linux community), the implication being that we have no reasonable grounds for our "faith". So, to tease out the nuances, consider the following:

[LIST=1]
[*]Do you have "faith" in the brakes in your car? If so, on what basis?
[*]Do you have "faith" in the plane on which you are flying? If so, on what basis?
[*]Do you have "faith" in the structural integrity of the roof over your head? If so, on what basis?
[*]How and why does slathering on some impenetrable after-market code from some impenetrable private company that you have no better understanding of than the OS itself somehow justify an increase in your "faith"? On what basis should we "believe" closed-source AV companies over open-source OS developers?
[*]How does AV work anyways? If they are directed towards Windows viruses, then isn't installing one on a Linux system like wearing a parachute on a boat? Or a lifejacket on a train?
[*]How will AV help you against ransomware? Socially engineered identity theft? Rootkits that load your OS as a VM and therefore hide "underneath" any AV scan?
[*]How do "hacked ads on popular sites" actually do their dirty work? If a popular site is compromised through spoofing, DNS poisoning, etc, can AV even catch this?
[/LIST]
It ought to be quite clear where I'm going with all of this: there are myriad factors that contribute to good security. In the Linux sphere, AV is not one of them. In a rather long association with these forums dealing especially with new users, I actually find the opposite is true: it is a useless Windows holdover that creates a false sense of security, perpetuates the delusion that security is about installing apps instead of adopting good behaviours, and wastes time, energy, money and attention addressing the wrong things.

Security is a complex topic that is almost 100% about modifying behaviours, hardening systems, working under least privileges and avoiding stupid actions; it is not about installing obscure, impenetrable apps. TheFu pointed you to a sticky that will give you a great introduction to good security habits. It is reproduced in my sig under: Security Basics

You are well advised to read it. That sticky is worth more than 100 AV apps.

---

### Post by j2ee on 2019-06-22
> **DuckHook said:**
> Depends what you mean by "believe" and "faith". This is often used as a passive-aggressive sneer by Linux detractors (I'm not accusing you of doing so—but it's a common ploy used against the Linux community), the implication being that we have no reasonable grounds for our "faith". So, to tease out the nuances, consider the following:

[LIST=1]
[*]Do you have "faith" in the brakes in your car? If so, on what basis? 
[*]Do you have "faith" in the plane on which you are flying? If so, on what basis? 
[*]Do you have "faith" in the structural integrity of the roof over your head? If so, on what basis? 
[*]How and why does slathering on some impenetrable after-market code from some impenetrable private company that you have no better understanding of than the OS itself somehow justify an increase in your "faith"? On what basis should we "believe" closed-source AV companies over open-source OS developers? 
[*]How does AV work anyways? If they are directed towards Windows viruses, then isn't installing one on a Linux system like wearing a parachute on a boat? Or a lifejacket on a train? 
[*]How will AV help you against ransomware? Socially engineered identity theft? Rootkits that load your OS as a VM and therefore hide "underneath" any AV scan? 
[*]How do "hacked ads on popular sites" actually do their dirty work? If a popular site is compromised through spoofing, DNS poisoning, etc, can AV even catch this? 
[/LIST]
It ought to be quite clear where I'm going with all of this: there are myriad factors that contribute to good security. In the Linux sphere, AV is not one of them. In a rather long association with these forums dealing especially with new users, I actually find the opposite is true: it is a useless Windows holdover that creates a false sense of security, perpetuates the delusion that security is about installing apps instead of adopting good behaviours, and wastes time, energy, money and attention addressing the wrong things.

Security is a complex topic that is almost 100% about modifying behaviours, hardening systems, working under least privileges and avoiding stupid actions; it is not about installing obscure, impenetrable apps. TheFu pointed you to a sticky that will give you a great introduction to good security habits. It is reproduced in my sig under: Security Basics

You are well advised to read it. That sticky is worth more than 100 AV apps.

Let's say I visit a popular website like CNBC.com, and the ads on the site got hacked and run codes that even CNBC doesn't know. How do I have a good security habit to prevent that? I suppose to read every single line of code even I visit a popular site like CNBC?

---

### Post by QIII on 2019-06-22
You can "what if" this to death.  If you are looking for the perfect recipe for security and safety, it doesn't exist.  Don't waste your time looking for it.  

Linux is not perfectly secure.  It is not impervious to the actions of bad actors.  No OS is.  Linux does, however, present a number of speed bumps and impediments.

The only way to avoid what you are worrying about is to disconnect the cable from the wall.

The world if full of risk.  You read up on best security practices, you assess what level of risk you are willing to accept and you mitigate against the risks you can.  Then, you go about your business.

If you are going to worry about it this much, I recommend a large pair of scissors.

Do you need antivirus?  No.  The "virus", as it applies to Windows, is foreign to Linux.  That does NOT mean that there are not other forms of malware, some similar to Windows viruses, that exist in proof of concept and a small few that exist in the wild.  The latter are generally avoided by applying the latest updates to your OS.  It might be a great favor to your Windows friends to use some form of antivirus to scan documents you are sending to them, but that won't be perfect since the antivirus packages available for Linux are not kept up-to-the-minute.

Can you be hacked?  Yes.  Can you be socially engineered? Yes.  Can you foolishly install software that is dangerous?  Yes.  Can you fail to use a firewall?  Yes?  Can you use password SSH on port 22?  Yes.  Can you allow root login over SSH?  Yes.  You can do a lot of things to open yourself up to trouble.

What to do?  Read, understand and apply security processes and methods.  Lather, rinse, repeat.  Security is not "fire-and-forget".  It is a constant process and takes effort.

Relax.  Drink an icy one.  Take a long walk down by the river.

---

### Post by DuckHook on 2019-06-22
> **QIII said:**
> You can "what if" this to death.  If you are looking for the perfect recipe for security and safety, it doesn't exist.  Don't waste your time looking for it.  

Linux is not perfectly secure.  It is not impervious to the actions of bad actors.  No OS is.  Linux does, however, present a number of speed bumps and impediments.

The only way to avoid what you are worrying about is to disconnect the cable from the wall.

The world if full of risk.  You read up on best security practices, you assess what level of risk you are willing to accept and you mitigate against the risks you can.  Then, you go about your business.

If you are going to worry about it this much, I recommend a large pair of scissors.

Do you need antivirus?  No.  The "virus", as it applies to Windows, is foreign to Linux.  That does NOT mean that there are not other forms of malware, some similar to Windows viruses, that exist in proof of concept and a small few that exist in the wild.  The latter are generally avoided by applying the latest updates to your OS.  It might be a great favor to your Windows friends to use some form of antivirus to scan documents you are sending to them, but that won't be perfect since the antivirus packages available for Linux are not kept up-to-the-minute.

Can you be hacked?  Yes.  Can you be socially engineered? Yes.  Can you foolishly install software that is dangerous?  Yes.  Can you fail to use a firewall?  Yes?  Can you use password SSH on port 22?  Yes.  Can you allow root login over SSH?  Yes.  You can do a lot of things to open yourself up to trouble.

What to do?  Read, understand and apply security processes and methods.  Lather, rinse, repeat.  Security is not "fire-and-forget".  It is a constant process and takes effort.

Relax.  Drink an icy one.  Take a long walk down by the river.

&#8593;+++1&#8593;

> **j2ee said:**
> Let's say I visit a popular website like CNBC.com, and the ads on the site got hacked and run codes that even CNBC doesn't know. How do I have a good security habit to prevent that? I suppose to read every single line of code even I visit a popular site like CNBC?

QIII's answer is spot on. The goal is not to get to "absolute" security, but to a state of "good enough" so that one can go about one's business without being debilitated by anxiety. This was the point of my first three questions—if you are hopelessly paranoid about brake failure, you won't drive. If you are hopelessly paranoid about plane safety, you won't fly. If you are hopelessly paranoid about roof integrity, you will be spending the rest of your life outdoors and sleeping out of a tent.

However, your question about a bad website is valid enough. Here are the measures that I take:

[LIST=1]
[*]My browsers are all run within VMs. This is a barrier to a bad website infecting my main box, but it will not stop a cunning phishing attack or expertly spoofed site. If at all unsure after a visit, I nuke the VM and restore from a pristine prior snapshot.
[*]I have installed uBlock Origin which blocks all ads. Ghostery which blocks trackers. Noscript which blocks all scripting. Cookie Autodelete which clears all cookies upon exiting a site. In short, it is very difficult for rogue scripts/trackers to run on my browser.
[*]My main browser is FF, not Chrome, because I prefer a browser that has no conflict of interest between my user goals and outside corporate goals.
[*]When visiting unknown sites, I use Links2 (in graphic form) which is not even capable of scripting or setting cookies. If a site won't run without either, I use Tor Browser.
[*]I never, ever click on e-mailed links. Especially those purported to come from my friends. I will carefully examine their URL and, if comfortable with them, type them in separately into a browser.
[*]The above is just browser hardening. I also have apparmor profiles set up, firewall rules both incoming and outgoing, routinely review my logs, and have backups of my backups, among other things that you can best review by visiting that sticky that everyone keeps referring you to.
[*]I like to think that I am savvy enough to smell a rat where one exists. A sense of caution and scepticism is as necessary in the online world as it is in the physical world. But if one is reasonably confident in one's wariness, then it is just as pointless being a virtual worrywart as it is being one in life.
[/LIST]
These measures are all technical. They cannot stop me from doing stupid things. If I download apps from the Internet instead of sticking to the repos, or add PPAs willy-nilly, or run obscure scripts that I found on some site because someone told me it would fix something, or install that cute cat screensaver from i-pwn-you.com, then I am the author of my own misery and no app, process, barrier or magic pill is going to save me. As a corollary to what QIII states, the biggest worry on the Internet is not some rogue site, but our own idiotic behaviour.

In the final analysis, all of these measures, as intricate as they are, cannot prevent me from getting pwned. There is always risk in life. That's just life.

---

### Post by j2ee on 2019-06-23
> **DuckHook said:**
> &#8593;+++1&#8593;



QIII's answer is spot on. The goal is not to get to "absolute" security, but to a state of "good enough" so that one can go about one's business without being debilitated by anxiety. This was the point of my first three questions—if you are hopelessly paranoid about brake failure, you won't drive. If you are hopelessly paranoid about plane safety, you won't fly. If you are hopelessly paranoid about roof integrity, you will be spending the rest of your life outdoors and sleeping out of a tent.

However, your question about a bad website is valid enough. Here are the measures that I take:

[LIST=1]
[*]My browsers are all run within VMs. This is a barrier to a bad website infecting my main box, but it will not stop a cunning phishing attack or expertly spoofed site. If at all unsure after a visit, I nuke the VM and restore from a pristine prior snapshot. 
[*]I have installed uBlock Origin which blocks all ads. Ghostery which blocks trackers. Noscript which blocks all scripting. Cookie Autodelete which clears all cookies upon exiting a site. In short, it is very difficult for rogue scripts/trackers to run on my browser. 
[*]My main browser is FF, not Chrome, because I prefer a browser that has no conflict of interest between my user goals and outside corporate goals. 
[*]When visiting unknown sites, I use Links2 (in graphic form) which is not even capable of scripting or setting cookies. If a site won't run without either, I use Tor Browser. 
[*]I never, ever click on e-mailed links. Especially those purported to come from my friends. I will carefully examine their URL and, if comfortable with them, type them in separately into a browser. 
[*]The above is just browser hardening. I also have apparmor profiles set up, firewall rules both incoming and outgoing, routinely review my logs, and have backups of my backups, among other things that you can best review by visiting that sticky that everyone keeps referring you to. 
[*]I like to think that I am savvy enough to smell a rat where one exists. A sense of caution and scepticism is as necessary in the online world as it is in the physical world. But if one is reasonably confident in one's wariness, then it is just as pointless being a virtual worrywart as it is being one in life. 
[/LIST]
These measures are all technical. They cannot stop me from doing stupid things. If I download apps from the Internet instead of sticking to the repos, or add PPAs willy-nilly, or run obscure scripts that I found on some site because someone told me it would fix something, or install that cute cat screensaver from i-pwn-you.com, then I am the author of my own misery and no app, process, barrier or magic pill is going to save me. As a corollary to what QIII states, the biggest worry on the Internet is not some rogue site, but our own idiotic behaviour.

In the final analysis, all of these measures, as intricate as they are, cannot prevent me from getting pwned. There is always risk in life. That's just life.

I doubt how many people do all these 7 steps to visit a popular website like cnbc.com, and these 7 steps are far away what people believe just install Ubuntu/other Linux distro then safe from virus and don't need antivirus at all.

---

### Post by oldos2er on 2019-06-24
OP's question has been answered multiple times now. Closed.

---

