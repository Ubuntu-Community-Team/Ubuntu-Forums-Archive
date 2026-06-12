---
title: "Google desktop clone for kde?"
date: 2007-03-26
forum: The Cafe
---

### Post by emerson999 on 2007-03-26
Anyone happen to know if there's work being done on a google desktop sidebar clone for kde? I received a windows machine for testing purposes a while back, and I have to admit that I really dig google's sidebar. Doesn't seem overly complex to put together a container bar, embed konq. inside, and then throw in beagle bindings. But I also don't want to waste even that much time if it's duplication of work that's already out there.

Anyone know if something like this has been released, or worked on by somebody?

---

### Post by maniacmusician on 2007-03-26
probably not outside of SuperKaramba widgets. It is a neat idea, but not as easy as you think. First, consider the reason that Google Desktop is so popular;

- Customizable. Any number of plugins and extensions can be added to it, and they're easy to manage.
- With an open and easy-to-implement API, almost anyone that knows how to code can write a plugin for Google Desktop.
- Most of the best plugins are made by Google themselves.
- There's a community built around it. If you make a clone, great, it'll be good for you, but how are you going to turn it into something viable that others can use? Can you build a community around it and get people to contribute? 


Would you write it in QT(4)? Can you implement an **easy** API to let regular users make plugins for it? Basically, how much work are you willing to put into it? What you proposed in your post is a pretty hack-ish way to do it that would be barebones at best. How far would you take this?

---

### Post by SunnyRabbiera on 2007-03-26
well I find gnomes deskbar to be pretty close to it, but personally I can live without either or.

---

### Post by emerson999 on 2007-03-27
> **maniacmusician said:**
> 

Would you write it in QT(4)? Can you implement an **easy** API to let regular users make plugins for it? Basically, how much work are you willing to put into it? What you proposed in your post is a pretty hack-ish way to do it that would be barebones at best. How far would you take this?

QT4 if possible, just because I'm used to it. I'm guessing I'll have to go for actual kde though to hijack konq's rendering engine. The only time I ever actually used the kde api was for that reason, and I haven't checked the qt4 webkit port since it was announced back in the day. 

As for the amount of work I'm willing to put into it, absolute minimum possible. I really don't expect it to be anything someone else would ever use, though of course I'd be tossing the source out there if I did it. Hack'ish all the way. Basic javascript support, with only enough extras put on top to get the gg's I use running. And 100% on that's up in the air. As much as I like coding, at the end of the workday I tend to be a bit tired of it. For hobby coding, I'm pretty much just an occasional weekend guy. Not nearly enough fuel there to power an actual project. 

 I know I'd probably be far better off just rewriting the gadget's I use in python, but I wrote a small widget system a while back and part of me is just curious how the other half lives. Really though, I'm just hoping someone will swoop in and mention somebody's allready done something similar that I could just patch up for my own needs.

---

### Post by Polygon on 2007-03-27
honestly google should just make a linux port themselfs, they use linux at google for crying out loud....

---

### Post by Dragonbite on 2007-03-27
I am not too up on the Google sidebar, but what about Opera's Widgets?  From what little I've read I do not believe it has to be run inside Opera.

Plus, the Opera I installed seems to run Qt.

---

