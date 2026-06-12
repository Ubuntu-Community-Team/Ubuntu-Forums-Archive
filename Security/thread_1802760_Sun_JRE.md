---
title: "Sun JRE"
date: 2011-07-12
forum: Security
---

### Post by daniel.cotter on 2011-07-12
I've got the Sun JRE installed, dpkg reports it (ii) installed and  healthy, but when I type ```
java -version
```  it tells me I am  using OpenJDK (IcedTea).  I need to run the sun proprietary version,  because of a site I visit which requires it (for the time being).

```
sudo update-java-alternatives -s java-6-sun
``` gets me  ```
update-java-alternatives: directory does not exist:  /usr/lib/jvm/java-6-sun
```Any suggestions how to define the sun  version as the global default?

Thanks in advance,
Daniel

---

### Post by FuturePilot on 2011-07-12
Make sure you have sun-java6-jre, sun-java6-bin and sun-java6-plugin installed.

Then try
```
sudo update-alternatives --config java
```

---

### Post by TBABill on 2011-07-12
I usually just open Synaptic (or can be done via terminal) and mark icedtea-plugin for removal, remove and enjoy. The system picks up my Sun Java plugin fine and works great.

---

### Post by mikewhatever on 2011-07-12
Have you installed java into /opt, possibly following this howto -> [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Inform-the-system-and-make-the-new-?](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Inform-the-system-and-make-the-new-?)

If so, make sure you update the java version correctly.

---

### Post by daniel.cotter on 2011-07-13
FP,

Worked like a charm, and I'm into the site I needed.

How did you know which packages are needed?  I am forever needing help, and never able to solve issues like this one, which turned out to be simple.

I am grateful for your help.
Daniel

---

### Post by FuturePilot on 2011-07-13
> **daniel.cotter said:**
> FP,

Worked like a charm, and I'm into the site I needed.

How did you know which packages are needed?  I am forever needing help, and never able to solve issues like this one, which turned out to be simple.

I am grateful for your help.
Daniel

You're welcome! :)

My knowledge comes from years of experience. Hang in there, you'll get better at it. ;)

---

