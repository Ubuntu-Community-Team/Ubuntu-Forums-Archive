---
title: "Music score Scan to midi or musicxml - deb packaging"
date: 2012-10-06
forum: Ubuntu Studio
---

### Post by mbohets on 2012-10-06
Hi,

I have been  looking for SW that enables one to scan sheet music and have the PC play it out via midi or musicXML, but did not find anything in the repo's.
When looking a bit further, I found several windows programs doing this, and also one
linux program (cross platform Win-MAC-Linux in fact), but no deb file to easily install it in linux.

As I use linux for some time now, I was thinking of doing someting back to the community by making a deb package, so I started reading up on how the Java 
programming language is structured and how to make a package.
In the new Ubuntu packaging guide, it is adviced to create the package first via Debian, as a lot of distro's are based on Debian, and by Creating the package for Debian, more people will benefit from the package.

So I went over to the Debian dev site and started reading up there.
It struck me however that Debian is not very welcoming for new packagers.
They require you to read up dozens of documents and politely tell you that as long as you don't perfectly know all of these documents, you should not waste their time by asking questions, and that you will be lucky if someone will dedicate
their time to help you out.
To me, this struck me a bit like RTFM and and **** off unless you know all pages by heart. 
but I may perhaps be looking in the wrong places ????

As I think this SW would help music students a lot while practicing, I think I would be
a nice addon in a Linux distro though, so I would like to ask an Ubuntu packager
to add this sw to the repo's
[http://audiveris.kenai.com/](http://audiveris.kenai.com/)
Windows alternatives are Photoscore, smartscore, midiscan, and a number of others.
I did not try yet if those work via WINE, but a native linux package for Audiveris
looks much better IMO.
It will be more user friendly to install  and avoid possible system infections via windows viruses while running wine

I contacted the developper to report a bug, and at the same time I told him about my packaging plans.  He was positive about it, but asked me to wait for the new release that will come out soon, so in the mean time I started reading on deb packaging, but having read the Debian things, I don't feel the urge to proceed with
this so much anymore.

A few years back while browsing throug the ubuntu site, it also seemed to be more
welcoming to new packagers, but at that time I just started using linux and was not ready to give something back to the community yet.

So I someone feels enthousiast about packaging this piece of sw  that will help 
musicians who at the same time use linux, IMO it would fill a gap in the linux 
music SW palette.

Best rgds,

---

### Post by wvengen on 2012-10-22
Hi, there has previously been a request for packaging in Debian: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=547671](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=547671) . I don't really have time to package it, but if you (or anyone) needs help in doing so, feel free to ask.

---

### Post by mbohets on 2012-10-23
Can you point me to some jave packages, an easy one to be able to understand
what is in it, and a more complex one to check out how it compares.
I'll probably learn more out of that than from the mountain of documents
to go through as described in the debian packaging guide.

---

### Post by hg21 on 2012-10-25
I don't know if this is helpful,  I have audiveris working (to some extent) in xubuntu.

I  extracted it to /opt/audiveris and set permissions of all files and directories in /opt/audiveris/ to read/write/execute.

I installed tesseract-ocr via synaptic.

Ran "java -jar /opt/audiveris/dist/audiveris-4.1beta.jar"

I had to rectify some errors; eg in plugins/musescore.js I had to correct the path to musescore.

A scanned in page of music as a .jpg file was received and going thro' the steps in step->score produced things much as described in the audiveris handbook.  Going on to export the .xml file and looking at it in Musescore showed a lot of errors.  I hope I might be able to do better as I learn more about the software and perhaps by training the neural net.

---

### Post by wvengen on 2012-11-02
Nice that you have it working, hg21, and are sharing how. For packaging, some other things are needed as well, obviously. One note: you don't need to set rwx permissions on all files. Only executables and directories need the +x bit.

To get started packaging, you can read the Debian documentation. It may be quite a lot, though, and a little overwhelming at first. Then Java packaging has special helpers to make that easier and cleaner, but that's some more reading. Also, (Java) packaging has gone through some changes, so you might find 'old' ways of doing it over the internet as well. Debhelper7 (DH7) is the latest and cleanest, try to stick to that.

I've done some Java packaging, and will try to give a hand on how to start. For now, you can begin reading at the following links.

Pointers:
[LIST]
[*] [http://www.debian.org/doc/manuals/maint-guide/](http://www.debian.org/doc/manuals/maint-guide/)
[*] [http://www.debian.org/doc/devel-manuals#packaging-tutorial](http://www.debian.org/doc/devel-manuals#packaging-tutorial) (advice: use Debhelper 7)
[*] [http://wiki.debian.org/Java/Packaging](http://wiki.debian.org/Java/Packaging)
[/LIST]

---

### Post by etienne@Rofti on 2012-11-17
Dear hg21

Is it possible to give an in-depth, detailed version of the steps you took to install and run Audiveris? I would be eternally grateful.

---

### Post by hg21 on 2012-11-20
Hi Etienne,

I hope I've remembered everything correctly and that I am not insulting you by being too detailed.

1. install tesseract-ocr

In a terminal:
sudo apt-get install tesseract-ocr

2. Go to [/url]http://www.allfreefonts.com/[/url]
download musical symbols.zip
In a terminal cd <your download folder>
unzip musical_symbols.zip
sudo mkdir /usr/share/fonts/truetype/music/
sudo mv Mus*.ttf /usr/share/fonts/truetype/music/

3. Go to:
[http://kenai.com/projects/audiveris/downloads](http://kenai.com/projects/audiveris/downloads)
download audiveris-4.1beta.3167-src.zip

4. In a terminal
sudo mkdir /opt/Audiveris
sudo chmod 777 /opt/Audiveris

cd /opt/Audiveris
sudo mv <your download folder>/audiveris-4.1beta.3167-src.zip .
unzip audiveris-4.1beta.3167-src.zip
(doing it this way should get the permissions right)

5. In a terminal.
cd <homedirectory>

java -jar /opt/Test/dist/audiveris-4.1beta.jar

This should open audiveris
If it doesn't look at the error messages in the terminal and try to correct
for them

6. If you get here OK I suggest that in audiveris

File->Input you should get a list of examples.
load one and then go to Step
in turn do Scale, Grid, Split .....Score. and look for error messages
if you find any report back
You will almost certainly get a warning (in blue) about libtesjeract.
I think you can ignore it.

Hope it works for you.
Note you will have to correct path to musescore if you use it (see my previous).

Hope it works for you

---

### Post by revdjenk on 2012-11-29
hg21
Thanks for the 'recipe' for getting audiveris into Linux.
I've followed all the steps, but the java part is the sticky part for me.
I am using Linux Mint13 64bit and have its openjdk installed. Is this sufficient for audiveris to run? and how/where do I point it to utilize it.
(I am a long-time Linux user, just not in doing CLI installs and such.)

---

### Post by revdjenk on 2012-12-06
Here is the error following the java.jar command in #5:

java -jar /opt/Audiveris/dist/audiveris-4.1beta.jar
Exception in thread "main" java.lang.UnsupportedClassVersionError: Audiveris : Unsupported major.minor version 51.0
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: Audiveris. Program will exit.

Does this mean I should choose an earlier version of audiveris to install?

---

