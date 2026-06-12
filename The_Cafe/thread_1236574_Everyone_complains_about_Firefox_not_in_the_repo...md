---
title: "Everyone complains about Firefox not in the repo...Try Swiftfox"
date: 2009-08-10
forum: The Cafe
---

### Post by Firestem4 on 2009-08-10
So I recently found a near-exact clone of Firefox called Swiftfox which is available at [www.getswiftfox.com](www.getswiftfox.com)

The biggest issue people have is that Firefox is not updated in the repositories due to the way canonical handles the repo's. 

Well, some of you should give swiftfox a try. Its 100% compatible and its much lighter weight too because they've compiled versions of Swiftfox for varying architectures (i686, AMD64, X86, PPC,) etc. Add their repo and you'll always have an updated firefox. 

Just something I thought the community might like to be aware of.

Edit: Version Chart for what Deb-version matches your CPU. [http://www.getswiftfox.com/proc.htm](http://www.getswiftfox.com/proc.htm)

---

### Post by wojox on 2009-08-10
I've seen that and often wondered about it. I take it you have it installed? Do you really like it?

---

### Post by Firestem4 on 2009-08-10
> **wojox said:**
> I've seen that and often wondered about it. I take it you have it installed? Do you really like it?

I like it quite a lot actually. It is desktop independent (I did not have to download 100mb's of GTK libraries to install it). Instead, i only needed the single Swiftfox .deb file which is 10mb's. It has great integration and because you can download the architecture-dependently compiled versions they run much faster on your machine (For example im running i686version for my intel centrino x2 on this piece of crap laptop. lol).

Running, Swiftfox seems to take an average 20~40mb's less of memory than Firefox does.

---

### Post by running_rabbit07 on 2009-08-10
Does it look the same? Could you give us a screenshot? Does it work the same with Flash? I have to have flash for my classes.

---

### Post by running_rabbit07 on 2009-08-10
> **Firestem4 said:**
> Running, Swiftfox seems to take an average 20~40mb's less of memory than Firefox does.

That's amazing. I doubled my RAM a few months ago just so I could run Google earth on Windows, because I would easily utilize 1.5 Gigs of RAM while running them together. Ever since I have started using Linux I have not used more than 512MB RAM except when I had 20 chapters of a text book open at the same time. (Not complaining, just in awe.)

---

### Post by Firestem4 on 2009-08-10
If something works in Firefox, it works in Swiftfox (if not better.) I have had no problems with Flash, Java, multimedia, or etc.

It has better integration since for instance, I didn't need any GTK libraries to install it.

(I have a custom theme installed called Energy, and the bottom of the screen is an Opera-like add-on called Extended Statusbar)

---

### Post by jadhav333 on 2009-08-10
Does swiftfox have plugin support like the extensions / plugins in firefox?

---

### Post by running_rabbit07 on 2009-08-10
Sweet, next time I boot into Ubuntu, I'll download it.

---

### Post by Firestem4 on 2009-08-10
> **jadhav333 said:**
> Does swiftfox have plugin support like the extensions / plugins in firefox?

Everything you can do in firefox you can do in Swiftfox. it has about:config and all that stuff.

I have all of my add-on's installed (It can also automatically port existing configuration and add-on's from your current firefox installation i believe. It says so on the website if im not mistaken)

---

### Post by MasterNetra on 2009-08-10
looks like its nothing more then a lighten version of firefox. Though I do have a question...I have a Intel Core2 duo processors...which deb would I get Intel Prescott or Older Intel??

---

### Post by unknownPoster on 2009-08-10
FYI...Swiftfox is just Firefox that has been rebranded and optimized for certain architectures. It's firefox that has just been recompiled with certain architectures in mind. :)

If it means anything to you, Swiftfox is compiled with the -03 flag while Firefox is compiled with the -Os flag. It also generally includes the flags, MMX, SSE and SSE2 flags.

If I remember correctly, Swiftfox doesn't include Pango either.

---

### Post by unknownPoster on 2009-08-10
> **MasterNetra said:**
> looks like its nothing more then a lighten version of firefox. Though I do have a question...I have a Intel Core2 duo processors...which deb would I get Intel Prescott or Older Intel??

You'd want to get Prescott or Nocona. Prescott is 32-bit while Nocona is 64-bit

---

### Post by Firestem4 on 2009-08-10
> **MasterNetra said:**
> looks like its nothing more then a lighten version of firefox. Though I do have a question...I have a Intel Core2 duo processors...which deb would I get Intel Prescott or Older Intel??

You are right. Its nothing more than a lightened version. However its actively updated and always updated on their repositories (no jumping through hoops.) Its very stable and who can say that the lightweight is not worth it? (I'm saving myself from wasting 100mb's for GTK+libraries that I don't need).


You will want the Prescott version. (Including link to Version Chart in first post)

---

### Post by Firestem4 on 2009-08-10
> **unknownPoster said:**
> 

If I remember correctly, Swiftfox doesn't include Pango either.


If you mean Tango, the theme. Its there by default.

---

### Post by unknownPoster on 2009-08-10
> **Firestem4 said:**
> If you mean Tango, the theme. Its there by default.

No, I mean Pango. :)

[http://en.wikipedia.org/wiki/Pango](http://en.wikipedia.org/wiki/Pango)

---

### Post by forrestcupp on 2009-08-10
> **unknownPoster said:**
> FYI...Swiftfox is just Firefox that has been rebranded and optimized for certain architectures. It's firefox that has just been recompiled with certain architectures in mind. :)

If it means anything to you, Swiftfox is compiled with the -03 flag while Firefox is compiled with the -Os flag. It also generally includes the flags, MMX, SSE and SSE2 flags.

If I remember correctly, Swiftfox doesn't include Pango either.
This is right.  And that is why Swiftfox can run any extension that is made for Firefox.  Because it basically *is* Firefox.

Swiftfox is great, though.  It seems speedier.  I've used it for a long time.  The only thing about it is that there is obviously a lag in releases from the main Firefox release.  But with the main Ubuntu repos, you don't get any version updates at all.

---

### Post by FuturePilot on 2009-08-10
> **unknownPoster said:**
> You'd want to get Prescott or Nocona. Prescott is 32-bit while Nocona is 64-bit

Some of the later Prescotts are 64bit. 

model name: Intel(R) Pentium(R) 4 CPU 3.40GHz
flags: 	boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **x86-64** constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr cpufreq

---

### Post by zekopeko on 2009-08-10
A "nice" thing to mention is that the binaries are proprietary.
[http://en.wikipedia.org/wiki/Swiftfox#License](http://en.wikipedia.org/wiki/Swiftfox#License)

---

### Post by Firestem4 on 2009-08-10
> **unknownPoster said:**
> No, I mean Pango. :)

[http://en.wikipedia.org/wiki/Pango](http://en.wikipedia.org/wiki/Pango)

Hm...didn't even know about that.

---

### Post by Firestem4 on 2009-08-10
> **zekopeko said:**
> A "nice" thing to mention is that the binaries are proprietary.
[http://en.wikipedia.org/wiki/Swiftfox#License](http://en.wikipedia.org/wiki/Swiftfox#License)

I didn't notice that. 

(It doesn't bother me though..It's still an open-source project)

---

### Post by PRC09 on 2009-08-10
I just installed it on amd64 and couldnt get flash to work plus it installed a bunch of ia32lib and lib32 files with it,so maybe no 64 bit flash yet.

---

### Post by unknownPoster on 2009-08-10
> **FuturePilot said:**
> Some of the later Prescotts are 64bit. 

model name: Intel(R) Pentium(R) 4 CPU 3.40GHz
flags:     boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx **x86-64** constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr cpufreq

I learned something today. :)

Both of my prescotts are fairly old in computer terms.

---

### Post by praveesh on 2009-08-10
Does it integrate perfectly with KDE (the OP has mentioned that it is desktop independent).  If it is a rebrand of GPL licensed firefox, how can it be a proprietory?

---

### Post by Firestem4 on 2009-08-10
> **praveesh said:**
> Does it integrate perfectly with KDE (the OP has mentioned that it is desktop independent).  If it is a rebrand of GPL licensed firefox, how can it be a proprietory?

I wouldn't say Perfectly but it does a much better job than the official Firefox does on my KDE desktop.

The compiled binaries are proprietary according to the poster who pointed it out. (It says so in the swiftfox forums that he has done his own development on the source code rather than just doing a straight compile with compile-architecture-flags. Im not a compile guru but i think thats a correct enough reference for it)

---

### Post by wojox on 2009-08-10
Hey thanks for the link and heads up Firestem4. I've got it downloaded and running your right it is quite a bit speedier and less of a resource hog. :P

---

### Post by Sealbhach on 2009-08-10
> **PRC09 said:**
> I just installed it on amd64 and couldnt get flash to work plus it installed a bunch of ia32lib and lib32 files with it,so maybe no 64 bit flash yet.

Same here on amd64, Flash on youtube is just a white box.

.

---

### Post by Firestem4 on 2009-08-10
> **Sealbhach said:**
> Same here on amd64, Flash on youtube is just a white box.

.

I will try this when I get home. My computer has a new AMD Athlon II X2 250 and I'm running 64bit Kubuntu. hrm....

---

### Post by Sealbhach on 2009-08-10
> **PRC09 said:**
> I just installed it on amd64 and couldnt get flash to work plus it installed a bunch of ia32lib and lib32 files with it,so maybe no 64 bit flash yet.

Yes, it won't work with 64-bit flash plugin. Found this on the Swiftfox forum:


> I have said in many locations including on getswiftfox.com that it is a 32-bit build. This is no secret and is not a bug. The deb for 64-bit systems is different from the 32-bit one in that it includes dependencies on 32-bit libraries that allow it to run on a 64-bit system. It doesn't mean you can run 64-bit plugins with it. If you have an issue with it then you are free to use something else. Thank you.
.

---

### Post by lovinglinux on 2009-08-10
If you are interested in Swiftfox due to optimization for specific processors, you can also try Swiftweasel, which is the same thing, but open source. The only difference I think is that Swiftweasel is released as a generic version for Intel, amd an so on, while Swiftfox has releases for more specific processor families, like Prescott. Either way, it should be more responsive than Firefox.

If you are interested in comparisons, I have a benchmark chart with a couple of Firefox versions since Jaunty release. I have increased my benchmark points from 210 to 1100 with several tips provided in my tutorial [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). The chart does not compare Swiftfox or Swiftweasel, but it compares compiled versions of FF 3.5 and 3.6a1 using PGO and the processor optimization flags, which is basically the same thing as running Swiftfox or Swiftweasel.

---

### Post by 243kof on 2009-08-10
I tried Swiftfox yesterday but it doesn't seem to either load or run faster than standard Firefox to me... :(

---

