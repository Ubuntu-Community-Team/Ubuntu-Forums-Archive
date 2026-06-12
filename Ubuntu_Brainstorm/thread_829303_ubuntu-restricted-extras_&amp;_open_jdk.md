---
title: "ubuntu-restricted-extras &amp; open jdk"
date: 2008-06-14
forum: Ubuntu Brainstorm
---

### Post by starcannon on 2008-06-14
First let me express how much I love Ubuntu, I've been using it exclusively (single boot) for over 5 years now, that said, I'll move on to my topic.

The Ubuntu Restricted Extras package is installing the open source solution for java, that is in my opinion a pretty bad mistake. I know that its there, I know how to uninstall it, and to install Sun-Java from synaptic, but a newbie wouldn't know this. If someone told them to ```
sudo apt-get install ubuntu-restricted-extras
``` with the hope that it would cure many of their proprietary needs, and then the newbie needed to use java, and found that it does not work as expected the first thing they are likely to do is say "linux sux, i'm going back to windows".

A restricted extra is just that, a "restricted extra" its not a free and open extra, and no offense to open jdk, ice tea, and all the people working on that project, but honestly your product is not ready for deployment on the average end-users computer, it needs to be 100% with all java applications first, until that happens its only a headache, a needless one at that when theres a perfectly working solution from Sun that costs no money on the end-users part. At the very least give an option during the package download process with the caveats appropriate to each package, both the Sun and the Open versions, let the end-user decide, it's all about choice.

Anyway, like I said, I love Ubuntu, but I don't think Richard Stallman's ideas about software are the only ideas that count. Theres room for commercial applications and closed source, sure it has to be carefully watched, but don't throw the baby out with the bathwater.

Thanks, and keep up the great work, I can't wait to try out Ibex.
~Starcannon

---

### Post by olskar on 2008-06-14
I completely agree with you! Open JDK is not ready yet and until it is ready, ubuntu-restricted-extras should install Sun-Java.

---

### Post by eragon100 on 2008-06-15
> **olskar said:**
> I completely agree with you! Open JDK is not ready yet and until it is ready, ubuntu-restricted-extras should install Sun-Java.

+ 1. I agree as well.

---

### Post by smartboyathome on 2008-06-15
I also agree. This is like substituting gnash for flash - a bad idea for right now.

---

### Post by olskar on 2008-06-15
Should a bug be filed about this? Is that the correct way to go?

---

### Post by smartboyathome on 2008-06-15
Yes, that is the correct way to go. File it against ubuntu-restricted-extras and explain that sun java should be used instead of open jdk.

---

### Post by olskar on 2008-06-15
One is already filed :)

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/219684](https://bugs.launchpad.net/ubuntu/+source/ubuntu-restricted-extras/+bug/219684)

EDIT: Time to vote ;)
[http://brainstorm.ubuntu.com/idea/9909/](http://brainstorm.ubuntu.com/idea/9909/)

---

### Post by olskar on 2008-06-16
I have now attached a debdiff to replace openjdk with sunjava, now we just have to wait and see if it gets accepted :)

---

### Post by Pjotr123 on 2008-06-16
I posted the original bug report on Launchpad, so of course I'm happy to support this Brainstorm initiative.  :-)

---

### Post by olskar on 2008-06-20
[http://www.jboss.org/feeds/post/java_is_finally_free_and_open](http://www.jboss.org/feeds/post/java_is_finally_free_and_open) :)

---

### Post by cariboo on 2008-06-21
In intrepid ubuntu-restricted-extras does install Sun java.

Jim

---

### Post by olskar on 2008-08-02
[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-July/000460.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-July/000460.html)

What does this mean? They decided to use a non working JRE?

---

### Post by smartboyathome on 2008-08-02
It is still installed with ubuntu-restricted-extras, it is just replacing the default java included with Ubuntu, which doesn't work with much stuff anyway.

---

### Post by olskar on 2008-08-02
Good, they got me worried :)

---

