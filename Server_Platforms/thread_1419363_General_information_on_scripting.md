---
title: "General information on scripting"
date: 2010-03-01
forum: Server Platforms
---

### Post by so0ky on 2010-03-01
Hello,

First I want to say thank you for doing this project, as well as having such a welcoming community.  I am new to Linux, much less being a server administrator with Linux, but I am willing to learn.  I purchased and am currently reading The Official Ubuntu Server Book, and I think I have found my first side project.

First, the book said Ubuntu Server is pretty much coded with a scripting language called Python.  I want to define the different init levels of my server.  I want to define like init 5 to have a GUI interface, just for kicks.  A GUI might come in handy when doing certain things in Ubuntu Server, I just don't know, simply because I've been working on the command line.

So my first question is, do I need to learn Python to script in Ubuntu Server?  I have very little experience coding let alone scripting.  The book has example of Upstart scripts, but I was wondering if the language is Python?

So I guess my question is a general question to scripting...

If I were to focus my time in learning Python as well, would I be able to customize/utilize more of Ubuntu Server?  I'm not exactly sure what to learn/read as well to this.  I'm trying to broaden my horizons, and I've decided to experiment with Ubuntu Server.

Thanks for reading, your time, and your help.  :)

---

### Post by Barriehie on 2010-03-03
I would start with BASH, it's pretty powerful and you can do a lot with it in regards to getting your feet wet.  When you've reached the limits of what it can do then I'ld explore an actual programming language.  I'm not running a server so those people can better advise as to what would be best to learn.  I know I've got a lot going on with bash and some going on with gawk and 1 or 2 things going on with python.

Python programs will start with:
```

#!/usr/bin/env python
```

BASH scripts will start with:
```

#!/bin/bash
```

My 2 cents. 8)

---

### Post by terazen on 2010-03-03
You could really use whichever method you want and get the job done.  I've gotten the most use out of scripts in bash, but I'm no expert.  I will say that a lot of the scripting methods are really similar so whichever you practice on to start will make the next one you use easier to pick up.

Edit:  The first few paragraphs of this page seemed pretty informative.  [http://docs.python.org/tutorial/appetite.html](http://docs.python.org/tutorial/appetite.html)

I use bash because I find it's quick and simple for the types of things I do with it (backups, text file manipulation, cronjobs...)

---

