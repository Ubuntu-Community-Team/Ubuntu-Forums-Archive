---
title: "Virus crossover?"
date: 2011-05-28
forum: Security
---

### Post by yeappp on 2011-05-28
Hello all hope your all well

I just wanted to know if i use my android phone and connect to my home network

which also has a  pc connected which runs ubuntu was to get infected by a virus rootkit etc which is on the same network 

Will this also make my phone infected with a virus too?

Also how does  virus or root kit or malware work if say i get a infected pc then i was to unplug that pc and use a brand new one with no virus that that mean theres no more virus etc on the network 

Many thanks

---

### Post by Thewhistlingwind on 2011-05-28
Unless the virus is written to exploit android, no.

Viruses are the result of malicious code. The code needs to be able to get read/write permissions on your machine, and be executed to be at all useful to the attackers. Like any other application, the code will not be able to execute if your computer is off.

Microsoft windows gets a lot of viruses because there are many security holes in the code of the OS. They are not fixed for a very long time. The Linux/Ubuntu developers make a point of fixing security vulnerabilities immediately. 

So because your using a Linux OS, which has low market share and thus is a rarely targeted platform, with constantly updated patches for security holes, and you don't go running every piece of code on the internet. For the time being, your chances of contracting a web virus border on the impossible. 

If your worried, you should look into implementing a MAC, turning on firewalls, and using other programs detailed in this forum to lock down your box.

The most vulnerable thing is your browser. (And the chances of that getting infected are MUCH *MUCH* higher!!!!) To secure it:

1. Use noscript
2. Use a flash cookie deletion program
3. You may want to block all cookies in general (There are managers to make this less of a pain when you need to enable them.)
4. Don't go where theres normally trouble
5. Use secure protocols such as SSH when logging into websites. (Assuming they support it, a banking website that doesn't shouldn't be used, even if it's legitimate.)
6. In addition to #5, check certificates if you have time.

---

### Post by yeappp on 2011-05-31
Hi thanks for replying very informative

Just to clarify so if a virus is on the Ubuntu machine lets just say  for example and i turn off my wireless  does this mean the virus is not affecting any other pc or phones that are using the same network connected to wireless

 and if i wanted to use a new installed ubuntu machine on the same network but was worried by a virus that was on the old pc that used to be connected  but no longer connected would i be right in saying the virus would not affect the new machine too simply because the wireless is switched off?


so bascially a virus just sits on that pc thats infected and not any other devices or pc connected to that network is this correct? ps other devices do not have print share or share folders enabled

what if the code had already executed and i turned off the pc afterwards disconnented it and never used it again is it still safe to use other devices on the network


also what is a virus trying to do and why do they have them? whats the main reason some one would want to send virus down your pc i assuming only for banking details ?otherwise why else please note i am am not talking about coperative websites just home users

---

### Post by stracky on 2011-06-01
Disconnecting the computer will prevent the virus from spreading.
It won't stop it if the virus got off the computer

As Thewistleingwind said, there are very few viruses that can run on Windows, Android, and Ubuntu

Viruses are not magical gremlins that live in computers.  They will only do what they were programed to do.

Networks are just connected computers.  If there are no other computers on the network, or the other computers are OFF, it cant spread over the network

Viruses are just programs.  They run ONLY when the computer is on.


You sound slightly confused.  And in the words of Frank Herbert, "Invalid data yields invalid results"

Read up on Viruses and Security
You may answer your own questions

---

### Post by emiller12345 on 2011-06-01
Just to play devils advocate, there exists viruses that are cross platform.  Struxnet was designed with multiple payloads for a variety of specific targets, including windows PS's and PLC's.

---

### Post by wlraider70 on 2011-06-01
To be the anti-devils advocate...
Stuxnet was a state sponsored virus it was very advanced.

Also in this case the virus has to be Lan aware and Written for linux, windows and android. It also may need to be able to run while the computer is turned off and disconnected form the network.

if you get this virus send me a file I want a copy.

---

### Post by tgm4883 on 2011-06-02
> **wlraider70 said:**
> To be the anti-devils advocate...
Stuxnet was a state sponsored virus it was very advanced.

Also in this case the virus has to be Lan aware and Written for linux, windows and android. It also may need to be able to run while the computer is turned off and disconnected form the network.

if you get this virus send me a file I want a copy.

Wait, how does a virus (or any code) run when a computer is turned off?

---

### Post by Thewhistlingwind on 2011-06-02
> **tgm4883 said:**
> Wait, how does a virus (or any code) run when a computer is turned off?

It doesn't, that was the point.

Anyway, send me a copy too, learning how to process my users data without power would be invaluable, I could slash energy bills into fractions!

---

### Post by tgm4883 on 2011-06-02
> **Thewhistlingwind said:**
> It doesn't, that was the point.

Anyway, send me a copy too, learning how to process my users data without power would be invaluable, I could slash energy bills into fractions!

Ah, I see what you said there. Misread it the first time.

---

