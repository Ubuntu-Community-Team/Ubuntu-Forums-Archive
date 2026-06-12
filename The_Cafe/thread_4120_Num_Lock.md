---
title: "Num Lock"
date: 2004-11-12
forum: The Cafe
---

### Post by adbak on 2004-11-12
It is disheartening that the num lock is not on by default when I boot up.  I was wondering if anyone knows if the option, at least, to have num lock on on boot-up is going to be included in Gnome 2.10?  If not, I think it would be a worthwhile addition as it inconveniences users (slightly though) to have to press the num lock button.

Nothing major, nothing of immediate concern, just a little wish (not that Ubuntu isn't already great).

---

### Post by oseb on 2004-11-12
$ sudo apt-get install numlockx

Control the state of NumLock
Provides control over the keyboard number lock from scripts.
Particularly useful for use with .xinitrc/.xsession or GDM/XDM/KDM sessions
Included is an optional script that can be used to start numlockx automatically
in every X session.
This script was provided by Ariel Shkedi <asdebian@dsgml.com>

---

### Post by bdoetsch on 2004-11-12
nonetheless, it would be real nice to have this included without having to configure stuff via scripts in /etc/init.d etc.

---

### Post by adbak on 2004-11-12
Numlockx works!

Thanks for the quick replies, guys.  Yet another reason why Ubu rocks!

---

### Post by HungSquirrel on 2004-11-12
Thanks for letting me know about this great little program.

---

### Post by mark on 2004-11-12
Thanks, oseb - this is one of those "little" that can be so annoying...

---

### Post by HiddenWolf on 2004-11-13
Ugh. I have more or less the same problem, but with the function keys.

I am on a ms-office keyboard at the moment. Don't ask me why, but if I go pick out a keyboard, I pick the one that types best, and it was ms at that moment.

However, it has the ms office shortcuts as primary options on the F-keys, and I have to turn on 'F-lock' to switch the F keys to their proper functions.

This, after a month of non-stop ubuntu, got very annoying. :-)

There probably is no solution, so I should be on the lookout for a new keyboard...

---

