---
title: "Steam does not install games"
date: 2009-11-23
forum: Wine
---

### Post by yester64 on 2009-11-23
Hi, i am running 9.10 64bit and i am trying to install some of my games under steam.
Problem is that it does not do it.

here is what happens when i try to install a game...

```
fixme:shdocvw:ClOleCommandTarget_Exec (0x1b84e0)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1b84e0)->(L"Done")
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x1b8440)->(0x32c76c)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x1b8440)->(0x32c76c)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1


```

Not sure whats with the 'not registered'. Steam runs fine, i can log in and browse (don't have flash though).

---

### Post by beastrace91 on 2009-11-24
What is your Wine version? Be sure you are using the latest (1.1.33 as I write this). To check your current Wine version run ```
wine --version
``` in terminal.

~Jeff

---

### Post by yester64 on 2009-11-24
> **beastrace91 said:**
> What is your Wine version? Be sure you are using the latest (1.1.33 as I write this). To check your current Wine version run ```
wine --version
``` in terminal.

~Jeff

Oh, i am sorry. Yes it is that version (which is beta if i am not mistaken).

---

### Post by beastrace91 on 2009-11-25
What game(s) are you trying to install?

~Jeff

---

### Post by yester64 on 2009-11-25
> **beastrace91 said:**
> What game(s) are you trying to install?

~Jeff

I just tried to install counterstrike source, but the screen goes only dark and nothing happens.
The error codes i did post. But i am not sure how to interpret these lines really.
I read on the wine forum that it could be 32vs64 problems, but someone said that both get installed. So right now i am not sure why it is not loading.
I installed the beta version from the software center, but i assume that it should be working. or? :confused:

---

### Post by beastrace91 on 2009-11-25
Try changing to a different Wine version - yes 1.1.33 is a beta package but betas typically provide better performance in Wine technology.

~Jeff

---

