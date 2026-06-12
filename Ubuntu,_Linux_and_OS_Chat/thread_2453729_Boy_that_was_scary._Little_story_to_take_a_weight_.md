---
title: "Boy that was scary. Little story to take a weight off"
date: 2020-11-16
forum: Ubuntu, Linux and OS Chat
---

### Post by hrafnagudh on 2020-11-16
I hope this is the right section to talk, in case it isn't apologies, I'm not very used to write in forums... I am a relatively new user, using Lubuntu for working on my thesis, since, well, it works better than windows.
I have my data on another partition, with the Linux partition without almost anything added.
I'm learning commands and stuff, and expecially the folder management is simply fantastic.

Today I was doing some experiments: opened the terminal, mkdir experiments, and inside it, doing stuff with folders, trying to learn with man how to do various stuff, and removing the contents of ./experiments with rm -r *. 
Problem is, at some point I must have cd in my root and going fast and distracted I did rm -r * in my home...
How many times did I read on the command line book about respect for commands...I realized where I was. I did ls. I was worried, to say the least.
BUT! someone in the beginning told me to install Timeshift. That worked. My important files being on the partition are still there and nothing seems to change except minor stuff.

That. Was. Scary. Lesson I learned, always try command with ls, before doing rm. Special thanks to ml9104 for being the one telling me about Timeshift :D, I owe you a beer.


Quick question, among the stuff lost, there are the folders that, with Desktop, were in the home/user. I recall being documents, video, images etc. Just for repairing all, can someone tell me which exactly were? (I believe they are the same for everyone upon installation?).

Well. There it is. Don't make too much fun off me please xD

---

### Post by CatKiller on 2020-11-16
Glad to hear your Teaching Moment came out OK. 

> **hrafnagudh said:**
> Quick question, among the stuff lost, there are the folders that, with Desktop, were in the home/user. I recall being documents, video, images etc. Just for repairing all, can someone tell me which exactly were? (I believe they are the same for everyone upon installation?).

The quickest and easiest way to check is to create a new user (also one more thing off the checklist that you'll have shown to yourself that you can do) and compare them. In addition to the directories there's an XDG file (whose name I can't remember off the top of my head) that specifies the directories and their special function, as a means of making the Linux desktop a bit tidier and more standardised.

Creating a new user (in general) can be a useful troubleshooting step: it helps you to distinguish between hardware/system-level problems, and those that are because of a particular user configuration.

---

### Post by DuckHook on 2020-11-16
> **hrafnagudh said:**
> IDon't make too much fun off me please xD
How can anyone make fun of you for doing the sort of stuff that we all did when we were learning the ropes? In my case, I pulled exactly the same stunt, but without the benefit of Timeshift. It was back before I knew about file recovery tools too. Lost everything.

The one benefit of learning the hard way is that the lesson really stuck. These days, I treat rm -rf the way I would treat a live hand grenade.
> **CatKiller said:**
> Creating a new user (in general) can be a useful troubleshooting step: it helps you to distinguish between hardware/system-level problems, and those that are because of a particular user configuration.
&#8593; This.

@hrafnagudh

An additional strategy—once you're comfortable enough with Linux—is to set up multiboot so that you have 2+ distinct OSes on 2+ distinct partitions. That way, even if you totally bork one of them, you can always boot into the other to try to repair the first.

---

### Post by hrafnagudh on 2020-11-17
Thanks to both :) I'll try do the new user thing, maybe in the future someday even the multiboot. For now, I'm sticking with doing the hundreds of folders I need with a single command :p 
Have a great day :D

---

### Post by ayesc0tty89 on 2020-11-17
I feel you. I done this years ago but to a dir that had a lot of my stuff stored, years worth. didn't get anything back and unlike you - I never backed it up!
It's how we learn. :)

---

