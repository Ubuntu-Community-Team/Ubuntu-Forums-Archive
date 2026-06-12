---
title: "Ubuntu logo in Synaptic means what?"
date: 2009-09-24
forum: System76 Support
---

### Post by ShowMeGrrl on 2009-09-24
I have a Starling netbook. In the Synaptic package manager, there are square boxes next to each program. I understand that when these boxes are fillled in, that means the program is installed on my computer.

What does it mean when the box is blank but there is a Ubuntu logo next to it?

---

### Post by jdb on 2009-09-24
> **ShowMeGrrl said:**
> I have a Starling netbook. In the Synaptic package manager, there are square boxes next to each program. I understand that when these boxes are fillled in, that means the program is installed on my computer.

What does it mean when the box is blank but there is a Ubuntu logo next to it?

The Ubuntu logo means the app was fine tuned for Ubuntu.
The box not checked means it's not installed.

jdb

---

### Post by ShowMeGrrl on 2009-09-24
Thank you jdb. I am beginning to think that the java runtime does NOT come automatically installed on the Starling as I earlier thought.

---

### Post by thomasaaron on 2009-09-24
I believe it has open jre on it (not Sun's).

Open a terminal and type...
```

java -version
```

EDIT: 
Here's a good ditty on Synaptic...
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by gila_monster on 2009-09-24
ShowMeGrrl, I think Thomas is correct -- I think the default is Open. Unfortunately, there are some websites that use Java that won't work with Open (I use a few), so I installed Sun Java instead and all is well. Sun requires you to agree to the license terms.

Short version is that Open only works for 98% of things. :)

EDIT: yeah, jumped in before reading [this thread]("http://ubuntuforums.org/showthread.php?t=1274153"). Thomas described things a bit better there.

---

### Post by samalex on 2009-09-24
[QUOTE="gila_monster"]ShowMeGrrl, I think Thomas is correct -- I think the default is Open. Unfortunately, there are some websites that use Java that won't work with Open (I use a few), so I installed Sun Java instead and all is well. Sun requires you to agree to the license terms.

Short version is that Open only works for 98% of things. 
[/QUOTE]
I had to remove the FOSS variant of Java that came with my PanP5 and install Sun Java because the version provided by Ubuntu didn't work on any of the websites for my online class.  It took me forever before I figured out what the problem was, but once I removed it (I think it was called IcedTea Java) and installed Sun Java everything worked great.

This is one of my gripes about Ubuntu in general because you can't make the FOSS purists and those who just want the system to work happy at the same time.  The Open Java/IcedTea Java fiasco I ran into is one example, and another is Ubuntu going with some open source PDF Viewer instead of the Adobe Acrobat Reader, which works great in Linux.  Again with school our assignments are PDF Forms and the FOSS PDF reader that came with Ubuntu couldn't edit and save the forms.  Installing the Adobe PDF Reader through Synaptic was simple enough, but some users might not know to do that and just give-up because it doesn't 'just work'.  

My opinion is if there's a native Linux client, like Sun Java and Adobe Acrobat Reader, Ubuntu needs to use it.  Don't go with a sub-par Open Source variant just because it's open source.  Yes this helps to satisfy the FOSS purists, but Ubuntu is already scum to these folks (including FSF) anyway because of Tomboy and F-Spot.

Sorry, I didn't mean to hijack the thread with my rant, but the Java problem struck a nerve with me because of the time spent trying to figure it out myself.

Take care --

</soapbox>
Sam

---

### Post by thomasaaron on 2009-09-24
> but the Java problem struck a nerve with me because of the time spent trying to figure it out myself.

That's what our forums are for! :popcorn:
:guitar:
But kudos on your self-sufficient streak. An admirable trait by any standard!

---

