---
title: "GLIBC-Enlightenment-Breezy-Knoppix"
date: 2005-10-07
forum: The Cafe
---

### Post by majikstreet on 2005-10-07
Hi,
I am on **breezy badger** (well actually this is being typed on windows because I broke my badger).

I was trying to install **e17**, and **didn't know that there was a breezy repo up.** I went through with the instructions for the elive repo, and managed to break my install. When ever I try to do MOST ANYTHING I get this error:
```

Symbol regexec, version GLIBC 2.3.4 not defined in file libc.so.6 with line time reference

```

**I have a copy of knoppix (3.4). Can I fix it using Knoppix 3.4? (In the badger, X won't even open.)**

majikstreet will be really grateful for your help!!


**I have a 256mb usb stick that I can mount in Knoppix-- unable to mount in the badger**

---

### Post by majikstreet on 2005-10-07
Id like some help please.

Thanks,
majikstreet

The person who helps me fix it gets 1,000,000 cookies. I will  be *VERY* grateful to them!

[B]Edited rather unkind bump to post. 
KB[/B]

---

### Post by Lovechild on 2005-10-07
Since you bumped so rudely all I'll tell you is that you screwed your glibc - googling will help.

---

### Post by majikstreet on 2005-10-07
[QUOTE=Lovechild]Since you bumped so rudely all I'll tell you is that you screwed your glibc - googling will help.[/QUOTE]
Lovechild,
I am really sorry that I bumped. I didn't mean for it to sound rude. I just am frustrated. I've been googleing as many search terms as I can think of, but I can't figure it out. If you could only be so kind to help me, I will be eternally grateful to you.

I didn't mean for anything that I have said in this topic to sound rude. I sincerly apologize. I just am very frustrated because of this.

majikstreet

---

### Post by Lovechild on 2005-10-07
[QUOTE=majikstreet]Lovechild,
I am really sorry that I bumped. I didn't mean for it to sound rude. I just am frustrated. I've been googleing as many search terms as I can think of, but I can't figure it out. If you could only be so kind to help me, I will be eternally grateful to you.

I didn't mean for anything that I have said in this topic to sound rude. I sincerly apologize. I just am very frustrated because of this.

majikstreet[/QUOTE]

The best of my 5 sec research showed that manually reinstalling glibc would do it, now this was on a fedora system but I guess you could grab glibc from the ubuntu pool and dpkg install it with force.

[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/)

---

### Post by majikstreet on 2005-10-07
[QUOTE=Lovechild]The best of my 5 sec research showed that manually reinstalling glibc would do it, now this was on a fedora system but I guess you could grab glibc from the ubuntu pool and dpkg install it with force.

[http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/)[/QUOTE]
I'm going to do something like that.

I found out that I can chroot into my system through knoppix. I *may* download a new knoppix if I can't fix it.

Thank you LoveChild!

---

### Post by majikstreet on 2005-10-07
OH MY GOD!

My computer booted up. I had to download glibc, libstdc, and libc6- but I GOT IT WORKING!

Thank you everyone.

---

### Post by Lovechild on 2005-10-07
[QUOTE=majikstreet]OH MY GOD!

My computer booted up. I had to download glibc, libstdc, and libc6- but I GOT IT WORKING!

Thank you everyone.[/QUOTE]

First you misspell my nick, now I have multiple personality disorder.. dang this is just not my day.

---

### Post by majikstreet on 2005-10-07
[QUOTE=Lovechild]First you misspell my nick, now I have multiple personality disorder.. dang this is just not my day.[/QUOTE]
?

Sorry if I offended you :)

---

