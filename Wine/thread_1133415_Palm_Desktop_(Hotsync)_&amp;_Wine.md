---
title: "Palm Desktop (Hotsync) &amp; Wine"
date: 2009-04-22
forum: Wine
---

### Post by sloppyc on 2009-04-22
I've got a Palm Centro, and I'd like to be able to sync it while in Ubuntu.  I had no problem installing the software, but when I try to sync via USB, nothing happens.  There's no indicator from the Hotsync application (it seems to be running nicely enough judging by the icon on the panel), and the phone gets no response and times out.

I've searched around and even posted about this at treocentral.com, but there don't seem to be (m)any Linux users there.

Running 8.04 LTS on the machine in question, but that may change if 9.04 plays nicely with my hardware (8.10 wouldn't, but I am running it on another machine that I also wouldn't mind syncing with my phone).


EDIT:  Scratch that.  In 8.04 Hotsync seems to crash every time I click the icon on the panel.  I'm not booted into 8.10 at the moment, so I can't check compatibility there.  I don't see a reference to my phone in /dev when I press the button on the cable, either.  Shouldn't it appear somewhere?  I was trying to follow these steps:
[http://wiki.winehq.org/JamesLiggett/Hotsync](http://wiki.winehq.org/JamesLiggett/Hotsync)

---

### Post by Meow27 on 2009-04-23
preferences -> palm os devices

i dont think it works for palm os 5 or higher though


which version of the palm os desktop software are you using? you may want to look for a different one, for now at least.

---

### Post by sloppyc on 2009-04-23
Yeah, gnome-pilot doesn't work.  PC and phone just sit there waiting for each other and time out.

The Palm OS on the Centro is 5.4.9, I believe.  You're suggesting I change that?  I don't think that's an option.

---

### Post by Meow27 on 2009-04-24
no, cahnce the desktop version, you still have the cd for it im assuming, so try the one that is offfered at palm.com, [http://kb.palm.com/wps/portal/kb/na/centro/centro/unlocked/home/page_en.html](http://kb.palm.com/wps/portal/kb/na/centro/centro/unlocked/home/page_en.html)

the version might work, but if it doesnt, switch back to the cd, i cant be of much help at the point though. sorry

---

### Post by sloppyc on 2009-04-24
I didn't think to try different versions of the Palm Desktop software.  I've got a later version - 6.2, I believe - because it was the only Vista-compatible version at the time.

---

### Post by Foaming Draught on 2009-04-26
Nope, you won't get Palm Desktop to work under Wine or Crossover.  And Evolution synching is patchy at best.

But why oh why don't you use JPilot?  It's in the repos, is less bloated than Evolution, is tailor made for the Palm, does everything which Palm Desktop does and more besides, is fast, rock-stable, synchs flawlessly  .... must I go on?

Get jppy at the same time if your handheld is running >Palm 5.0.

---

### Post by sloppyc on 2009-04-27
> **Foaming Draught said:**
> But why oh why don't you use JPilot?


Because I'd never heard of it :P  Thanks, I'll give it a go:)

It works!  That's awesome, thanks a ton.  I'll play around and see if I can find a way to sync with Gmail now, that would be too much to hope for though, I'm sure.

---

