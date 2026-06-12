---
title: "light *box WMs"
date: 2008-05-11
forum: The Cafe
---

### Post by geo909 on 2008-05-11
Hi everybody,

I'm thinking about installing linux on an old PC,
so a *box WM would be more appropriate (Fluxbox, openbox,blackbox,etc).

Do you happen to know which of them is lighter?
Not "better", just "lighter". I'm not starting no WM-dispute in this thread!

---

### Post by kerry_s on 2008-05-11
for *box's the lightest would be openbox as it's just empty.

i prefer jwm myself, it's the smallest, lightest, fastest, etc...
it's great if you just want the best wm, but don't want to mess around to much. i don't use a background or icons, but you can.

---

### Post by urukrama on 2008-05-11
You won't notice a big difference between those three. I'm not sure Openbox is lighter than Fluxbox(I don't use Fluxbox, so I can't compare). Jwm is, I believe, even lighter. Icewm is pretty light as well.

[Here]("http://gilesorr.org/wm/memory.html") is a table that might help. Note that it is a little outdated, and may no longer be accurate.

I would go for whatever window manager you like best. I'd much rather work in an environment that I like, than use something that is *just* a little lighter.

---

### Post by geo909 on 2008-05-11
> for *box's the lightest would be openbox as it's just empty.

i prefer jwm myself, it's the smallest, lightest, fastest, etc...
it's great if you just want the best wm, but don't want to mess around to much. i don't use a background or icons, but you can.



Wait, JWM is the DSL one, right?

48MB ram used!
Is that ubuntu?!!!

Can you tell me what distro do you use with JWM?

---

### Post by eragon100 on 2008-05-11
I am going to get either a 486 or a pentium 2 laptop from someone.

If it's a 486 I am going to install minix 3 on it :lolflag:

Would fluxbuntu (ubuntu with fluxbox, d'uh) run on a pentium 2, say, 233 MHz and 64 mb RAM :confused:

---

### Post by geo909 on 2008-05-11
> **urukrama said:**
> You won't notice a big difference between those three. I'm not sure Openbox is lighter than Fluxbox(I don't use Fluxbox, so I can't compare). Jwm is, I believe, even lighter. Icewm is pretty light as well.

[Here]("http://gilesorr.org/wm/memory.html") is a table that might help. Note that it is a little outdated, and may no longer be accurate.

I would go for whatever window manager you like best. I'd much rather work in an environment that I like, than use something that is *just* a little lighter.

So ICEWM is lighter than the *box ones?
Also, can you tell me how should I read the table? When a WM is heavier than another? When it uses less libraries?

---

### Post by kerry_s on 2008-05-11
> **geo909 said:**
> Wait, JWM is the DSL one, right?

48MB ram used!
Is that ubuntu?!!!

Can you tell me what distro do you use with JWM?

yes, dsl uses jwm, alot of small distro's switched from *box to jwm. it may not look it but it can actually do alot, with out adding extra programs to do it. i've even mimicked other de setups. :) you might still find some of my fancier screen shots over there on the dsl forums, i'm "kerry" over there.
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=26;t=19467;hl=kerry;st=10](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=26;t=19467;hl=kerry;st=10)

no, i use to use ubuntu, but debian is smaller, faster, more stable. also debian runs better on my old rig(450mhz 256mb ram) i use the etch kernel though. the the 2.6.2* kernels don't work right for me.

i build mine up from a debian base, using the net installer->
[http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso)

when it comes to package selection, uncheck everything, that gives you a base install aka: command line system.

log in as root
apt-get install xorg jwm
type> exit <to get out of root
log in as your user
startx

continue building up.

thats the basics, keep in mind i've done it a lot, i pretty much know what i want, just did this install 2 days ago using->
apt-get install xorg synaptic jwm clex rungetty iceape-browser grun

then i work from there.

---

### Post by eragon100 on 2008-05-11
Well, anyone, will it run on those specs?

---

### Post by geo909 on 2008-05-11
> **kerry_s said:**
> yes, dsl uses jwm, alot of small distro's switched from *box to jwm. it may not look it but it can actually do alot, with out adding extra programs to do it. i've even mimicked other de setups. :) you might still find some of my fancier screen shots over there on the dsl forums, i'm "kerry" over there.
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=26;t=19467;hl=kerry;st=10](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=26;t=19467;hl=kerry;st=10)

no, i use to use ubuntu, but debian is smaller, faster, more stable. also debian runs better on my old rig(450mhz 256mb ram) i use the etch kernel though. the the 2.6.2* kernels don't work right for me.

i build mine up from a debian base, using the net installer->
[http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso)

when it comes to package selection, uncheck everything, that gives you a base install aka: command line system.

