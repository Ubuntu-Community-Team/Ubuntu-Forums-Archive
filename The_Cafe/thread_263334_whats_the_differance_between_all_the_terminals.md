---
title: "whats the differance between all the terminals"
date: 2006-09-23
forum: The Cafe
---

### Post by Rule on 2006-09-23
hey everyone :D

i've been wondering what is different about all the terminals out there like gnome-terminal, eterm, aterm, xterm and all other other "popular" ones out there.

TIA

Rule

---

### Post by H.E. Pennypacker on 2006-09-23
I believe it's all about the features they have.  They all use the same backend (the command line...forgot what its called...bash?).  I sound silly right about now, so I'll let someone else answer the question.

I've really understood what bash is, and I am sure someone will provide an answer I won't understand.

---

### Post by bonzodog on 2006-09-23
There is essentially little difference between the terminals, except for some handle UTF-8 and some don't.

aterm, eterm, wterm just use different toolkits to render the terminal window and widgets. 

rxvt is the original power users terminal. uses gtk to render, and has a long line of switches and options to change how it presents. There is a UTF-8 compliant version called urxvt.

Xterm is the basic, bog standard terminal built just using the X toolkit. it has a few switches to allow how it presents, but cannot do translucency and is not UTF-8 compliant. I learnt this week that there is a version called uxterm, which is.

Gnome-terminal, Konsole, and Terminal for Xfce, are all graphically configurable, and can use different back ends (this option is usually in the 'advanced' section.). I currently have Terminal for Xfce using vt-utf8 for it's backend.

To get a list of the terms available to Linux, go to /usr/share/terminfo, and browse through the different subdirs. All this section does is provide the main terminals with the info to emulate other vt types if you need to change the way that bash handles code.

---

### Post by Bloodfen Razormaw on 2006-09-23
Of those I have used:

xterm - Weak, and the most bloated terminal.  Slow as a sloth.  Not very configurable, and what is configurable is difficult to configure.  The README for the source code says it all: Abandon all hope, ye who enter here.
rxvt - Similar to xterm.  Not especially powerful.  However, it is not nearly as bloated as xterm is.  An acceptable choice for a very light terminal.
aterm - The terminal for AfterStep.  Not especially powerful, but if you want something light and fast at any cost, this is a good choice.
gnome-terminal - Much faster than xterm.  Average features.  Easier to configure than xterm/rxvt/aterm.  Horrible internals, but it won't bother the user.
konsole - The most powerful that I am aware of.  Faster than all the above except aterm and maybe rxvt.  Easy to configure, and embeddable in other apps.  This would be my recommendation, as it approaches the light terminals in speed and memory use but offers many more features.
eterm - Pretty useless.  Focuses on looking good, and fails miserably.

---

### Post by Lord Illidan on 2006-09-23
There's also yakuake based on Konsole. It is a drop down terminal ala` Quake.. try it, mate, it is so convenient I have it installed immediately.. Just  press F12 and down it comes...

It is in the repos...so get cracking!

---

### Post by henriquemaia on 2006-09-23
> **Lord Illidan said:**
> There's also yakuake based on Konsole. It is a drop down terminal ala` Quake.. try it, mate, it is so convenient I have it installed immediately.. Just  press F12 and down it comes...

It is in the repos...so get cracking!

Nice tip. I didn't know of this console so I installed to test it. It's just great and also very handy. Thanks a lot!

---

### Post by jISh on 2006-09-23
> **Rule said:**
> hey everyone :D

i've been wondering what is different about all the terminals out there like gnome-terminal, eterm, aterm, xterm and all other other "popular" ones out there.

TIA

Rule
And for the record, bash is the Bourne Again SHell, in simple terms it's your command line.

---

### Post by Lord Illidan on 2006-09-23
Aye, and there are also others like fish, ash, etc...Wikipedia them...lots of nice info!

---

### Post by kerry_s on 2006-09-23
I use xterm and eterm,both are light weight and fast.

Xterm is your basic term and is in every distro because most apps are set up to use it by default. Depending on the WM it can be fast or slow, Most of the time it will be the fastest since it has nearly no bloat from extra features.

Eterm is also very fast but much more customizeable in the way of looks. it can be transparent,a different backgrounds everytime you open it, have all the decorations hidden...Here is a shot of six eterm's layered on top of each other with different setups ->

---

### Post by Rule on 2006-09-24
thanks for the replies guys :D i'm currently using aterm with transparent windows, also yakuake is quite nice if I have windows open on all my desktops and I dont want to close or minimize them :cool:

---

### Post by M7S on 2006-09-24
> **Lord Illidan said:**
> There's also yakuake based on Konsole. It is a drop down terminal ala` Quake.. try it, mate, it is so convenient I have it installed immediately.. Just  press F12 and down it comes...

It is in the repos...so get cracking!
Gnome users can use tilda instead. Also in repositories.

---

### Post by xmastree on 2006-09-24
'Scuse me butting in, but how can one terminal be more or less powerful than another?
Surely, they're only as powerful as the commands you type into them?

---

### Post by -Rick- on 2006-09-24
> **xmastree said:**
> 'Scuse me butting in, but how can one terminal be more or less powerful than another?
Surely, they're only as powerful as the commands you type into them?
Well to name a few...
* The looks of the terminal-app itself
* The text scrolling speed
* Features(tabs, bookmarks etc)

---

### Post by sumguy231 on 2006-09-24
Wow, yakuake was a great suggestion. I had tried tilda, but it got in the way and wasn't as easily customizable.

---

### Post by henriquemaia on 2006-09-25
> **M7S said:**
> Gnome users can use tilda instead. Also in repositories.
Another great tip. Thanks!

I prefer tilda to yakuake.

---

### Post by 3rdalbum on 2006-09-25
Eterm is a great choice if you're running Enlightenment.

I would just like to say that your choice of X terminal program itself isn't anywhere near as important as your choice of shell (the backend). Most people can't really tell the difference between the Xterms, but some of the shells are very different and very useful. I'm a Fish man myself.

---

