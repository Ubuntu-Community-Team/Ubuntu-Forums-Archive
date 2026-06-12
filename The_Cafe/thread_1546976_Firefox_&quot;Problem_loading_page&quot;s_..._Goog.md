---
title: "Firefox &quot;Problem loading page&quot;s ... Google suspected"
date: 2010-08-06
forum: The Cafe
---

### Post by ceref on 2010-08-06
Hi all ... I have stand alone Ubuntu 10.04 Lucid and new to Ubuntu and Linux (ex windows drone). 

My Firefox is presenting a lot of "Problem loading page" error messages and a lot of hung pages waiting for the next called page. I notice that "Google analytic s" and "c counter" always fire up even when I am not using Google search. I even have problems getting into this forum site and getting into Ubuntu diagnostic help site ... I just don't get there. Everything goes through Google !    

I suspect the total interference of Google is screwing up "us" the competition. 

Anyone have a solution or suggestion ... Ubuntu is fantastic and I want to put it on my other machines and I would like to get this problem sorted first. 

Hope you having a good day.

---

### Post by Islington on 2010-08-06
I dont think that is the source of your hung pages and load times, but you can always install an addon like noscript or adblockplus to block google analytics. :KS

---

### Post by lovinglinux on 2010-08-06
Disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

Also disable the feature to block web forgeries and attack sites on Firefox (Edit >> Preferences >> Security).

Block Analytics with the extensions already suggested.

---

### Post by prshah on 2010-08-06
> **ceref said:**
> My Firefox is presenting a lot of "Problem loading page" error messages and a lot of hung pages waiting for the next called page. 

Hi, please see this thread for a possible solution to your problem:
[[SOLVED] Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showthread.php?t=718709") The solution is presented in the last-but-one post on the second page, but I would recommend you go through the entire thread (will not take too long).

---

