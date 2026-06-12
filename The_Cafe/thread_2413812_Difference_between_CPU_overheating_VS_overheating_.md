---
title: "Difference between CPU overheating VS overheating due to malware/virus?"
date: 2019-03-02
forum: The Cafe
---

### Post by %7#28K8 on 2019-03-02
So, I've searched about this but I didn't get much of an answer. Even if there was one, I haven't found it. I'm really curious as to what is the difference between the two especially when all of the sudden, a laptop I have reinstalled and updated many times and never got too hot, overheated after I installed an OS that I suspect was infected. Anyone?

---

### Post by Frogs Hair on 2019-03-02
More info about the computer is needed. The main sources of heat are cpu, mechanical harddrives, and graphics cards if installed.

---

### Post by QIII on 2019-03-02
What leads you to suspect that you installed an OS that was infected?  Where did you get it?

---

### Post by %7#28K8 on 2019-03-02
> What leads you to suspect that you installed an OS that was infected?  Where did you get it?

Well, for starters, I've been reinstalling the OS often on my laptop and it never got too hot to the extent I can't put it on my lap, after I installed the ISO that was in my computer and put it into the usb, I installed the live usb and while I was using it, it overheated and it was *really* weird. I think someone messed with my laptop just like how my phone got some weird malware in it when I left it unlocked.

---

### Post by QIII on 2019-03-02
Have you [checked the hash]("https://help.ubuntu.com/community/UbuntuHashes") to see if the iso has been tampered with?

---

### Post by %7#28K8 on 2019-03-02
Unfortunately, after I installed the OS, I reformatted the usb, thinking that I have to reinstall it again.

However, is there a way for me to check the hash of the OS? If it's possible, that is...

---

### Post by %7#28K8 on 2019-03-02
> More info about the computer is needed. The main sources of heat are  cpu, mechanical harddrives, and graphics cards if installed.

Should I put the info here? I have already collected it, just the matter of which info not to show.

---

### Post by QIII on 2019-03-02
> **gggddyy said:**
> Unfortunately, after I installed the OS, I reformatted the usb, thinking that I have to reinstall it again.

However, is there a way for me to check the hash of the OS? If it's possible, that is...

Check the hash of the downloaded ISO you are using to load on to the USB.

---

### Post by %7#28K8 on 2019-03-02
MD5SUM, SHA1 and SHA256SUM all matches.

I either forgot to mention something and just misunderstood something. Sorry. If you mean to check the hash of the suspected infected ISO, I no longer have it (it was erased as I reinstalled it with the infected ISO). However, the one I just downloaded has all the hashes matched.

---

### Post by QIII on 2019-03-02
Then it is highly unlikely that anyone has somehow managed to add an "infection" to your OS via the ISO.  You may eliminate that as having anything to do with the overheating.

---

### Post by %7#28K8 on 2019-03-02
Oh, I'm glad but do you mind if you could give me an explanation or a link as to why's that? Just curious, thanks

---

### Post by Frogs Hair on 2019-03-03
> **gggddyy said:**
> Should I put the info here? I have already collected it, just the matter of which info not to show.

It is helpful to know what hardware you are using especially if it's older. Newer Ubuntu versions are more resource hungry.

To identify the process/s causing the the problem you can use the following command. ```
top
```

---

