---
title: "have sun's java enabled as default"
date: 2007-10-26
forum: Ubuntu Brainstorm
---

### Post by Hibble on 2007-10-26
why not have  sun's java enabled as default for java aplications possibly under restricted drivers(not shore about the licencing)

reason for this is that having installed suns java 6 from the repository's  some programs still tried to use gjc. 1/2 the time this is ok but strange errors happen and there is a higher cpu usage whilst running java applications. directing applications to use sun's java as default if its installed would have saved me many problems.

---

### Post by qamelian on 2007-10-26
Originally, this wasn't possible because of licensing issues. I would assume that the reason it isn't done now is that Sun's Java bundle is fairly large and there may simply not be enough space on the single CD to include it without removing something else to make way for it.

---

### Post by sloggerkhan on 2007-10-26
Maybe the package install for sun java should also switch java default to sun's?

---

### Post by qamelian on 2007-10-26
> **sloggerkhan said:**
> Maybe the package install for sun java should also switch java default to sun's?

I believe it does now, but some apps may be "hard-coded" to call the GNU java instead. I could be wrong about this, but I don't recall needing to run update-alternatives to switch to Sun's Java on Gutsy.

---

### Post by 1337455 10534 on 2007-10-26
+1
But only for the DVD version.
I Strongly support installing java ***_as an update!_*** for computers with over 2 GBs (its 125 MB, rite?)... Update manager would have to detect:
and take HDD info (df i think), determine if 2 GB is available, and install the correct version.

I am actually not that much of a Java fan, I half-resent, half-appreciate it.. It sucks memory like crazy but its portable and easier than the Cs. *sigh*

---

### Post by Hibble on 2007-10-27
If applications are hard coded then yes there is a problem.(very few should be as gjc is not normally on windows etc..)   Basically after installing sun's java through synaptic the following command line should be run.

```
sudo update-java-alternatives --set java-6-sun
```

This changes the java virtual machine to be sun's as default

```
java -version
```

Will show witch version before and after the change. now whenever a program calls java on the command line, from applications menu etc.. the proper java will be used.


**If suns java can be part of the default install all the above would be unesesery.**

---

### Post by smartboyathome on 2007-10-27
> **Hibble said:**
> If applications are hard coded then yes there is a problem.(very few should be as gjc is not normally on windows etc..)   Basically after installing sun's java through synaptic the following command line should be run.

```
sudo update-java-alternatives --set java-6-sun
```

This changes the java virtual machine to be sun's as default

```
java -version
```

Will show witch version before and after the change. now whenever a program calls java on the command line, from applications menu etc.. the proper java will be used.


**If suns java can be part of the default install all the above would be unesesery.**

This is a problem of the developer then, and not of Ubuntu, that a certain Java is hard coded as the Java it uses.

---

### Post by Kevin on 2007-10-28
Installing Sun's Java package will make all Java software use it by default in Gutsy (I think, at the very worst, update-alternatives would need to be run, but i haven't had to do that in Gutsy)

However, programs such as Azureus from the repos, or OpenOffice, are compiled using GCJ.  This means that Java programs like these will run using precompiled binaries created from GCJ.  These programs can not use Sun's Java in Ubuntu.

---

### Post by xlinuks on 2007-10-28
Right, and since the programs from the repos are (so much) outdated (like Azureus) you should consider downloading the brand new version and use a "fast and compatible" Java:
[http://xlinuks.googlepages.com/azureus.png](http://xlinuks.googlepages.com/azureus.png)

I as I java developer have never considered GCJ for it has alway run (much) more slowly and there were (and are) serious compatibility issues. Hoping for OpenJDK and IcedTea to finally get done and be _the only_ Java in Hardy Heron.

Just my 0.02 $

---

### Post by qamelian on 2007-10-28
> **Kevin said:**
> Installing Sun's Java package will make all Java software use it by default in Gutsy (I think, at the very worst, update-alternatives would need to be run, but i haven't had to do that in Gutsy)

However, programs such as Azureus from the repos, or OpenOffice, are compiled using GCJ.  This means that Java programs like these will run using precompiled binaries created from GCJ.  These programs can not use Sun's Java in Ubuntu.

No, that isn't quite right, at least not for OpenOffice. OpenOffice is not compiled using GCJ. It isn't written in Java; Java is simply used to add some of the functionality. If you look under Tools > Options in OOo, you will find an option to select which version of Java to use. Mine is running quite happily on the latest Sun Java 1.6. 

The only reason an app would not use the version of Java that you have set as default would be if that application was specifically told to use a different JVM. This sometimes happens when an app is written using one of the alternative JVMs and uses code that might be incompatible with other JVMs for some reason.

---

