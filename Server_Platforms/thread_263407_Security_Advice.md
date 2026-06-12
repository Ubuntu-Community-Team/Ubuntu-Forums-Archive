---
title: "Security Advice?"
date: 2006-09-23
forum: Server Platforms
---

### Post by iONiK on 2006-09-23
I need some advice on what to edit in Kubuntu Linux to have better security, seeing as I am t3h l337 newb. I know that Unix-based systems can be a little dodgy...

---

### Post by wildseven on 2006-09-23
hey hey again.
well now that the virus question is mostly gone.

for more security, you can use firestarter as a firewall. I'll get more into detail this time.
Firestarter by default blocks everything. Nothing in, nothing out. You have to tell it to allow the ports you would like to use. This is why it is very secure.

For more protection, you can not make a root account. ubuntu uses sudo which grants the user super user powers for 15 minutes then it re prompts you. The reason you shouldnt make a root account is because when a hacker gets in, the one name on most system that will definitely be there is well...you guessed it. root. so don't make the root account. 

other than that, the rest of the security is somewhat common sense.

never make your password a dictionary word.

if you are still parnoid about hackers, ontop of firestarter, you can get another box and make it into a gateway running either red hat or fedora core.

if you see people attempting to login to your computer remotely, make yourself a script to drop their IP's.

you should be pretty safe with linux.

good luck.

---

### Post by iONiK on 2006-09-23
Thank you. But I also need security tools... Like... I dunno, a Linux version of CrackerJack?

---

### Post by wildseven on 2006-09-23
im sorry, i don't know what crackerjack is, but what kind of tools are you looking for? by the sound of crackerjack, are you looking for like a password cracker or something?

---

### Post by iONiK on 2006-09-23
CrackerJack is the BEST Unix password cracker ever.

But yeah, i mean like wardialers, any of that stuff I can get... You know?

---

### Post by wildseven on 2006-09-23
im sure if you look around google you can find what you want.

um the tools i mostly use are: 
HUNT for arp poisoning, cracking, brute force, and bunch of other neat things

aircrack for cracking WEP and WPA

nmap for port scanning

kismet for wardriving

ethereal for network packet sniffing

just google what you need.

good luck.

stay outta trouble ^^

---

### Post by Carbon Based on 2006-09-23
> **iONiK said:**
> Thank you. But I also need security tools... Like... I dunno, a Linux version of CrackerJack?
[Try the sticky at the top of this forum.]("http://www.ubuntuforums.org/showthread.php?t=9836")

---

