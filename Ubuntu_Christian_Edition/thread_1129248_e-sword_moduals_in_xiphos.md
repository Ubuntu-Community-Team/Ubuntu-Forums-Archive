---
title: "e-sword moduals in xiphos"
date: 2009-04-18
forum: Ubuntu Christian Edition
---

### Post by wildman4god on 2009-04-18
Hello,
     A friend of mine is asking me about switching him over to ubuntu and he uses the e-sword program, now we were looking and linux bible study software alternatives and we came across xiphos, formerly gnomesword, anywho, it can use modules from the sword project but we want to know if it will use the modules that he bought for e-sword. I am expecting to do some file transplanting here, i am not expecting anything to be easy. also how does e-sword work under wine in ubuntu as well as installing moduals.

---

### Post by jonathonblake on 2009-04-18
> **wildman4god said:**
>  it can use modules from the sword project but we want to know if it will use the modules that he bought for e-sword. 

Legally, no.
Illegally, yes.  

>  also how does e-sword work under wine in ubuntu as well as installing modules.

On the plus side:
* e-Sword can be installed as a portable apt for Linux;   

On the down side:
* e-Sword functions that require manual editing of the Windows registry may work in Linux;
* I haven't been successful in setting up e-Sword as a networked based application in Linux;
* Some a11y options in e-Sword aren't available on Linux;

What I consider to be the three most useful utility programs for e-Sword, do not run on Linux.

jonathon

---

### Post by wildman4god on 2009-04-18
I just read on wine db that e-sword works perfectly if installed with a special script and thats the only reason they gave it a gold rating instead of platinum.

---

### Post by refdoc on 2009-04-21
> **jonathonblake said:**
> Legally, no.
Illegally, yes.  


As with so many things this is a matter of your local legal situation. Jonathon's black/white response is therefore a bit off. In some legislations it is entirely acceptable to use your content in other formats, in others not. The point of comparison is probably - are you allowed to rip your music CD to mp3 and carry it around on your iPod (not whether you do this, but whether you are allowed to do so - big difference... If yes, then you are fine. If not then not. I am no lawyer and can give you little advise whether this is legal in your country.

Another point is e-sword's EULA. In some countries EULA's are allowed to restrict your otherwise legal fair use rights in others fair use or equivalent does not exist and in yet other countries EULA's have no particular relevance, particular if they intend to restrict your fair use rights.

Irrespective of all of the above, in pretty much any country under the sun (apart a few  outliers) it is illegal to pass on your copyrighted module unless you cease using them. In some countries even if you cease using them you are not entitled to pass them on if the EULA forbids to do so.

Bottomline, if you want to know what you are allowed to do research your country's copyright law.

Wrt the technicalities e-sword modules are nothing special but simply re-named access databases which are entirely straight forward to read out with any mdb viewer.

Cheers

---

### Post by Pepe Lebuntu on 2010-01-03
Okay, let's assume for a moment that it's NOT naughty to, having paid your $20 to read your Bible in E-Sword, use a different program to do so - same product, same single-user-only of product, same function of the product. In this case, how exactly would one go about transfering their e-sword stuff over to Xiphos. Please note, it would be great if it took over Bibles, Commentaries, Dictionaries, Topic Notes, Study Notes (I have five years of keeping my prayer diary in Study Notes form in my E-Sword - I simply cannot throw away all that).

---

### Post by refdoc on 2010-01-05
Assuming you are dealing with your very own content, stuff for which you have licences allowing data shifting or fair use rules in your country allow you to shift:

e-sword 8 used access databases for their modules.

e-sword 9 uses sqlite.

Both are amply documented formats and for both there are excellent viewers etc available. In ubuntu is mdbviewer, which deals with access tables quite nicely and can export them to csv files etc.

e-sword 9 files are encrypted, I am not sure how this pans  out for user created stuff.

Once you know what you are dealing with content wise (i.e. which bit of which table belongs where) it is up to you to figure out how to create a module with that.

CrossWire has some good documentation for creation of modules. There are several import formats.

I would think for a beginner the imp format is the easiest as it allows importing of all kinds of material into all our major book forms ("Bible", "Commentary", "Dictionary", "General Book")

If it is a straight Bible text without any features whatsoever then VPL may also be useful. 

[http://www.crosswire.org/wiki/Main_Page](http://www.crosswire.org/wiki/Main_Page)

Create your module import file, a configuration file, run a module import script, copy the results into the right places in your computer and your done.

I am sure there are also in some corners of the internet some scripts which make all that easier, but as I have had no use for e-sword resources so far, I have never investigated the matter further.

---

