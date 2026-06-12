---
title: "Madagascar penguins advertise Intel Core i5"
date: 2010-10-26
forum: The Cafe
---

### Post by SeijiSensei on 2010-10-26
[http://www.youtube.com/watch?v=s9c4rQDChEI](http://www.youtube.com/watch?v=s9c4rQDChEI)

Saw this on ESPN this evening and wished there was a Linux logo of some kind snuck in there somewhere!

Pixar's rendering farm has run on commodity Linux boxes since [2003](http://news.cnet.com/2100-1001-983898.html). Pixar's premiere software platform, [RenderMan](http://blogs.computerworld.com/pixars_rendering_software_big_on_linux_servers_not_mac), usually runs on Linux servers though the workstation clients are multi-platform.

---

### Post by Lucradia on 2010-10-26
Intel doesn't like linux when it comes to their processors though (AMD does instead.) However, Intel graphics work great with linux, just never good with 3D Gaming. :V

---

### Post by toupeiro on 2010-10-26
> **Lucradia said:**
> Intel doesn't like linux when it comes to their processors though (AMD does instead.) However, Intel graphics work great with linux, just never good with 3D Gaming. :V

Intel GPU's != Intel CPU's by a long shot....  Intel processors work amazing with Linux.  I run dual Xeon 5670's at work and they blow the doors off any AMD Opteron chip I've ever used.

---

### Post by Lucradia on 2010-10-27
> **toupeiro said:**
> Intel GPU's != Intel CPU's by a long shot....  Intel processors work amazing with Linux.  I run dual Xeon 5670's at work and they blow the doors off any AMD Opteron chip I've ever used.

I meant "normal consumer" processors, which this thread is about, not server processors.

---

### Post by toupeiro on 2010-10-27
> **Lucradia said:**
> I meant "normal consumer" processors, which this thread is about, not server processors.

Ok.  My Core i7 runs circles around my friends brand new hex-core AMD chip.  Same architecture as the Xeon, fundamentally... (minus 2 cores and some cache)

And Xeon's are NOT just for servers, nor are the ones I am referring to in a server.  Some people actually *need* compute power. :P

---

### Post by cascade9 on 2010-10-27
Didnt Pixar used to have an opteron render farm? I gues that they found a way to decrease the cost of upgrading the farm. 

> **toupeiro said:**
> Intel GPU's != Intel CPU's by a long shot....  Intel processors work amazing with Linux.  I run dual Xeon 5670's at work and they blow the doors off any AMD Opteron chip I've ever used.

True Intel CPUs and Intel GPUs are very different things. Intels made lots of great CPUs, but as far as GPUs go, its fail, fail and then fail some more. 

The 5670s are very fast, but if you copmpared them to opterons in the same price range, things might be different (newegg lists the 5670 @ $1460 for 6 cores, vs $744 for an opteron 6168 12 core). For almost anything running on a server chip, I'd rather have 24 slower cores than 6 fast cores.

---

### Post by toupeiro on 2010-10-27
> **cascade9 said:**
> Didnt Pixar used to have an opteron render farm? I gues that they found a way to decrease the cost of upgrading the farm. 



True Intel CPUs and Intel GPUs are very different things. Intels made lots of great CPUs, but as far as GPUs go, its fail, fail and then fail some more. 

The 5670s are very fast, but if you copmpared them to opterons in the same price range, things might be different (newegg lists the 5670 @ $1460 for 6 cores, vs $744 for an opteron 6168 12 core). For almost anything running on a server chip, I'd rather have 24 slower cores than 6 fast cores.

not always the case at all, and I have a prime example.

An UltraSparc T2 processor can out-thread ANYTHING AMD or Intel currently make, but throw a heaping single threaded process at it and you're crawling in comparison..  Memory bus architecture, hyper-threading, and a lot of the other CPU extensions in the Intel is what trumps AMD.  The cores clock close to the same speed.

It's like racing a tuned Italian supercar and a 70's musclecar with a Blown 440 Hemi with a 6-back.  It depends on which race you are trying to have, and more doesn't always mean better.  If we learned anything from AMD in the last 5 years, it's that, but now it's Intel thats outsporting them.

I'm not saying the AMD chips are slouches by any means, but I am saying that to scale they can't touch the Intel.  I 2 clusters of servers running heavy loads, one with Opeteron and one with Xeon current gen processors and huge amounts of memory and the intels stomp all over them.  Plus, AMD has a horrible design flaw in their Integrated Memory Controller which they have not worked around yet (though I hear maybe the Next generation might have it fixed, finally!), where if you full up the entire memory bus with DIMM chips, it actually downsteps your clock speed on your memory channels.  It's been well documented with AMD and almost any vendor which has used them over the years..

---

### Post by renkinjutsu on 2010-10-27
I've never been a build-it-yourself and buy-all-the-parts kind of guy.. Not to mention, I've only owned one computer in my life (this one). But I think I'll give it a shot and build a new system when AMD's next-gen processors come out.

[http://www.youtube.com/watch?v=uwhuNcx4BTY]("http://www.youtube.com/watch?v=uwhuNcx4BTY")

Look at that! .. and it's for LAPTOPS!

Has intel demo'd any Sandy Bridge stuff yet?

---

### Post by cascade9 on 2010-10-27
> **toupeiro said:**
> not always the case at all, and I have a prime example.

An UltraSparc T2 processor can out-thread ANYTHING AMD or Intel currently make, but throw a heaping single threaded process at it and you're crawling in comparison..  Memory bus architecture, hyper-threading, and a lot of the other CPU extensions in the Intel is what trumps AMD.  The cores clock close to the same speed.

Opinions vary, and this probably isnt the best place to go into 'whjats good and what is crap' but IMO hyperthreading isnt that useful. Maybe for what you do it is, whats good for the goose might be bad for the gander in some cases. ;) 

Id put the iX (and iX based Xeons) being faster mainly down to the chip archichture, which considering how new it is, I'd expect that. AMd hasnt had a totally new chip architecture for what, 7 years? 

If intel cant build a whole new chips thats faster than what AMD is offering from older tech, then Intel has got serious issues. Or they have done something stupid like getting in bed with a nasty memory vendor, design all the decent chipsets tou se the new memory, then realise that its not all that they thought it would be.  

BTW, "the cores clock close to the same speed"? Err......5670s run at 2.93GHz, and 6168s at a lowly 1.9GHz. 

> **toupeiro said:**
> 
It's like racing a tuned Italian supercar and a 70's musclecar with a Blown 440 Hemi with a 6-back.  It depends on which race you are trying to have, and more doesn't always mean better.  If we learned anything from AMD in the last 5 years, it's that, but now it's Intel thats outsporting them.

I'm not saying the AMD chips are slouches by any means, but I am saying that to scale they can't touch the Intel.  I 2 clusters of servers running heavy loads, one with Opeteron and one with Xeon current gen processors and huge amounts of memory and the intels stomp all over them.  Plus, AMD has a horrible design flaw in their Integrated Memory Controller which they have not worked around yet (though I hear maybe the Next generation might have it fixed, finally!), where if you full up the entire memory bus with DIMM chips, it actually downsteps your clock speed on your memory channels.  It's been well documented with AMD and almost any vendor which has used them over the years..

I'm not really fond of car/computer comparisons, but if I was going to do that for current Xoen/Opterons, I'd say it was more like 6 2010 utes (opps, pickup, you crazy americans renaming austrlian inventions LOL) with a 1 ton capacitcy vs 12 1984s utes with a 3/4 ton capacity. 

Sometimes the 2010s are faster, sometimes the 1984s. 

BTW, this is interesting- 

[http://www.anandtech.com/show/2978/amd-s-12-core-magny-cours-opteron-6174-vs-intel-s-6-core-xeon/7](http://www.anandtech.com/show/2978/amd-s-12-core-magny-cours-opteron-6174-vs-intel-s-6-core-xeon/7)

An OS change and a little bit of optomisation makes a big difference. 

See, in some ways I would say that the opertons are 'slouches'. But its not juist about pure speed, in at least some situations cores can make up for speed........its all about getting what works best for you. ;)

---

