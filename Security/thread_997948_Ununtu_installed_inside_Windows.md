---
title: "Ununtu installed inside Windows"
date: 2008-11-30
forum: Security
---

### Post by MrN1ce9uy on 2008-11-30
I originally had Windows Vista on my laptop PC.  I downloaded Ubuntu and installed it 'within' Windows (I think that's what the option was called.)  So when I boot my pc I have to choose to either run Windows or Ubuntu.  So my question is, If I am in Ubuntu and browsing the internet and downloading stuff, would viruses and malware that are out there still be able to infect Windows on my pc even though I am in Ubuntu at the moment? 

Thanks

*Edit: Also would the firestarter firewall be sufficient security for my Ubuntu OS?

---

### Post by Kinstonian on 2008-11-30
Theoretically, it's possible if your Windows partition is mounted with the appropriate permissions, that *nix malware could do anything from reconfiguring Windows to load malware when it boots, to simply delete Windows files.

However, I must say that is **extremely** unlikely.  I know of no *nix malware that does that.  The risk of infecting your Windows computer comes 99.9% from what you do when you're using Windows.

---

### Post by markharding557 on 2008-11-30
> **Kinstonian said:**
> Theoretically, it's possible if your Windows partition is mounted with the appropriate permissions, that *nix malware could do anything from reconfiguring Windows to load malware when it boots, to simply delete Windows files.

However, I must say that is **extremely** unlikely.  I know of no *nix malware that does that.  The risk of infecting your Windows computer comes 99.9% from what you do when you're using Windows.

I was not aware there was any linux malware,is there any evidence of this?

---

### Post by Kinstonian on 2008-11-30
> **markharding557 said:**
> I was not aware there was any linux malware,is there any evidence of this?

Malware is as you might expect stands for malicious software.  There are viruses such as the [RST-B](http://www.virustotal.com/analisis/8be7bdfac4902d4d9bb3eb4222ffad07), there are bots such as the [VulnScan](http://www.virustotal.com/analisis/7f1dafaf34ed8679bfb5d50abc4771fc), and there are of course rootkits, which is well known.  All of this malware was from one incident involving a honeypot that got compromised.  Fortunately there are obviously not nearly as much malware for *nix as there is for Windows... but it's out there.

---

### Post by cariboo on 2008-11-30
Here's a link to a Wikipedia article:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

The article makes it sound worse then it actualy is, but you should be aware that there is Linux malware around.

Jim

---

