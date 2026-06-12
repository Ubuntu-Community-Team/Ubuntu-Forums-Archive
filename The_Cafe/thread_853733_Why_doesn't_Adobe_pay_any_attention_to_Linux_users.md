---
title: "Why doesn't Adobe pay any attention to Linux users?"
date: 2008-07-08
forum: The Cafe
---

### Post by kaldor on 2008-07-08
I've used Linux for about 4 months now. Flash player is driving me mad. Youtube is worthless now. I did those manual fixes via synaptic, can't remember which. Worked for a while, now I can't even watch anything with flash.


The Windows version of flash is flawless from what I see. Why doesn't Adobe pay attention to people who don't use Windows?


Discuss.

---

### Post by sharks on 2008-07-08
because IMHO Linux users dont pay money compared to users os Window$ to them.

---

### Post by zmjjmz on 2008-07-08
Well, they won't be paying money if there's nothing to buy.

---

### Post by cardinals_fan on 2008-07-08
Because Linux has much smaller desktop marketshare.  Just be grateful that they have Linux support at all.

Maybe I'm just lucky, but the only problem I have with Flash is that menus fall behind Flash content.

---

### Post by zmjjmz on 2008-07-08
I only have one problem with flash, but it seems that the fault is more in my sound setup than flash itself.

Flash 10 beta is very good actually.

---

### Post by LaRoza on 2008-07-08
I am using Flash 10 Beta 2. It works pretty well. Youtube works fine.

---

### Post by zmjjmz on 2008-07-08
Yeah, I have this odd sound problem with Youtube where it becomes dragged out as if it was reverberating through a synth or something, but for some reason espeak and cplay don't work either, so it's just a sound problem.

---

### Post by cardinals_fan on 2008-07-08
> **LaRoza said:**
> I am using Flash 10 Beta 2. It works pretty well. Youtube works fine.
I don't use beta software on principle.

EDIT: Not including Google's betas.  Because they often keep stable software in beta for no reason at all.

---

### Post by saulgoode on 2008-07-08
I have zero problems with Flash. I just don't install it.

---

### Post by jesusprice on 2008-07-08
flash works well I just have minor sound issues. Between watching a flash movies (youtube) and then having no sound when I play an mp3 on my desktop.

---

### Post by samjh on 2008-07-08
Very few problems here.  I'm using Flash 9.  The only issue is the occasional "grey box" phenomena; there was also the 2-second freeze error, but that is a Pulseaudio issue, not Flash.

---

### Post by tamoneya on 2008-07-08
I have minor problems with flash but not because they dont provide a linux version but because I run 64 bit and they dont provide 64 for linux or windows.  It really annoyed me when they announced flash player 10 and it didnt have 64 bit. I am however optimistic since they are starting with 64 bit in CS4 for windows.

---

### Post by madjr on 2008-07-08
> **kaldor said:**
> I've used Linux for about 4 months now. Flash player is driving me mad. Youtube is worthless now. I did those manual fixes via synaptic, can't remember which. Worked for a while, now I can't even watch anything with flash.


The Windows version of flash is flawless from what I see. Why doesn't Adobe pay attention to people who don't use Windows?


Discuss.


well try flash 10 beta 2

