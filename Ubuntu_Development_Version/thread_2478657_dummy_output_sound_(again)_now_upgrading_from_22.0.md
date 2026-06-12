---
title: "dummy output sound (again) now upgrading from 22.04 to 22.10 devel."
date: 2022-09-01
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-09-01
Hello,

this issue has happened some time now, yet I didn't have the time to post it. Unfortunately, I tried many solutions and no one worked. So you will ask: why to post this now? 

In case someone faces that problem, searching the internet will find many solutions. In my case none worked. To name but a few differences that I had with these solutions and I remember were: I had sound from viber messages, aplay -l showed soundcard output instead of having null output. I remember that I changed kernel to no avail, followed this:
[https://aaroalhainen.medium.com/how-i-fixed-my-ubuntu-20-04-no-audio-dummy-output-issue-eaa525838e0d](https://aaroalhainen.medium.com/how-i-fixed-my-ubuntu-20-04-no-audio-dummy-output-issue-eaa525838e0d),
to no avail either, except from the fact that I didn't have timidity.

So I tried a new kinetic (new at that time) startup disk and saw that when I chose the option (try ubuntu) my sound was recognized as it used to. Then I proceeded in a fresh installation of 22.10 and everything was (still is) fine. As a result, I'm posting this in case you face the same problem, when upgrading from 22.04 to 22.10, to try "that solution" as well and save time. It's not an actual solution, since you have to reinstall, at least you know that the latest version will support your sound card and something was messed up during your upgrade. 

Regards!

---

### Post by Claus7 on 2022-12-02
Hello,

a link for another proposal that solved the issue: [https://ubuntuforums.org/showthread.php?t=2481456](https://ubuntuforums.org/showthread.php?t=2481456)

Regards!

---

### Post by grahammechanical on 2023-01-01
I only noticed this problem the other day when I was testing 23.04 for playing DVDs. Solutions offered here work. Especially the touch and systemctl codes. Thank you.

Regards

---

