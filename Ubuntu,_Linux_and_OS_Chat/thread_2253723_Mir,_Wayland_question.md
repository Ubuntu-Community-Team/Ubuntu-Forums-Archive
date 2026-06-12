---
title: "Mir, Wayland question"
date: 2014-11-21
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-11-21
I know these are works in progress, but when they're done what will happen to things like Conky, xdotool, wmctrl, xprop, etc?

I got the impression that my window manager, Openbox, won't work in Wayland. I'll search for a link.

---

### Post by grahammechanical on 2014-11-22
Anything written to work with X will not work and that includes xdiagnose. Which leaves the way open for someone to write utilities to work with Mir and any Wayland compositor that comes along.

In Ubuntu on Mir the command startx will not be any good. Recovery mode will lose the FailsafeX option. There must be much more like that. I just hope that the developers of both MIr and Wayland compositors understand that people on forums like this need information about commands and logs so that we can help those who have problems.

I am not sure that developers are aware of just how easy some people find it to break the OS. Or how much they (the developers) need real people to try out their work and give feed back. 

Regards.

---

### Post by vasa1 on 2014-11-22
> **grahammechanical said:**
> Anything written to work with X will not work and that includes xdiagnose. ...
At the risk of sounding truly stupid would that mean that programs like Conky, wmctrl and xdotool won't work? I *suspect* they won't but just want to have someone competent say so explicitly.

---

### Post by /ADM on 2014-11-22
> **vasa1 said:**
> At the risk of sounding truly stupid would that mean that programs like Conky, wmctrl and xdotool won't work? I *suspect* they won't but just want to have someone competent say so explicitly.

Conky is built on the X Window System.  It won't work.

---

### Post by deadflowr on 2014-11-22
> **/ADM said:**
> Conky is built on the X Window System.  It won't work.

You can run conky with no gui, from a console.
So it isn't fully reliant on X.

---

### Post by /ADM on 2014-11-22
> **deadflowr said:**
> You can run conky with no gui, from a console.
So it isn't fully reliant on X.

True you can, but I would say that the majority run conky on their Desktop as a GUI.  Even I would never bother running it in a terminal, maybe if it was 1980 but not in 2014.

---

### Post by grahammechanical on 2014-11-22
If there is no X then commands and utilities that work with X will not work with Mir or any Wayland compositor. But there are many applications in Ubuntu. In fact the whole desktop environment and everything that follows runs on X. So, a lot of work has to be done to make sure all this stuff continues to work in Ubuntu on Mir.

I have heard that work is being done to develop a rootless X session. That is necessary for applications like Gimp and Libreoffice. It all takes time. And I have no idea what the Wayland developers are doing to solve these kinds of problems. So, I say nothing about that.

The important thing, whether a distribution uses Wayland or Mir, is that we get the full user experience that we are used to. Otherwise, any OS using Wayland or Mir will get no further than being an experimental curiosity. 

Regards.

EDIT:

> [COLOR=#333333][FONT=Ubuntu Beta]In reality though, certain legacy applications will not be able to transition away from X completely, and we will provide an in-session rootless X server that is integrated with Mir. It acts as an on-demand compatibility layer between legacy X applications and the session-level Unity/Mir instance.[/FONT][/COLOR]

[https://wiki.ubuntu.com/Mir/Spec](https://wiki.ubuntu.com/Mir/Spec)

"May you live in interesting times!" An old Arabic curse, so I have heard.

---

### Post by buzzingrobot on 2014-11-22
I haven't been following Mir that closely.  Will Unity 7 run on Mir?  Shuttleworth has indicated the desktop will default to Unity 7, for some period of time, with Unity 8 as an opt-in.

---

### Post by rrnbtter on 2014-11-22
Greetings,
@OP, I think your fears are valid with regard to loss of support for some applications. There is a lot to be gained by moving forward and the new direction is already showing up in the updates. Oddly one of my old customers lamented the loss of Picture it! in Windows 7. This professional photo minipulation program had some nifty pointers, arrows etc that could add to a photo. When the arrow was dragged into the photo a rotator would appear that let the user point the arrow at the desired object in the picture. This program was widely used by real estate appraisers. Since it was built on Explorer 6 it was dropped. Oddly it can be run on Linux under Wine with Explorer 6 loaded.  I hope you make out ok with your desired programs and the move forward. Its a wait/see. Good luck!

---

### Post by sffvba[e0rt on 2014-11-22
AFAIK there will always be a compatibility layer, xwayland and xmir isn't there?

---

### Post by vasa1 on 2014-11-22
> **rrnbtter said:**
> Greetings,
@OP, I think your fears are valid with regard to loss of support for some applications. ...  I hope you make out ok with your desired programs and the move forward. Its a wait/see. Good luck!
I hope so too. As Graham pointed out these are interesting times ... But those of us who can't code can only watch.

---

### Post by Sef on 2014-11-23
> [COLOR=#000000]But those of us who can't code can only watch[/COLOR]

Or learn to code.

---

### Post by vasa1 on 2014-11-23
> **Sef said:**
> Or learn to code.
And if you get to be a [top coder]("http://www.businessweek.com/articles/2013-04-10/silicon-valley-goes-hollywood-top-coders-can-now-get-agents") you needn't hang around forums ;)

---

### Post by /ADM on 2014-11-24
> **Sef said:**
> Or learn to code.

I wouldn't worry about learning to code, I would worry about the countless hours it would take to understand how to make correct changes to a rather large codebase 'and' getting those changes approved and merged.

If you have much of a life, it's not possible ;)

---

### Post by ibjsb4 on 2014-11-24
And on a bright note, Enlightenment has Wayland support and I expect to see some sort of X compatability.

---