### Post by xlinuks on 2007-10-28
OpenOffice is not written in Java, only some (little) functionality is written in Java. Go to their site and search for "how to help the project" you'll notice a lot of languages there.

---

### Post by Hibble on 2007-10-28
Compiled java applications produce what is known a 'java bitecode' this code should then run identically on any OS with any mixture of hardware in a java virtual machine. only limitation is that code compiled to java 1.3 specification will run on java 1.3+ hava code compiled to java 1.4 will run on 1.4+ but not 1.3 and java 6(1.6) will run on java 1.6+ but not 13. or 1.4

Problems appear for us java developers when we develop code to the current standard java 6 but GCJ and other implementations are not as complete or less efficient than suns version. So update-alternatives should be automatically be run when a user upgrades to suns java from GCJ.

The average user will not understand what is going wrong with ubuntu and wont understand the differences between GCJ and Suns version or ubuntu and a virtual machine for that matter.

Most java open source projects also use suns java to compile not GCJ.

Here a reasonable analogy. If i have a 1950 ford somthing(GCJ) and buy a new 2007 ford(suns java).  So why is it that when i go for a drive the default set of keys given to me is for the 1950 ford. I chose to buy a new car so why is it not used.

GCJ could be default in Gobuntu but the default in ubuntu should be suns proper version.

---

### Post by andrewpmk on 2007-10-28
How long will it be until IcedTea is ready? Surely we should start looking at replacing proprietary Sun Java with free Sun Java.

---

### Post by amano on 2007-10-28
Since IcedTea is a very new project,  I guess it will take some time. On the other hand they just move and adapt code from other java implementations, which will take less time than writing the stuff from scratch. 

I guess that some parts are already working now.

The wiki is not really helpful to learn about its current status: [http://icedtea.classpath.org/wiki/Main_Page](http://icedtea.classpath.org/wiki/Main_Page)

>   What does and doesn't work in IcedTea?

Sound, javascript, and snmp do not work: these areas are mostly stubbed.
[edit]
What is the status of crypto and ssl?

The GNU Classpath crypto code has been merged into IcedTea, and ssl has been implemented.
[edit]
What is the status of graphics?

All major graphics areas have been replaced/implemented, either using GNU Classpath code or new code written for IcedTea. Bug fixes are ongoing.
[edit]
What is the status of sound?

Sound is completely stubbed. Sun is working on a Free sound-engine. In the meanwhile, we are planning to integrate the work we are doing for GNU Classpath into IcedTea as soon as it is ready (ETA: before the end of August).
[edit]
What is the status of javascript?

Javascript is completely stubbed, and there are currently no plans for IcedTea to fill these stubs.
[edit]
What is the status of snmp?

SNMP is completely stubbed, and there are currently no plans for IcedTea to fill these stubs. 

---

### Post by gnomeuser on 2007-10-30
> **andrewpmk said:**
> How long will it be until IcedTea is ready? Surely we should start looking at replacing proprietary Sun Java with free Sun Java.

Fedora 8 ships with IcedTea, it's not complete but it runs every java app I've thrown at it so far (not many though). It's complete enough to run Eclipse a huge and complicated codebase.

IcedTea definitely should be ready for Hardy, it would make infinitely more sense to go with that than Sun-java. Fedora and Red Hat are really investing heavily in getting it the last few steps towards being a 100% replacement, I have no doubt that it's the way of the future.

---

### Post by pay on 2007-11-12
I also agree with icedtea as the default over gcj. Java programs seem to run better with icedtea than gcj and using icedtea, 64bit users can have a firefox plugin without having to use blackdown java 1.4.

---

### Post by coolen on 2007-11-12
If it can fit on the Live CD, IcedTea would be great for Hardy.
The fact that it's in Fedora seems to suggest they're making good progress. Certainly sounds like it.

---

### Post by LaserJock on 2007-11-13
You guys know IcedTea is in Gutsy don't you?

-LaserJock

---

### Post by pay on 2007-11-13
> **LaserJock said:**
> You guys know IcedTea is in Gutsy don't you?

-LaserJockYes but when you install Azureus it doesn't pull it in, it pulls in gcj instead. The average user probably doesn't know the difference, that's why it needs to be the standard java implementation that other programs pull in.

---

### Post by smartboyathome on 2007-11-13
> **pay said:**
> Yes but when you install Azureus it doesn't pull it in, it pulls in gcj instead. The average user probably doesn't know the difference, that's why it needs to be the standard java implementation that other programs pull in.

This is because it is a binary compiled to GCJ. You can apt-get source it and compile it to use IcedTea, but until the default is switched, it won't be changed. :(

btw, I haven't tried IcedTea yet, but is it any faster than GCJ?

---

