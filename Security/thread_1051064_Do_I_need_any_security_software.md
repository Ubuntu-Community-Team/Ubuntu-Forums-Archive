---
title: "Do I need any security software?"
date: 2009-01-26
forum: Security
---

### Post by X40nick on 2009-01-26
Hi, 

I have installed Ubuntu again on my laptop, but I am slightly concerned about security. 

I have a few questions, which I will be very grateful for anyone to answer:

1. Do I need any anti-virus, firewall, anti-spyware software installed?
2. I was aware that Linux was virus and spyware free? Is this still true?
3. Are there any Linux viruses?
4. Will I have to pay?

Thank you. 

I am not worried about anti-virus to protect Windows users, it is their choice not to use it, so I don't need to protect them. 

Thank you for reading, and I look forward to you're answers. 

Nick.

---

### Post by x33a on 2009-01-26
read this:

[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

### Post by hyper_ch on 2009-01-26
> **X40nick said:**
> 1. Do I need any anti-virus, firewall, anti-spyware software installed?
antivirus: not really
firewall: is already installed - sort of
anti-sypware: not really

> **X40nick said:**
> 2. I was aware that Linux was virus and spyware free? Is this still true?
Mostly - as user just installing anything from any places could give you viruses but you'll have to take a part into installing that.

> **X40nick said:**
> 3. Are there any Linux viruses?
There are... about 30 known ones... all proof-of-concept... none out in the wild

> **X40nick said:**
> 4. Will I have to pay?
Pay what for?

---

### Post by OrangeCrate on 2009-01-26
> **X40nick said:**
> Hi, 

I have installed Ubuntu again on my laptop, but I am slightly concerned about security. 

I have a few questions, which I will be very grateful for anyone to answer:

1. Do I need any anti-virus, firewall, anti-spyware software installed?
2. I was aware that Linux was virus and spyware free? Is this still true?
3. Are there any Linux viruses?
4. Will I have to pay?

Thank you. 

I am not worried about anti-virus to protect Windows users, it is their choice not to use it, so I don't need to protect them. 

Thank you for reading, and I look forward to you're answers. 

Nick.

If you take your guidance from these two sources, you'll be fine:

[http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by adamlau on 2009-01-27
> 1. Do I need any anti-virus, firewall, anti-spyware software installed?
Depends on what software packages and services you run, or plan to run.

> 2. I was aware that Linux was virus and spyware free? Is this still true?
Linux itself is generally hardened against both. The rest depends on the software you run.

> 3. Are there any Linux viruses?
Yes. And rootkits.

> 4. Will I have to pay?
Not if you do not want to. Plenty of FOSS security tools out there. Stick with the basics and you should be fine: chown, chmod, passwd, /etc/fstab, /etc/sysctl.conf, netstat, ufw, AppArmor. Throw in Nmap and you should be good to go :) .

---

### Post by X40nick on 2009-01-27
Thank you for you're replies, I am now clear on what needs to be done. But I just have one more question:

Should I install Firestarter? Or just activate the firewall which ships with Ubuntu? And from one of those guides can be activated by entering a simple command. 

Thank you. 

Nick.

---

### Post by nubdora on 2009-01-27
> **X40nick said:**
> 

Should I install Firestarter? Or just activate the firewall which ships with Ubuntu? 

No, don't install firestarter. If you want a gui for the iptables frontend, ufw, use gufw.

---

### Post by hyper_ch on 2009-01-27
why do you think you even need to play around with the firewall? what are you going to do on your computer?

---

### Post by X40nick on 2009-01-28
I have activated the firewall with sudo ufw enable, I want is secure - and that gives peace of mind. 

Thank you.

---

### Post by hyper_ch on 2009-01-28
> **X40nick said:**
> I have activated the firewall with sudo ufw enable, I want is secure - and that gives peace of mind. 

Thank you.

Security is a process. Just doing something without knowing could rather put you at risk than protect yourself...

---

### Post by X40nick on 2009-01-28
Well, the firewall will do the protecting for me.

---

### Post by hyper_ch on 2009-01-28
in what ways? against what will it protect you?

---

### Post by jerome1232 on 2009-01-28
> **X40nick said:**
> I have activated the firewall with sudo ufw enable, I want is secure - and that gives peace of mind. 

Thank you.

btw "sudo ufw enable" did nothing that wasn't already being done.

ufw is a frontend to iptables, you've got to use ufw to actually add some rules, currently you have iptables set to accept all traffic (which is actually okay because you don't have anything listening for connections from the internet anyways so packets will get dropped).

Check out "man ufw"

If you want to actually use iptables to start blocking traffic.

```
sudo ufw default deny
```

If your behind a router, all the incoming taffic is already being dropped by your router.

---

### Post by X40nick on 2009-01-29
I am connected via my wireless router, and I activated that command? So basically my computer is pretty secure now? Or was it already secure in the first place? 

Nick.

---

