---
title: "MonoDevelop 2.0 is awesome"
date: 2009-02-02
forum: The Cafe
---

### Post by Mr. Picklesworth on 2009-02-02
Just grabbed the latest [MonoDevelop]("http://www.monodevelop.org/Main_Page") (development version) from its SVN repository. I am even more impressed with this than I was with 1.0. This IDE needs to be renamed or something, because right now people assume at a glance that it's specific to Mono. That it is written in Mono really just means that this IDE is incredibly flexible.

So, new in this version that excites me is more bindings! Support for Vala and Python. As usual, this isn't just wimpy syntax highlighting; the two languages become a part of the IDE as much as Mono is. (Only integrated debugging trails a little bit behind).

Also new is code folding; a must-have, in my opinion, but up to now bizarrely missing in the Linux desktop IDE world.

Hopefully the MSBuild stuff won't scare people off. It is really a lot tidier than what they had before.

I can now safely use this IDE for everything, and it still doesn't feel bloated. They really did the user interface right.

For 2.0 to compile, you will need to add [this PPA]("https://edge.launchpad.net/~mono-ubuntu/+archive/ppa"), install mono-devel, boo (and others... sorry, try apt-get build-dep monodevelop and hopefully that will get most of it). Then compile the thing and enjoy :)
Instead of installing it, you can use make run. Saves a bit of bother since it isn't a debian package.

(On this topic, the new Glade with GTKBuilder support is also superb. Friendly software development tools for Linux are really starting to take off!)

---

### Post by SKLP on 2009-02-02
Sounds great! I already had that PPA added, so I'm going to build MonoDevelop 2 now to try it out a bit.
Thx for the tip.

---

### Post by SKLP on 2009-02-02
Or not...

Noticed that it required a separate plugin for Boo support (which I want to use), and then I wont get it to work with make run.

Guess I'll wait for some debs then.

---

### Post by Mr. Picklesworth on 2009-02-03
OMG I just noticed it doesn't have an option to indent with tabs! It's all by spaces. Posted to the mailing list in the hopes that it's just hiding somewhere, but this is horrifying.

I'm going to go sob in a corner now :(



I had trouble bothering with the plugins, which is why I just grabbed a checkout from SVN. They seem to do well keeping it stable. With the SVN checkout, it's all in the same place and can be chosen happily via the configure script.

Edit:
It's just the Python binding that has hardcoded spaces to indent. That's okay; the Python end feels a bit unfinished anyway.

---

### Post by MikeMontreal on 2009-02-04
In VS (MS visual studio) the tab character count is a setting in the options of the IDE. Perhaps the same thing exist with settings in monodevelop 2. 

BTW, I have come across this thread looking for help installing monodevelop 2, but no luck as of yet as I am a complete Linux novice (only installed intrepid and mono in the last couple days) Reviewed installation via command line for packages but I have lucked out with the dependency pango. Going to read up on side by side installation and reset my VPC image. 

Am I missing something here that there are no threads on installing this step by step within intrepid - are there not a lot of people using this?

Any directions for learning about monodevelop 2 package installation and the goings on would be appreciated.
 
Thanks.

---

### Post by Mr. Picklesworth on 2009-02-04
Really the best way to deal with dependency issues when building from source is to pull open Synaptic Package Manager and search for whatever it is missing. For Pango, for example, you'll want the C# bindings; probably libpango-cil or something like that. You'll also want mylibrary-dev. (And the documentation for such things you'll need to explicitly specify that you want them installed; it usually is visible in Devhelp).

---

### Post by jrusso2 on 2009-02-04
> **Mr. Picklesworth said:**
> Really the best way to deal with dependency issues when building from source is to pull open Synaptic Package Manager and search for whatever it is missing. For Pango, for example, you'll want the C# bindings; probably libpango-cil or something like that. You'll also want mylibrary-dev. (And the documentation for such things you'll need to explicitly specify that you want them installed; it usually is visible in Devhelp).

It would be nice if somehow they could list the name of the package instead of the name of the group of packages that may or may not contain what your looking for.

---

### Post by bufsabre666 on 2009-02-05
meh, i'll stick with eclipse.

---

### Post by MikeMontreal on 2009-02-05
Hello all again,

Thanks for any responses to my comment; always good to know there are people out there willing to contribute.

I did some searching on the mono site: [http://www.go-mono.com/forums/](http://www.go-mono.com/forums/), and low and behold right there in the group list is a thread about Intrepid and monodevelop 2.  - should have done that in the start.

Thread name: Error compiling Monodevelop 2 alpha 2 on Ubuntu Intrepid. There are others as well.

IMO - This dependency issues made me think of DLL hell in windows, and if you ever had to deal with that you should understand my surprise when I failed to install a simple IDE under linux - the shame, the shame. :(

Thanks again for your comments, will keep you posted on my efforts.

Long live Leopold Scotch...


Update,

Well, I can say I am not that frustrated for failing to get mono-develop 2+ working, considering I am a new-bee to Linux and its quite a bit to assimilate in a very short time. I did indeed learn quite a bit and I have a lot more to learn so I will keep chugging along. 

However,  I am left feeling disappointed with the lack of 'detailed' support for getting the latest versions of developer tools like mono and mono-develop installed considering its potential to the DotNet community - especially for a parallel install. I imagined things to be a bit easier at this point in the game; someone should have a script somewhere for installing from SVN. Should not the developers of these programs provide the installation scripts? 
 
I guess I will be using openSUSE till the bigger community of UBUNTU get around to making it happen for my Intrepid installation. Another UBUNTU defect I suppose...

Long Live Leopold Scotch...

---

### Post by SKLP on 2009-02-10
I ended up compiling it anyways and trying it out...
Was overall a very good IDE, but not usable for me as I'd like to use boo atm, and there is a horrible bug in the boo plugin: [https://bugzilla.novell.com/show_bug.cgi?id=324223](https://bugzilla.novell.com/show_bug.cgi?id=324223)

---

### Post by directhex on 2009-02-10
> **MikeMontreal said:**
> I guess I will be using openSUSE till the bigger community of UBUNTU get around to making it happen for my Intrepid installation. Another UBUNTU defect I suppose...

99.999% of both "communities" are consumers, not producers. And given your tone, I can't be bothered explaining the logistical problems with MD2 on Intrepid.

---

