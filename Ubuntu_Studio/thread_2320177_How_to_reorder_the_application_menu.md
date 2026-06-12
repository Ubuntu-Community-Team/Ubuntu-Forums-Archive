---
title: "How to reorder the application menu"
date: 2016-04-11
forum: Ubuntu Studio
---

### Post by HARARCA on 2016-04-11
Hi everyone,

Even if my question is more XFCE specific, I wanted to ask here since Ubuntustudio have some tweaks in the applications menu.

I wanted to know how can I change the structure of the applications menu. After some research I've find out that there are three main types of files to manage the menu: .menu, .directory and .desktop

As far as I understand there must be a .menu where the structure is written in XML format but I couldn't find it. Just some template files to create a custom one. I don't want to build the whole menu. Just move some items and the GUI only let me to change the order of the items in the same level.

Thanks in advance!

---

### Post by ajgreeny on 2016-04-11
Either **alacarte** or **menu-libre** can do that I think.  Look for **Main-menu** or **Menu-editor** in the menu you should already have for them, though you may need to install alacarte if you want to try that.

I tend to use alacarte for both the standard applications-menu and the whisker-menu in 14.04, simply because I'm used to it.

---

### Post by HARARCA on 2016-04-12
Hi ajgreeny!

Thank you very much for your answer!

Alacarte is already installed in Ubuntustudio. That's what I meant with "GUI". I've just tried menulibre and I could move items through the categories and directories, something that I couldn't with alacarte. The problem was that it rebuilt the whole menu and hide all the custom directories that come with Ubuntustudio like "Audio production" or "Graphic Design", so I had to recover the default values with alacarte.

If it can help, I tell you how to came this idea. I installed SuperCollider from Ubuntu Software Center, and the icon appears under the "Media Playback" category and I wanted it to be under the custom "Audio Production".

I know that it's not a big deal to organize the menu, but since I'm a linux noob I want to play with it in order to know and understand better the this awesome OS. That's why I prefer to mess with files rather than using graphical applications.

Thank you once more!

---

### Post by Chalisque on 2016-04-22
The initial version of this post is in quotes at the bottom. It was starting to look like a rant, which is not what I intend. I've left it there for those who want to read it, and tried to produce a nicer version above.

Context:
I am very keyboard centric, and like environments where I can do most things from the keyboard, and where similar tasks are accomplished in similar ways. I prefer one well thought out menu paradigm which, whilst possibly suboptimal for tasks like the 'start menu', means I only have to learn one paradigm for doing a large number of tasks. The efficiency gained in doing this, for me, outweights 'local optimality' achieved by having a 'start menu' paradigm optimised for that task, but different than other menus. Once I understand a simple menu (as I have since Windows 2), I find it annoying to have to learn a new paradigm for accomplishing the same task, with minimal increase in efficiency.

AboutMe:
I should add that like some, I have an autistic spectrum condition, and anxiety issues. Minimising anxiety of using a computer is one reason I dislike Windows, and the ease I found with previous ubuntu studio releases, and xfce, along with enough decent multimedia stuff working out of the box, was what converted me to it as my main platform. Just putting across how these 'computer induced anxieties' mean, in raw, often comes out like a rant.

MainPoint:
I would like to modify the 'start menu' plugin (Whiskers). I would like to be able to do this as easily as possible. 
Basic questions then are:
1) which package (and is there an easy way to find out the appropriate package)?
2) what commands are necessary to get a working build environment?
3) how to save the 'as installed' version so I can try a modified version and revert?
Please bear in mind the point regarding 'autistic condition and anxiety': just 'working it out' often causes sufficient frustration that it is necessary to give up and do something else.


[ In my imagination, this should be as simple as having a 'modify start-menu' command, which produces a working build environment somewhere, from which I can build and then install atop the original (so that upon removal, the original is restored). I know this isn't how it works at present. ]

initialVersion = "Slightly related, I have just installed 16.04 (in a VM at first). I am very keyboard centric, and loved how accessible ubuntustudio and xfce are from a keyboard. For me, this Whiskers menu is a regression: with a simple menu, I can bring it up with super-Esc (custom shortcut), then just use cursor keys and return. It would be nice to add keyboard shortcuts to that. The new Whiskers is not as keyboard-accessible as before. Quick question: how hard is it to reprogram on a fresh install of ubuntu studio? One trouble I have quite a bit with ubuntu is getting working build environments for packages (e.g. "apt-get build-dep gimp; apt-get source gimp" does not end up with something where 'configure; make' works). The other issue I have more and more with modern UI ideas is that, whilst visually intuitive, when doing things from the keyboard, each works in a different way. That means much more learning. I keep trying to get into UI programming, but find the difficulty of getting a working build environment excessive (and the frustration results in my doing something else instead)."

---

