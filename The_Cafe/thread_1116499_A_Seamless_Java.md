---
title: "A Seamless Java?"
date: 2009-04-05
forum: The Cafe
---

### Post by Mattatk on 2009-04-05
It seems to me that Java is not integrated as smoothly as would be the case in, say, windows.(I have had pretty much no experience with Mac  :frown: .) Java for Linux feels more like a quick patch that Sun decided to slap on the OS. Or maybe Java is just designed in a way that makes it better on windows. A conspiracy, possibly? Or maybe I just didn't install it right. I really don't know. I would be interested to hear of others' experiences with Java in Linux.(specifically Ubuntu)

---

### Post by DocForbin on 2009-04-05
What exactly are you talking about?

---

### Post by majamba on 2009-04-05
> **DocForbin said:**
> What exactly are you talking about?

That 's what i was thinking too? Seemless Java no way!!!!!!!

have you realized that technically java application runs a little bittle slower than C++ one and use more memmory than C++ one. Let it is little bit faster but java still slow.

---

### Post by RiceMonster on 2009-04-05
I don't see the difference between it on Linux and Windows. Java apps are slow memory hogs on whatever system you run them on.

---

### Post by Mattatk on 2009-04-05
Well, even more than just being slower, the reliability seems worse to me. Sometimes runescape works, but usually it doesn't. Also sun's negligence to ubuntu's variation of su, and the fact that they never tell you it's as simple as:
```
sudo aptitude install sun-java6-plugin
```

seemed inconsiderate to me.

---

### Post by DocForbin on 2009-04-05
> **Mattatk said:**
> Well, even more than just being slower, the reliability seems worse to me. Sometimes runescape works, but usually it doesn't. Also sun's negligence to ubuntu's variation of su, and the fact that they never tell you it's as simple as:
```
sudo aptitude install sun-java6-plugin
```

seemed inconsiderate to me.
so you have a buggy app that happens to be written in java on your system...

---

### Post by Armor Nick on 2009-04-05
I've always found Java to be a fairly good language to program with, and the apps work great on most of my pc's, regardless of whether it's windows or linux.

---

### Post by chris4585 on 2009-04-05
I got limewire to run on a linux box with 128mbs of ram once... I thought that was a accomplishment.

---

### Post by blastus on 2009-04-05
Java is not slow. Java applications tend to consume a large amount of memory and have longer start up times than C++ (due to JVM) but who cares. Java was made for the Internet and it is a given that for most applications you'll be network-bound more than anything else. For server side applications there is no difference between Java and say C++. Even for desktop applications Java is on par with native applications; for example on a Quad Core Windows machine Eclipse doesn't run any slower than Visual Studio 2008.

---

### Post by Polygon on 2009-04-05
he most likely means the user interface for java applications.

it looks bad no matter what OS you use, its because those java programs are using the java graphics API rather then using the native windows or linux or mac os x ones, becuase its easier to make it cross platform.

but then the bad side is, that it looks ugly.

(example picture)

[IMG]http://img219.imageshack.us/img219/4674/screenshot001l.png[/IMG]

---

### Post by jespdj on 2009-04-05
Java desktop applications don't necessarily look ugly. Swing (Java's GUI toolkit) has pluggable look-and-feels.

The default look-and-feel indeed does not look great, but a programmer can just as easily choose to use the native look-and-feel of the OS that the program is running on (that would be GTK+ on GNOME), and then the app would not look ugly. If a Java program looks ugly, then that's the programmer's fault for not caring about selecting the right look-and-feel.

Java programs also do not run slow. Java programs unfortunately are slow to start up (because the JRE takes a relatively long time to load). This is, however, going to get better in the future. Since one of the later Sun Java 6 updates, Sun has implemented the "Java Kernel", which is the first step towards speeding up Java startup time. What this does is load only the part of the JRE (the core) that is really necessary to run the program, instead of loading the whole JRE when starting up a program. And one of the big topics in the development of Java 7 is the modularization of Java, which means that Java is going to be divided into modules, so that programs only need to load those modules that they actually need.

Until now, Java has been a huge success in the enterprise software world, where it runs on big servers - Java has not so much been a success for desktop applications. If Sun implements those things described above right, Java might become more interesting for desktop apps.

---

### Post by Mattatk on 2009-04-06
Interesting. Guess that sums it up then. Learn something new everyday, I suppose.

---

### Post by kpkeerthi on 2009-04-06
If you are particularly concerned about how Java GUI applications look (although Java 6 has made immense stride on this area) check out [SWT]("http://www.eclipse.org/swt/"). SWT is a Java API that provides even more richer widgets for building GUI applications.

---

### Post by CraigPaleo on 2009-04-06
> **Polygon said:**
> he most likely means the user interface for java applications.

it looks bad no matter what OS you use, its because those java programs are using the java graphics API rather then using the native windows or linux or mac os x ones, becuase its easier to make it cross platform.

but then the bad side is, that it looks ugly.

HJ Split is exactly what I was thinking of when I read the OP. All the other Java apps I use give me more options, including my GTK theme. 
HJ split offers three and the windows option doesn't work, for obvious reasons. So two really - and both uglier than sin IMO.

@ the OP. See Frostwire using GTK and all the other options available

I don't mind longer start up times of larger apps so long as there is a splash screen telling me that the app is loading.

---

### Post by CraigPaleo on 2009-04-06
> **Mattatk said:**
> Also sun's negligence to ubuntu's variation of su, and the fact that they never tell you it's as simple as:
```
sudo aptitude install sun-java6-plugin
```

seemed inconsiderate to me.

Actually, that's not really Sun's fault. Ubuntu doesn't include restricted extras by default because they aren't open source. To get them all in one command, use ```
sudo aptitude install ubuntu-restricted-extras
```

From Synaptic description of *ubuntu-restricted-extras*:
> **Commonly used restricted packages**
This package depends on some commonly used packages in the Ubuntu
multiverse repository.

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (gstreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio
files), and DVD playback.

This way, you won't have to hunt down everything individually as you discover you're missing them. I think these should be included by default -- at the very least, Sun Java and the Flash plugin since they are so popular.

---

