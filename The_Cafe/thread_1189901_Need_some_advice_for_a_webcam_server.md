---
title: "Need some advice for a webcam server"
date: 2009-06-17
forum: The Cafe
---

### Post by dmizer on 2009-06-17
I have a project for a friend which requires a dedicated webcam server. The following is a list of minimum requirements:

[LIST]
[*]Record video and audio on demand
[*]Simple browser based interface (something as basic as a webpage with a giant start and stop button would be sufficient)
[*]Save video in a specified folder for later retrieval
[*]FLOSS (perhaps obvious, but you never know)
[*]Can run on a P4 with 512M of ram (bonus points for an even smaller footprint)
[/LIST]
The following features would be nice but not essential:
[LIST]
[*]configurable record timeout/size limit
[*]playback
[*]Debian package installable in Ubuntu
[/LIST]

I'm looking for something that allows us to open up a web page push a record button and the cam starts recording. The video does not need to stream, it just needs to record; but playback of saved video would be nice.

---

### Post by gn2 on 2009-06-17
Zoneminder might be worth a look: [http://www.zoneminder.com/](http://www.zoneminder.com/)

EDIT: Just searced in Synaptic and it's in the 8.04 repos.

---

### Post by gn2 on 2009-06-17
oops

---

### Post by ukripper on 2009-06-17
> **gn2 said:**
> Zoneminder might be worth a look: [http://www.zoneminder.com/](http://www.zoneminder.com/)

EDIT: Just searced in Synaptic and it's in the 8.04 repos.

+1 it works great with ubuntu.

---

### Post by dmizer on 2009-06-17
I've been working on getting it installed. It's a real pain because even though I've installed it through the repos, it still needs Cambozola which requires ant to compile and I can't get ant to work. I keep getting the JAVA_HOME pointer error:
```
BUILD FAILED
/home/dmizer/cambozola-0.70/build.xml:40: Unable to find a javac compiler;
com.sun.tools.javac.Main is not on the classpath.
Perhaps JAVA_HOME does not point to the JDK.
It is currently set to "/usr/lib/jvm/java-1.5.0-gcj-4.2-1.5.0.0/jre"
```
Though I've only just begun to research this problem.

Edit -> Solved with this:
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by cariboo on 2009-06-17
A friend of mine gave me a webcam+server that does everything you want, but sound. It uses a java applet for viewing the output. Check out this [ebay]("http://shop.ebay.com/items/__webcam-server?_kw=webcam&_kw=server&_ckw=bui") page.

---

### Post by bgiannes on 2009-06-19
i've just starting on a webcam server project as well.

i've been trying out "webcam-server", it works but is very basic and bugy just do a apt-get install webcam-server, to try it.

to get it to work you need to run 
export LD_PRELOAD=/usr//lib/libv4l/v4l1compat.so just before loading webcam-server -s.

only port 8888 seems to work?


next i was going to try "motion" this program rec video/jpgs to a folder, or so i've read.  i think it has a gui? sudo apt-get install motion  and info here [http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

UPDATE
just install "motion" no gui but it looks like it's working out of the box! i just need to work out how the config files work.

---

