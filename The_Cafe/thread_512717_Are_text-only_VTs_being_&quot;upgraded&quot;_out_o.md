---
title: "Are text-only VTs being &quot;upgraded&quot; out of existence?"
date: 2007-07-29
forum: The Cafe
---

### Post by Thrasyllus on 2007-07-29
I use the TTY virtual terminals a *lot*. They are neater and eye-friendlier than the terminal under X. It's also neat to be able to switch back and forth between six of them, and to forget everything else when you're working on one. With various other distros (RedHat and Slackware) it was easy to tweak them the way I wanted; I even wrote my own keyboard map which served me through a half-dozen upgrades. 

Now, to my great sadness, my questions about the TTY screenfonts are totally ignored, and I notice that similar questions have been ignored, or not meaningfully dealt with, since at least last November. I also found an article on "UsingTheTerminal" in the Ubuntu wiki which doesn't mention the virtual terminals at all (except for a passing mention of using F1 which isn't very informative). 

As it is, the organization of terminal screenfonts make them highly disagreeable, especially if one wants to look at text with accented letters. Border rules also don't work, so Midnight Commander looks awful. Yet it wouldn't take much overhead to make proper terminals available. I am beginning to suspect that this feature is being "upgraded" in the same way  bureaucrats "rationalize" a department they have been appointed to shut down, by first making sure it doesn't work.

It's not that I don't use X - I'm there most of the time, and the GUI terminal *is* useful when I need to cut and paste things. But surely the linux community should be in favour of choice.

So I hope the above speculations are just paranoia on my part, and that someone will turn up with the advice I need (see other posts under "Thrasyllus" - there aren't many).

---

### Post by bonzodog on 2007-07-29
What you need to do is make sure that the Framebuffer is running - Ubuntu does not do this by default. Normally, you just need to append something like 'vga=795" (1280 x 1024 x 68k) to the end of the main booting line in grub, then reboot.

Slackware and Fedora do.

Then, once you are in Framebuffer, you should be able to set fonts.

I still have a fully active framebuffer in Zenwalk, with a special font.

---

### Post by init1 on 2007-07-29
> **bonzodog said:**
> What you need to do is make sure that the Framebuffer is running - Ubuntu does not do this by default. Normally, you just need to append something like 'vga=795" (1280 x 1024 x 68k) to the end of the main booting line in grub, then reboot.

Slackware and Fedora do.

Then, once you are in Framebuffer, you should be able to set fonts.

I still have a fully active framebuffer in Zenwalk, with a special font.
I was wondering about that. How do I set fonts in the command line?

---

### Post by Thrasyllus on 2007-07-30
Thank you Bonzodog! Please excuse my ignorance while I ask a couple more questions.

(1) Do the TTY virtual terminals (the ones you get by typing alt-ctrl-F1 through alt-ctrl-F6) also depend on the framebuffer? I thought the framebuffer was for graphics. I don't need an aesthetic type design, I simply want to be able to see the accents available from my French-Canadian keyboard é, è, ç. etc. on the old-fashioned white-on-black screens just as we see them in X. 

(2) Assuming the answer to the first questioin is yes, I'm unsure about the way you put quote marks around the command you suggest. Is it only "vga=795" or should it include the dimensions between round brackets? And is 795 the precise number or merely "something like"?

Cheers, Axel

---

### Post by Nikron on 2007-07-30
You should try out gensplash, it makes your terminals pretty =P.  Also, here's a list of possible things you can set vga equal to.  You set vga=xxx in the kernel line of you menu.lst.  As for changing the console font in ubuntu, I can't help you there because all you have to do in Arch is edit the font section of /etc/rc.conf. 

I generally don't use my tty except when compiling, and I need something stable and out of the way.

 14 #  FRAMEBUFFER RESOLUTION SETTINGS
 15 #     +-------------------------------------------------+
 16 #          | 640x480    800x600    1024x768   1280x1024
 17 #      ----+--------------------------------------------
 18 #      256 | 0x301=769  0x303=771  0x305=773   0x307=775
 19 #      32K | 0x310=784  0x313=787  0x316=790   0x319=793
 20 #      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
 21 #      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
 22 #     +-------------------------------------------------+

edit: added picture of

---

### Post by Brunellus on 2007-07-30
> **Thrasyllus said:**
> I use the TTY virtual terminals a *lot*. They are neater and eye-friendlier than the terminal under X. It's also neat to be able to switch back and forth between six of them, and to forget everything else when you're working on one. With various other distros (RedHat and Slackware) it was easy to tweak them the way I wanted; I even wrote my own keyboard map which served me through a half-dozen upgrades. 

Now, to my great sadness, my questions about the TTY screenfonts are totally ignored, and I notice that similar questions have been ignored, or not meaningfully dealt with, since at least last November. I also found an article on "UsingTheTerminal" in the Ubuntu wiki which doesn't mention the virtual terminals at all (except for a passing mention of using F1 which isn't very informative). 

