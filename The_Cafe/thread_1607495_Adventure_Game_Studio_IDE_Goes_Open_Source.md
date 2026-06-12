---
title: "Adventure Game Studio IDE Goes Open Source"
date: 2010-10-27
forum: The Cafe
---

### Post by DeadSuperHero on 2010-10-27
I consider this to be really big, important news. Depending on how far the word can be spread and how well the community could try pitching in, I'd love to see the Linux game dev community grow as a result of this.

For those of you who didn't even know what AGS is, it's a game IDE for Windows. I've used it for years and loved it, and there was really nothing for Mac or Linux with AGS aside from shoddily-put-together game runtimes. 

Anyways, Chris Jones, the developer of AGS, has decided to open up the source code to his editor, although the compiler itself is still closed (though it's noteworthy to mention that a new compiler can be swapped in to the editor technically. He's slowly open-sourcing it in stages to "test the waters" so to speak.

Anyways, the editor is written in .NET v2.0, and can actually be built with Mono, provided you have the Win.Forms libraries. One fellow managed to get it built and running on OpenSUSE natively.

[Screenshot Here](http://img199.imageshack.us/img199/2844/screenshotnar.png)

Anyways, I just figured I'd post this as there's been interest for quite some time in porting the editor over to Mono, and eventually re-writing a UI in either Qt# or GTK#. If there are any Mono devs interested in trying to port it, write a new UI in a more Linux-friendly toolkit, or submit patches to aid portability, feel free to check out [this thread.](http://www.bigbluecup.com/yabb/index.php?topic=42063.0)

Anyways, it's exciting to see this development come through. AGS is a great developer for the less-technical programmers (specifically indie game designers), and could aid in the development of many, many native AGS Linux games. Heck, the AGS community alone pumps out dozens and dozens of games every couple months, even a small fraction of that would be a huge boost to the Linux gaming community.

---

### Post by Quadunit404 on 2010-10-27
Okay, now I'm interested. I have the source open in MonoDevelop and I'm trying to build it. However, I get the following error in DialogOption.cs when building:

"The private field 'AGS.Types.DialogOption._entryPointOffset' is defined but its value is never used."

Anybody have a clue what to do?

---

### Post by DeadSuperHero on 2010-10-27
I got to about that point and got stuck. Do you have Win.Forms libraries?

---

### Post by Quadunit404 on 2010-10-27
Pretty sure I do. Let me check Synaptic...

Yep, I do have Win.Forms libraries installed. They're for CLI 1.0 and 2.0.

---

### Post by Sslaxx on 2010-10-30
One of the things we're waiting on at the moment is for Chris to create a source repository for the AGS Editor code.

DeadSuperHero? Smiley is the one on the AGS forums who got it to compile on OpenSUSE - so if you haven't already, PM him about it. From his post on the AGS forums it does look like he had to do a fair bit to get it to compile (not just Win.Forms - stuff like PInvoke).

---

### Post by fallenshadow on 2010-10-30
If you wanted to get support from devs then it might have been better to post in the programming section. :)

I will be following this development with interest because in my opinion there isn't enough easy to use game development tools available on Linux.

I would really love to help out but Im afraid my Mono experience is very, very lacking! :(
Ive only used MonoDevelop once in my life! :D

---

### Post by Sofox on 2010-10-30
You should cross post in the Gaming and Leisure forum: [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

More interest over there on Linux games.

---

### Post by directhex on 2010-10-30
I did some analysis of this.

There are two problems:

1) It uses a closed-source audio library called irrKlang, which cannot run on Ubuntu (it must be ported to use a different audio library)

2) It uses a closed-source library, AGS.Native.dll, which is written in Managed C++ (which is not portable via Mono)

---

### Post by inobe on 2010-10-30
i love what your doing, keep up the great work.

---

### Post by DeadSuperHero on 2010-10-31
> **directhex said:**
> I did some analysis of this.

There are two problems:

1) It uses a closed-source audio library called irrKlang, which cannot run on Ubuntu (it must be ported to use a different audio library)

2) It uses a closed-source library, AGS.Native.dll, which is written in Managed C++ (which is not portable via Mono)

1) You mentioned on Twitter the possibility of using SDL as a backend, I seem to recall. Where would one even start with hooking this into the code to remove the irrKlang dependency?