### Post by fng on 2004-11-13
some logitech keyboards (like mine :() also have that annoying f-lock button :(

---

### Post by HiddenWolf on 2004-11-13
*g*
I wish I could find one of those old IBM keyboards, but with a usb-adapter.

Just 104 keys, that's it, and a pleasure to type with.

---

### Post by TravisNewman on 2004-11-13
[QUOTE=HiddenWolf]*g*
I wish I could find one of those old IBM keyboards, but with a usb-adapter.

Just 104 keys, that's it, and a pleasure to type with.[/QUOTE]
 I have one of those old IBM Keyboards! The ones that were actually made out of metal instead of plastic so you wake up half the neighborhood when you write an email!! I have a ps2 adapter for it. I haven't used it in forever because I like to stay up later than my fiancee sometimes and I know it would keep her up.

You should come to Blacksburg, VA, HiddenWolf. There's a thrift store there that has about 200 of those old keyboards for $1.98 each.

But thanks for that numlock howto, that's been eating me up.

---

### Post by ariel on 2005-11-11
I also have this microsfot keboards with the f-lock key. For winxp i found an utility that  automatically sets the "f-lock" at boot time (so i have my real F1, F2, F... keys working.

I wish so much i could find the same for Linux!!!! any clue anyone?

TY!

---

### Post by aysiu on 2005-11-11
[QUOTE=bdoetsch]nonetheless, it would be real nice to have this included without having to configure stuff via scripts in /etc/init.d etc.[/QUOTE] Welcome to KDE. Personally, I don't mind a one-time copy and paste into the /etc/init.d or whatever. But if you want it all GUI with one click... KDE.

---

### Post by etc on 2005-11-11
I'd kill myself if numlock came up on boot, because it would override half my keys on my laptop keyboard.

---

### Post by aysiu on 2005-11-11
[QUOTE=etc]I'd kill myself if numlock came up on boot, because it would override half my keys on my laptop keyboard.[/QUOTE] Yeah, that's not what we're talking about. We're talking about adding the KDE functionality to Gnome--easy GUI configuration of what's default on boot--numlock or no numlock.

No one's saying *everyone's* computer should start with numlock on. The issue is that for those of us who *do* want it on, it should be easy to turn on and have it stay on. You can do this easily in KDE. You have to jump through a few more hoops in Gnome to do this.

---

### Post by stimpack on 2005-11-11
[QUOTE=fng]some logitech keyboards (like mine :() also have that annoying f-lock button :([/QUOTE]

Yeah I love logitech mice, but after buying a logi keyboard with stupid f-lock (seriously cant think of a worse computing design decision except maybe a centralised windows registry) I wont buy another logi keyboard. If theres a fix somewhere great, but for the moment using a cheap keyboard, the stupid f-lock nightmare is in a box somewhere.

---

### Post by wmcbrine on 2005-11-11
[QUOTE=HiddenWolf]I wish I could find one of those old IBM keyboards, but with a usb-adapter.[/QUOTE]
If you want a brand-new version, try [http://www.pckeyboard.com/](http://www.pckeyboard.com/) . They bought the design from Lexmark, who got it from IBM. It's the latter-day version, though, not the true original Model M. On the plus side, you can get it in black, like the one I'm using now. (Hmm, actually they don't seem to have my model anymore. Oh well.) Some of their models have USB; for others, you can get an adapter cheap (about $10 at NewEgg for a dual adapter -- mouse plus keyboard).

Also, the old ones hold up astoundingly well. If you find one, you might have to clean it, but that's probably all it'll need. I have one that lasted over a decade, until I spilled a glass of water into it. It still works, except for the Ctrl keys.

---

### Post by cvmostert on 2005-11-15
yup, thanx for the numlockx mister... have not rebooted yet, but set it to 'on' ... believe it will work great.

---

### Post by BoyOfDestiny on 2005-11-15
[QUOTE=stimpack]Yeah I love logitech mice, but after buying a logi keyboard with stupid f-lock (seriously cant think of a worse computing design decision except maybe a centralised windows registry) I wont buy another logi keyboard. If theres a fix somewhere great, but for the moment using a cheap keyboard, the stupid f-lock nightmare is in a box somewhere.[/QUOTE]

Phew, other people hate f-lock too. Funnily enough, my only 2 MS products, are my keyboard and mouse. 

I hate f-lock because I use the normal shortcuts, and I still use the F keys for what they should be used for. 

Also, I can no longer prnt+screen, and ctrl+break (humor me on that one, I run dosgames in dosbox) without turning f-lock off.

---

### Post by zenwhen on 2005-11-15
[QUOTE=aysiu] The issue is that for those of us who *do* want it on, it should be easy to turn on and have it stay on. You can do this easily in KDE. You have to jump through a few more hoops in Gnome to do this.[/QUOTE]

```
sudo apt-get install numlockx
```

That is all there is to it. I think you are making a mountain out of a molehill on this one.

As a side note:
I really do not understand why anyone would consider this to be such a hassle. I fear the day one can use Linux without ever touching the command line. One of the most powerful things about Linux will be put to the side in favor of panes full of check boxes and wizards, which is arguably much less intuitive than a quick search for the right command and a copy-paste into a terminal. Then, once you know the command, you know it. It will then always be faster than going though some odd set of configuration panels in a hodgepodge GUI. 

Sure, a lot of users will be happy with a CLI-free OS, but they will know a lot less. They will also miss out on a lot of great applications that aren't going to be gui-fied any time soon. It is a shame that people are so afraid of learning, really.

---

### Post by mothbitten on 2005-11-23
[QUOTE=zenwhen]```
sudo apt-get install numlockx
```

That is all there is to it. I think you are making a mountain out of a molehill on this one.

As a side note:
I really do not understand why anyone would consider this to be such a hassle. I fear the day one can use Linux without ever touching the command line. One of the most powerful things about Linux will be put to the side in favor of panes full of check boxes and wizards, which is arguably much less intuitive than a quick search for the right command and a copy-paste into a terminal. Then, once you know the command, you know it. It will then always be faster than going though some odd set of configuration panels in a hodgepodge GUI. 

Sure, a lot of users will be happy with a CLI-free OS, but they will know a lot less. They will also miss out on a lot of great applications that aren't going to be gui-fied any time soon. It is a shame that people are so afraid of learning, really.[/QUOTE]

It's a hassle because it makes something that should be dead easy into a mutistep process. You think it's perfectly fine to have to search the forums and download a program just to get numlock to stay on? Admittedly, there are some cases where doing things the hard way is beneficial, but to go through even this minimal annoyance for numlock makes no sense at all. It's just numlock. Microsoft had it figured out back in 1995. You click the numlock key and it stays on, end of story. How hard is that to do? It's a stupid little shortcoming in an otherwise excellent product, and it should be resolved, not classified as a learning opportunity.

---

### Post by aysiu on 2005-11-24
[QUOTE=zenwhen]```
sudo apt-get install numlockx
```
That is all there is to it. I think you are making a mountain out of a molehill on this one.[/quote] When did I make it into a mountain? I just don't understand where a simple click functionality in KDE isn't in Gnome, and you have to download an entire new program to get it to stick (and, according to the Ubuntu Guide--and maybe it's wrong--you also have to edit a config file).

> 
As a side note:
I really do not understand why anyone would consider this to be such a hassle. I fear the day one can use Linux without ever touching the command line. You fear the day? The day already happened! Linspire and Mepis already do this.

> One of the most powerful things about Linux will be put to the side in favor of panes full of check boxes and wizards, which is arguably much less intuitive than a quick search for the right command and a copy-paste into a terminal. Then, once you know the command, you know it. It will then always be faster than going though some odd set of configuration panels in a hodgepodge GUI. I love the command-line a lot, but it shouldn't be used for everything. Some things are good for checkboxes and wizards--others aren't. The command-line is good for:

1. Things you use a lot and for which it's easier and faster to type something than to click through some step-by-step process.
2. Complicated stuff that's hard to understand but that you can just copy and paste from a post in this forum.

I don't believe that should apply to wanting to have numlock on or off by default.

Didn't you read my thread [Why I think the command-line is user-friendly?](http://www.ubuntuforums.org/showthread.php?t=59334). You seem to think I'm some advocate for everything being point-and-click. Some things should be; others shouldn't.

---