As it is, the organization of terminal screenfonts make them highly disagreeable, especially if one wants to look at text with accented letters. Border rules also don't work, so Midnight Commander looks awful. Yet it wouldn't take much overhead to make proper terminals available. I am beginning to suspect that this feature is being "upgraded" in the same way  bureaucrats "rationalize" a department they have been appointed to shut down, by first making sure it doesn't work.

It's not that I don't use X - I'm there most of the time, and the GUI terminal *is* useful when I need to cut and paste things. But surely the linux community should be in favour of choice.

So I hope the above speculations are just paranoia on my part, and that someone will turn up with the advice I need (see other posts under "Thrasyllus" - there aren't many).
your questions on the TTY screenfonts were ignored because most Ubuntu users spend exactly zero time outside of X.  I can cast my mind back wearily to a time when X broke for many users, and the number of panicked posts on these forums shot up a hundredfold.  

If it helps you any, I ended up configuring terminal fonts and keymaps in my TTY terminals on one of my installs.  My install report was on my blog, and permalinked here:

[http://ouij.livejournal.com/207594.html](http://ouij.livejournal.com/207594.html)

Note especially the section "Pimp this Hooptie!"

---

### Post by init1 on 2007-07-30
> **Thrasyllus said:**
> Thank you Bonzodog! Please excuse my ignorance while I ask a couple more questions.

(1) Do the TTY virtual terminals (the ones you get by typing alt-ctrl-F1 through alt-ctrl-F6) also depend on the framebuffer? I thought the framebuffer was for graphics. I don't need an aesthetic type design, I simply want to be able to see the accents available from my French-Canadian keyboard é, è, ç. etc. on the old-fashioned white-on-black screens just as we see them in X. 

(2) Assuming the answer to the first questioin is yes, I'm unsure about the way you put quote marks around the command you suggest. Is it only "vga=795" or should it include the dimensions between round brackets? And is 795 the precise number or merely "something like"?

Cheers, Axel
The framebuffer does affect the terminal, and to activate it, you need to add vga=whatevernumber to change the resolution. This is done in the /boot/menu.list. The kernel argument would look something like:
```

kernel /boot/vmlinuz root=/dev/thedriveandpartition **vga=795**

```
And yes, vga=795 is just one option.

---

### Post by Thrasyllus on 2007-07-31
Monumental thanks to Brunellus and init1 !

No success yet despite trying a few different settings in /etc/console-tools/config and /boot/grub/menu.lst. 

But some interesting facts appear. First, the font is definitely there in both the TTY and GUI terminals. They are identical. It's just that certain characters don't get echoed on the TTY screen. For instance, going down the right-hand end of the key rows from top right to bottom right, the characters (in my setup) are à , ç , è , and é. On the TTY screen they show respectively as a degree symbol, a small rectangular bullet, a blank, another blank. However: 

(1) In an old Forth program where I defined **é** as a command (because I had run out of keyboard shortcuts and I don't like long commands), the **é** function still works even if the command just looks like a blank on the screen; 

(2) if I type the no-show characters to a file using vim in a TTY terminal, and then read it in the GUI terminal,  the characters all appear properly.

If you only use the GUI or if you are unilingual English, you might not notice there is a problem. Anyway, what needs to be fixed is the echo of certain characters. 

Another curious thing. When I looked at the last lines in /etc/console-tools/config as suggested in Brunellus's excellent livejournal entry, I saw

**SCREEN_FONT_vc{1-6}=lat0-sun16**

But when I tried to **locate lat0-sun16** it was nowhere to be found in the Ubuntu system! (In fact **locate** did turn up lat0-sun16 in a directory left over from my old Fedora distro, thereby showing that the database is up to date.) Changing the appropriate lines to other consolefont references did not have any visible effect. 

So that's where I'm at. Any ideas?

---

### Post by init1 on 2007-07-31
> **Thrasyllus said:**
> Monumental thanks to Brunellus and init1 !

No success yet despite trying a few different settings in /etc/console-tools/config and /boot/grub/menu.lst. 

But some interesting facts appear. First, the font is definitely there in both the TTY and GUI terminals. They are identical. It's just that certain characters don't get echoed on the TTY screen. For instance, going down the right-hand end of the key rows from top right to bottom right, the characters (in my setup) are à , ç , è , and é. On the TTY screen they show respectively as a degree symbol, a small rectangular bullet, a blank, another blank. However: 

(1) In an old Forth program where I defined **é** as a command (because I had run out of keyboard shortcuts and I don't like long commands), the **é** function still works even if the command just looks like a blank on the screen; 

(2) if I type the no-show characters to a file using vim in a TTY terminal, and then read it in the GUI terminal,  the characters all appear properly.

If you only use the GUI or if you are unilingual English, you might not notice there is a problem. Anyway, what needs to be fixed is the echo of certain characters. 

Another curious thing. When I looked at the last lines in /etc/console-tools/config as suggested in Brunellus's excellent livejournal entry, I saw

**SCREEN_FONT_vc{1-6}=lat0-sun16**

But when I tried to **locate lat0-sun16** it was nowhere to be found in the Ubuntu system! (In fact **locate** did turn up lat0-sun16 in a directory left over from my old Fedora distro, thereby showing that the database is up to date.) Changing the appropriate lines to other consolefont references did not have any visible effect. 

So that's where I'm at. Any ideas?
Yeah, I tried the vga=whatever thing and it didn't work either. I don't know why. It works in other distros, like finnix. The TTY text much smaller.

---

### Post by Thrasyllus on 2007-07-31
Are these threads monitored by people who are officially connected with Ubuntu, or should we report this problem somewhere else?

---

### Post by Brunellus on 2007-08-01
> **Thrasyllus said:**
> Are these threads monitored by people who are officially connected with Ubuntu, or should we report this problem somewhere else?
These threads are NOT tracked by official devs.  If you have found what you believe to be a legitimate bug and/or have a legitimate feature request, please add it to the bugtracker at Launchpad.

---

### Post by macogw on 2007-08-01
> **Brunellus said:**
> your questions on the TTY screenfonts were ignored because most Ubuntu users spend exactly zero time outside of X.  I can cast my mind back wearily to a time when X broke for many users, and the number of panicked posts on these forums shot up a hundredfold.  

If it helps you any, I ended up configuring terminal fonts and keymaps in my TTY terminals on one of my installs.  My install report was on my blog, and permalinked here:

[http://ouij.livejournal.com/207594.html](http://ouij.livejournal.com/207594.html)

Note especially the section "Pimp this Hooptie!"
those posts are what prompted me to learn to use the command line more.  it's coming in very handy with my "install debian without a DE, then compile Enlightenment 17 from CVS" plan.

---

### Post by Thrasyllus on 2007-08-03
Brunellus, I posted a query on answers.launchpad.net. Thanks again. Earlier I didn't mention how much I enjoyed your livejournal entry: very much.

---

### Post by Brunellus on 2007-08-03
> **Thrasyllus said:**
> Brunellus, I posted a query on answers.launchpad.net. Thanks again. Earlier I didn't mention how much I enjoyed your livejournal entry: very much.
Glad you enjoyed the entry.  

If you're looking for a feature request, though, you should try bugs.launchpad.net  --the devs take these into account for adding features.

---