[http://www.linuxloop.com/news/2008/07/05/installing-flash-player-10-prerelease-on-linux/](http://www.linuxloop.com/news/2008/07/05/installing-flash-player-10-prerelease-on-linux/)

else the only thing you can do is vote and report

|
|
|
v

---

### Post by steveneddy on 2008-07-08
> **tamoneya said:**
> I have minor problems with flash but not because they dont provide a linux version but because I run 64 bit and they dont provide 64 for linux or windows.  It really annoyed me when they announced flash player 10 and it didnt have 64 bit. I am however optimistic since they are starting with 64 bit in CS4 for windows.

I run 64 bit and I use Flash 10 beta.

Runs great here.

use nspluginwrapper - I can't tell a difference.

No more pop under menus.

---

### Post by tamoneya on 2008-07-08
> **steveneddy said:**
> I run 64 bit and I use Flash 10 beta.

Runs great here.

use nspluginwrapper - I can't tell a difference.

No more pop under menus.

Do you have a specific guide you followed or did you just follow instructions for flash 9 with nspluginwrapper.

---

### Post by gaspard.leon on 2008-07-09
I'm using the latest flash beta from Markus Thielmann's PPA:

[https://launchpad.net/~thielmann/+archive]("https://launchpad.net/~thielmann/+archive")

Just add this to your sources:
```
deb http://ppa.launchpad.net/thielmann/ubuntu hardy main
```

Then remove the normal [FONT="monospace"]flashplugin-nonfree[/FONT] package and add [FONT="monospace"]flashplugin-nonfreebeta[/FONT]

works like a charm on my:
Ubuntu 8.04 + Nvidia 5900XT 

there are still bugs, but CPU usage on You Tube is ~30% solid, instead of ~40% to 100%
Fullscreen works smoothly with no spike in CPU...

Overlaid DHTML menus (like at [www.toyota.com](www.toyota.com)) work although some stuff is not hardware accelerated yet so that particular site is slow as molasses...

---

### Post by keiichidono on 2008-07-09
Using Flash 10 beta 2 and things work pretty fine.

---

### Post by karellen on 2008-07-09
because it doesn't matter to them. Linux has an insignificant desktop market share, so they don't bother

---

### Post by mcduck on 2008-07-09
I'd say Adobe is paying a lot more attention to Linux users than Macromedia ever did.. ;)

Anybody remember running Flash 8 on Linux? I didn't think so, as there wasn't any Linux plugin, after Flash 7 Macromedia stopped providing flash plugin for Linux and many flash sites were completely broken for Linux users until Adobe aquired macromedia and started releasing stuff for Linux again..

---

### Post by barbedsaber on 2008-07-09
because there aren't enough of us for them to care. yet...

---

### Post by cookieofdoom on 2008-07-09
There aren't enough of us for Adobe to make money on... Even if they made Photoshop for Linux with all the development time that would go into it they'd probably lose money in the end. Just keep building up the community and Adobe and other companies will want to make Linux software because we'll be a larger market.

I've converted 5 people so far... going on 6, I think.

---

### Post by atomkarinca on 2008-07-09
If people complained about this to Adobe instead of the forum members, I think we would've gotten somewhere by now.

---

### Post by steveneddy on 2008-07-09
> **tamoneya said:**
> Do you have a specific guide you followed or did you just follow instructions for flash 9 with nspluginwrapper.

I literally followed the guide on the Adobe Flash web site.

It worked perfectly.

I actually had the nspluginwrapper, so i just had to DL the software, extract the folder, move the file to the correct folder, and then the command was

```

nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

```

That's funny because it was the last thing I did in terminal and popped up first.

Anyway, I had moved the **[COLOR="Blue"]libflashplayer.so[/COLOR]** file to the folder

[COLOR="Blue"]**/usr/lib/mozilla/plugins**[/COLOR]

and invoked the code, restarted Firefox, and went to the Dell.com web site to see if it changed anything.

Which it did and now the world is round again.

---

### Post by steveneddy on 2008-07-09
On another note, I would donate $10 to Adobe for a lifetime membership to Flash and Shockwave downloads for Linux if they would port if correctly and make it open sourced.

If many of us did that, then many of the open sourced applications we like to use would eventually come around to our way of thinking.

Some of you say, "What! Money given away to who!?"

But I buy t-shirts and stickers from the Ubuntu store, Suse store, Google store, PCLinuxOS store and many other open sourced projects to help support the cause, so a little going to the software that i really want to use on my Linux machine for a lifetime of use sounds OK to me.

---

### Post by grossaffe on 2008-07-09
> **cardinals_fan said:**
> I don't use beta software on principle.
Is that why you stopped using windows?

---

### Post by arm-c on 2008-07-10
Well,

I think Adobe is doing fairly well when compared with other commercial companies out there... Still, my relationship with Adobe is love/hate at moment.  The ONE SINGLE APP that they need to port to Linux completely is Acrobat Standard / Professional (either one).  I haven't found an equivalent opensource program to do what Acrobat Standard does.  Sure, there are many ways to make PDF, split PDF, etc... in Linux Land, but no single program to match the Standard version feature for feature.  This is an application I WOULD PAY FOR! -- just not the full price :)

I am currently using the Adobe Air for Linux PreRelease.  Not bad and it is ALMOST THERE.

Adobe is doing considerable amount for Linux... I just wish they would do more!  Hopefully they will stick to their pledge about releasing Linux versions.

---

