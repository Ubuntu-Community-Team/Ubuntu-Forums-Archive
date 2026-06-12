---
title: "Moving the graphical toolkit into a separate process"
date: 2008-06-07
forum: Ubuntu Brainstorm
---

### Post by vmlinuz on 2008-06-07
Author: Eduard Christian Dumitrescu <inventatoru_AT_yahoo_DOT_ca> (GPG key 7B9C1EA0)


**MOTIVATION**

    As time goes by, people are having more and more of a hard time running GNOME (or KDE) on low-spec computers. It turns out that most of the wasted memory is used up by the graphical-toolkit related libraries [1]. The situation is certainly not getting better, a simple test shows us that GNOME's calculator application (gcalctool) consumes *seven* megabytes of RAM [2]. I strongly believe we should implement the graphical toolkit as a separate process.

    First, (Ubuntu) Linux is supposed to be as accessible as possible to all users. I personally have a 320MB-Pentium 3 at home, and if I start up more than five applications (excluding OpenOffice), the RAM gets filled and I start hearing a desperate kernel swapping pages back and forth (yes it's a pretty noisy hard-disk). Starting an application on that 733-MHz computer takes *a few seconds*. All that time wasted on initializing and loading things that were already in memory. It's not because the kernel is smart about mmap()'s that toolkit programmers should be careless. By all this, I am simply drawing attention over the fact that we don't want our beloved Linux to become a bloated resource-hog as some of our competitors. Moving everything that is graphics-related into a separate process that would do all the drawing would be a great solution, because the applications wouldn't have to use up all that memory for libraries. That would be perfect for 98% of applications that just need to draw buttons and text entries. For the other 2%, shared memory is perfect. 

    Second, modularity. The graphical toolkit server can use any output method, may that be X11-OpenGL, X11-XRENDER, GTK2, QT, DirectFB, Microsoft Windows or Mac's current API; the client won't even have to know about it. Moreover, the client may even be on another computer.

    Third, power. The developer can do almost anything, including the migrating a graphical application from one display/computer to another, with different OSes (probably with some limitations), implementing multi-pointer capabilities, and other dreamy stuff. Also, no more GTK-related headaches - the programmer doesn't need to spend hours on designing an application where all widgets must have distances between them that are aesthetically pleasing. This new toolkit would have, from the developer point of view, just a little more abstractization than GTK. 

    Lastly, speed. By using this toolkit, a graphical application will probably start as fast as a shell utility.

    Think about it.


**IMPLEMENTATION DETAILS**

I am going to refer to the toolkit as GTK3, to the client library as libGTK3 and to the server as "the GTK3 server".

The GTK3 server exposes itself through D-BUS. The server also must accept connections through a standard UNIX socket.

When a GTK3 application starts up, it connects to the server by obtaining the (file) name of its UNIX socket through D-BUS.

Then, every API call, for example, the equivalent of gtk_set_label(), would actually be a macro that expands to something along the lines of gtk_widget_set(widget, "label", TYPE_STR, "text"). For greater data transfers, like pixmaps or other, shared memory may be used. OpenGL-in-GTK may be done several different ways, which remain to be implemented.

All events, property changes, pretty much everything will be done by using the socket connection to the server. (idea: use shared memory with a circular buffer).

This document is not in any way complete, and simply is a hint of the future work.


[1] [http://live.gnome.org/MemoryReduction](http://live.gnome.org/MemoryReduction)
[2] [https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/238159](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/238159)



If you have any ideas, comments, questions, just post here. I'll be happy to answer you.

---

### Post by sas on 2008-06-07
I don't understand what the difference is in terms of memory between the current approach of having one shared gtk library that is loaded into memory once and shared between all applications and having one GTK server that is communicated to by many clients.

Have you asked any of the developers of GTK what they think of your plan? :)

---

### Post by vmlinuz on 2008-06-07
The difference is that with my approach, the overhead per application is probably less than 200 KB, since a lot of data always stays on the server and therefore is shared among all applications.

(And no, I'm kind of afraid of asking them)

---

### Post by vmlinuz on 2008-06-07
Here's my point: even if at server start-up, six megabytes will be consumed for fonts and pixmaps and everything, after that, there will be almost no overhead per application i.e. when you start a GTK hello world, probably no more than 200 KB will be consumed.

---

### Post by angustia on 2008-06-07
there is already something like that: [gtk-server]("http://gtk-server.org/intro.html")

but, it uses one server for one application.

or, something like "server side widgets", like in [Y windows system]("http://www.y-windows.org") (seems a dead project).

you are blaming on the toolkit for the bloat of applications, so you will have to prove your point with practical examples before trying to convince some GTK developer, like this:
[LIST=1]
[*]make a prototype of your server (maybe hack the gtk-server code to make it multiclient)
[*]pick some representatives applications and hack them to use your serve
[*]look at the resource usage of the whole system when using your server and without it. (individual usage shown in top doesn't count, because many of those MB are shared)
[/LIST]

You should also have in mind that a shared gtk-server becomes another point of failure (along with the X server). And, it should have to be painless to change existing applications to use this system, ideally, just relinking from "libgtk" to "libremote-gtk". 

In my opinion, even if you prove that system to be better and painless to use, it doesn't worth the risk of crashing all applications cause by one of them. At this days the most used application is the web browser, so if you get to reduce the memory usage of the toolkit for your low memory computer, the browser and all its javascript, flash, animations and plugins will force you to buy more RAM anyway.

excuse my english

P.S.: a remote, http based, scripted gtk-server seems a interesting project.

---

### Post by vmlinuz on 2008-06-07
> **angustia said:**
> there is already something like that: [gtk-server]("http://gtk-server.org/intro.html")
That's interesting but it's not what I want.


> 
or, something like "server side widgets", like in [Y windows system]("http://www.y-windows.org") (seems a dead project).

Interesting but that thing is just one big security hole.


> you are blaming on the toolkit for the bloat of applications
I *am* blaming the toolkit because it consumes a lot of memory *per application*.


> so you will have to prove your point with practical examples before trying to convince some GTK developer, like this:
* make a prototype of your server (maybe hack the gtk-server code to make it multiclient)
* pick some representatives applications and hack them to use your serve
Nope, I'd rather rewrite from scratch anything that's graphical. My purpose is not to stay compatible with GTK2, but rather create something better. (see below for more)


> * look at the resource usage of the whole system when using your server and without it. (individual usage shown in top doesn't count, because many of those MB are shared)
It's easy: to see the RAM freed by my "magic solution", just count the number of running GTK2 applications and multiply the number by 10 MiB.


> You should also have in mind that a shared gtk-server becomes another point of failure (along with the X server). 
GTK2 and X.org (almost) never crash - why would my server crash? (see below for more arguments)


> And, it should have to be painless to change existing applications to use this system, ideally, just relinking from "libgtk" to "libremote-gtk". 
Lemme see... no. GTK2 applications stay GTK2 applications. For GTK3 applications, the code is simply different - rewriting is required.


> In my opinion, even if you prove that system to be better and painless to use, it doesn't worth the risk of crashing all applications cause by one of them. At this days the most used application is the web browser, so if you get to reduce the memory usage of the toolkit for your low memory computer, the browser and all its javascript, flash, animations and plugins will force you to buy more RAM anyway.
The browser's a different story. His problem is that libc6's malloc() uses sbrk(), instead of using mmap(). The result is that the memory gets fragmented and never gets freed. And my 320MB-computer works perfectly fine when only Firefox 3 is running. Even with ten tabs opened.


> excuse my english
No problem :).


> P.S.: a remote, http based, scripted gtk-server seems a interesting project.
It may be one of the future input front-ends of my GTK3. We'll see...



If you want a simple example of this useless overhead, simply see how much vmData memory (/proc/*/status) gcalctool uses. It uses SEVEN megabytes. Look at mixer_applet2's memory usage. TWENTY megabytes for an application that does almost nothing! Excuse me, but it's running out of style!


For a little example of my solution:

* GTK3 server is running happily.
* An application starts up. It tries connecting to GTK3.
* GTK3 creates a new thread who's only task is to respond to the client's requests.
* The application wants to create a window. It sends "new:window(7='Application Title');" to the server. (the actual protocol won't ever look like that, this is just for the demonstration)
* The server talks to Xserver and creates a new window, and sets WM_NAME and WM_ICON_NAME to 'Application Title'.
* The applications tells the server it wants to listen on mouse click events on the window.
* Guess what happens next? Yes, the user clicks the window.
* The server sends the event to the application.
  ... a few hours later ...
* The application crashes or the user gets tired of clicking and does Ctrl-C.
* The server senses the dead connection, closes the window, and cleans up everything.


GTK3 features:

* Multiple backends, including animated OpenGL (how's that for a change?).
* Less or almost no memory overhead per application/client.
* After server is started, memory usage stays pretty much the same.
* Easy API - although Glade is a great thing, it could be a lot better. The developer doesn't care and does not want to care about fancy stuff like aesthetically spacing widgets. He/She wants to _rapidly_ write an application that _works_ and that _looks great_.
* Faster response on systems with OpenGL - all drawing done by GPU.
* No plug-in or component loading into the server, ever (to answer your stability-related questions). The code running on it must be crystal-clear and perfectly pure - no bugs allowed.


Thank you for your response.

---

### Post by daengbo on 2008-06-08
You have too many logical errors to mention here. Foremost is that your assessment of the memory requirements is all wrong. Shared libraries are SHARED. If you have only one GTK+ application running (say the calculator), it may take up 7MB, but the cost of adding the calculator is much smaller.

The bottom line -- do better memory profiling before blasting and use a single toolkit for your desktop. Choose a GTK+ desktop and all GTK+ applications (keeping the Gnome libraries out will save memory) or choose an all-KDE desktop/app combination. Either of these options will keep your memory usage out of swap.

If one of your apps is Firefox, forget keeping within 320MB. Replace with Konqueror or Epiphany/Webkit.

---

### Post by smartboyathome on 2008-06-08
> **daengbo said:**
> You have too many logical errors to mention here. Foremost is that your assessment of the memory requirements is all wrong. Shared libraries are SHARED. If you have only one GTK+ application running (say the calculator), it may take up 7MB, but the cost of adding the calculator is much smaller.

The bottom line -- do better memory profiling before blasting and use a single toolkit for your desktop. Choose a GTK+ desktop and all GTK+ applications (keeping the Gnome libraries out will save memory) or choose an all-KDE desktop/app combination. Either of these options will keep your memory usage out of swap.

If one of your apps is Firefox, forget keeping within 320MB. Replace with Konqueror or Epiphany/Webkit.

Epiphany/Webkit doesn't have nearly enough features as a normal web browser should, but FF3RC2 only takes up less than 100 megs of memory on my arch system.

---

### Post by bruce89 on 2008-06-08
> **smartboyathome said:**
> Epiphany/Webkit doesn't have nearly enough features as a normal web browser should...

Surely then it's perfect for GNOME.

Maemo does something like this proposal, it has a process called maemo-launcher which most programs forks off to save memory.

---

### Post by smartboyathome on 2008-06-08
> **bruce89 said:**
> Surely then it's perfect for GNOME.

Not quite yet. They haven't done cookies primarily, but also the plugins don't work with it yet.

---

### Post by bruce89 on 2008-06-08
> **smartboyathome said:**
> Not quite yet. They haven't done cookies primarily, but also the plugins don't work with it yet.

Saying as it's planned to have WebKit only for 2.24, this will be done soon. If not, it'll be 2.26.

---

### Post by smartboyathome on 2008-06-08
> **bruce89 said:**
> Saying as it's planned to have WebKit only for 2.24, this will be done soon. If not, it'll be 2.26.

Yes, but it isn't done yet, that is why I wouldn't recommend it quite yet. :(

---

### Post by vmlinuz on 2008-06-08
Thank you for your answer, daengbo.

You *could* have read all that has been said before, but I don't mind re-clarifying.

> Shared libraries are SHARED. If you have only one GTK+ application running (say the calculator), it may take up 7MB, but the cost of adding the calculator is much smaller.
Okay, a little experiment. Follow me through this, okay?
[LIST]
[*]Start a terminal
[*]Become admin:
```
$ sudo bash
```
[*]Drop all fs caches in order to have absolutely correct results
```
# echo 1 > /proc/sys/vm/drop_caches
```
[*]We no longer need admin rights:
```
# exit
```
[*]Now start up five gcalctool's
[*]Go back to your terminal, and type in "cat /proc/meminfo | grep MemFree"
[*]Close one of the gcalctool's
[*]Re-execute "cat /proc/meminfo | grep MemFree"
[*]Repeat for each gcalctool remaining
[/LIST]
I am aware that I could have written a script that does that, but that would've ruined your fun into realizing all by yourself that the simplest GTK application takes seven megabytes of overhead.

My results: 
```
eduard@eduard-laptop:~$ cat /proc/meminfo | grep MemFree
MemFree:        **154876 kB**
eduard@eduard-laptop:~$ cat /proc/meminfo | grep MemFree
MemFree:        **163192 kB**
eduard@eduard-laptop:~$ cat /proc/meminfo | grep MemFree
MemFree:        **171368 kB**
eduard@eduard-laptop:~$ cat /proc/meminfo | grep MemFree
MemFree:        **179700 kB**
eduard@eduard-laptop:~$ cat /proc/meminfo | grep MemFree
MemFree:        **187892 kB**
eduard@eduard-laptop:~$ cat /proc/meminfo | grep MemFree
MemFree:        **196068 kB**
```


Thank you for your answer.

---

### Post by daengbo on 2008-06-08
Thanks for the info. It's nice except that MeMFree isn't accurate.

[Read]("http://elinux.org/Runtime_Memory_Measurement") and [learn]("http://www.ibm.com/developerworks/linux/library/l-linux-memory.html").

IF you're still not convinced, put your ideas up on [http://live.gnome.org/ThreePointZero]("http://live.gnome.org/ThreePointZero") and get your ideas accepted.

---

### Post by vmlinuz on 2008-06-09
Please do your homework: in neither of your documents it says that /proc/meminfo is inaccurate. Please read your own documents. 

And I know /proc/[0-9]*/* are not perfectly accurate, why do you think I used MemFree in the first place?

MemFree is about physical memory, so the kernel does correct bookkeeping in over that.


Second, even if it was *inaccurate*, eight or six megabytes per GTK application are still far too much.


But, thank you for your posting.

---

### Post by daengbo on 2008-06-09
> **vmlinuz said:**
> Please do your homework: in neither of your documents it says that /proc/meminfo is inaccurate. Please read your own documents. 

Are you trolling?
> Unfortunately, the existing memory measurement techniques do not give a 100% accurate accounting of memory pages (since some pages are counted more than once by some measures). See Accurate Memory Measurement - that page describes techniques (and patches) which can be used to measure the runtime memory more accurately. 
This **first line** of the article I gave you states quite clearly that advanced techniques and patches need to be used to give *more accurate* (not even fully accurate) runtime memory usage.

In fact, the memory tools in Linux are quite famous for their inaccuracy. MemFree measures the amount of free memory ... sure, but it also includes the aggressive caching and buffers the kernel uses. These are unnecessary and used simply to speed up operation. The kernel will generally use as much physical memory as it has available for this type of thing.

Go over to ThreePointZero and put your ideas up for the devs to look at. Your plan may have merit. Talking about memory management in this simplistic way will make them dismiss you, though.

I don't intend to reply further.

Cheers

---

### Post by vmlinuz on 2008-06-10
> Are you trolling?
[...]
This first line of the article I gave you states quite clearly that advanced techniques and patches need to be used to give more accurate (not even fully accurate) runtime memory usage.
I am extremely sorry for this inconvenience; I misread the article - again, I am very sorry, I hope you will forgive me, and I will try not to repeat the same mistake ever again.


Yes, as you said, I am being simplistic about this memory measurement in this case - let me explain with an example: after I start an exact number of gcalctool's, my system will inevitably start swapping pages - that explanation may look a little dumb, but by that I am only trying to prove that a GTK+ application requires too much memory. If anyone can *prove* I'm wrong and that gcalctool (or pretty any normal GTK+ application) takes only 400-500 KB of memory, hats off to that, and I drop any claim about GTK+'s memory requirements.


Also, I decided to (temporarily) rename my project to "Icky", not to create confusion about "gtk3", since GNOME/GTK+ do not endorse my project in any way.

---

### Post by angustia on 2008-06-10
you're blaming a whole project (dated back to 1997) for something you see in one specific program, and you don't seem willing to make any further investigation about the causes. 

What if it's gcalctool logic the memory waster? 

what if there is some memory pool used inside? (if they use one, those 7 Mb could be the ammount needed for some specific need and not most of the time)

You're talking to start a project based on those claims --> don't expect people to help you without proofs. Your complains are about memory usage, your post is about using some kind of toolkit server and at the end you started talking about starting a new toolkit, those are three different things.

if you are concerned about memory waste, identify the exact places where those wastes are.

if you think a centralized toolkit server is better design, start hacking gtk-server and then show us what you got.

if all you want is yet another toolkit, it's on you to make it, when you have something barely usable you can expect others to join, and nothing more. 


and please, read [this]("http://mooreslore.corante.com/archives/2004/10/26/linus_calls_hurd_dead.php")

excuse my english, again

---

### Post by vmlinuz on 2008-06-10
> **angustia said:**
> you're blaming a whole project (dated back to 1997) for something you see in one specific program, and you don't seem willing to make any further investigation about the causes. 

What if it's gcalctool logic the memory waster? 

what if there is some memory pool used inside? (if they use one, those 7 Mb could be the ammount needed for some specific need and not most of the time)

You're talking to start a project based on those claims --> don't expect people to help you without proofs. Your complains are about memory usage, your post is about using some kind of toolkit server and at the end you started talking about starting a new toolkit, those are three different things.

if you are concerned about memory waste, identify the exact places where those wastes are.

if you think a centralized toolkit server is better design, start hacking gtk-server and then show us what you got.

if all you want is yet another toolkit, it's on you to make it, when you have something barely usable you can expect others to join, and nothing more. 


and please, read [this]("http://mooreslore.corante.com/archives/2004/10/26/linus_calls_hurd_dead.php")

excuse my english, again

I do not currently have the time to recompile stuff and run debuggers and profilers, sorry. If anyone wants to do it, go ahead, I'd be happy to know precisely what the problems are.

I decided to write a new toolkit; it will have many more features than just a low memory and CPU consumption...

Even though answering to all messages here is a little counter-productive for me, I don't really mind. Right now I am working on writing the 0.01 version of my toolkit, temporarily codenamed "Icy" [https://launchpad.net/icy](https://launchpad.net/icy). I might want to put up a wiki or a forum or something in the near future in order to receive suggestions from people. And yes, it will be a new API, different than GTK2.


And your english is just fine :)

---

