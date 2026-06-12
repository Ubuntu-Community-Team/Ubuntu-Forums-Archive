---
title: "Easy shift / ctrl / AltGr / etc hack on xf86-input-evdev"
date: 2011-06-06
forum: The Cafe
---

### Post by teika on 2011-06-06
Hi. This hack provides for example "space/shift dual role key". When you press the space key alone, it's a space; but when you press it with another key, it's a shift. Any pairs of keys are possible. This means your hands stay almost always at their home postion. Now I can't type comfortably without it.

It's a fork of Xorg "evdev" driver (= _xf86-input-evdev_, or in debian/ubuntu _xserver-xorg-input-evdev_).

* **[Readme]("http://gitorious.org/at-home-modifier/at-home-modifier/blobs/raw/master/README")** tells the detail.
* **[homepage]("http://gitorious.org/at-home-modifier/pages/Home/")**. You can get the source tarball and git access instruction.

_FAQ_
Q: Can I input Shift+Space if my Space is Space/Shift dual-role key?
A: Turn both of your Space and Shift into Space/Shift keys.

_News for 2.8.0 (Jun 2013)_
Merges the upstream 2.8.0, and has no changes in ahm itself since 2.7.3. For full changes, read **[README](http://gitorious.org/at-home-modifier/at-home-modifier/blobs/raw/master/README)**, "News" section:

_Installation_
*I'm not a debian-ish distro user!* Fortunately, there's an [Ubuntu PPA]("https://launchpad.net/~yurivkhan/+archive/ahm") for this hack contributed by [Yuri Khan]("https://launchpad.net/~yurivkhan"). (Thanks!) I don't give general instruction and caution on PPA here. Use it at your own risk, but the source package may be nice; at least looking into debian/ directory will help.

_Alternatives_
* [xcape](https://github.com/alols/xcape). See the homepage for how to compile. It's a userland software, so you don't have to catch up the upgrade of xf86-input-evdev.
* Obsolete alternatives are [Space2Ctrl](https://github.com/r0adrunner/Space2Ctrl) in C++ and [keydouble](https://github.com/baskerville/keydouble) in C, which is a fork of Space2Ctrl.

_Notice_
Probably I don't develop any more this hack *as a fork of xf86-input-evdev*. It's better to do all in user space, rather than as an X driver.

If you want some progress, improve xcape. I'm also interested in a rewrite in Python, which will be easier to allow flexible configuration. It'd be great if it'd be integrated into [AutoKey](http://code.google.com/p/autokey/), but its development seems to have stopped.

With best regards.

---

### Post by teika on 2011-11-12
Hi. at-home-modifier-2.6.3 is released. Changes since the last post (2.6.0) are:

* Fast type fix
Users of this hack often have “tongue-twister of finger”: Suppose you want “ x”. If you press space/shift, press x, and release space/shift (before releasing x), you’ll get an upper-case X instead.
Fixes of this kind are attempted with new “AhmDelay” and “AhmFreezeTT” options.

* Cancellation by timeout
Suppose you were about to input shift + A and pressed space/shift, but you changed your mind. If you release the space/shift key, you’ll receive one space, but it’s not what you want!
This can be fixed by long enough press now.

* Reset
When something is wrong, leave the keyboard untouched for 10 secs. Then all are reset to the initial state.

* Gtk widget double press issue.
To push a gtk button, sometimes you had to press space/shift key twice, but this is fixed. If it doesn’t work out-of-box, set “AhmPaddingInterval” option. (This “bug” is not the author’s fault, but what’s bad for users are bugs.=)

For full changes, read README, "News" section:
[http://gitorious.org/at-home-modifier/at-home-modifier/blobs/raw/master/README](http://gitorious.org/at-home-modifier/at-home-modifier/blobs/raw/master/README)

With best regards.

Homepage: [http://gitorious.org/at-home-modifier/pages/Home](http://gitorious.org/at-home-modifier/pages/Home)

---

### Post by teika on 2011-11-28
I've added installation instruction. See the first post.

---

### Post by kindahero on 2011-12-21
this sounds cooool.. will say after using for few days.

---

### Post by teika on 2011-12-28
Hi. at-home-modifier-**2.6.4** is released. It has one minor fix, "mouse support":
When you press space/shift and a mouse button, the result used to be shift + click, ok, but also followed by an extra, unwanted space, as if the click hadn't happened. It's because each device ignored others. Now it's fixed, as long as the mouse is also handled by evdev driver. (Notebook touchpads are dealt by synaptics driver, so it's not fixed, and won't be fixed. Use AhmTimeout option as a workaround.)

For building, read the **[ first message in the debian thread]("http://forums.debian.net/viewtopic.php?f=3&t=65950&p=378437#p378437")**.

@kindahero:
Thank you for checking. Good luck!

If you find the news or README difficult to understand, then feel free to ask. 
<quote>"What's inconvenient is a bug." - Teika kazura</unquote>

---

### Post by Yuri Khan on 2012-01-05
I have built xserver-xorg-input-evdev with your patch and posted it in my PPA: [ppa:yurivkhan/ahm]("https://launchpad.net/~yurivkhan/+archive/ahm"). Had to resolve a merge conflict with an Ubuntu-specific patch but had no problem otherwise.

The concept is quite nice. I mapped my home row to [Hyper Super Alt Ctrl | Ctrl Alt Super Hyper] and bound some compiz actions to Super- and Hyper- combinations. It works as expected, though I seem to suffer from a variation of “finger tongue-twister” that AhmDelay does not fix — maybe I’m releasing the second key a little bit earlier than the first one, which then counts as a modifier.

It would be good to have run-time configurability e.g. via xinput set-prop. After all, such tweaks ought to be per-user only. As of now, I have them configured per-device.

I would also like to point you to [a similar work](http://www.ruska.it/michal/fork.html) by Michal Maruska, he seems to put some thought into deciding when to autorepeat a held key in cases when it is also a transmod, and into rollover detection (basically what you call “tongue-twisters”).

---

### Post by teika on 2012-01-14
Spasibo, Yurocheka, znaesh... No, I don't speak Russian. ;) 

On xinput: it'd be nice if it were possible to use xinput, but it seems no. If you do:
 $ xinput list-props <keyboard id>
it doesn't show any keyboard options, including those of non-ahm. I know on-the-fly setting of options is great, but it may need socket or something that I don't know at all.

I haven't studied notes by Michal Maruska yet. It looks well written, but I'm afraid any theories may fail, and it could only be solved by experiences. Perhaps autorepeat is not so much involved, and "tongue-twister" is the sole issue. Possibly should I write a key logger? (It has to be good enough, and also a good way to analyze the log is required. I'm not good at both.)

# Michal always go ahead of me. He's written a huge fork of Sawifsh WM.

One Gentoo user requested autorepeat, too. I've made a pointer:
[http://at-home-modifier.2300353.n4.nabble.com/Some-users-have-requested-autorepeat-tp4294256p4294256.html](http://at-home-modifier.2300353.n4.nabble.com/Some-users-have-requested-autorepeat-tp4294256p4294256.html)

Thanks for helpful comments. I'm a bit busy now. :P

---

### Post by Yuri Khan on 2012-01-14
> **teika said:**
> Spasibo, Yurocheka, znaesh... No, I don't speak Russian. ;) 

[COLOR="Gray"]That’s very clear. The Japanese equivalent of using the diminutive name form would be addressing a total stranger as &#12385;&#12419;&#12435;. No offense though.[/COLOR]

> **teika said:**
> On xinput: it'd be nice if it were possible to use xinput, but it seems no. If you do:
 $ xinput list-props <keyboard id>
it doesn't show any keyboard options, including those of non-ahm. I know on-the-fly setting of options is great, but it may need socket or something that I don't know at all.

Of course properties do not work “out of the box” for all xorg.conf settings. It will need some coding before it will work.

Other evdev keyboard-related settings are actually xkb options, and can be set via setxkbmap and/or xkbcomp. I don’t think that way is appropriate for ahm options though.

> **teika said:**
> I haven't studied notes by Michal Maruska yet. It looks well written, but I'm afraid any theories may fail, and it could only be solved by experiences.

He seems to have an evdev fork of his own, though I was unable to get it to work on my machine.

> **teika said:**
> Perhaps autorepeat is not so much involved, and "tongue-twister" is the sole issue.

Actually yes. Key rollovers seem to be essential for touch typing; autorepeat is only meaningful for the space and cursor movement keys. (Though you do use Space/shift as the motivating example.)

> **teika said:**
> Possibly should I write a key logger? (It has to be good enough, and also a good way to analyze the log is required. I'm not good at both.)

That’s one of the few cases where a keylogger is a good thing :)
I’d suggest writing the log as lines of tab- or comma-separated keycodes and timestamps, and some elementary analysis can then be done in {Open|Libre}Office.

---

### Post by teika on 2012-01-30
I've found an alternative, **[Space2Ctrl](https://github.com/r0adrunner/Space2Ctrl)**, by Victor Moreira.

* s2c works in the user space, while ahm (=at-home-modifier) is the fork of an X input driver.
* s2c uses "X Record Extension" to detect events. I haven't given a try yet, but it probably stands between the X server and clients (or Xlib).
*** This (probably) means it can't coexist with other softwares which use Record Extension, e.g. AutoKey or xnee.
* s2c doesn't require much updates; ahm has to keep up with the upstream (= X).
* s2c is written in C++. (I don't understand C++. :P)
* The s2c code is slim; it's easier for users to hack.
*** Ahm is a fork, so the distinction of the genuine ahm part and the original X code is not clear.
* s2c is rudimentary. The sole keycode pair is hard-coded, and has no option. According to the author (in private correspondence), "more of a personal hack, very poorly tested and documented."

Read the git commit log to know the author's email address. He said he'd like more users, so sending patches may be welcome.

News: Ahm development hasn't seen any progress after the 2.6.4 release.

---

### Post by teika on 2012-02-16
An implementation in C, "keydouble" is developed by "baskerville" aka "bloom" in the ArchLinux forum. See the [web site](https://github.com/baskerville/keydouble) hosted at github. You may find the news at the [Arch forum thread](https://bbs.archlinux.org/viewtopic.php?pid=1057549#p1057549).

---

### Post by teika on 2012-03-14
Xorg has released xf86-input-evdev-2.7.0. It has multitouch support.

I've merged it to my hack, which is available at the GIT repo, "master" branch. I don't make a release at least for a week, but you can try it. (It's been running for 30 min without problem. =)

To use the multitouch support, you need:
* >=xorg-server-1.11.99.901
* >=inputproto-2.1.99.3
* mtdev

At-home-modifier itself doesn't have any progress since the last release.

I don't have any multitouch device, so I won't test it.

---

### Post by teika on 2012-04-22
Hi, folks. Not a news of ahm update, but of a good keyboard.

keyboard glossary:
[https://en.wikipedia.org/wiki/Keyboard_technology](https://en.wikipedia.org/wiki/Keyboard_technology)
[http://www.overclock.net/t/491752/mechanical-keyboard-guide](http://www.overclock.net/t/491752/mechanical-keyboard-guide)

I recommend Japanese keyboards for at-home-modifier, because you can press many keys with thumbs. Image here:
[https://en.wikipedia.org/wiki/File:KB_Japanese.svg](https://en.wikipedia.org/wiki/File:KB_Japanese.svg)

The bottom row of my keyboard is:
Esc-BS-Spc-Ret-Tab *and*
Alt-Shift-Ctrl-Shift-Alt
(The middle one is the space bar.) as described in the README of ahm. Japanese keyboards enable such stunt which is really comfy.

I use a membrane keyboard, whose touch is bad for your finger. There hasn't been good keyboards with enough many thumb keys.

Recently a new keyboard with "cherry mx brown switch", OWL-KB109BM(B)IIB, came out:
[http://www.owltech.co.jp/products/keyboard/KB109BM_B_II/KB109BM_B_II.html](http://www.owltech.co.jp/products/keyboard/KB109BM_B_II/KB109BM_B_II.html) (Japanese)
You can buy one from amozon.co.jp, at 8000 yen or so (roughly equal to $100; these days yen is high.). They offer an English interface, too. I dislike google/apple/amazon monopoly, though. (Who likes?)
There's also "cherry mx **blue**" one, OWL-KB109BM(B)II, too. They say blue is noisy.

There's already many other cherry switch or capacitive switch Japanese keyboards, but they have a long space bar, which doesn't suit my purpose.

I haven't bought yet. Not cheap, but interesting. Night night.

---

### Post by Yuri Khan on 2012-04-29
I have built a 2.7.0 AHM package for Precise; it seems to work for me.

[https://launchpad.net/~yurivkhan/+archive/ahm](https://launchpad.net/~yurivkhan/+archive/ahm)

---

### Post by teika on 2012-05-05
Thanks, Yuri-&#12385;&#12419;&#12435;!

FYI, starting from 2.7.0, xserver-xorg-input-evdev can be built with the support of mtdev. (Called libmtdev in debian.) It's a multitouch protocol handler. In quantal (the next Ubuntu), mtdev support is enabled, so it'll be better for ahm to add it too. (Not necessry now.)

Regards.

---

### Post by teika on 2012-06-06
At-home-modifier-**2.7.1** is released. (Called whimsically 2.7._1_, not 2.7.0.) It merges the upstream 2.7.0, but has no changes in ahm since 2.6.4.

The Xorg's 2.7.0 has mulitouch support. If you want it, you need Xorg server >= 1.11.99.901 and "mtdev" library.

Modifications from the upstream 2.7.0 are:
* An upstream bugfix of horizontal scroll, X.Org Bug 46205, is included. (The fix is published after the 2.7.0 release.)
* Added an option to configure script "--without-mtdev". The upstream code always checks mtdev, and enables it when found. If you don't pass the above option, it falls back to the original behavior.

Read [README](http://gitorious.org/at-home-modifier/at-home-modifier/blobs/raw/master/README) for the details.

* [Source tarball](http://gitorious.org/at-home-modifier/download/blobs/raw/master/source/ahm-2.7.1.tar.gz)
* [Patch against Xorg's original 2.7.0](http://gitorious.org/at-home-modifier/download/blobs/raw/master/patch/ahm-2.7.1.patch)

I don't write Debian support for 2.7.1.

_Notice_
Probably I don't develop any more this hack *as a fork of xf86-input-evdev*. It's better to do all in user space, not as an X driver. (And personally I'm terribly weakened.)

If you want some progress, improve "Keydouble" or so. I'm also interested in a rewrite in Python, which will be easier to allow flexible configuration. (In reality I don't think I'll ever write one.) It'll be great if it's integrated to AutoKey, but the AutoKey developer is not interested.

To make these hacks more popular, you can upvote [my answer here](http://stackoverflow.com/a/8935973) to [a question on Emacs Pinky](http://stackoverflow.com/questions/52492/what-is-the-best-way-to-avoid-getting-emacs-pinky) in StackOverflow.

Regards.

---

### Post by teika on 2012-11-20
Hi. At-home-modifier-**2.7.3** is released. It merges the upstream 2.7.3, but has no changes in ahm itself since the last release, 2.7.1.

Sources:
* [The full source tarball]("http://gitorious.org/at-home-modifier/download/blobs/raw/master/source/ahm-2.7.3.tar.gz")
* [The patch against Xorg's original 2.7.3]("http://gitorious.org/at-home-modifier/download/blobs/raw/master/patch/ahm-2.7.3.patch")

I don't write Debian support for 2.7.3, but Yuri Khan seems to have already published (wow) 2.7.3. See [his PPA]("https://launchpad.net/~yurivkhan/+archive/ahm").

...Well, I can't update the first post, which is my own, of this thread. WTF.

Regards.

---

### Post by teika on 2013-06-08
There's another alternative, [xcape](https://github.com/alols/xcape) by Albin Olsson. It replaces keydouble and space2ctrl.

It's not in Debian/Ubuntu. See the homepage for how to compile.

---

### Post by teika on 2013-06-27
Hi. I release at-home-modifier-**2.8.0**. It merges the upstream 2.8.0, but has no changes in ahm itself since the last release, ahm-2.7.3. Those with new devices may want to use it. Don't worry, the dependency is the same as upstream-2.7.3, Raring's version.

* [Upstream news for 2.8.0](http://lists.x.org/archives/xorg/2013-March/055572.html)

Sources:
* [The full source tarball](http://gitorious.org/at-home-modifier/download/blobs/raw/master/source/ahm-2.8.0.tar.gz)
* [The patch against Xorg's original 2.8.0](http://gitorious.org/at-home-modifier/download/blobs/raw/master/patch/ahm-2.8.0.patch)

I don't write a Debian-ish support for 2.8.0. Please consult [PPA by Yuri Khan](https://launchpad.net/~yurivkhan/+archive/ahm).

Regards.

---

