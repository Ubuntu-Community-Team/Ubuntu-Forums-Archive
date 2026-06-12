---
title: "How to increase java heapsize"
date: 2016-07-19
forum: Virtualisation
---

### Post by tranvanthien on 2016-07-19
Hi all

I've installed Ubuntu 16.04 64bit on Virtualbox in windows 7 32bit. Then i install SuperR's Kitchen [URL="http://forum.xda-developers.com/chef-central/android/kitchen-superrs-kitchen-t3202296"]http://forum.xda-developers.com/chef-central/android/kitchen-superrs-kitchen-t3202296

[/URL]to deodexing android MM 6.0.1 ROM but failed. here is the message error. Please help. Thank you.
```
Deoptimizing boot.oat ...
----------------------------------------------------

Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
    at org.jf.dexlib2.analysis.AnalyzedInstruction.<init>(AnalyzedInstruction.java:84)
    at org.jf.dexlib2.analysis.MethodAnalyzer.buildInstructionList(MethodAnalyzer.java:515)
    at org.jf.dexlib2.analysis.MethodAnalyzer.<init>(MethodAnalyzer.java:162)
    at org.rh.smaliex.DexUtil$ODexRewriterModule$1$1.getInstructions(DexUtil.java:402)
    at org.jf.dexlib2.immutable.ImmutableMethodImplementation.of(ImmutableMethodImplementation.java:82)
    at org.jf.dexlib2.immutable.ImmutableMethod.<init>(ImmutableMethod.java:72)
    at org.jf.dexlib2.immutable.ImmutableMethod.of(ImmutableMethod.java:95)
    at org.jf.dexlib2.immutable.ImmutableMethod$1.makeImmutable(ImmutableMethod.java:129)
    at org.jf.dexlib2.immutable.ImmutableMethod$1.makeImmutable(ImmutableMethod.java:120)
    at org.jf.util.ImmutableConverter$3.next(ImmutableConverter.java:139)
    at com.google.common.collect.ImmutableCollection$Builder.addAll(ImmutableCollection.java:301)
    at com.google.common.collect.ImmutableSet$Builder.addAll(ImmutableSet.java:522)
    at com.google.common.collect.ImmutableSortedSet$Builder.addAll(ImmutableSortedSet.java:551)
    at com.google.common.collect.ImmutableSortedSet.copyOf(ImmutableSortedSet.java:326)
    at org.jf.util.ImmutableConverter.toSortedSet(ImmutableConverter.java:137)
    at org.jf.dexlib2.immutable.ImmutableMethod.immutableSetOf(ImmutableMethod.java:116)
    at org.jf.dexlib2.immutable.ImmutableClassDef.<init>(ImmutableClassDef.java:110)
    at org.jf.dexlib2.immutable.ImmutableClassDef.of(ImmutableClassDef.java:139)
    at org.jf.dexlib2.immutable.ImmutableClassDef$3.makeImmutable(ImmutableClassDef.java:210)
    at org.jf.dexlib2.immutable.ImmutableClassDef$3.makeImmutable(ImmutableClassDef.java:201)
    at org.jf.util.ImmutableConverter$2.next(ImmutableConverter.java:105)
    at com.google.common.collect.ImmutableCollection$Builder.addAll(ImmutableCollection.java:301)
    at com.google.common.collect.ImmutableSet$Builder.addAll(ImmutableSet.java:522)
    at com.google.common.collect.ImmutableSet.copyOf(ImmutableSet.java:321)
    at org.jf.util.ImmutableConverter.toSet(ImmutableConverter.java:103)
    at org.jf.dexlib2.immutable.ImmutableClassDef.immutableSetOf(ImmutableClassDef.java:197)
    at org.jf.dexlib2.immutable.ImmutableDexFile.<init>(ImmutableDexFile.java:47)
    at org.jf.dexlib2.immutable.ImmutableDexFile.of(ImmutableDexFile.java:58)
    at org.rh.smaliex.DexUtil$ODexRewriter.rewriteDexFile(DexUtil.java:342)
    at org.rh.smaliex.OatUtil.convertToDex(OatUtil.java:269)
    at org.rh.smaliex.OatUtil.extractDexFromBootOat(OatUtil.java:207)
    at org.rh.smaliex.OatUtil.bootOat2Dex(OatUtil.java:115)


```

---

### Post by bapoumba on 2016-07-19
*Thread moved to **Virtualisation**.*

Edit : is this an Android App ?

---

### Post by MAFoElffen on 2016-07-19
@bapoumba
It's more a java programming/development question, having to do with the settings of the Java Virtual Machine. He is repackaging Android App adk's.  I know the answer and am familiar with, so I'll answer it here.

@OP
Look for a text file with a ".vmoptions" extension, usually located in the same directory as the toolset. I use the Android SDK with Eclipse, but the java setttings for JVM (Java Virtual Machine) are the same, whichever toolset you use.

There are 2 settings that you are going to want to play with. They are "Xms" and "Xmx". Xms is the amount of memory JVM starts on. I usually bump mine up to 128M to 256M. Xmx is the memory limit of the JVM while running. I usually bump mine to between 1024M to 4096M.

Play with those 2 settings until you get a good tune to the app's you are working with and your own system. Do not set the memory to more than your system can afford to allocate (ie- rule of thumb for max is less than half your total).

---

### Post by bapoumba on 2016-07-19
> **MAFoElffen said:**
> @bapoumba
It's more a java programming/development question, having to do with the settings of the Java Virtual Machine. He is repackaging Android App adk's.  I know the answer and am familiar with, so I'll answer it here.

..
OK cool, thanks :)

---

