---
title: "Addressing Misconceptions/Misinformation in Studio4 Thread"
date: 2011-07-28
forum: Ubuntu Studio
---

### Post by Scott L on 2011-07-28
@ moderators &#8211; the audience of this post is the community at large and is intended to clarify misconceptions and to correct erroneous statements from previously posted comments.  
  
  Hello everyone, I am Scott Lavender, the project lead for Ubuntu Studio.  Recently a thread was posted about Studio4 and the &#8220;deficiencies&#8221; of Ubuntu Studio in comparison.  While I will not address Studio4 in this post (I have not experience with it), I would like to address comments made about Ubuntu Studio that I feel need to be corrected or clarified.
  
  Also, I would to apologize for the &#8220;wall-of-text&#8221; that will follow, however I very strongly believe in educating so people can make informed decisions and opinions.
  
  Without further ado, I will quote the statements of concern and then clarify presently:
  
  
  
  > So many people working on Ubuntu Studio  There are very few people that work on Ubuntu Studio; currently I would say that four people work on Ubuntu Studio.  None, including me, dedicate all their time to it.  Several are musicians, and therefore spend many hours playing music, and others have other commitments that demand their time as well.
  
  Furthermore, I believe of those four, who I will loosely term &#8220;active&#8221;, exactly none are programmers.  Knowing how to code isn&#8217;t a requirement for contributing or &#8220;developing&#8221; Ubuntu Studio.
  
  
  > no real-time kernel  This is a sticky wicket.  The term &#8220;real-time kernel&#8221; has become an over simplification or a misnomer&#8230;almost a &#8220;holy grail&#8221;. 
  
  I think what most people _mean_ when they say &#8220;real-time kernel&#8221; is two fold; achieving the lowest possible and stable latencies and being able to adjust irq priorities to avoid irq conflicts.  Historically, the &#8220;real-time kernel&#8221; has afforded the best opportunity for lowest, stable latencies and it also provide the only means to adjust irq priorities [1].
  
  The &#8211;generic kernel has absorbed a significant amount of the code from the real-time patch, therefore performance from this kernel has greatly improved.  And beginning with the 2.6.39 kernel, adjusting the irq priorities is included as well, eliminating the necessity of the invasive real-time patch.
  
  Warning: heretical statement follows - Therefore, for many people, the real-time kernel isn&#8217;t really required.  Especially if the &#8211;lowlatency kernel, which is built from the stock Ubuntu kernel, is included in the repositories.
  
  Side note: I tested the &#8211;generic kernel with several older Dell P4, with 1.5 gigs memory and using the on-board audio card I was able to get ~5 msecs of rock stable latency (this means without xruns).  I used two of those machines to test the &#8211;lowlatency kernel and while recording a track,  playing back a track, opening Inkscape, and compressing a folder I could still achieve less than 2 msecs stable latency _without an xrun_. 
  
  
  > has a lower latency  This is an opaque comment at best.  I doubt this was verified by testing Ubuntu Studio and Studio4 in a comparison test on the same hardware.
  
  As reported above, I have consistently been able to achieve 5.3 msecs of stable latency (i.e. without xruns) while recording with older machines.
  
  To further inform, latencies are hardware dependent, Not everyone older P4 will achieve the same results, many might but I haven&#8217;t tested them.  For my time and money I will continue to purchase inexpensive Dell&#8217;s from Ebay, set them up with Ubuntu Studio and give them away to family, friends, and needy musicians.
  
