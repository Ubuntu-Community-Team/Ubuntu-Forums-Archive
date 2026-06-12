---
title: "Once again: Apparmor and Firefox default profile - few questions."
date: 2012-10-12
forum: Security
---

### Post by kleenex on 2012-10-12
Hello, I have a few questions about Firefox and default profile for AppArmor. First: should I create additional profiles for [COLOR=Green]usr.lib.firefox.firefox.sh[/COLOR] and [COLOR=Green]usr.lib.firefox.firefox[/COLOR]? It seems to be important, because Firefox calls [COLOR=Green]/usr/lib/firefox/firefox.sh[/COLOR] before it starts. Second: I can still save files in every folder in user home directories[1] without any message. I am using default profile, which is available with Ubuntu. Could someone told me if everything is okay and , simply, everything is working[2]? Entries from[COLOR=Green] /var/log/syslog[/COLOR] file are correct?  I'm still unconvinced.

I apologize for the topic and questions, but I wonder for example, why I can still save files in user directories or what about creating profile for [COLOR=Green]usr.lib.firefox.firefox.sh [/COLOR]etc. 

[1] ```
**# I added this entry:**
deny @{HOME}/ w,
```[2] ```
[COLOR=Blue]# sudo apparmor_status |grep firefox
**[COLOR=Black](these profiles are in enforce mode.) [/COLOR]**[/COLOR]
/usr/lib/firefox/firefox{,*[^s][^h]}
/usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
/usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
/usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper

**# /var/log/syslog file contains something like this:**
Oct 12 13:17:57 testing kernel: [  453.674896] type=1400 audit(1350040677.264:38): 
apparmor="DENIED" operation="open" parent=2844 
profile="/usr/lib/firefox/firefox{,*[^s][^h]}" 
name="/dev/nvidiactl" pid=2846 comm="firefox" 
requested_mask="rw" denied_mask="rw" fsuid=1000 ouid=0

```

---

### Post by Hungry Man on 2012-10-12
The Firefox profile is screwed up because the abstractions are so convoluted. That's why you can still write to there.

I suggest you file a bug because I see this question pop up very often on this forum and others. The Firefox profile could very likely be easily tweaked by removing the unnecessary abstractions and instead adding variable rules for libraries (*/*.so rm,).

I don't think you need to create a profile for the .sh file. Not sure.

---

### Post by kleenex on 2012-10-12
Hi **Hungry Man**. You mean a bug about saving files in every user directory, right? Do You think, that it can be classified as a bug? Do You know anything about messages from [COLOR=Green]/var/log/syslog[/COLOR] file - they are correct? Thank You and sorry for these stupid questions.

---

### Post by Hungry Man on 2012-10-12
Yes, this constitutes a bug. The profile is providing unnecessary rights. The abstractions are used too much.

The questions aren't stupid though, like I said they come up often because these issues happen a lot.

It looks like, from that profile, the .sh file won't open. Set the profile to complain first so it doesn't break outright.

---

### Post by rookcifer on 2012-10-12
> **kleenex said:**
> Hi **Hungry Man**. You mean a bug about saving files in every user directory, right? Do You think, that it can be classified as a bug? Do You know anything about messages from [COLOR=Green]/var/log/syslog[/COLOR] file - they are correct? Thank You and sorry for these stupid questions.

The problem is the user-files abstraction allowing writing to anywhere in /home.

The best bet is just to use the profile I made.  You can find it [here. ]("http://rookcifer.blogspot.com/2012/09/custom-firefox-apparmor-profile-for.html")

---

### Post by kleenex on 2012-10-12
Hi **rookcifer**. I see you have created profiles also for [COLOR=Green]usr.lib.firefox.sh[/COLOR] and [COLOR=Green]usr.lib.firefox[COLOR=Black]. Do you think, that I also should do it?I am asking You, because I am not using** gnome-mplayer **or** totem-plugin**. Anyway, thank You for the link and really GREAT post!

[/COLOR][/COLOR]**Hungry Man** - okay, if I find some free time I report this bug.

---

### Post by rookcifer on 2012-10-12
> **kleenex said:**
> Hi **rookcifer**. I see you have created profiles also for [COLOR=Green]usr.lib.firefox.sh[/COLOR] and [COLOR=Green]usr.lib.firefox[COLOR=Black]. Do you think, that I also should do it?I am asking You, because I am not using** gnome-mplayer **or** totem-plugin**. Anyway, thank You for the link and really GREAT post!

[/COLOR][/COLOR]**Hungry Man** - okay, if I find some free time I report this bug.

You can still use my profiles for Firefox even if not using totem or gnome-mplayer.

---

