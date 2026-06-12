---
title: "Getting started"
date: 2015-02-06
forum: Ubuntu Application Development
---

### Post by hmiersch on 2015-02-06
Hi. 
I want to get started in application programming and resurrect the projects I put on ice when I decided to switch from OSX to Ubuntu. Problem is, I don't know where to start. 
I have eclipse installed along with the CDT because I'm not wild about java. 
Needless to say I'm talking about writing GUI apps, not just command line stuff.
So, how do I get started? Can someone point me in the right direction? Thanks.

Edit: forgot to mention I want to write apps for Ubuntu AND android, including at least one library that works on both platforms.

---

### Post by TheFu on 2015-02-06
Android is java, a bastardized version of java, so you'll be writing android apps in that dialect.

For Ubuntu, it really depends on which language you want to use. Personally, I'd avoid using eclipse - bloated, slow, java, but you'll use whatever editor you like.  Unix systems are development environments. It was designed that way, so you just need to pick a language and get started.  Linux is extremely flexible, so you can pick almost any language you like to program. If you want speed and to run on Win/Mac/Linux platforms, then picking something like Qt or GTK+ as the cross-platform libraries would be a good start. Then you can pick from any language supported on the platforms you want that having bindings for the library.

Oh - and there are tools to build non-java applications on Android, but these are all toys in comparison to a native java application. If that is good enough - I'd ask on the android dev sites what those folks recommend. Android will be the limiting OS, not Ubuntu/Linux.

---

