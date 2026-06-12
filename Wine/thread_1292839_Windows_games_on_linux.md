---
title: "Windows games on linux"
date: 2009-10-16
forum: Wine
---

### Post by 2ndsayton on 2009-10-16
Kinda new here and Im still finding my feet. Ive got windows vista ultimate and Ubuntu 8.0.4 on dual boot but Im thinking of totally dropping windows. Im also planning of migrating out of console gaming to more PC gaming. 

To keep it short - 

How well do windows games run on Linux in general?

Say a new game comes our how likely is it work immediately, as in compatibility ?
             
Linux > Windows ?

Basically Im looking for a light OS to game on and vista just feels slow. Windows 7 also looks like competition for linux which is the main reason im here.

Off-topic but nice smiley  :guitar:

---

### Post by phreakyo on 2009-10-16
Frankly, don't expect to be playing brand new games immediately on linux. 

There are some exceptions where it turns out to work well on release (thinking of Wolfenstein here). Also, the biggest name games usually get more attention from debuggers and developers for wine/crossover, so you could probably have them playable in a few months - but again, generally you won't be playing them immediately.

End story - if you are serious about keeping up with latest games, stay on Windows.

---

### Post by Freddie1984 on 2009-10-16
I have had Ubuntu 8.04 for going on 2yrs and my experience with running windows games on my comp has been tricky but if you have the time and alittle know how there is always a way to get what you want. I think with the right emulator you will have some success in getting it done.

---

### Post by 2ndsayton on 2009-10-16
Thanks I guess. Looks like ill be doing the same as everyone else then, putting up with vista a little longer until Windows 7

---

