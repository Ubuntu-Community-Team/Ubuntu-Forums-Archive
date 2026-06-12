---
title: "Security issues-unknown reasons-help"
date: 2015-12-29
forum: Security
---

### Post by sofasurfer on 2015-12-29
I have not had any problems before, until a day or 2 ago when I started getting this window popping on MANY of the sites I go to all the time. I am still able to access many site but many other sites are giving me this window. What has caused this and what is require to fix it.

Another thing that I just remembered, and I have ignored it till now, is that my firefox window closes quite often and I have to reopen it.

Is this a virus? A hacker? 
What is the best virus cleaner and firewall that I can use for free?

Thanks.

---

### Post by HermanAB on 2015-12-29
If you are worried about the security of your system - re-install it.  It only takes about 30 minutes to do - less time than trying to figure out what is or isn't going on, and reinstalling is the only real way to be sure that the system is good.

When you reinstall, use proper passwords and don't install remote control daemons like FTP server, a web server or VNC and you'll be fine.

---

### Post by sofasurfer on 2015-12-29
Thanks for your reply.
In my first post I forgot to post the picture of the screen that is popping up. So here it is.
As for reinstalling, I have done it a million times in the past but I never felt good about doing it without backing up all of my personal files. I have always wiped the system clean and then reinstalled my files. However, now I have so much to backup that I do not have a place to back then all up.  That is why I wanted to find out what my current problem is and why it is occurring.

[ATTACH=CONFIG]266445[/ATTACH]

---

### Post by The Cog on 2015-12-29
Clicking on the technical details should show you more info as to why it doesn't like the site's certificate. That may give you a clue.

The last time I saw this, it was while using a tablet that had allowed the battery to go so flat that it had lost the time and date. It had defaulted to Jan 1970, and all the site certificates were not valid until more than 40 years later. I entered the correct time and the error went away. Of course, I'm not saying that's your problem, but it was the technical details that told me the certificates were "out of date".

---

### Post by haplorrhine on 2015-12-29
> **sofasurfer said:**
> However, now I have so much to backup that I do not have a place to back then all up.
SD flash memory is really cheap [though possibly insecure]("http://www.bunniestudios.com/blog/?p=3554"), otherwise maybe an extra (external) harddrive or some temporary cloud storage?

---

### Post by HermanAB on 2015-12-30
You can make re-installs easier by making a separate /home partition.  Then you don't need to copy all your data - just don't reformat /home.  It is still a good idea to keep backups, but you save half the time.

---

### Post by claracc on 2015-12-30
> **The Cog said:**
> Clicking on the technical details should show you more info as to why it doesn't like the site's certificate. That may give you a clue.

The last time I saw this, it was while using a tablet that had allowed the battery to go so flat that it had lost the time and date. It had defaulted to Jan 1970, and all the site certificates were not valid until more than 40 years later. I entered the correct time and the error went away. Of course, I'm not saying that's your problem, but it was the technical details that told me the certificates were "out of date".

+1

Completely agree. I would search why firefox doesn't like these site certificates

---

### Post by bashiergui on 2015-12-30
> **HermanAB said:**
> If you are worried about the security of your system - re-install it.  It only takes about 30 minutes to do - less time than trying to figure out what is or isn't going on, and reinstalling is the only real way to be sure that the system is good.

When you reinstall, use proper passwords and don't install remote control daemons like FTP server, a web server or VNC and you'll be fine.Wow. 
This advice is akin to killing a gnat by detonating a thermonuclear warhead. I'm not saying it wouldn't be effective, but it's probably not the *very* first thing I'd suggest.

---

### Post by matt_symes on 2015-12-30
Hi

I have been getting these as well.

I believe they are due to Google dropping SHA1 in their attempt to move the industry to the SHA2 family.

This particular issue is not (unlikely) an infection / man-in-the-middle.

Kind regards

---

### Post by mikodo on 2015-12-30
I am using DuckDuckGo search engine in Firefox browser with the extension [HTTPS Everywhere]("https://www.eff.org/https-everywhere/faq"), from [Electronic Frontier Foundation]("https://www.eff.org/") and I had no problem accessing that site you received the pop up in and opened many of its' pages in HTTPS. I just noticed that that addon has a feature that I have never used called SSL Observatory, that can amongst other things help diagnose problems. Have a look at the screeny of it in the bottom.

I wonder if you used DDG search engine if you would get better results given, what matt_symes just indicated?

---

### Post by sofasurfer on 2016-01-02
[ATTACH=CONFIG]266512[/ATTACH]I tried to access a website, today, that I have never been to before and I got the "Connection is Untrusted" window again. I clicked on "details" and got this message..."www.rt.com uses an invalid security certificate. The certificate is not trusted because the issuer certificate is not trusted. (Error code: sec_error_untrusted_issuer)". 

This message indicates that the problem is with the website, not my computer. This is most confusing because that would indicate that lately there is a rash of websites that all have untrustworthy certificates"...whixh has never happened before. This indicates that the problem MUST be at my end. 

And ideas?

---

### Post by sammiev on 2016-01-02
> **sofasurfer said:**
> [ATTACH=CONFIG]266512[/ATTACH]I tried to access a website, today, that I have never been to before and I got the "Connection is Untrusted" window again. I clicked on "details" and got this message..."www.rt.com uses an invalid security certificate. The certificate is not trusted because the issuer certificate is not trusted. (Error code: sec_error_untrusted_issuer)". 

This message indicates that the problem is with the website, not my computer. This is most confusing because that would indicate that lately there is a rash of websites that all have untrustworthy certificates"...whixh has never happened before. This indicates that the problem MUST be at my end. 

And ideas?

rt.com works great on FireFox here without any invalid security certificate.

---

### Post by matt_symes on 2016-01-02
Hi

> **sammiev said:**
> rt.com works great on FireFox here without any invalid security certificate.

And here.

Do you have up to date certificates ? The package is

```
ca-certificates
```

Kind regards

---

