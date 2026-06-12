---
title: "Is android ubuntu based?"
date: 2011-04-19
forum: The Cafe
---

### Post by u-noob-tu on 2011-04-19
I was watching a video about custom android roms and flashing them to a phone, when the guy on the video went to his settings and showed his kernel version. You can clearly see the word "ubuntu" under the numbers. I knew android is linux based, but is it based off of ubuntu as well? Or did he get a kernel that is in some way related to ubuntu? 

Here's the link: [http://www.youtube.com/watch?v=g01sEWLcYdk]("http://www.youtube.com/watch?v=g01sEWLcYdk")

---

### Post by Johnsie on 2011-04-19
Certainly not. They do share alot of the same code though as they are both based on the Linux kernel.

[http://developer.android.com/guide/basics/what-is-android.html](http://developer.android.com/guide/basics/what-is-android.html)

At the application level the Android apps mostly use java.

---

### Post by m_duck on 2011-04-19
They are not. However Ubuntu will run on some phones like the HD2.

I've not watched the video, but IIRC the user and hostname of the computer on which the kernel for the ROM in question was compiled are listed with the kernel version in settings. I suspect that whoever compiled the kernel for that ROM was using an Ubuntu box with 'ubuntu' as part of their username or hostname strings on their development computer.

---

### Post by Cypher on 2011-04-19
No Android is based on the mainline Kernel from kernel.org and not necessarily the Kernel maintained on any one particular distribution..

Ubuntu, however, is the preferred host for Android development but that name shouldn't end up in the Kernel name itself..

Regards

---

### Post by sanderd17 on 2011-04-19
When I check the kernel version on my phone, it says
```
2.6.29.6-Kalim
kalimochoaz@KalimochoAz-HPUbuntu#1
```

But I know Kalim is working on a Ubuntu computer (and it seems to be a HP)

---

### Post by Simian Man on 2011-04-19
> **Cypher said:**
> Ubuntu, however, is the preferred host for Android development but that name shouldn't end up in the Kernel name itself..

No it's not, you can develop for Android on all major OSs.

---

### Post by u-noob-tu on 2011-04-19
> **Simian Man said:**
> No it's not, you can develop for Android on all major OSs.
 
he was saying that ubuntu is the most common/preferred OS for android developement, not that its the only one.

---

### Post by Dragonbite on 2011-04-19
Canonical, I heard, was fairly involved with Google's Android development with the ChromeOS so I would not be surprised if they were tapped too for the Android.

---

### Post by u-noob-tu on 2011-04-19
So basically, the only reason "ubuntu" was in the kernel settings is because the maker of that kernel had ubuntu in their username and/or they used an ubuntu box? I never would have guessed that. 

Another question: in the same video, the kernel number on the phone is 2.6.32 (if I remember correctly). Is that the Linux kernel 2.6.32 and android just isn't using the newest one? Or has google customized the Linux kernel and given it a different version number?

---

### Post by earthpigg on 2011-04-19
> **u-noob-tu said:**
> 
Another question: in the same video, the kernel number on the phone is 2.6.32 (if I remember correctly). Is that the Linux kernel 2.6.32 and android just isn't using the newest one? Or has google customized the Linux kernel and given it a different version number?

pretty sure that indicates that they took vanilla 2.6.32 and added their own patches. kind of a half-fork, i suppose you could call it.

good, because it means any good stuff coming out of android kernel development could theoretically be merged if anyone wanted to. i think.

edit: note that we aren't using the newest kernel either. it [looks like]("http://www.kernel.org/") 2.6._38_ is the current stable kernel.

---

### Post by LowSky on 2011-04-19
I've compiled my own version of Cyanogenmod 7 a few weeks ago, on Ubuntu, and when you read the kernel version on the Android device it will say Ubuntu.

---

