---
title: "WannaCry and Wine"
date: 2017-05-13
forum: Security
---

### Post by vasa1 on 2017-05-13
Some ransomware is making the news: [https://www.wordfence.com/blog/2017/05/massive-global-ransomware-attack-underway-patch-available/](https://www.wordfence.com/blog/2017/05/massive-global-ransomware-attack-underway-patch-available/)

It seems to be affecting Windows machines that haven't been patched since some time in March 2017.

I'm just wondering if Wine users could be affected. I'm not a Wine user.

---

### Post by wildmanne39 on 2017-05-13
It was a bad attack some 45,000 hacks all across the world, I would imagine wine is susceptible also but no confirmation on that.

Edit:

I did find this:

[http://www.zdnet.com/article/crypto-ransomware-strikes-linux-but-attackers-botch-private-key/](http://www.zdnet.com/article/crypto-ransomware-strikes-linux-but-attackers-botch-private-key/)

---

### Post by claracc on 2017-05-13
The zdnet article addressed is dated  november 2015, is it still valid whats it is said in it?

Thanks

---

### Post by HermanAB on 2017-05-13
You won't cry with WINE.

WINE doesn't have the same bugs as Windows and it doesn't have SMB either.

---

### Post by SeijiSensei on 2017-05-13
Moreover, even if wine were infected somehow, you could just replace your ~/.wine directory with yesterday's backup.  You do have yesterday's backup of /home, right?  I keep an archive of clean VirtualBox images for the same reason.  If one somehow got infected, I'd just blow it away and revert to my clean image.

---

### Post by mastablasta on 2017-05-16
with some extra effort. as it is known you had to get the file in email and then run it. so in case of Linux you would need to run wine application and then open the file (probably).
or run some outlok on wine and open the email there.

what is more likely is if you have a drive shared with windows and without any passwords etc., it could encrypt it. 

looks like the difference between this and older version is that current version spread through network after infecting one PC via email. another attack vector with older one was malicious sites.

the one thing that was not menaitoned is if the antivirus on windows would have caught it.

---