> anyone who wants to do serious music production is going to want a real-time kernelMost of this has been addressed in the two previous sections.  

  But I think it&#8217;s worth stressing that users should be educated about what is really meant by &#8220;real-time kernel&#8221;.  It isn&#8217;t magical, it will not make recording your music somehow better, it will not make your music better, and it is neither a panacea nor a magic bullet.  It is a method to provide lower stable latencies and to adjust irq priorities.
  
  And as noted above, this is mitigated by the assimilation of the real-time patch code into the mainline kernel provided unheard of performance for a &#8211;generic kernel as never before.
  
  
  > Studio4 comes with Kdenlive and OpenShot  It becomes obvious that the original author is not currently familiar with Ubuntu Studio as Ubuntu Studio has been shipping OpenShot.
  
  However, it is true that Kdenlive does not ship with Ubuntu Studio.  I believe the original reason was to avoid shipping additional KDE libraries.  The ISO images have been upwards of 1.6gigs and this was an attempt to keep the size from getting larger.
  
  Although, if users _want_ Kdenlive then please let us know and we will consider including it.  Remember, Ubuntu Studio is made for the users, please let us know what you want.
  
  Finally I want to note that  any application in the repositories is only a &#8220;sudo apt-get install foo&#8221; away.
  
  
  > comes with Reaper by default  This is an interesting position, perhaps not a pleasant one.
  
  Reaper is another DAW, similar to Ardour.  However, I believe that Reaper isn&#8217;t licensed under the GPL or similar and cannot be downloaded and used for free.  Furthermore, I believe that someone has already contacted Cockos.
  
  
  > it&#8217;s faster, more modern, and more complete  More vague comments lacking data to prove validity.
  
  
  > qjackctl just automatically starts up in realtime mode right out of the box without having to edit settings  This statement is slightly confusing so I will simply it by addressing two separate concepts.
  
  I _think_ that this statement is _not_ saying that qjackctl starts automatically when the computer is turned on.  I _believe_ that the user will need to click an icon or select a menu entry.  I am not disputing anything, just clarifying what I believe to be the comment's intent.

  
  However, It does say that when qjackctl starts JACK it will do so in real-time mode.  Ubuntu Studio does the same and has done so for several releases.  Again, the commenter does not seem familiar with recent Ubuntu Studio releases.
  
  
  
  To summarize:  an appreciable amount of comments made by the Studio4 thread OP contained either misconceptions or erroneous information.  I hope that I have helped correct many of these.
  
  Even eliminating the possibility that the OP was exhibiting willful bias, I would hope that readers will be discerning consumers of information from this person based on the amount of fallacies his/her statements contained in the future.
  
  
  Also, I am very serious about receiving user feedback about what applications users would like to see.  Granted, if one person wants an application I will not force thousands of people to download it as well by included it, but if I see enough desire it will most likely be included.  Remember that only applications in the repositories can be included though.  Email the developer mailing list [2] or me directly [3].
  
  Lastly, the Ubuntu Studio team needs your help to make a better product.  If you would like to contribute please contact the mailing list [2] or me directly [3].  Coding or development experience is _NOT_ a requirement!
  
   Thank you for reading,
Scott Lavender
Ubuntu Studio Project Lead 

  
  
  [1] [http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)
  [2] [EMAIL="ubuntu-studio-devel@lists.ubuntu.com"]ubuntu-studio-devel@lists.ubuntu.com[/EMAIL]
  [3] [EMAIL="scottalavender@gmail.com"]scottalavender@gmail.com[/EMAIL]

---

### Post by falkTX on 2011-07-28
Hi Scott,

I'm glad you cleared that information ;)


Stuff like that should not be kept unspoken :)

---

### Post by vapor0 on 2011-07-28
Mr. Lavender,

With all due respect, maybe instead of writing essays, you should get to work compiling a realtime kernel. 

If you think studio recording is better with a lowlatency kernel, you should really try it with a realtime kernel. It makes a huge difference, and as much as you try to gloss over this, it all reeks of fail.

Also, you make an awful lot of assumptions in your post. Like me not testing the two distros on the same hardware LOL. I've got an Ubuntu Studio machine sitting right here!

Anyway, I don't feel like arguing, and besides, I'm already in IM contact with another member of your team, so this is kind of redundant. Not to mention, I expect my crazed Internet stalker friend to appear soon, and I have no desire to turn your "essay" into a shouting match.

Thanks for reading. :D

---

