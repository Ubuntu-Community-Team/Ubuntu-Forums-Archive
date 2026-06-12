---
title: "Java7 got it working but never missed it"
date: 2012-12-21
forum: The Cafe
---

### Post by sdowney717 on 2012-12-21
From here
[http://thedaneshproject.com/posts/how-to-install-java-7-on-ubuntu-12-04-lts/](http://thedaneshproject.com/posts/how-to-install-java-7-on-ubuntu-12-04-lts/)

Does it matter much seeing I have never noticed it not working. When I went to the test site, java was not working. What this means is none of the things I do with the PC needed java at all.

It is working now.

---

### Post by Ji Ruo on 2012-12-22
That's interesting, I haven't had a problem using the open jdk for Java 7. I wonder if their problems stemmed from having Java 6 as the default on precise.

Java 7 had some critical vulnerabilities recently which have supposedly been patched as of update 9. Java 6 has had known vulnerabilities for much longer and I believe they are still unpatched. It is wise to consider Java unsafe for the immediate future and not to run it unless you need to and you trust the source. The problem with cross-platform technologies is that when they have flawed implementations it can affect all platforms - your Linux or Mac system will be just as vulnerable as a Windows pc.

---

### Post by Pjotr123 on 2012-12-23
Java remains tricky, as far as security is concerned anyway. I advise to disable the plugin in your browser, and only enable it when you need it, for as long as you need it.

Instruction for disabling in Firefox:
[https://sites.google.com/site/easylinuxtipsproject/firefox#TOC-Disable-Java-and-openJDK-by-default](https://sites.google.com/site/easylinuxtipsproject/firefox#TOC-Disable-Java-and-openJDK-by-default)

Instruction for disabling in Chrome / Chromium:
[https://sites.google.com/site/easylinuxtipsproject/chrome#TOC-Improve-the-settings](https://sites.google.com/site/easylinuxtipsproject/chrome#TOC-Improve-the-settings)

I advise this for both openJDK and Oracle Java, as the code is largely the same.

---

