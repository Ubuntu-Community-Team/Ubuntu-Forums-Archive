---
title: "LUKS security concern"
date: 2010-11-13
forum: Security
---

### Post by zhaotianwu on 2010-11-13
We've been talking about the security issues with full-disk encryption,  e.g. LUKS. Most of those concerns seem to center around someone who has  physical access to your computer, like evil maid attack, cold boot  attack, etc. However, isn't the most dangerous and insidious enemy is  from online, like rootkit, Trojan, spyware, keylogger, etc. 

So,  my question is, to what degree having your system partition encrypted  with LUKS helps guard against those invisible enemies from online (or,  you can call them hackers)? You know, the running time is the most  vulnerable time for a LUKS encrypted computer.

---

### Post by OpSecShellshock on 2010-11-13
To the first part of you question the answer is no, web-based threats are not as pressing or dangerous as physically present attackers.

As for the second question, encryption of the disk really won't help against web-based threats because while the system is actively in use it's not encrypted. The encryption protects the data when the device is powered off.

---

### Post by zhaotianwu on 2010-11-13
> **OpSecShellshock said:**
> To the first part of you question the answer is no, web-based threats are not as pressing or dangerous as physically present attackers.

As for the second question, encryption of the disk really won't help against web-based threats because while the system is actively in use it's not encrypted. The encryption protects the data when the device is powered off.

So what is the most effective means to protect against web-based threats in Ubuntu? Can you hint some starting point that I can do some readings? Many thanks.

---

### Post by cariboo on 2010-11-13
In a default installation there are no ports listening, so you don't have to worry about anyone accessing your system from the internet. The only thing you really have to worry about is browser hijacking. and the only way to prevent that is to be aware of where you are going on the internet.

---

### Post by zhaotianwu on 2010-11-14
> **cariboo907 said:**
> In a default installation there are no ports listening, so you don't have to worry about anyone accessing your system from the internet. The only thing you really have to worry about is browser hijacking. and the only way to prevent that is to be aware of where you are going on the internet.


Can you explain a bit more about "no ports listening"? Is it the case even if I am using root instead of /username? Can you provide a guide or link for beginner's security guide under Ubuntu 10.10? Thanks.

---

### Post by azcrumpty on 2010-11-14
This [guide]("http://www.techotopia.com/index.php/Security+_Essentials")  tends  to spell out security in a comlete way.  They have many easy to read guides about security.

---

