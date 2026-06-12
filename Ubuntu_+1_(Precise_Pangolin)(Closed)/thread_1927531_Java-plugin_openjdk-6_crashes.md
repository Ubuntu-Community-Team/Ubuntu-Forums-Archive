---
title: "Java-plugin openjdk-6 crashes"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Stinger on 2012-02-18
Hi, since updating to new Unity, etc. I'm not able to run any java related apps in my web-browser , Firefox or Google-chrome.

I filed this bug-report [Bug #934937]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/934937")

Anyone else affected ?
If you are, please add yourself as affected to this bug

---

### Post by Stinger on 2012-02-18
You can test if openjdk is working in your browser here:
[http://java.com/en/download/testjava.jsp]("http://java.com/en/download/testjava.jsp")

It should show information about java-version etc.
But if you just got an empty field without any java-info, it's not working, just like me.

---

### Post by Stinger on 2012-02-20
As a temporary workaround this guide can be used, until the developers has a fix for the bug.
There is a howto for both 32 and 64 bit:

[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

I added a screenshot , java is working now \\:D/

---

### Post by Stinger on 2012-02-24
God news this bug [#935296]("https://bugs.launchpad.net/ubuntu/+source/java-atk-wrapper/+bug/935296") which seems to be a duplicate of my [bug #934937]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/934937") has got the developers attention ( maybe playing minecraft is more important than webbanking :biggrin: ) it is now marked as a high priority bug and targeted for beta-2

There is another workaround too, posted on this bug by Xerxes in [comment #20]("https://bugs.launchpad.net/ubuntu/+source/java-atk-wrapper/+bug/935296/comments/20")
Maybe someone would like to give it a go and report back ?

---

### Post by Stinger on 2012-02-24
[Bug #935296]("https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/935296") just got a new headline an hour ago, [Matthias Klose]("https://launchpad.net/~doko") changed it from > minecraft fails to start after latest precise updates... to > java-atk-wrapper prevents java applications from starting.
That makes my bug the duplicate now, neat little trick :biggrin:.
Ok ok, I'll mark it as duplicate :shock:, just kidding....

---

### Post by Stinger on 2012-02-25
The bug has been fixed in:
openjdk-6 6b24-1.11.1-2ubuntu2 and openjdk-7 also,
by disabling the accessibility wrapper.
This line is taken from the changelog:
> * Disable the accessibility wrapper, doesn't work yet. LP: #935296.

It is still present as a high priority bug for the java-atk-wrapper package and targeted for beta-2

Openjdk is back to working again =D>

---

