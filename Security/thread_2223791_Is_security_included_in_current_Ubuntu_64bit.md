---
title: "Is security included in current Ubuntu 64bit"
date: 2014-05-12
forum: Security
---

### Post by vik2 on 2014-05-12
Advise need, I've installed Ubuntu the other day and running firewall config. I looked up antivirus and security software and nothing. I remember when I had Ubuntu about 3 years ago, I had Clamav? and there was a small number of security programs. This is my only OS, so security is a a must. Cheers Vik

---

### Post by cariboo on 2014-05-13
Have a look at the security stickies at the top of the page, especially [this]("http://ubuntuforums.org/showthread.php?t=510812") one.

---

### Post by vik2 on 2014-05-14
Thanks for the well written link, very good read. Security wise I installed Dr web, traffic light and a privacy add on for my browser, will run RKhunter weekly and installed a antivirus and firewall. I'm seeing with Ubuntu it's more about intrusion and information/privacy issues than virus control. Is there any thing else to install or all good with what I've got in security?

---

### Post by cariboo on 2014-05-15
Most of what you installed really is of no use on Ubuntu, because there are no active viruses in the wild, what you have to watch out for more than anything else is browser exploits, depending on which browser you are using. For securing Firefox, have a look [here]("http://www.insanitybit.com/2012/06/02/the-definitive-guide-for-securing-firefox/"), and for Chromium, look [here]("http://www.insanitybit.com/2012/06/02/the-definitive-guide-for-securing-chrome/"). although the article is about Chrome everything works for Chromium too.

---

### Post by jon43 on 2014-05-15
> **cariboo907 said:**
> Most of what you installed really is of no use on Ubuntu, because there are no active viruses in the wild, what you have to watch out for more than anything else is browser exploits, depending on which browser you are using. For securing Firefox, have a look [here]("http://www.insanitybit.com/2012/06/02/the-definitive-guide-for-securing-firefox/"), and for Chromium, look [here]("http://www.insanitybit.com/2012/06/02/the-definitive-guide-for-securing-chrome/"). although the article is about Chrome everything works for Chromium too.

100% agree about browser exploits being the primary concern. Make sure you secure your browser.

The AV and firewall do absolutely nothing in Ubuntu. There are no open ports by default, so the firewall is redundant. There are also no "ubuntu viruses" for the AV to look for- the definitions are all going to be Windows malware, so unless you are dual-booting, you're just running a program with (I assume) elevated privileges for no reason. RKhunter is useful, but you really need to be a pro to determine if it's one of the many false alarms or a real threat. 

Your Ubuntu install isn't going to pickup any random spyware just browsing the web, with the exception of possibly something that exploits your browser directly. The only thing Ubuntu users really need to be afraid of is a hacker who really wants to target your specific system. If that happens, all bets are off- but none of the basic security software you're talking about is going to protect you from that scenario in any OS.

---

### Post by cariboo on 2014-05-15
The included firewall, is enough for most users, you can enable it on the command line with the following command:

```
sudo ufw enable
```

or if you'd rather use a gui app, gufw is in the repositories, use your favourite method for installing packages.

---

### Post by vik2 on 2014-05-16
Ok, in summary, Ubuntu 14.04 has by default blocked ports but I can install a firewall if I want a little more control but not needed. As there is no known viruses, malware and other related issues, no antivirus needed, but I can install one if I like. Keep all updates updated, but the major issue is browser security, to which adding security extensions like a ad blocker, anti script, pro privacy, something like trafficlight and a secure downloader is a help as long as I surf smart and keep me computer clean and backed up, while storing me sensitive information on a usb. And of cause I can encrypt, use software like snort and functions like RKhunter if I'm more of a expert, but my basic set up of firewall and browser security extensions should be ok if I use smart.

---

