---
title: "Firefox 9 rc2 and web banks - problems"
date: 2011-11-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-11-18
Just want to know if anyone is experiencing problems with their online web banks when using new Firefox 9 rc2.

At least here in Finland (and Sweden) Nordea's web bank does not operate when Firefox 9 rc2 is used.
Instead, Firefox 8 must be used.
I know banks do have a very strict policy when security is considered.
So maybe Firefox 9 should be more mature or even released until it is accepted.

Edit.
I meant to write beta2, not rc2

---

### Post by lovinglinux on 2011-11-18
Try using User Agent Switcher and set your Firefox to look like Firefox 8.

---

### Post by effenberg0x0 on 2011-11-18
Hey Harry, 

My 4 banks won't run when I use openjdk-*. What I always have to do is apt-get remove openjdk-* and install sun java jdk. It is a good option anyway as it makes eclipse faster to use the proprietary java.

This tutorial works, there's a nice zenity-based script: [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html) except that my banks won't accept Oracle Java 7, only version 6 (Windows Default...). You can download 6 in the same link they give at that page. Run the script, etc. Only thing you have to check (they don't mention there) is sudo chown you:you $HOME/.mozilla/plugins -R && killall firefox/chromium before use otherwise it won't work.

---

### Post by Harry33 on 2011-11-19
> **effenberg0x0 said:**
> Hey Harry, 

My 4 banks won't run when I use openjdk-*. What I always have to do is apt-get remove openjdk-* and install sun java jdk. It is a good option anyway as it makes eclipse faster to use the proprietary java.

This tutorial works, there's a nice zenity-based script: [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html) except that my banks won't accept Oracle Java 7, only version 6 (Windows Default...). You can download 6 in the same link they give at that page. Run the script, etc. Only thing you have to check (they don't mention there) is sudo chown you:you $HOME/.mozilla/plugins -R && killall firefox/chromium before use otherwise it won't work.

Hi effenberg,

The Java issue is well known regarding the Finnish Sampo Bank.
However, Nordea does not use Java based web Bank.
Everything works well with FF 8. I have no Java software installed.

---

### Post by effenberg0x0 on 2011-11-19
> **Harry33 said:**
> Hi effenberg,

The Java issue is well known regarding the Finnish Sampo Bank.
However, Nordea does not use Java based web Bank.
Everything works well with FF 8. I have no Java software installed.

I see, lucky you: I think all banks here use it, it's a pain in the ***. Actually, in one of my banks, you need to have sun-java to even be able to input your password in. Once in your account, it must recognize and authorize the PC, so it sends an SMS to the mobile you register with them when you opened the account. Then, 10 minutes later when you receive the SMS, the session expired and you have to restart everything again. Faking user-agent would be much easier....

---

### Post by vasa1 on 2011-11-19
Just curious. How do you have Firefox 9 **rc2**? Won't that be available only just before Firefox 9 is about to be released as a stable version to the general public?

(I assume **rc** = release candidate.)

---

### Post by sammiev on 2011-11-19
Tried my online banking 2 days in a roll with FF9 and no issues here. :D

---

### Post by Harry33 on 2011-11-20
> **vasa1 said:**
> Just curious. How do you have Firefox 9 **rc2**? Won't that be available only just before Firefox 9 is about to be released as a stable version to the general public?

(I assume **rc** = release candidate.)

Right, sorry.
What meant was Firefox 9 b2, the one from the repos, so beta it is.

---

