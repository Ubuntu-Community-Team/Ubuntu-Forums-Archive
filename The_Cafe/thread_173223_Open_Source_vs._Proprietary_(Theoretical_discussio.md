---
title: "Open Source vs. Proprietary (Theoretical discussion)"
date: 2006-05-10
forum: The Cafe
---

### Post by PrimoTurbo on 2006-05-10
Perhaps this is an unfair assumption since I’m not a developer and know very little about programming. What I’m wondering about is the development of both of these software models.

Is it true that Open Source is often developed by a large group of people and then sort of stitched together in order to work by also a very large group of people? While proprietary is usually developed by a smaller group of people and then the stitching is overseen by a few of the individuals?

The reason why I ask this is because I’m wondering about the quality of the code, for example I’m okay at graphic design. So let’s say I decided to create an open source collaborate digital art work on a very large scale, and I selected a theme. Let’s say a large city on a canvas of 50000x40000 pixels. Now I started this drawing and then when I placed in certain amount of basic elements I released it and allowed others to contribute. Over time many added and removed certain parts and changed colors, etc. The end result will definitely not be my actual vision of the image, it will be a collection of certain parts and certain people might retouch my work based on their opinion.

So isn’t the open source model in a way like a big painting being done by hundreds if not thousands of people? All distributions despite the fact that they might have a stricter guideline of the outcome still use many parts which are done by the overall community. Each of these parts is then made to fit in with the distribution.

I’m not trying to start an argument but a discussion, but what I’m trying to get at is that the overall result will not be 1) The original vision 2) Efficient due to different people developing and contributing different ideas. Perhaps a painting is then a bad example since art has little to do with efficiency unless the purpose is to promote something or to advertise, then certain colors or text might be better. 

Anyways what are your thoughts? Do you see any flaws with my argument? If so what are they? Please remember I don’t claim this is how it is this is simply something I came up with while thinking so it’s probably all wrong but I figured I’ll throw it out and see what people say.

---

### Post by mostwanted on 2006-05-10
I suggest you read the book "The Cathedral and the Bazaar" which explores the open source development model. It's a really great book and it's available online for free.