2) Yeah, currently that library remains closed for no real reason other than the author wanting to keep it closed. This makes it kind of difficult to get the editor itself to build anything natively. 

A third problem is the Win.Forms dependency, just mainly because it doesn't integrate at all on Linux natively. As I've been told by sslaxx in the AGS thread, swapping out the toolkit is non-trivial, as an entire interface would need to be designed and implemented from scratch, although perhaps it would be beneficial to lay that groundwork in place while we're waiting for Chris Jones to open up that final bit of the engine?

If you want, I can try and start up an AGS Linux project page on Launchpad, and we can try taking the existing code and re-factoring it piece by piece to address the existing issues while we wait for it to go fully open. At the very least it would get some of the problems out of the way and at least make most of the engine buildable in and of itself.

---

### Post by directhex on 2010-10-31
> **DeadSuperHero said:**
> 1) You mentioned on Twitter the possibility of using SDL as a backend, I seem to recall. Where would one even start with hooking this into the code to remove the irrKlang dependency?

Probably a good first step is to inventory all the places irrKlang is currently used, and for what - Tao.SDL is probably the right option if it's all sound effects, gStreamer# if it's music.

> A third problem is the Win.Forms dependency, just mainly because it doesn't integrate at all on Linux natively. As I've been told by sslaxx in the AGS thread, swapping out the toolkit is non-trivial, as an entire interface would need to be designed and implemented from scratch, although perhaps it would be beneficial to lay that groundwork in place while we're waiting for Chris Jones to open up that final bit of the engine?

WinForms is ugly, but not a blocker. The other parts are blockers - i.e. once the thing is fully functional on Linux using Winforms, you can start worrying about the toolkit.

IMHO the first step should be the audio part.

---

### Post by DeadSuperHero on 2010-10-31
Very good, then.

I've started [a Launchpad team page]("https://launchpad.net/%7Eagslinux") for anyone interested in drawing together blueprints and ideas, and for the ease of access will push the current code into bazaar in a few minutes.

Also, some build instructions, courtesy of Smiley over at the AGS boards:

> In MonoDevelop, disable "treat warnings as errors" for each project, otherwise it will complain about some unused fields.
Mono has problems loading some of the icons. Saving them again in Pinta solved that.
And you have to 'disable' the debugger and source control parts.

At the very least, this is a starting point to build parts of it...

---

### Post by Quadunit404 on 2010-10-31
Sent a request to join.

---

### Post by Sslaxx on 2010-11-01
> **Quadunit404 said:**
> Sent a request to join.
If you aren't already, it might be a good idea to join the AGS forums, too. [http://www.bigbluecup.com/yabb/index.php](http://www.bigbluecup.com/yabb/index.php)

---

### Post by xenogia on 2010-11-04
I also joined :D

---

### Post by phrostbyte on 2010-11-04
I got it build successfully without much issue. It crashes on startup however due to the P/Invokes. :)

---

### Post by phrostbyte on 2010-11-04
There is way too much stuff going on in AGC.Native.dll for this to be realistically ported to Linux without at least having this DLLs source code. It's not just simple remapping of P/Invokes to POSIX/Linux equivalents. The dependencies on irrKlang seem pretty trivial however.

---

### Post by Shazzner on 2010-11-04
I don't want to be snarky about all this, but it really is pointless until he fully releases the source code.

---

### Post by techrush on 2010-11-05
I cant wait until this is fully realized and released!

---

### Post by Sslaxx on 2011-01-04
> **Shazzner said:**
> I don't want to be snarky about all this, but it really is pointless until he fully releases the source code.
Full source code is to be released.

[http://www.bigbluecup.com/yabb/index.php?topic=42104.msg564285#msg564285](http://www.bigbluecup.com/yabb/index.php?topic=42104.msg564285#msg564285)
[http://www.bigbluecup.com/yabb/index.php?topic=42016.msg564113#msg564113](http://www.bigbluecup.com/yabb/index.php?topic=42016.msg564113#msg564113)

---

### Post by Sslaxx on 2011-04-27
Apologies for bumping this thread, but. An initial release of the engine source code has been made!

[http://www.bigbluecup.com/yabb/index.php?topic=43383.0](http://www.bigbluecup.com/yabb/index.php?topic=43383.0)

---