### Post by gadget3000 on 2009-10-19
I have an Xfi soundcard so gaming is practically impossible on Linux for me. I have tried though and its taken me ages to get left 4 dead to a playable fps. Same for TF2. I didn't know crossover did a trial though until now so I'm trying that and if it works, buying it. Then it's bye bye Windows 7 RTC.
Once valve gets its linux libraries released Linux downloads will go crazy. Hopefully. This is valve we are talking about.:(

---

### Post by beastrace91 on 2009-10-19
> **2ndsayton said:**
> Thanks I guess. Looks like ill be doing the same as everyone else then, putting up with vista a little longer until Windows 7

[Windows 7 == Windows Vista 1.1](http://jeffhoogland.blogspot.com/2009/10/comments-on-windows-7.html)

That being said if you really want to do the latest and greatest PC gaming stick to Windoze.

~Jeff

---

### Post by Dullstar on 2009-10-20
> **Freddie1984 said:**
>  I think with the right emulator you will have some success in getting it done.
WINE:

**W**INE **i**s **n**ot an **E**mulator.

---

### Post by Freddie1984 on 2009-10-21
> **Dullstar said:**
> WINE:

**W**INE **i**s **n**ot an **E**mulator.


I am ok with your opinion but the truth is WINE is an Emulator. 

Microsoft Windows Compatibility Layer (Binary Emulator and Library)
Wine is a compatibility layer for running Windows applications on Linux.
Applications are run at full speed without the need of cpu emulation. Wine
does not require Microsoft Windows, however it can use native system dll
files in place of its own if they are available.


[ [img]http://www.badongo.com/t/640/7530878[/img]](http://www.badongo.com/pic/7530878)

---

### Post by hikaricore on 2009-10-21
> **Freddie1984 said:**
> I am ok with your opinion but the truth is WINE is an Emulator. 

Microsoft Windows Compatibility Layer (Binary Emulator and Library)
Wine is a compatibility layer for running Windows applications on Linux.
Applications are run at full speed without the need of cpu emulation. Wine
does not require Microsoft Windows, however it can use native system dll
files in place of its own if they are available.


[ [img]http://www.badongo.com/t/640/7530878[/img]](http://www.badongo.com/pic/7530878)

No really WINE is not an emulator.
Screenshotting the description from the Ubuntu package doesn't make your belief to be true.

[http://wiki.winehq.org/FAQ#head-c9e6502ad636315e905d07f7e44594757a6738e3](http://wiki.winehq.org/FAQ#head-c9e6502ad636315e905d07f7e44594757a6738e3)

---

### Post by handy on 2009-10-21
> **Freddie1984 said:**
> I am ok with your opinion but the truth is WINE is an Emulator. 

Microsoft Windows Compatibility Layer (Binary Emulator and Library)
Wine is a compatibility layer for running Windows applications on Linux.
Applications are run at full speed without the need of cpu emulation. Wine
does not require Microsoft Windows, however it can use native system dll
files in place of its own if they are available.


[IMG]http://www.badongo.com/pic/7530878[/IMG]

Wine is not a compatibility layer, it is the rewrite in a legal fashion, of the required Windows system files.

There is a big difference there, in that there is a missing layer or emulation, as Wine actually *does it*, it does not pretend to do it.  Wine does not fool the software it is running, it does the job that the software wants, & quite often it removes inherent Windows bugs in the process.

A compatibility layer is another level of interpretation to slow things down.

A supply of the legally totally rewritten libraries & such is not.

Many people find that Windows software that they run under Wine or Crossover for example runs as fast if not faster than it does natively. (I know I do)

Unfortunately this is not the situation for all Windows software, though this is not at all due to a slow down due to a layer of emulation, it is due to certain files having not as yet having been fully *duplicated* in Wine.

---

### Post by YokoZar on 2009-10-21
> **hikaricore said:**
> No really WINE is not an emulator.
Screenshotting the description from the Ubuntu package doesn't make your belief to be true.

This argument isn't really helpful.  It's semantics at best.

The point is there's confusion about what the word "emulator" means, as it has multiple meanings.  Some people expect something like DOSBox or zsnes, which are basically virtual machines that emulate a complete CPU.  Wine doesn't do that, which is why it doesn't work on different architectures.

But "emulator" can also mean "does the stuff a different system does".  This is also what "compatibility layer" can mean, for instance the Linux compatibility layer that Solaris has.  Wine would fit this definition, at least when it works.

So I shy away from calling it an emulator and aim instead for functional phrases like "runs Windows programs".  Emulator's not technically *wrong*, it just gives some people the wrong ideas (eg that it's slow or is a "container" application in its own right).

It's sort of like when people say WINE instead of Wine.  I don't like it, but at this point I've just stopped caring as it's ultimately harmless - the best I can do is update the FAQ and hope it spreads.

Cheers.

---

### Post by handy on 2009-10-21
Interestingly, I find anyway, that I oppose people's incorrect (imho) interpretation of what Wine is/does.

Which means that the meaning of my responses are therefore dynamic. :)

---

### Post by hikaricore on 2009-10-21
> **YokoZar said:**
> It's sort of like when people say WINE instead of Wine.  I don't like it, but at this point I've just stopped caring as it's ultimately harmless - the best I can do is update the FAQ and hope it spreads.

Cheers.

Wine was originally WINE so I call it as such.
Some of us are set in our ways.  :)

---

### Post by handy on 2009-10-21
> **hikaricore said:**
> Wine was originally WINE so I call it as such.
Some of us are set in our ways.  :)

Yes I sometimes use WINE as well due to it at least being the original name.

So they have changed it to Wine now?

---

### Post by hikaricore on 2009-10-21
> **handy said:**
> Yes I sometimes use WINE as well due to it at least being the original name.

So they have changed it to Wine now?

Pretty much.

[http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

> **1.1. Why do some people write WINE and not Wine?**

They are using the acronym "Wine Is Not an Emulator", the original name for the project. While recursive acronyms are clever, there really is no point to the capital letters. They look ugly, so please use the simpler, current name of the project: Wine. It's what we use. 

---

### Post by handy on 2009-10-22
> **hikaricore said:**
> Pretty much.

[http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

Thanks, I'll try to keep that in mind in the future. :)

---

