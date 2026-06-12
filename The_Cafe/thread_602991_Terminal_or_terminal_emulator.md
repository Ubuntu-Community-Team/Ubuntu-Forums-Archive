---
title: "Terminal or terminal emulator?"
date: 2007-11-04
forum: The Cafe
---

### Post by voteforpedro36 on 2007-11-04
I was just wondering. What is the difference between a terminal and a terminal emulator? I searched, and only the difference between a terminal and console.

And examples of each, if you don't mind ;).

---

### Post by ofb on 2007-11-04
Off the top of my head, a terminal is the end of a line. So, back in the day when the computer was a mainframe serving many user accounts, what you'd be sitting at with your keyboard and display would be a terminal.

A terminal emulator is when you're using a computer (a turing machine) to provide the function of a terminal in software. This usage would typically come up because the computer would be 'imitating' a particular type of terminal in order to communicate with the mainframe.

A very popular terminal is/was the VT100. So if I telnet right now to the server of the local freenet (if they still exist) I'd be using VT100 emulation.

[http://en.wikipedia.org/wiki/Vt100](http://en.wikipedia.org/wiki/Vt100)

That kinda help?

---

### Post by voteforpedro36 on 2007-11-04
Yeah, it kinda helps. So, can you go and download a terminal, as opposed to a terminal emulator? And when I go to gnome-terminal, that is a terminal emulator?

---

### Post by ssam on 2007-11-04
most of the time people use the terms interchangably

the term virtual terminal, or VT is sometimes used. I think strictly speaking those are what you get if you do CTRL+ALT+F1 to F6. but i might be wrong there..

---

### Post by p_quarles on 2007-11-04
> **voteforpedro36 said:**
> Yeah, it kinda helps. So, can you go and download a terminal, as opposed to a terminal emulator? And when I go to gnome-terminal, that is a terminal emulator?
Gnome-terminal is, yes, a terminal emulator. 

Like ssam says, the terms get used more or less interchangably. My understanding is that (if you want to get really technical) the contemporary equivalent of a straight up terminal would be the keyboard, monitor and mouse. 

I say that because after I followed ofb's link, I did a little further reading. The "terminal" is basically the human-machine interface. It wasn't actually a computer itself, since it didn't do any processing, it just allowed you to interact with the computer. Thin clients are a very similar kind of machine to what was originally called a terminal.

Also, I believe that "vt" stands for "video terminal." Again, this terminology is outdated now, but refers to good ol' days when many computers required you to use switches or punch cards to interact with them.

---

### Post by ofb on 2007-11-04
> **p_quarles said:**
> the terms get used more or less interchangably.

Exactly. The distinction between hardware and software just isn't relevant any more. The use of two terms is a holdover from an overlap period when we had both dumb terminals and computers running software to emulate dumb terminal functions.

So no, *technically* you cannot download a terminal - that would be a terminal emulator insomuch as there is any distinction between the two terms. But for all practical purposes today you can go ahead and just say "terminal".

The only thing that would be incorrect usage would be to look at a real VT100 hardware terminal in a museum and call it a "terminal emulator". It's not - it's a real, pure, terminal.

 
> Also, I believe that "vt" stands for "video terminal." Again, this terminology is outdated now, but refers to good ol' days when many computers required you to use switches or punch cards to interact with them.

Let us not forget paper scrolls. There's a long period of keyboard with essentially a typewriter running accordian paper to display your "CLI" -- no video. The ScrLk key got a lot more use in those days.

[http://www.the-adam.com/adam/rantrave/ibm_360.jpg](http://www.the-adam.com/adam/rantrave/ibm_360.jpg)

---

### Post by HermanAB on 2007-11-04
Well, the distinction faded, because DEC went out of business and you cannot buy terminals anymore. 

A good example of turning old PCs into terminals is LTSP and Edubuntu.

---

### Post by FuturePilot on 2007-11-04
> **ssam said:**
> 

the term virtual terminal, or VT is sometimes used. I think strictly speaking those are what you get if you do CTRL+ALT+F1 to F6. but i might be wrong there..

You are absolutely correct! ;)

---

### Post by meestahp on 2009-08-26
> **ofb said:**
> 
[http://www.the-adam.com/adam/rantrave/ibm_360.jpg](http://www.the-adam.com/adam/rantrave/ibm_360.jpg)

Haha, See there, you can see the effects of the man typing the umount command. :lolflag:

---

### Post by overdrank on 2009-08-26
> **meestahp said:**
> Haha, See there, you can see the effects of the man typing the umount command. :lolflag:

[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

