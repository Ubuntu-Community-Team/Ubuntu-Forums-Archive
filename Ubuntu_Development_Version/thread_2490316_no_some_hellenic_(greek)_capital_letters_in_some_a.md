---
title: "no some hellenic (greek) capital letters in some applications"
date: 2023-08-29
forum: Ubuntu Development Version
---

### Post by Claus7 on 2023-08-29
Hello,

for ~two days now, I noticed that I cannot type some hellenic (greek) capital letters in text editor, libreoffice, gnome-calendar, gnome-terminal, application finder to name but a few. The letters affected are not all yet: &#961;, &#965;, &#968;, &#950;. I can bypass this by pressing shift+letter.

Regards!

---

### Post by TheFu on 2023-08-29
Are the required characters part of the vi/vim digraph set?
[https://vim-jp.org/vimdoc-en/digraph.html](https://vim-jp.org/vimdoc-en/digraph.html) has a table with hundreds of symbols.

---

### Post by Claus7 on 2023-08-30
Hello,

> **TheFu said:**
> Are the required characters part of the vi/vim digraph set?
[https://vim-jp.org/vimdoc-en/digraph.html](https://vim-jp.org/vimdoc-en/digraph.html) has a table with hundreds of symbols.

thank you for your response. Checking history of synaptic I can spot an update of vim just yesterday. I think that I noticed the issue prior to that date. On the other hand language-pack-el was updated one day before.

I was able to spot the letters in the link you provided, yet there it has the entire hellenic alphabet. Does vim affect all these programs? I mean that something inside vim can affect e.g. gnome-calendar? 

It should be an update, because things were working normally. I should mention that browsers do not face such an issue. For example here I can type the capital letter of &#968; which is &#936; without having to press shift, just pressing Caps Lock. 

Is this digraph vim or language package related?

Regards!

---

### Post by TheFu on 2023-08-30
I'm sorry. I missed that this sub-forum is for 23.10 alpha code. My mistake.

Vim digraphs are self-contained, provided the file system supports UTF8.  Sometimes my practical side gets the better of me.  They also work over a remote terminal without any GUI, which is how I mostly work. Obviously, most users don't work that way, so vim really isn't a solution for them. Sorry to have wasted your time.

---

### Post by Claus7 on 2023-08-30
Hello,

> **TheFu said:**
> I'm sorry. I missed that this sub-forum is for 23.10 alpha code. My mistake.

Vim digraphs are self-contained, provided the file system supports UTF8.  Sometimes my practical side gets the better of me.  They also work over a remote terminal without any GUI, which is how I mostly work. Obviously, most users don't work that way, so vim really isn't a solution for them. Sorry to have wasted your time.

thank you for your explanation and response. Not at all, I was able to find out something new. Now I think that things are narrowed down to package-el. I will try to keep an eye on that package and see if this is indeed the issue, yet shouldn't browsers affected as well? We will see...

Regards!

---

### Post by TheFu on 2023-08-30
> **Claus7 said:**
>  thank you for your explanation and response. Not at all, I was able to find out something new. Now I think that things are narrowed down to package-el. I will try to keep an eye on that package and see if this is indeed the issue, yet shouldn't browsers affected as well? We will see...

I think 95% of the language handling is in the console language packs and the GUI toolkits - GTK+ or Qt - depending on the system.
However, Mozilla uses their own cross-platform GUI toolkit, so it makes sense when that doesn't "just work" with the settings that work fine for all the Gnome stuff.  I don't/won't load chrome onto any of my systems, ever, so can't say which GUI toolkit is used there.  Perhaps looking at the package dependencies would help?

Vim is self-contained. No GTK+ or Qt dependencies, at least for the console version.  I've only used gvim by mistake. It behaves "wrong".

---

### Post by Claus7 on 2023-08-30
Hello,

> **TheFu said:**
> I think 95% of the language handling is in the console language packs and the GUI toolkits - GTK+ or Qt - depending on the system.
However, Mozilla uses their own cross-platform GUI toolkit, so it makes sense when that doesn't "just work" with the settings that work fine for all the Gnome stuff.  I don't/won't load chrome onto any of my systems, ever, so can't say which GUI toolkit is used there.  Perhaps looking at the package dependencies would help?

Vim is self-contained. No GTK+ or Qt dependencies, at least for the console version.  I've only used gvim by mistake. It behaves "wrong".

no chrome for me as well, so I cannot tell. vim behaves the same as the rest: meaning it doesn't show correctly the capital letters. Mantic still has a long way till the final release, so I hope that it is fixed. 

The last console package installed in my system according to synaptic is gnome-console at 30/8 and 16/8 and 12/8.

Other console packages are too old to mention.

Regards!

---

### Post by TheFu on 2023-08-30
There should be console language packs so that errors for admins are in their native language, not always English.  One of them also picks the correct keyboard layout, since keyboards are different around the world.  There's always been 2 different keyboard and language settings.
1) consoles
2) GUIs - usually X11, but with Wayland, I have no idea how that handles the different keyboards and languages.

---

### Post by Claus7 on 2023-08-31
Hello,

I suppose that this might be part of a big change, since there was an issue about keyboard picking up during installation as well. See how it gets.

Regards!

---

### Post by Claus7 on 2023-09-02
Hello,

testing anew in a brand new installation iso, I no longer face such an issue. Gnome is now 45 beta.

Regards!

---

### Post by Claus7 on 2024-01-03
Hello,

for some time now this issue has reappeared under mantic. Checking noble development though, this issue is fixed anew.

Regards!

---

### Post by jbicha on 2024-01-07
Yes, this sounds like [LP: #2035076]("https://launchpad.net/bugs/2035076")

---

### Post by Claus7 on 2024-01-08
Hello,

> **jbicha said:**
> Yes, this sounds like [LP: #2035076]("https://launchpad.net/bugs/2035076")

thank you for your response. I tested my ubu box and my report is in the link you provided. Just to mention that indeed, this issue is observed under ubuntu mantic wayland at the moment.

Regards!

---

### Post by Claus7 on 2024-01-14
Hello,

the proposed solution from the link provided concerning the bug, solves anew the issue.

Regards!

---