### Post by falkTX on 2011-07-28
Actually, compiling a realtime kernel is not that hard, putting that into the Ubuntu repos is the difficult part.
Someone has to maintain that kernel and watch for security flaws...

I've tried both realtime, lowlatency, preempt and generic kernels.
The 2.6.39 kernel, when configured properly, can actually provide results as good as realtime (and being newer, it has more HW support and fixes built-in).
This is why the latest AVLinux dropped their rt kernel for the 2.6.39 one.
And don't forget about the new firewire stack situation. You can't use it with 2.6.33

I used 2.6.38-lowlatency myself for a long time (now on 2.6.39), and it was very good :guitar:
In fact, this is the default [lowlatency] kernel on the KXStudio-Team PPAs

---

### Post by Scott L on 2011-07-28
> With all due respect, maybe instead of writing essays, you should get to work compiling a realtime kernel. 

If you think studio recording is better with a lowlatency kernel, you should really try it with a realtime kernel. It makes a huge difference, and as much as you try to gloss over this, it all reeks of fail.Firstly, what would a real-time kernel provide me when I can achieve less than 2 msecs of stable latency and adjust irq priorities with the -lowlatency kernel?


 
 
  The following is directed more at the users and other readers in this thread:
I also want to provide some information for users contrasting some aspects of the -lowlatency kernel against the real-time kernel, at least within the Ubuntu ecosphere.

The real-time kernel requires an invasive patch that is provide by an independent and external source.  They release the patch within their own cadence, so this means that the patch is neither available for all kernel releases nor is it guaranteed to be congruent with the kernel version that Ubuntu uses.  For the user this means that the only available real-time kernel is an older version (which may not matter) and it may not align with the version that the latest Ubuntu release uses (which may matter greatly).
   
  In contrast, the –lowlatency kernel does not require a patch.  It can be created from any released version and will always align with the Ubuntu kernel.
   
  Furthermore, and I apologize if I am presumptuous for talking for the Ubuntu Kernel Team (UKT), I do not think that the UKT wants to maintain a real-time kernel, partly for the reasons stated above.

---

### Post by akavir on 2011-07-28
Thanks scott for clarifying the deceptive information from the other thread.  I have no wish to bring that hostility here, but this is what I was trying to get people to see and understand, and it's great to hear it from the horse's mouth!

---

### Post by dawiba on 2011-07-28
Well said Scott L :)

@vapor0

What latencies are you actually achieving using Studio 4?
What hardware are you using?

---

### Post by fedexnman on 2011-07-28
No rt kernel will be needed , even with firewire devices with release of 2.6.39 kernel . Now thats what i call some progress ! avlinux 5.0 uses this kernel and its solid , i tried the avlinux 5.0 live dvd a couple of weeks ago, its solid using firewire . At the moment im using ubuntustudio 10.4.3 with a rt kernel and software ppa from tangostudio's website and its great.   Scott l  thank you for your hard work on ubuntu studio aswell .

---

### Post by vapor0 on 2011-07-28
@ Scott: You never know until you try. Give a realtime kernel a shot! 

You say you're able to get good latency with your soundcard without it, but there's a lot of computers in the world. 

If you haven't tried it, you're debating theory.

---

### Post by akavir on 2011-07-28
> **vapor0 said:**
> there's a lot of computers in the world.

And that's why the generic kernel is the best choice for the widest array of support with a newer kernel.

---

### Post by vapor0 on 2011-07-28
And that's why Ubuntu Studio used to come with a choice.

Noob.

---

### Post by sgx on 2011-07-29
You want a stress test that musicians can verify? Take a complex
yoshimi/zynaddsubfx patch, and play it as a six finger chord.
Use the multitimbral functions to add more of the same patch, and report the choking point, your kernel, and your cpu/ram. The results will be good enough to draw reasonable conclusions, if you can do maths, or use calculators.

Guitar players or non-musicians could do a similar test, using multiple instances of rakarrack to supply fx for a hydrogen demo song, until it all goes pear shaped.
Cheers

