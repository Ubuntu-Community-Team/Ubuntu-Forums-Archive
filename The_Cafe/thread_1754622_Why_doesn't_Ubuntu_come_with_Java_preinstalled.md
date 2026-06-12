---
title: "Why doesn't Ubuntu come with Java preinstalled?"
date: 2011-05-10
forum: The Cafe
---

### Post by brawnypandora0 on 2011-05-10
I STILL haven't figured out how to install Java. There are so many packages available, and I don't understand which one I'm supposed to choose. Likewise, the instructions on the Java website are too complicated.

Since Java is so ubiquitous, why won't Ubuntu include it in the cd?

---

### Post by dh04000 on 2011-05-10
It comes with OpenJDK, which shares 95% of its code with Java, except for a few pieces of patented tech. Those parts were replaced with open source versions. This will work with 95% of java applications.

If you want to sun/oracle java then:

software center -> search (Sun Java) -> install Sun Java(TM) Runtime Environment(JRE) (also called sun-java6-bin)

That should install the other associated files needed.



What are you trying to run? Is it minecraft? That's the only thing I find that does work on OpenJDK. Even with the Sun Java version, minecraft doesn't like to startup on linux, follow the instructions at minecraft.net site using the minecraft.jar to launch.

---

### Post by Not unique on 2011-05-10
Does the restricted extras come with Java? Would it be easier to install just that and have it all done in one so to speak.
Anyway putting Java in with Ubuntu would increase the size a lot, Maybe they could put it with updates?

---

### Post by 3Miro on 2011-05-10
Just install "ubuntu-restricted-extras", this comes with Java Flash and other such goodies.

---

### Post by fballem on 2011-05-10
Another way to do it is to enable the Partner repositories in your source (I use Synaptic settings). I believe that you need to enable both the repository and the source repository.

Once you have done that, then select the reload button in synaptic, which will update the package listings.

You can then search for sun-java6. I typically install the sun-java6-jre and the sun-java6-jdk - there are other things that will be installed as part of these.

Hope this helps,

---

