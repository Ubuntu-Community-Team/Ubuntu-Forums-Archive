---
title: "Thread with code that broke my Ubuntu"
date: 2018-02-24
forum: Ubuntu, Linux and OS Chat
---

### Post by douglaswja on 2018-02-24
*Disclaimer, i am new to Ubuntu*

This is the URL ([https://ubuntuforums.org/showthread.php?t=2061180](https://ubuntuforums.org/showthread.php?t=2061180)) containing the instructions by NikTh that caused my Ubuntu to become unusable. Meaning that at the login page, if i typed in my password, the screen would turn black, and restart the login page. All i could do was constantly type in my password, but could not open any system settings or terminal.

The problem began when my screen started flickering while watching Youtube videos. I assumed that a driver was needed for ubuntu, and so searched 'ubuntu screen flicker' on google. I followed the instructions provided by NikTh and was completely unable to access Ubuntu after that. (AKA Stuck at password page)

I had to Dual Boot into Windows, delete the Ubuntu partition, and reinstall it.

I am not sure if i did something wrong, i was aware that the solution he provided was for Ubuntu 12.XX (if i rmb correctly), so perhaps the solution is outdated, as i am using Ubuntu 16.04 LTS.
I am raising this issue as it is the first thread that appears on Google when 'Ubuntu screen flicker' is searched, and it may possibly be outdated.

---

### Post by wildmanne39 on 2018-02-24
*Thread moved to **Ubuntu, Linux and OS Chat, a more appropriate forum**.*

Hello and welcome to the forum!

Yes it is probably outdated since it is six years old, it is always best practice to post and ask your own question if the thread you are looking at is very old, different version of ubuntu or you do not have the same hardware, you did not say is hardware the same?

Over the years the reason for an issue occurring can be completely different from the reason it occurred several years earlier in a much older version of ubuntu. 

We do not edit other users posts from years ago to bring them up to date, we are a more ask your question and we will do our best to help you solve your issue.

---

### Post by cruzer001 on 2018-02-24
That is a good place to start; show us your system specs.  In terminal:

```
inxi -b
```

---

### Post by oldos2er on 2018-02-25
> **douglaswja said:**
>  perhaps the solution is outdated, as i am using Ubuntu 16.04 LTS.

I'm afraid there's no "perhaps" about it. It's important to note the date and Ubuntu version of any information on the internet, and if it isn't relevant to your version, be very skeptical. Best to inquire here first before making any changes that you don't know how to recover from.

Anyway, welcome. I hope this learning experience won't put you off Linux.

---

### Post by monkeybrain20122 on 2018-02-25
While the thread is old, I can't see anything in and of the commands themselves that would create your problem. basically NikTH just told the OP in that thread to install the Nvidia proprietary driver and those commands haven't changed AFAIK (Op has problem because he was using nouveau) It sounds like your problem is caused by the driver not building against the kernel. You haven't told us your Ubuntu and kernel version,  but recently there had been some issues with certain 4.13.x kernel with certain version of Nvidia drivers (as you can see the repository had many Nvidia driver, not sure which one is "nvidia-current" So at this point you should boot to recovery or low graphic mode (something like that, I am not sure off the top of my head) from "advanced option" (it would show if you tab esc or shift when you boot) remove all the nvidia stuff and go back to noveau and reboot. Once you can get back to the desktop you can update kernel, install the right version of Nvidia etc.

---

### Post by mc4man on 2018-02-25
While nvidia-current was once the latest driver in recent times it's nowhere near, now it installs nvidia-304 which is not suitable for many nvidia gpu's
At an appropriate point in the boot you could have just gone to a tty and removed nvidia*, then installed a newer driver ..

---

### Post by kansasnoob on 2018-02-25
Without hardware specs it's impossible to know what graphics driver would be appropriate for that machine.

---