---

### Post by vapor0 on 2011-07-29
Here's a thought for those who like to debate theory:

Why is there an -rt patch for Linux kernel 3.0, if realtime scheduling is no longer desirable?

Those articles which say that certain features of the realtime patch have made it into the mainline kernel make it clear that not all of them are, and the ones that are aren't included for the sake of realtime audio processing.

Trying to skirt the issue isn't going to convince anyone, and will only serve to drive users to other distros, like [Studio 4]("http://www.getstudio4.com").

---

### Post by sgx on 2011-07-29
> **Scott L said:**
>  While I will not address Studio4 in this post (I have not experience with it), I would like to address comments made about Ubuntu Studio that I feel need to be corrected or clarified.
  
 Reaper is another DAW, similar to Ardour.  However, I believe that Reaper isn’t licensed under the GPL or similar and cannot be downloaded and used for free.  Furthermore, I believe that someone has already contacted Cockos.  

These two statements say a lot. I can't tell whether you know less
about reaper, ardour, or Studio 4, and the rest of what you said is old news, for those who have been recording with linux for several years. I proposed a test in the previous post, that people who are vocal, or curious, or furious, should use, or something similar of their own creation. Especially those wanting to maximize their productivity, and release excellent versions of linux. Test, verify and publish, and compare.

Cheers

---

### Post by sgx on 2011-07-29
And then there are the darkhorse kernels using bfs, and a very different, but effective approach to maximizing resources.:popcorn:

---

### Post by dawiba on 2011-07-29
@vapor0

What latencies are you actually achieving using Studio 4?
What hardware are you using?

---

### Post by vapor0 on 2011-07-29
:popcorn:

---

### Post by dawiba on 2011-07-29
@vapor0

Thanks for your reply. It speaks volumes :)

---

### Post by falkTX on 2011-07-29
> **vapor0 said:**
> @ Scott: You never know until you try. Give a realtime kernel a shot! 

You say you're able to get good latency with your soundcard without it, but there's a lot of computers in the world. 

If you haven't tried it, you're debating theory.
Really? What makes you think that the leader of UbuntuStudio has never tried a realtime kernel...?

[QUOTE=vapor0]Why is there an -rt patch for Linux kernel 3.0, if realtime scheduling is no longer desirable?[/QUOTE]
You're not getting the point here...
It's not like -rt is not desirable, but considering the costs (high susceptible to hard-locks, specific kernels only, and the need to patch drivers like NVIDIA and ATI), a lowlatency can be a working, stable, and, as the name says, **low-latency**.

It depends on your hardware of course, but if you're able to get very low latencies with the lowlatency kernel, a realtime kernel is no longer required for you.

