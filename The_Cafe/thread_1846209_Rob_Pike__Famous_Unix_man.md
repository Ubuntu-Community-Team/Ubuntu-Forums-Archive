---
title: "Rob Pike : Famous Unix man"
date: 2011-09-18
forum: The Cafe
---

### Post by Off Shore on 2011-09-18
I came across this little gem from year 2000 wherein Rob Pike's views on systems research are analysed.
[http://www.advogato.org/article/82.html](http://www.advogato.org/article/82.html)
For those of an academic mind there is also a link there to Pike's 2000 paper on the subject.

Now, you chaps might well ask, why is this old dufffer posting links to 11 year old papers?

Its because Rob Pike happens to be one of the architects behind Google's GO language and he has been interviewed this month by one of the UK's leading Linux Magazines. 
Guess what, he now thinks Operating Systems are irrelevant and the key area is the API. 

> 
-that operating systems seem to be becoming a commodity that doesnt matter anymore. Everyone builds their environment so its either portable or runs to the same API, so it doesnt matter what the operating system is 

What do you bright, upcoming chaps make of it?

---

### Post by NMFTM on 2011-09-18
[img]http://imgs.xkcd.com/comics/mac_pc.png[/img]

---

### Post by llua+ on 2011-09-18
^
/thread

---

### Post by Off Shore on 2011-09-18
> **llua+ said:**
> ^
/thread

That might just be perceived as a tad rude by some of the people who post here.
I always try to avoid discord with other posters. They all seem a decent bunch on the whole, as indeed Im sure you are.

---

### Post by Porcini M. on 2011-09-18
> **Off Shore said:**
> 
What do you bright, upcoming chaps make of it?

Makes sense to me, especially with virtualization reaching such prominence. The OS has always served as the low-level interface between software & hardware, but now that the hardware is being increasingly abstracted away, the OS is less & less relevant (though the APIs need to remain consistent).

Perhaps the browser is the new OS..? :o

---

### Post by Dangertux on 2011-09-18
Hmm... Despite that tacky web comics are well...tacky. That one has a very valid point.

While at their core operating system architectures are still different like night and day. The line is blurring as the world slowly moves toward a more 'rewarding' online experience.

So it's not really shocking to hear that someone who is a key developer for Google's API feels that operating systems are old hat. 

For the most part, the end user experience is very defined by the web experience, not so much the operating system. Which indeed is more of a conveyance for them to get to said 'rewarding' web experience.

Personally I like mucking about with the internals of many operating systems, and pretty much anything else I can get my hands on. So, I enjoy the subtle differences.

---

### Post by IWantFroyo on 2011-09-18
> **llua+ said:**
> ^
[/THREAD]

Fixed.

As for whether the operating system matters, I think it does. Some operating systems run faster, some are more compatible with what programs you use, and so on. Also, what about BASH? You can't run that on Windows.

---

### Post by Porcini M. on 2011-09-18
> **IWantFroyo said:**
> Also, what about BASH? You can't run that on Windows.

Yes you can - via cygwin.

---

### Post by IWantFroyo on 2011-09-18
> **Porcini M. said:**
> Yes you can - via cygwin.

The UNIX way is more elegant. Besides, I just get a feeling like I can't code in Windows. It tries to do everything for me, and usually disastrously fails.
The first day I had Win7 on my new lappy, I tried to make a .bat file just for the heck of it. No matter what I did, it saved it as a .bat.txt. Same with .javas. They got turned into .java.txt.

I really don't know cygwin. Is it possible to run .sh files with complete compatibility? Or do you have to mess around with file locations and the like? Or is it just a terminal?

---

### Post by Porcini M. on 2011-09-18
> **IWantFroyo said:**
> 
I really don't know cygwin. Is it possible to run .sh files with complete compatibility? Or do you have to mess around with file locations and the like? Or is it just a terminal?

I don't know about "complete" compatibility, but I haven't run into any problems. Of course, the OS & file system is windows, so you have to take that into account re paths, binary formats, etc.

---

### Post by IWantFroyo on 2011-09-18
> **Porcini M. said:**
> I don't know about "complete" compatibility, but I haven't run into any problems. Of course, the OS & file system is windows, so you have to take that into account re paths, binary formats, etc.

The Windows filesystem method really ticks me off. Whenever I try to use a Windows computer for work (which I don't often do), I always have a few seconds of panic while I frantically try to figure out where my /home went.

---

### Post by Porcini M. on 2011-09-18
> **IWantFroyo said:**
> The Windows filesystem method really ticks me off. Whenever I try to use a Windows computer for work (which I don't often do), I always have a few seconds of panic while I frantically try to figure out where my /home went.

Cygwin sets up a C:\cygwin directory, under which there's a home. Cygwin interprets C:\cygwn as "/", though you can get to the whole filesystem via another path (I forget what that that is).

---

