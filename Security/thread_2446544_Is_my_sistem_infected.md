---
title: "Is my sistem infected?"
date: 2020-07-02
forum: Security
---

### Post by belyayev on 2020-07-02
I've recently changed from Windows 10 to Ubuntu because I suspected it was infected, and I confirmed it after analyzing with ClamAV the external hard drive I used for saving my files: it found two trojans and a Sality virus, and who knows what was on the actual system files (I deleted it with the Ubuntu installation). Before changing all my passwords I decided to check if Ubuntu was infected, and both RKHunter and Chrookit found positives. I used RKHunter three times, and each one it found one suspected file, and in the first one it found like 100 suspected rootkits, the second one 20, and the last one 10 (with an interval of a few minutes between each analysis), and Chrookit found 2 suspected files:
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/debug/.build-id /usr/lib/jvm/.java-1.8.0-openjdk-amd64.jinfo /usr/lib/modules/5.4.0-26-generic/vdso/.build-id /usr/lib/modules/5.4.0-39-generic/vdso/.build-id
/usr/lib/debug/.build-id /usr/lib/modules/5.4.0-26-generic/vdso/.build-id /usr/lib/modules/5.4.0-39-generic/vdso/.build-id
(I still don't send the RKHunter results because I don't know how)
Also, when I connected the external hard drive it asked me to run a daemon (I don't remember that the exact message was), I accepted and a message came out saying that it could not be opened because it doesn't have the necessary permissions. Now that I know what a daemon actually is I'm quite worried about it...

---

### Post by TheFu on 2020-07-02
RKHunter and Chrookit found _FALSE_ positives.
They think any file/directory that begins with a '.'  is a possible problem.

---

### Post by belyayev on 2020-07-03
Thanks

---

### Post by TheFu on 2020-07-03
> **belyayev said:**
> 
Also, when I connected the external hard drive it asked me to run a daemon (I don't remember that the exact message was), I accepted and a message came out saying that it could not be opened because it doesn't have the necessary permissions. Now that I know what a daemon actually is I'm quite worried about it...

Don't "accept" anything you don't understand. If you don't capture the message, preferably as text, not an image, nobody can help. You may see that in a system log file. Those are in /var/log/.  Many desktops have "Log file viewers" - I've never used those because 1 command in a shell can search all of those log files for interesting stuff.  Yes, you need to learn to read log files.  Don't be daunted and don't let your eyes glaze over.  Read them aloud. The messages almost always say what happened.

---

