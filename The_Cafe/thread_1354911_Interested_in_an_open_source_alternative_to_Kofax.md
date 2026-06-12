---
title: "Interested in an open source alternative to Kofax?"
date: 2009-12-14
forum: The Cafe
---

### Post by integr8e on 2009-12-14
I've begun developing an application that will serve as an open source alternative to those provided by [_Kofax_](http://www.kofax.com/), [_Abbyy_](http://www.abbyy.com/), and [_Iris_](http://www.irislink.com/).  Once completed, it will support plugins, be able to generate, print, and read barcoded cover sheets, import documents, capture documents from a scanner, extract text from documents, and export them to an external file (or in my case, a hot folder mapped to an [_Alfresco_](http://www.alfresco.com/) repository).

It was started out of necessity, as many of our clients are smaller businesses who cannot afford to drop $10 grand on a scanning station, and should they choose the more affordable desktop application, would prefer not to pay an additional $1.5+ grand for the privileges of generating and scanning barcoded cover sheets.

I have no intention of developing my own barcode or scanning libraries, or engineering my own OCR engine, but instead have chosen to leverage existing open source solutions that accomplish those tasks, and have gotten the application off to a good start.

Is there an interest in the community for such an application?  To my knowledge, there is no [working] open source solution of this type in the wild, so it would be the first of its kind.  If there is an interest, under what license should I place it?  And are there any developers who would be interested in helping me get it off the ground?

The core application is written in Java, as I am most familiar with it and Java is cross platform (I can compile a single binary on 64-bit Linux and deploy it on 32- and 64-bit Linux, Windows, [Open-]Solaris, BSD, Mac OS-X, etc.), but there is plenty of room for C++ developers as interacting with the OCR engine and the Sane and Twain drivers requires use of the JNI (Java Native Interface), which allows the interoperability of Java and native C/C++ code.

Any help or suggestions I can get will be greatly appreciated.  I am currently the only developer working on this, and could really use some assistance by somebody with a bit more experience than myself.

---

### Post by integr8e on 2009-12-15
I'm a software engineer, not marketing engineer, so if your looking for an inspirational speech, you're probably not going to get it from me :D

What license should I place the application under?  I would put it under the GPL, but it will eventually have some extensions that interact with proprietary software, so would the GPL be applicable?  How about the Apache license?  Would it meet my requirements?  I need some help deciding on a license, as I've never dealt with licensing software before.

If I can decide on a license, I can go ahead and upload the application to SourceForge.net.

---

### Post by edmicman on 2010-01-13
Hey, just came across this post via a Google search.  I can't say I'm that familiar with licensing schemes, but wanted to let you know I'd totally be interested in a project like this.  There's a project I've been bouncing around that would definitely make use of a robust document management system, and after using Kofax at work there's definitely an opportunity for those who would like the functionality but yeah, can't shell out the big bucks.

So yeah, count me in as interested.  I'm a developer, too, but don't have much experience with Java anymore.  Do you have a project page set up yet?

---

### Post by alimahwer on 2010-02-17
Hi, We are on the same page. I've been working on a project based on the open source ECM Alfresco, community edition. I found that an open source alternative to Kofax is the main missed component of this edition. 

I'm a Java developer but I don't know what kind of contribution you asking for.

---

### Post by darsu on 2010-02-17
I don't know how relevant this is, but I was just investigating implementation of a form OMR tool for our business because of the prohibitive expense of commercial system licenses. Alas, my boss changed his mind and doesn't want me to pursue the project at this time, but I want to hack away at it as a private project.

I settled on Python and OpenCV for the rough proof-of-concept stage, but I'm open to considerations of coordination if I get things done.

---

### Post by dc_ubuntoo on 2010-09-02
Hello all,
i'm very interested in this initiative, i'm a big open source fan and i'm a .net and Java developer. i know that monodevelop is a great way to go fr .net applications on linux
if you're looking for a contributor, i'd be more than happy to hop in

---

### Post by juancarlospaco on 2010-09-02
Post wheres the code.
Post wheres the Donate button.
Beware of Oracle Patent trollz :(

---

