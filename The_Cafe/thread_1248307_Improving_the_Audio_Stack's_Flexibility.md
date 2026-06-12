---
title: "Improving the Audio Stack's Flexibility"
date: 2009-08-24
forum: The Cafe
---

### Post by allquixotic on 2009-08-24
Hey guys,

I recently made a long blog post (more like a paper) describing a method for achieving maximal compatibility with programs using disparate audio APIs. I thought it might be of interest to the Ubuntu community because:

1. I developed the instructions on 9.04, and it's particularly easy to follow the HowTo using 9.04

2. If it were made more robust, it may be something that could go into the main configuration of Ubuntu.

3. It makes me think of the possibility of creating a program that manages an "audio stack" -- conceptually, such a program just keeps track of different versions of configuration files and startup scripts that "go together" as one coherent stack. Ideally users could switch between stacks with different properties. It's a rather advanced concept, but considering the number of apps I found using different audio APIs, it's necessary right now.

If I have some time, I might try and prototype such an audio stack manager. I promise it won't be a daemon; there's no reason to run such a program all the time! It just needs to be run when it's time to change from one configuration to another, which is itself a rather elementary operation.

Anyway, the blog post has nothing to do with an audio stack manager; it's just about getting an audio stack that works with all the apps I use. Enjoy!

[http://tiyukquellmalz.org/blogs/blog5.php/2009/08/23/dreaming-of-universal-audio-stacks](http://tiyukquellmalz.org/blogs/blog5.php/2009/08/23/dreaming-of-universal-audio-stacks)

---

### Post by MaxIBoy on 2009-08-24
I don't know how much my input matters, but here goes.

I've been plagued by issues with Pulseaudio from the beginning, and ALSA was also inadequate. One day, I installed OSS4, spent a half hour configuring various things (like ALSA, SDL, and OpenAL) to use OSS backends. I have never had a single sound problem since, besides the fact that pulseuadio keeps trying to reinstall itself on my system. :)

OSS4 is a terrific sound system in my experience on two computers.

---

### Post by bigbrovar on 2009-08-24
Pulse Audio is a general PITA .. although i think the idea is cool but its still bleeding edge for average user, i use kde and i noticed i have little of no sound issue at all

---

### Post by JillSwift on 2009-08-24
Heh. An abstraction layer for all the other abstraction layers? ;)

Not that I'm calling it a bad idea.

I'm amazed that so many have had problems with Pulse, I made a single adjustment to my install of pulse (just to make it work better with and in place of ALSA) and it's not given me one whit of trouble since. Then again, that's the problem with software that's not quite yet mature, works on some systems better than others.

---

### Post by allquixotic on 2009-08-24
Thanks for the replies, folks. Let me examine them one at a time:

@MaxIBoy: I have used OSS4 in-kernel before, and I think it's a great project. The builtin software mixing is very promising. You really *can't* write an app that takes exclusive control of the sound card with OSS4. Nice.

The downside is that, for a year and a half, I've had a persistent issue with my 82801JI Intel sound card and OSS4. You see, when I insert oss_hdaudio.ko, the kernel panics. **Hard**. So hard that it can't even update the log ring buffer and flush it to disk. No dumps. No ability to load a crash kernel. I mean it just totally crashes the system. So it's hard to debug, and hasn't been fixed :(

Oh, and, if you're using OSS4, you still wouldn't be able to use Ardour without having JACK. Or the new GNOME volume control without having PulseAudio. I'm not sure how well Skype works with OSS4, either. Hmm -- maybe someone could create a variant on my stack that uses OSS4 as the basis :)

@bigbrovar: Pulse should be enabled by default on KDE, so if you don't have any problems, then you don't use apps that are incompatible with "raw" PulseAudio. That's fine, but I do use such apps. :)

@JillSwift: What I introduce in the blog post isn't an abstraction layer -- it's the primordial thoughts and conclusions and groundwork that might lead up to such a thing. I haven't written a magical program of that sort yet. :) But the "manual" method is still doable in the absence of such a program. Heck, once you get a "good" audio stack configuration -- that is, one which lets all the programs **that you use** coexist with software mixing -- you're pretty much done!

I guess Canonical's customization of the audio stack thus far has been so minimal that only the most elementary programs will run out of the box and cooperate with software mixing. A vast majority of the less common apps require customization of the audio stack.

Once you start using more and more audio apps, you have two options: either do ad-hoc hacks to your configuration files each time you want to run a different app, and keep adjusting by shifting in and out different daemons; or, just run them all at the same time (the method I chose) and forget about it.

I guess my next blog post will be a challenge to the general public to throw an audio app at me that doesn't work with my universal audio stack. I'll test it and either admit defeat or declare victory. Might be fun :)

---

