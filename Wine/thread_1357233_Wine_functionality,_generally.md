---
title: "Wine functionality, generally"
date: 2009-12-17
forum: Wine
---

### Post by kumoshk on 2009-12-17
This may sound like a stupid question, but&#8212;

Why does Wine not work perfectly? This is not a complaint. I'm just curious as to the science of how Wine works. And yes, I know there are a million possible reasons, and I don't suppose it should be an easy matter to do perfect emulation.

Particularly, I'm wondering why often little things like font colors might not render properly (as with the Amazon Kindle e-book reader software for Windows). Some of the essential text is invisible on the screen that pops up when you try to use it after installation.

Do programmers make their stuff incompatible on purpose? Is it because they use new libraries that Wine developers haven't had the liberty of preparing for?

---

### Post by castlefox on 2009-12-17
First of all WINE is not an emulator is what the acronym stands for.  (I know someone else was gonna say this.  But I dont know why correcting someone on this is that big of deal.)

Wine is built in the dark.  And by that I mean there is not code dumps from direct X, its all from scratch.  Then they see what errors occur and then tweak it again.  It is part of the reason why development of WINE is so hard.  

I dont think programmers try to make app and games not work in Wine.  

Does Kindle software have DRM stuff build in that could be bother some to wine?

---

### Post by kumoshk on 2009-12-18
> **castlefox said:**
> Does Kindle software have DRM stuff build in that could be bother some to wine?
Not sure. I know it supports drm formats, but I don't think that should have much to do with the non-book text I meant to refer to, although I suppose it's possible that they extend its use to such odd things (it's a page with a form, with input boxes and a button or two, but the text for the forms and perhaps the buttons doesn't show up, so it's difficult to know what you're supposed to type there to make the program usable).

So, Wine isn't an emulator, eh? Reminds me of how Lame isn't an MP3 encoder . . . I don't get the latter, yet, but I think what you said about Wine makes sense. Thanks.

---

### Post by beastrace91 on 2009-12-18
> **castlefox said:**
> First of all WINE is not an emulator is what the acronym stands for.  (I know someone else was gonna say this.  But I dont know why correcting someone on this is that big of deal.)

Because saying Wine is an emulator implies a whole slew of things. Wine is providing a software layer - not a hardware layer. If Wine was a full emulator then it would for instance be able to run the x86 Windows applications on ARM & Cell processors - but this is not what it does. Its a technicality really but it matters :)

~Jeff

---

### Post by kumoshk on 2009-12-18
> **castlefox said:**
> I dont think programmers try to make app and games not work in Wine.
Hmm. On the other hand, is there a way they can specifically ensure their programs will work with wine, without testing them on Wine? I mean, are there some particular libraries Windows programmers can use that are definitely compatible, all-around? If not, would they be hard for a Wine developer to make (as far as that sort of thing goes)?

---

### Post by YokoZar on 2009-12-19
> **kumoshk said:**
> Hmm. On the other hand, is there a way they can specifically ensure their programs will work with wine, without testing them on Wine?
No.  Even Wine developers don't know when particular applications will work without testing them.  Even applications using parts of the API that have already been written could turn out to be relying on particular rare Windows bugs that we have to duplicate.  This is even true if we've written conformance tests and were reasonably certain that part was working: we might not think to test for something until an application does it weirdly enough.

> I mean, are there some particular libraries Windows programmers can use that are definitely compatible, all-around? If not, would they be hard for a Wine developer to make (as far as that sort of thing goes)?
Development priority is given to the parts of the API that applications actually use.  So I suppose one way to make an application probably work in Wine is to make it very similar to an application that already works in Wine.

---

### Post by beastrace91 on 2009-12-19
> **YokoZar said:**
> make it very similar to an application that already works in Wine.

Thusly why most anything source engine based works under Wine :)

~Jeff

---

