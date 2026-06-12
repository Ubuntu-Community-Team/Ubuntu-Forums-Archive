---
title: "Best distro for programming games?"
date: 2008-07-20
forum: The Cafe
---

### Post by Soeasy1 on 2008-07-20
I have been programming windows games for some while now(no money in it, just for my entertainment) and while i really want to move to linux, linux seems to have a big downfall in games. Not just playing them, but making them as well, as i havent found any good C++ IDE's and I've never been in a world without directx(though im well aware of opengl). So i actually have several questions:
1. which linux distro is best for programming
2. what is a\are there any good C++ IDE's for linux
3. what libraries would i need to make a fully featured 3d game for linux(graphics,sound,input,ect.)

Thanks,
~Soeasy1~

---

### Post by Soeasy1 on 2008-07-20
Im gonna hit the hay, so goodnight all.
Just putting a note out there so you dont get pissed if you respond and i seem to ignore you

---

### Post by Exershio on 2008-07-20
There's plenty of options for programming games in Linux. For C++, I'd recommend using SDL for 2d graphics/input/audio/window handling/etc, and using OpenGL (which works wonderful when combined with SDL) for doing 3d rendering.

As for a good C++ IDE, this is really just personal preference. You can check the "what's your favorite IDE" thread if you want a whole bunch of people's opinions, but *in my opinion*, the best C++ IDE for Linux is Code::Blocks. There is also KDevelop, another great IDE, if you use KDE. I've also heard great things about Eclipse and Anjuta.

And as for the distro to use for programming, that really doesn't matter at all. All distros are relatively the same thing with different packages. Any distro can accomplish the same task as another distro (though some are built for certain things, I've never seen a "programming" distro.) Ubuntu works just as well as Gentoo, which works just as well as Arch Linux, or openSUSE, or Fedora. The distro you pick should reflect what you want out of Linux as a whole, not just for a specific task (programming). Really depends if you want to compile everything by source, or have a full out of the box setup, or do a very minimalistic setup.

Finally, here are some links for previously mentioned stuff:

[http://codeblocks.org](http://codeblocks.org) Code::Blocks official website
[http://libsdl.org](http://libsdl.org) SDL website
[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php) (Very nice SDL tutorials for C++)

---

### Post by Soeasy1 on 2008-07-21
Ok, thanks a lot, your post was very helpful. So for example, I could use code::blocks and ubuntu just as well as using KDevelop and OpenSuse

Thanks!

---

### Post by LaRoza on 2008-07-21
> **Soeasy1 said:**
> 
1. which linux distro is best for programming
2. what is a\are there any good C++ IDE's for linux
3. what libraries would i need to make a fully featured 3d game for linux(graphics,sound,input,ect.)


1. They are all the same. If you are using Ubuntu and have the internet, there is no need to change.
2. See sticky in Programming Talk (under development)
3. OpenGL, SDL and their ports. Python has PyGame (uses SDL) and there are many game engines for languages from C to Python.

---