[http://www.catb.org/~esr/writings/cathedral-bazaar/](http://www.catb.org/~esr/writings/cathedral-bazaar/)

It's number 2 book on that list.

Also, it's not stitched together by many people. There's one or a few maintainers and they create the program. It's possible, because the source is openly available, for many people to send in patches to specific issues the developers would never have fixed themselves. If it somehow doesn't please the developers they can just choose to not add the patch.

---

### Post by yaaarrrgg on 2006-05-10
This is a common worry about open source, and an interesting topic.  I'ev been thinking about this too.

First let's look at a real case.  It's is difficult to quantify goodness and badness.  Although, say we gage overall software quality by the number of security bugs a program has.  Then, let's compare Windows and Linux on a typical day:

Ubuntu (0 unpatched security holes) [http://secunia.com/product/6606/](http://secunia.com/product/6606/)
Windows XP (highly critical security holes)  [http://secunia.com/product/22/](http://secunia.com/product/22/)

Oddly, open source is doing much better than closed source, in terms of security holes.  

This might seem baffling at first, but is easily explained by a number of factors.  While anyone can proof read the source, the number of develpers isn't really as large as you might expect.  

Also, the group can have a structure similiar to proprietary groups.  Instead of a monetary incentive though, other factors can come into play (personal reputation, satisfaction). 

Also, in your painting analogy, what is lacking is any kind of evolutionary process.  In open source projects, the best compete against the best, merge, and produce better offspring.  It's more like natural selection than a free form painting with no contraints. 

There is money in open source too, of course.  Many companies like JBoss take the approach: the software is free, but offer paid support contracts and documentation.

---

### Post by megahertza on 2006-05-10
I like to think of it this way. If a open source program has a bug, a user with understanding of programing can get the source files and possibly create a fix for it, he can then send that to the maintainers. On the other hand, closed source user can really on report bugs, the creators of the program then decide to fix it or not. 

For open source, bugs and improvements can be made by users at little effort from maintainers. Leaving maintainers to focus on much larger objectives.

If you found a bug in windows and you knew you could fix it. You could only report the bug. The bug no mater how big or small may never get fixed.

"Many hands make light work" Assuming theres some kind of oganisation to it.

---

### Post by PrimoTurbo on 2006-05-10
Yeah that makes sense, the painting was a horrible example to be honest but it's 2:00 AM and I can't sleep.

I will take a look at "The Cathedral and the Bazaar", maybe even buy a copy as I hate reading a full book on a computer screen. I've heard of the book before also, I've recently read some stuff on the GNU website and this is why this topic has come up.

I'm not saying Open Source is less secure, because it is clearly FAR more secure then anything else. As soon as something is found then it's patched fast, the problem is that how efficent is the solution if a lot of different people are providng them is what I mean. A problem might be fixed, but perhaps there is a better way to fix it? When a patch is sent to the developer of a certain software, the person might look at it and not consider that there are better ways because the person already has a solution. If the patch is accepted then others glance over and don't try anything else.

Also everything seems to depended on everything else, because everything is seperated. For example does Linux boot so much slower then many proprietary operating systems like OSX or Windows? Is it because there is limited optimization?

---

### Post by megahertza on 2006-05-10
What I have found is that my windows boots faster then ubuntu but takes it time when loading programs after login. 

There are tools you can use to boot ubuntu faster, [http://www.ubuntuforums.org/showthread.php?t=89491&highlight=faster+boot]("http://www.ubuntuforums.org/showthread.php?t=89491&highlight=faster+boot")

This should help.

---

### Post by PrimoTurbo on 2006-05-10
That's true you can't click start for 2 seconds. But even then why is Linux generally slower at booting?

---

### Post by megahertza on 2006-05-10
It generally boots a few items that aren't nessary, but somepll they are for them. For me loading RAID is not nessary, bc my motherboard just doesn't support it. 

Ubuntu had to be built for the needs of many. For windows, if had special component on your motherboard they would require you to install drivers, this includes drivers for Video cards, usb devices, APG, PCI-X and so on.

If you remove items from the ubuntu boot that you don't need you'll see a difference

---

### Post by mostwanted on 2006-05-10
[QUOTE=PrimoTurbo]I will take a look at "The Cathedral and the Bazaar", maybe even buy a copy as I hate reading a full book on a computer screen.[/QUOTE]

Me too. What I did was print out of the PDF on *real* paper :p

---

### Post by kabus on 2006-05-10
> Is it true that Open Source is often developed by a large group of people and then sort of stitched together in order to work by also a very large group of people? While proprietary is usually developed by a smaller group of people and then the stitching is overseen by a few of the individuals?

If you follow the mailing lists of a few free software projects for a while you will see that decisions are usually made by a small group of people, or even a single person.

> For example does Linux boot so much slower then many proprietary operating systems like OSX or Windows? 

"Linux" doesn't, a default Ubuntu install does.

---

### Post by egon spengler on 2006-05-10
[QUOTE=PrimoTurbo]As soon as something is found then it's patched fast, the problem is that how efficent is the solution if a lot of different people are providng them is what I mean. A problem might be fixed, but perhaps there is a better way to fix it? When a patch is sent to the developer of a certain software, the person might look at it and not consider that there are better ways because the person already has a solution. [/QUOTE]

This is only makes sense if you believe that with closed source solutions a fix for a bug is developed yet the developers instead of moving on say "Hey, we know this bug has been fixed but let's keep working on it and see if there are any other ways to fix this".

Seems possible but not likely to me and of course it is equally possible that open source devs would do the same thing

---

### Post by Kvark on 2006-05-10
This is how your open source big city artwork example would work:
1. You draw a city block and put it online together with a description of your vision to draw a whole city.
2. Some of the people who see your city block image thinks it's a fun idea and decides to draw houses to send to you.
3. When you recieve houses from people you decide which ones to add to the city and what changes to make to the houses before adding them.
4. Eventually the city will contain houses drawn by many different people but it will be in line with your original vision because you have full control over what goes into the city.
5. Someone decides that your city image is great but they want to turn it into a winter wonderland but you refuse because it doesn't fit into your vision. So they fork it and now both you and them get exactly what you/they want and people can send wintery houses to them or normal houses to you.

---

### Post by commodore on 2006-05-10
As in python programming: painting!=coding

Painting and programming are too different to compare like that.

---

### Post by Immaculate on 2006-05-10
To me, proprietary isnt a good word for it. Just call it open source and closed source.

But... You can look at all the security holes and stuff all you want, but it doesent matter. Its all numbers. The accual damage the holes do matters. I can tell you this, with no antivirus on either, I have ran very well with no viruses at all on XP and Ubuntu. Last time I had a virus was many years ago, on windows ME.

You can say all you want about anything, but in the end, it doesent matter. Some open source things are better then the closed source ones (Firefox > Internet Explorer), and some closed source things are better then open source (uTorrent > Azureus, Foobar2000 > all) and some things are debated (Linux ? Windows, Opera ? Firefox).

---

### Post by az on 2006-05-10
[QUOTE=Immaculate]To me, proprietary isnt a good word for it. Just call it open source and closed source.
[/QUOTE]

Open or closed, the point is that you get the freedom to do what you want with it.  Java, Cedega, and a host of other software is avaiable in source code, but you are not free to use it as you want to.  "Proprietary" really captures the idea that it is not your's to use.

The power of free-libre open source software is that you can "stand on the shoulders of giants"  As stated, the painting is not a good analogy since writing software is more about putting algorythms into a format that they are understood by the computer - something completely different from art.  

Everybody can have a different vision about what the painting can look like, but there are much fewer ways to go about solving a computer program.  Usually, many people have the same idea (chances are most people would think of the same way of getting something done) with slightly different implementations of it;  which is shy software patents are a bad idea, BTW.  

The only things those two analogies have in common is the need for people to work together.  The toolchain, the licence and the precendence is there for collaboration in FLOSS.

One of the basic tenets of programming is to reuse code.  Do not reinvent the wheel.  Software freedom is the natural extension of that.

Which is why when Bill Gates originaly pitched his idea to IBM execs, they refused - they did not want to go down the path of making software proprietary.  

Why does ubuntu breezy not boot as quickly as windows XP?  Well, because nobody with enough time/knowledge/motivation tried to solve that problem before.  It was addressed at the last Ubuntu Development Summit (UBZ) and the result is that Dapper boots a lot quicker (the same amount of time as Windows XP, AFAIK.)

There are a variety of things that are not addressed "properly" in free-libre software simply because no one has done so.  The stregth is that these sort of things work themselves out as more people join the mix.  More users means more developers and more people "scratching their own itches"

---

### Post by aysiu on 2006-05-10
Just to expand a bit on Azz's analysis of the analogy, I think it might be more appropriate to say that if someone created a new version of the airbrush or paintbrush or some other artistic technique and said, "Hey, even though I did invent this, I want you all to look at the blueprints for it and tell me if the design of the product could be improved."

A painting is a work that is just there to be looked at. A software program or paintbrush is a tool that does its job, and it can do its job better if it's improved upon.

---

### Post by Havoc on 2006-05-10
A good analysis about Linux, plus a good points about Free Software vs Proprietary Software is [this one]("http://linux.oneandoneis2.org/LNW.htm").

Manages to make his point in a fairly coherent way.Plus, he's got some references on the side, if you want to go deeper into the subject.

:cool:

---

### Post by RavenOfOdin on 2006-05-10
[QUOTE=PrimoTurbo]
I will take a look at "The Cathedral and the Bazaar", maybe even buy a copy as I hate reading a full book on a computer screen. I've heard of the book before also, I've recently read some stuff on the GNU website and this is why this topic has come up.
[/QUOTE]

I was just about to bring that up. :)

[QUOTE=azz]Open or closed, the point is that you get the freedom to do what you want with it.  Java, Cedega, and a host of other software is avaiable in source code, but you are not free to use it as you want to.  "Proprietary" really captures the idea that it is not your's to use.

The power of free-libre open source software is that you can "stand on the shoulders of giants"  As stated, the painting is not a good analogy since writing software is more about putting algorythms into a format that they are understood by the computer - something completely different from art.  

Everybody can have a different vision about what the painting can look like, but there are much fewer ways to go about solving a computer program.  Usually, many people have the same idea (chances are most people would think of the same way of getting something done) with slightly different implementations of it;  which is shy software patents are a bad idea, BTW.  

The only things those two analogies have in common is the need for people to work together.  The toolchain, the licence and the precendence is there for collaboration in FLOSS.

One of the basic tenets of programming is to reuse code.  Do not reinvent the wheel.  Software freedom is the natural extension of that.
[/QUOTE]

As the saying goes "Laziness is the first virtue of the programmer." :D

I understand what you're saying about proprietary vs. free vs. open source software, I was thinking about that just yesterday after reading a book on the subject.  Software can be free, but not open source. Software can be open source, but not free.  The aim of FLOSS is to create a medium between the two, which the versatility of the GPL provides.

Five dollars or ten dollars might not be considered as "free" to some people, in order to obtain a burned CD of RH or Debian with packaging and source, but really, is it that much of a problem?  The GPL already states that freedom is its aim and not money.

Personally, I'm more in favor of open source, but seeing as the two walk hand in hand about 90% of the time, what with downloads and encouragement/entitlement to copy and distribute as is under the GPL (which brings me back to these words "create a medium between the two") I don't have much to complain about. 

Its like trying to have your cake, and eat it too, but actually managing to do both by taking a photo of the cake before you eat it.

---

### Post by Immaculate on 2006-05-10
My point Azz is not to go into theory, but saying that each piece of software is very different, and its background is different. Its developers are different. In theory, a bunch of people all around the world working on a piece of software sounds great. And it often is. But I can think of many closed source programs better then their open source counterparts, and also many open source programs better then their closed source counterparts. So this makes me believe that it isnt exactly if it is open source or not that makes it a good program, but many other factors.

And I am most definitally not on the extreme side supporting open source or supporting closed source. I just feel it isnt all about that. I like the fact that people can change it the way they want (however I wont ever do so) but my point isnt about that, its about if open source or closed source makes better software. And I feel many other factors influence it.

Though, I gotta say, open source wins with the whole standards thing. I dont want a company controling the file format I use, I want all software to be able to open it (well, to a certain extent... You know what I mean anyway ;P).

---

### Post by PrimoTurbo on 2006-05-11
Very good points especially Azz’s explanation. However I still don’t believe Ubuntu boots as fast as WindowsXP even on Dapper, because I can boot into XP with in 30 seconds and it takes at least twice as long with Dapper with optimized boot options.

---

### Post by public_void on 2006-05-11
For the building software analogy, I think writing software is like building a house. They both go though the same processes from getting requirements, to design, then implementation etc. It also scales well as it can apply to both small and large projects. i.e. building a dog house is more complex than buildings a skyscraper. 

Whatever analogy, they are heuristic, and so none can fully describe the software process.

---

### Post by az on 2006-05-11
[QUOTE=PrimoTurbo] However I still don&#8217;t believe Ubuntu boots as fast as WindowsXP even on Dapper, because I can boot into XP with in 30 seconds and it takes at least twice as long with Dapper with optimized boot options.[/QUOTE]

What do you mean optimised boot options?

There is a wiki page about boot charting; maybe you should submit your results.
[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)
[https://lists.ubuntu.com/archives/ubuntu-devel/2005-November/012965.html](https://lists.ubuntu.com/archives/ubuntu-devel/2005-November/012965.html)

Anyway, your original post was to ask whether FLOSS was "better" than proprietary software.  It is what it is;  I guess it depends on what you look at.  The improvement in boot times between Breezy and Dapper, to me, shows the strength of FLOSS.  If you don't have the same results, you draw a different conclusion.

But if you want to compare the development model, and not just the end result, you have to take into consideration a lot of factors.  Not the least of which is that Free-libre hardware drivers are generally reverse-engineered, and they can compete with proprietary drivers for other OSes that are officially supported by the manufacturers.  Despite this handicap, FLOSS is gaining marketshare.

One of the first knoppix releases was a small version running kde 2.2.2 (Debian Woody - summer 2002).  I cannot find it anymore, I can just find subsequent version of knoppix-lite which run kde 3.1.  It would be a great demonstration for people to boot that old (four years) knoppix version, the Warty live cd and then compare with the current Dapper.

By experiencing these "snapshots" of the software, you would really get a good sense of just how fast the software is evolving, despite minimal involvement from hardware vendors.

---

### Post by helpme on 2006-05-11
[QUOTE=azz]  Not the least of which is that Free-libre software is generally reverse-engineered, and it can compete with proprietary software that is officially supported by the manufacturers.
[/QUOTE]
What?????????

---

### Post by az on 2006-05-11
[QUOTE=helpme]What?????????[/QUOTE]
Yeesh!  I meant to refer to hardware *drivers*.

I will change it to: "Not the least of which is that Free-libre hardware drivers are generally reverse-engineered, and they can compete with proprietary drivers for other OSes that are officially supported by the manufacturers"

Sorry about that.

---

### Post by helpme on 2006-05-11
[QUOTE=azz]Yeesh!  I meant to refer to hardware *drivers*.

I will change it to: "Not the least of which is that Free-libre hardware drivers are generally reverse-engineered, and they can compete with proprietary drivers for other OSes that are officially supported by the manufacturers"

Sorry about that.[/QUOTE]
Doh, no need to be sorry. Had I used my head for a change it would have been obvious that you were refering to drivers. Silly me.

Anyway, I know that reverse engineering is involved in a lot of drivers, but I doubt it is in the majority of drivers, but I don't really have numbers on this.

---

