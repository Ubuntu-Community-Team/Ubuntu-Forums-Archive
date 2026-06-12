---
title: "Workspace Login for Privacy"
date: 2012-09-09
forum: Security
---

### Post by mike acker on 2012-09-09
Would it be possible for a Workspace to offer "change user" effectively allowing us to log into a workspace with a alternate user ID?

this would have huge implications for privacy. we do not want the scripting in a web page or other executable document to be running an inventory of our home directories and libraries

---

### Post by thnewguy on 2012-09-09
It sounds to me what you are after is either a virtual machine or a process sandbox. Ubuntu provides these through virtualization and AppArmor.

---

### Post by bodhi.zazen on 2012-09-10
Sure, kdm and gdm both offer these features.

From the command line (gdm)

```
/usr/bin/gdmflexiserver -a
```

---

### Post by d3v1150m471c on 2012-09-10
> **thnewguy said:**
> It sounds to me what you are after is either a virtual machine or a process sandbox. Ubuntu provides these through virtualization and AppArmor.

+1

this is going to be your most secure option

---

### Post by mike acker on 2012-09-10
thanks . i'll look into AppArmor . what concerns me is the capability of Java, and JavaScript, which are both often used in browsers. Java, I'm told, is basically similar to C or C++ . that being the case, a web page using java would be able to inventory a client machine .

i generally run with Java dis-abled but web sites generally won't render unless javascript is enabled ( yes I know about Firefox / NoScript ) .  

so my next chore is to review the question: what capabilities does java-script have ?   guess i better take myself to kindergarten .

---

### Post by wacky_sung on 2012-09-12
> **mike acker said:**
> thanks . i'll look into AppArmor . what concerns me is the capability of Java, and JavaScript, which are both often used in browsers. Java, I'm told, is basically similar to C or C++ . that being the case, a web page using java would be able to inventory a client machine .

i generally run with Java dis-abled but web sites generally won't render unless javascript is enabled ( yes I know about Firefox / NoScript ) .  

so my next chore is to review the question: what capabilities does java-script have ?   guess i better take myself to kindergarten .
Actually you need to look into all browsers addons or extensions beside Java.If you wanna safe, run it in virtual drive which save you all the trouble and exploits/hack.:lolflag::lolflag::lolflag::lolflag:

FYI even Apparmor can be exploited / misconfigure. Noscript is good but at time, it overkill your time for every page you browse.:lolflag::lolflag::lolflag::lolflag:

---

