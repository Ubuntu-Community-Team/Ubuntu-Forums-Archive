---
title: "always secure"
date: 2004-10-25
forum: Server Platforms
---

### Post by meyerm on 2004-10-25
Hi there,

I'm wondering how up-to-date ubuntu is when it comes to security announcements and package updates. For now there are no announcements in these forums, are there any automatic security programs which check your installation for unsafe packages and informs the admin (or updates automatically)? And how fast are these mechanisms/security teams (time from "problem detected" until "new package is available")?


Thank you very much
Marcel

---

### Post by jdong on 2004-10-25
Subscribe to the ubuntu-security mailing list. Set the forum's age, too. It's set to only show a day's posts, which is quite weird!

You use **apt-get update && apt-get dist-upgrade** to update Warty on a regularly basis. Warty (in theory) should be receiving only security updates and bugfixes, but if you want to restrict it to security ONLY, then use **apt-get update && apt-get upgrade -t warty-security**

---

### Post by Seti on 2004-10-28
Remember, if you have a network connection during installation, setup will automatically prompt you get updates. It then downloads and installs all the updated package versions.

---

### Post by cacofonix on 2004-10-28
How would you set up cron to do the checking for upgrades?

---

### Post by meyerm on 2004-10-31
Sorry for not reacting. I guess I failed in setting my forums settings correct to get informed by email when an answer is available.

Thank you for your answer. It's nice to hear warty will only be updated for security/bug-fixes. Meanwhile there are a lot more security announcements in the forum, so it seems my question gots answered: Ubuntu seems to be quite recent when it comes to security issues. :-)

What exactly did you mean with "Set the forum's age"? Sorry for my english.

---

### Post by jdong on 2004-10-31
[QUOTE=meyerm]Sorry for not reacting. I guess I failed in setting my forums settings correct to get informed by email when an answer is available.

Thank you for your answer. It's nice to hear warty will only be updated for security/bug-fixes. Meanwhile there are a lot more security announcements in the forum, so it seems my question gots answered: Ubuntu seems to be quite recent when it comes to security issues. :-)

What exactly did you mean with "Set the forum's age"? Sorry for my english.[/QUOTE]
 Originally, the forum was set to hide all posts that were more than a day old. The admin fixed that, so now all the posts show.

---

### Post by jdong on 2004-10-31
[QUOTE=cacofonix]How would you set up cron to do the checking for upgrades?[/QUOTE]

Please search the howto forum. There was a discussion about this.

---

### Post by regeya on 2004-11-01
Speaking from the perspective of a former Gentoo user, I can honestly say I'm offended by your sig.  That's not representative of the Gentoo community at large.  Funny sig, but if you think that's a good indication of the overall intelligence level of Gentoo users, I hope you're not a Ubuntu developer, for the sake of my system's security.

Sorry for being harsh; I guess I'm just being humorless.  Meh.  :twisted:

---

### Post by jdong on 2004-11-02
I didn't mean for the sig to make fun of Gentoo in any way, shape, or form. I was, and still am, a die-hard Gentoo fan. I just needed a funny quote (this one I found from funroll-loops.org). It related somewhat to Debian/Ubuntu, so I thought I'd use it. I have NOTHING against Gentoo, or their forum users. I found  those people to be quite friendly and knowledgeable, actually.

---

### Post by HiddenWolf on 2004-11-04
Gentoo has a very friendly community.

Part of the reason I stick to ubuntu know is because it seems we're going that way ourselves.

---