Just give it a try. Here's my (ported from alessio's) 2.6.38-lowlatency kernel, for lucid (shoule be compatible with Puppy):
[https://launchpad.net/~kxstudio-team/+archive/kernel/+files/linux-image-2.6.38-8-lowlatency_2.6.38-8.42%2Ball1~lucid1_i386.deb](https://launchpad.net/~kxstudio-team/+archive/kernel/+files/linux-image-2.6.38-8-lowlatency_2.6.38-8.42%2Ball1~lucid1_i386.deb)

[QUOTE=vapor0]Those articles which say that certain features of the realtime patch have made it into the mainline kernel make it clear that not all of them are, and the ones that are aren't included for the sake of realtime audio processing.[/QUOTE]
Actually, no.
The realtime kernel is not just for audio production, it's also useful for servers and other hardware that requires real-time disk access.
Note how 2.6.39 introduced realtime's IRQs code. So, in fact, stuff got merged into the kernel that is mainly used for audio processing.

[QUOTE=vapor0]Trying to skirt the issue isn't going to convince anyone, and will only serve to drive users to other distros, like Studio 4.[/QUOTE]
Sorry, but you're the one that is not convincing...
Please give a try to "my" lowlatency kernel, and checkout the results. Or, even better, get the AVLinux one.

---

### Post by vapor0 on 2011-07-29
You need to re-read what I said:

> **aren't** included for the sake of realtime audio processing.

I was saying that the parts of the realtime patch that made it into the mainline kernel **weren't** put there with realtime audio processing in mind. (I apologize for the convoluted sentence.) I read that the changes were kind of "snuck in through the back door" using another reason as an excuse.

As for whether Mr. Lavender has tried a realtime kernel, obviously I meant testing it compared to that low-latency one. 

But I'm glad you're finally admitting that a realtime kernel is desirable; there's a reason Ubuntu Studio used to come with it.

---

### Post by falkTX on 2011-07-29
[QUOTE=vapor0]As for whether Mr. Lavender has tried a realtime kernel, obviously I meant testing it compared to that low-latency kernel.[/QUOTE]
You should probably ask first I guess...
They did a lot of testing regarding kernels, and the conclusion is that realtime kernel is not worth the trouble.
Lowlatency works fine (just as good as generic), it's always supported (you can also use any version), and there are no specific patches needed (like realtime needs)

[QUOTE=vapor0]But I'm glad you're finally admitting that a realtime kernel is desirable; there's a reason Ubuntu Studio used to come one.[/QUOTE]
Hm... back in the old days, there was a big difference between generic and realtime, but not anymore.
The purpose of the rt-kernel patch developer is to get those all those patches into the mainline kernel some day, so sooner or later realtime will go away (or at least we hope so!)

Still, in the present day, lots of people don't need realtime anymore.

For me, I use my laptop for developing and a bit of gaming too (sometimes it's deserved after all the hard work!), so I don't really care much about the realtime kernel.
For example, if you have a hard-lock (caused by the realtime kernel while doing testing), and you had some files opened in a text editor, you'll most likely lost those files... :(
^ This happened to me quite a lot, so I no longer use a realtime kernel while developing stuff.

---

### Post by vapor0 on 2011-07-29
Studio 4 has never locked on me once, I've never even heard of it or any of its predecessors having that problem.

But if you don't use your laptop for audio production, then I agree you don't need it. Why would you?

In the olden days, Ubuntu Studio always had a realtime kernel in the repos. :guitar: Didn't always work, but at least it felt like they were trying.

---

### Post by falkTX on 2011-07-29
> **vapor0 said:**
> Studio 4 has never locked on me once, I've never even heard of it or any of its predecessors having that problem.
Haha, you probably never developed an app/plugin I guess?
It's as simple as a non-breaking while loop in the audio-process...

> **vapor0 said:**
> But if you don't use your laptop for audio production, then I agree you don't need it. Why would you?
I do some stuff from time to time, but lately I've been too busy for that.
My last piece was this - [http://soundcloud.com/falktx/claudia-3](http://soundcloud.com/falktx/claudia-3)
(it's far from complete, but whatever)

> **vapor0 said:**
> In the olden days, Ubuntu Studio always had a realtime kernel in the repos. :guitar: Didn't always work, but at least it felt like they were trying.
And they still keep trying...
They tried really hard to make one for Maverick, but too much Ubuntu bureaucracies...

As Scott spoke in the IRC  yesterday:
'UbuntuStudio will be the first distro with a fully audio-production-capable generic kernel!'
:biggrin:

---

### Post by vapor0 on 2011-07-29
If it's because of Ubuntu bureaucracies, then I apologize. I did not know. :confused:

---

### Post by fedexnman on 2011-07-29
Vapor0  , you seriously need to try the 2.39 kernel on the avlinux5.0 live dvd , it works like a charm , I kid you not , youll see what everyones talking bout ,  its ok to be fustrated , im back using 10.4.3 with a rt kernel for now. 10.10 and 11.04 dont use the 2.39 kernel, or rt kernel . so I understand your frustrated. Im sure ubuntustudio 11.10 is gonna rock with the newer 3.0 series , kernel with the irq threading . So id just use 10.4.3 till 11.10 gets release in october.

---