log in as root
apt-get install xorg jwm
type> exit <to get out of root
log in as your user
startx

continue building up.

thats the basics, keep in mind i've done it a lot, i pretty much know what i want, just did this install 2 days ago using->
apt-get install xorg synaptic jwm clex rungetty iceape-browser grun

then i work from there.

Thanks for the very useful info! I will think about it very seriously.
Debian has huge repositories like ubuntu, right? That's the main reason
I was thinking of ubuntu..

So I guess something like debian base + jwm + XFE would run flawlessly(?) on a 64MB ram machine using some very minimal stuff (Dillo, pine etc) while one preserves the pros that a popular distro has..

Btw,I checked that XP has a minimum requirement of [64 MB ram]("http://www.microsoft.com/windowsxp/pro/evaluation/sysreqs.mspx")! Maybe XP with blackbox (there's a win version) and a bunch of uneeded services stopped would be a good choice for an old PC?!:lolflag:

---

### Post by geo909 on 2008-05-11
> **eragon100 said:**
> Well, anyone, will it run on those specs?

Well, a 486 would be really tough to handle. Unless you do some network controlling stuff for example, it will be useless IMO (there's always minix though ;D).
A PII, well it deepends..
The most popular mini distros (Puppy linux for example) wouldn't boot on a PII as live CDs, so you should do it the hard way. I think a minimum of 32 MB ram is required for puppy. DSL linux said to have been installed successfully 
on a 16MB ram computer but I guess that was mainly for doing a show. But I really don't know and that's my subjective opinion. Maybe if someone has an experience with resurrection of ancient PCs would tell us..

---

### Post by kerry_s on 2008-05-11
> **geo909 said:**
> Thanks for the very useful info! I will think about it very seriously.
Debian has huge repositories like ubuntu, right? That's the main reason
I was thinking of ubuntu..

So I guess something like debian base + jwm + XFE would run flawlessly(?) on a 64MB ram machine using some very minimal stuff (Dillo, pine etc) while one preserves the pros that a popular distro has..

Btw,I checked that XP has a minimum requirement of [64 MB ram]("http://www.microsoft.com/windowsxp/pro/evaluation/sysreqs.mspx")! Maybe XP with blackbox (there's a win version) and a bunch of uneeded services stopped would be a good choice for an old PC?!:lolflag:

yeap, ubuntu is built from a snap shot of debian sid/unstable. same things in the repo's.

base + jwm + XFE = is fine for 64mb, just experiment, i try something different with each install. like for instance less gui tools, where i used rox-filer for the file manager, i'm using clex a terminal file manager, there's also mc, but i did a install with mc already. for editor i would normally use leafpad or xedit, this time i'm using vim. just small changes nothing big, but still different. :) also i'm not really tweaking the look, it's mostly stock this time, not like the pic on the dsl forum where i changed everything from the colors to the look. i'll probably add a couple of icons to the toolbar, but i'm not the icon type, prefer straight text.

that xp requirement is a lie, i've tried it.

---

### Post by geo909 on 2008-05-11
> base + jwm + XFE = is fine for 64mb, just experiment, i try something different with each install. like for instance less gui tools, where i used rox-filer for the file manager, i'm using clex a terminal file manager, there's also mc, but i did a install with mc already. for editor i would normally use leafpad or xedit, this time i'm using vim. just small changes nothing big, but still different.

Yes, the thing about mini distros on old PCs is really about if you are able to work with non-fancy staff like command line tools, curses, non-gtk,non-qt things..

If you do, it's ok.

I'll have the tools you mentioned in mind, although I would really miss the copy-paste feature that one has when he uses GUIs (or there is something about that, too).

> also i'm not really tweaking the look, it's mostly stock this time, not like the pic on the dsl forum where i changed everything from the colors to the look. i'll probably add a couple of icons to the toolbar, but i'm not the icon type, prefer straight text.

 Does a better theme with some glassy fancy-looking pixmaps makes the WM heavier or is it negligible?

> that xp requirement is a lie, i've tried it.
Oh, I was worried for a moment X-D

---

### Post by kerry_s on 2008-05-11
copy and paste is highlight middle click, same as with gui.

no pixmap themes in jwm, you can tweak the colors and tool bar look, but that's about it. you can add as many toolbars as you want, i've used them for desktop icons, you can also swallow programs(gui to), it barely fazes jwm, might go up by a couple of kb.

for example here's my file manager swallowed to the desktop, icons work the same way as you would put them on the toolbar.

---

### Post by chucky chuckaluck on 2008-05-11
here are a couple of screenshots of xmonad. as you can see from htop running in urxvt, the whole thing (including two instances of urxvt) only uses 30mb of ram. in the second shot, all running in urxvt, there's a clock, scrot, streamripper, cplay and htop running, all at a cost of 49mb ram. i'm posting this from firefox and that's kicked it up to 78mbs. with nothing running other than urxvt and htop, jwm was already using 78mbs, on my laptop. 

you could cut down on a lot of memory use if you're using lighter weight apps...

urxvt instead of xterm (using them isn't all that different)
cplay instead of mpd (exaile is a moose)
kazehakase is lighter than firefox (i use elinks most of the time)
xmonad, awesome and dwm all use less memory than jwm, or any of the boxes.

etc.


edit: should have mentioned i'm using arch.

---

### Post by eragon100 on 2008-05-11
Yeah I said if it's a 486 I am going to install minix 3 on it :)

---

### Post by geo909 on 2008-05-11
Thanks for the additional info! I'll look all of them.

> copy and paste is highlight middle click, same as with gui.

Forgive my english: Can you explain that again? 
Is there anything like Ctrl+C, Ctrl+V? 

BTW, is there anything like fluxbox's keygrabber (not built in the WM, as additional program.)

Finally, doesn't the base system makes any difference in the RAM load?
Why people don't use Debian -for example- with light stuff?

---

### Post by geo909 on 2008-05-11
> **chucky chuckaluck said:**
> here are a couple of screenshots of xmonad. as you can see from htop running in urxvt, the whole thing (including two instances of urxvt) only uses 30mb of ram. in the second shot, all running in urxvt, there's a clock, scrot, streamripper, cplay and htop running, all at a cost of 49mb ram. i'm posting this from firefox and that's kicked it up to 78mbs. with nothing running other than urxvt and htop, jwm was already using 78mbs, on my laptop. 

you could cut down on a lot of memory use if you're using lighter weight apps...

urxvt instead of xterm (using them isn't all that different)
cplay instead of mpd (exaile is a moose)
kazehakase is lighter than firefox (i use elinks most of the time)
xmonad, awesome and dwm all use less memory than jwm, or any of the boxes.

etc.


edit: should have mentioned i'm using arch.

That's impressive, really..
But is there a point to run just 30MB of Ram when you have 1GB of it?!
Man, that's exaggerating:shock:!!

---

### Post by chucky chuckaluck on 2008-05-11
> **geo909 said:**
> That's impressive, really..
But is there a point to run just 30MB of Ram when you have 1GB of it?!
Man, that's exaggerating:shock:!!

somewhere, there's a thread i started called "all hail the bloat". i have gone through phases in which i would open synaptic and just load up (usually a bunch of kde stuff). but, i've gotten pretty sick of gui apps and use only firefox and gimp (and occassionally gcolor2 and leafpad when modifying some theme). i like terminal apps. they're easy and quick to use and don't have a lot of fluffy distractions. they also happen to be lightweight. as memory is cheap, i don't feel too badly just letting sit there on the shelf.

---

### Post by cardinals_fan on 2008-05-11
Openbox is the best!  Lightweight and easy to customize.

---

### Post by kerry_s on 2008-05-11
> Forgive my english: Can you explain that again?
Is there anything like Ctrl+C, Ctrl+V?


i guess that really boils down to what text editor you use. i use vim, it can be done-> [http://www.vim.org/tips/tip.php?tip_id=866](http://www.vim.org/tips/tip.php?tip_id=866)


> BTW, is there anything like fluxbox's keygrabber (not built in the WM, as additional program.)


of course you can set keyboard shortcuts or use a program like xbindkeys.(see pic)

> Finally, doesn't the base system makes any difference in the RAM load?
Why people don't use Debian -for example- with light stuff?

it depends on what your after, i'm like fusia(chucky chuckaluck), i'm sick of all the bloat, every things getting so fat these days.

> here are a couple of screenshots of xmonad. as you can see from htop running in urxvt, the whole thing (including two instances of urxvt) only uses 30mb of ram. in the second shot, all running in urxvt, there's a clock, scrot, streamripper, cplay and htop running, all at a cost of 49mb ram. i'm posting this from firefox and that's kicked it up to 78mbs. with nothing running other than urxvt and htop, jwm was already using 78mbs, on my laptop.


hmm, that's weird, just jwm before i launch any programs(startup) uses less than 15mb, after i launch programs it idles back down to about 18 to 20mb. most be that arch backbone. :lolflag:

---

### Post by cardinals_fan on 2008-05-11
> **geo909 said:**
> 
Forgive my english: Can you explain that again? 
Is there anything like Ctrl+C, Ctrl+V? 

BTW, is there anything like fluxbox's keygrabber (not built in the WM, as additional program.)

Highlight = Copy, Middle-Click = Paste

Xdotool simulates keypresses.  Very useful.

---

