---
title: "DSL slow-down"
date: 2004-12-27
forum: The Cafe
---

### Post by red devil on 2004-12-27
Hi,
I'm new to Ubuntu... love it to death already, best distro I've tried so far (inc Suse, Mandrake, Linspire, Lycoris) but I've noticed a dramatic slow-down in my DSL internet connection.
The rest of Ubuntu apps run fairly quickly on my Dell Inspiron 8000 notebook (800MHz Pentium III, 256MB RAM, 2MB DSL line) but the net connection is s-l-o-w and I'm using Firefox, which is normally quite a slick, quick browser.
Wonder if anyone has noticed the same thing and has any ideas on how to speed things up a bit.
I'm not a total newbie but I'm still learning, so keep it simple please!

---

### Post by shimon on 2004-12-27
call your isp this has nothing to do with ubuntu

---

### Post by red devil on 2004-12-27
Hmm... maybe, except that my other box (running Windows XP, I'm afraid) is flying on the same DSL connection.

---

### Post by hashimoto on 2004-12-27
[QUOTE=red devil]Hi,
I'm new to Ubuntu... love it to death already, best distro I've tried so far (inc Suse, Mandrake, Linspire, Lycoris) but I've noticed a dramatic slow-down in my DSL internet connection.
The rest of Ubuntu apps run fairly quickly on my Dell Inspiron 8000 notebook (800MHz Pentium III, 256MB RAM, 2MB DSL line) but the net connection is s-l-o-w and I'm using Firefox, which is normally quite a slick, quick browser.
Wonder if anyone has noticed the same thing and has any ideas on how to speed things up a bit.
I'm not a total newbie but I'm still learning, so keep it simple please![/QUOTE]
 Try disabling IPv6 in Firefox. See here: [http://ubuntuguide.org/#disableipv6-mozilla](http://ubuntuguide.org/#disableipv6-mozilla)

BR
Hashimoto

---

### Post by red devil on 2004-12-27
Thanks for the suggestion Hashimoto but I'm afraid I had already tried that, having earlier read the link you suggested.
Anyone got any other suggestions?

---

### Post by oddabe19 on 2004-12-27
[QUOTE=red devil]Thanks for the suggestion Hashimoto but I'm afraid I had already tried that, having earlier read the link you suggested.
Anyone got any other suggestions?[/QUOTE]
 if your card is using the realtek 8139too driver, theres a bug or something that can really really slow down your connection.  I had the same problem, so have several other people, but it seemed to go away with updates.

---

### Post by mark on 2004-12-27
[QUOTE=red devil]Thanks for the suggestion Hashimoto but I'm afraid I had already tried that, having earlier read the link you suggested.
Anyone got any other suggestions?[/QUOTE]
Perhaps you could try this: [http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841) This is the procedure I've gone through to completely disable IPv6, which speeded up browsing, ftp, etc. quite noticeably.

---

### Post by BWF89 on 2004-12-27
Every once in awhile my DSL slows down too. Just wait about 10-20 minutes and it usually goes back to normal...

---

### Post by hashimoto on 2004-12-28
[QUOTE=BWF89]Every once in awhile my DSL slows down too. Just wait about 10-20 minutes and it usually goes back to normal...[/QUOTE]
 Well, I actually noticed that my DSL goes dead every now and then. I mean, nothing happens if i try to browse or read email. Haven't tried to find the reason yet, I just simply reboot 
Yes, I know this isn't Windows (sorry for cursing, know I shouldn't use bad language here)

Hashimoto

---

### Post by costoa on 2004-12-29
You need to do a bandwidth speed test on both machines, one at a time and one right after the other. You could try [http://chi.speakeasy.net/](http://chi.speakeasy.net/)'s java app. Your a bit far from Chicago but maybe there's something similar that's closer. 

Judging speed from a web browser's page load isn't very accurate. What's the layout of your network? Are you using a linksys/netgear style router? Could you have a bad ethernet cable?

Try the java app speed test and let us know the results. That will help in choosing the next step.

Good Luck.

---

