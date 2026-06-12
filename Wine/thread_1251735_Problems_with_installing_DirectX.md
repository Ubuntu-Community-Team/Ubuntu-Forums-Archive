---
title: "Problems with installing DirectX"
date: 2009-08-28
forum: Wine
---

### Post by pevzi on 2009-08-28
I have problems with installing DirectX in wine. After running DirectX Installer using winetricks I see the following error in terminal:

err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
.....

So no one of files are copied and DirectX doesn't install (but winetricks says that installing is successfull). After googling I found that quite many people met the same problem but I couldn't find any solutions. What can I do to install DirectX correctly?

Thanks.

---

### Post by scorp123 on 2009-08-28
> **pevzi said:**
> I have problems with installing DirectX in wine.  If you want Direct3D in a virtual machine you might have better luck with this guide:


"Running 3D DirectX Games Using Virtualbox And Wine3D"
[http://www.ubuntumagazine.net/?p=1668](http://www.ubuntumagazine.net/?p=1668)


EDIT: My knowledge about WINE was outdated it seems?
[http://scassick.wordpress.com/2008/11/14/install-direct-x-90c-with-wine/](http://scassick.wordpress.com/2008/11/14/install-direct-x-90c-with-wine/)

Sorry about that. I completely missed that it is indeed possible now.

---

### Post by scorp123 on 2009-08-28
Another possibility:

"CrossOver Games"
[http://www.wine-reviews.net/wine-reviews/cxgames-linux/play-windows-games-on-linux-with-crossover.html](http://www.wine-reviews.net/wine-reviews/cxgames-linux/play-windows-games-on-linux-with-crossover.html)

---

### Post by hikaricore on 2009-08-28
You shouldn't ever need to install directx... what are you trying to do?

---

### Post by pevzi on 2009-08-28
Hmm. In old versions of Ubuntu (for example 8.04) I installed DirectX in Wine successfully. And it worked, and helped to run a lot of games. So I think it's not as useless as you think it is (:

---

### Post by pevzi on 2009-08-28
> **scorp123 said:**
> 
[http://scassick.wordpress.com/2008/11/14/install-direct-x-90c-with-wine/](http://scassick.wordpress.com/2008/11/14/install-direct-x-90c-with-wine/)

Thanks but it not works (

---

### Post by hikaricore on 2009-08-28
> **pevzi said:**
> Hmm. In old versions of Ubuntu (for example 8.04) I installed DirectX in Wine successfully. And it worked, and helped to run a lot of games. So I think it's not as useless as you think it is (:

The issues with games can be solved by adding 1 or 2 libraries.
Installing DirectX is overkill and can lead to other issues, this is a fact.

---

### Post by pevzi on 2009-08-29
> **hikaricore said:**
> The issues with games can be solved by adding 1 or 2 libraries.
Installing DirectX is overkill and can lead to other issues, this is a fact.
Can you name these libraries? Because I tried to extract some CABs from DirectX package but it was useless.

---

### Post by hikaricore on 2009-08-29
You still haven't said why you even need directx libraries, these are only needed on a per game basis.
As I said before unless you are having trouble with something there is no reason for it.

---

### Post by ackanao on 2009-08-29
@pevzi
You should never ever install DirectX in Wine unless you know exactly what you're doing - but if you want to mess up your wine prefix feel free to do so. Before you go and screw things up, please read this:

Wine User Guide:
[http://www.winehq.org/docs/wineusr-guide/index]("http://www.winehq.org/docs/wineusr-guide/index")

Wine FAQ:
[http://wiki.winehq.org/FAQ]("http://wiki.winehq.org/FAQ")

and specially this:
[http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2]("http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2")

hikarikore is right you only need few DX libraries and if you want to extract them use cabextract - it's in the repos just use: 

```
sudo apt-get install cabextract
``` (read man pages to see how to use it)

@hikarikore
I have a suggestion - please make one sticky with explicit warning about DirectX because these questions will never stop and it's really annoying answering them all over again.

-----------
ackanao

---

### Post by hikaricore on 2009-08-29
> **ackanao said:**
> 
@hikarikore
I have a suggestion - please make one sticky with explicit warning about DirectX because these questions will never stop and it's really annoying answering them all over again.

-----------
ackanao

This is a good idea, however you may want to ask YokoZar to add it to the WINE sticky as I have stepped down from forum moderation and no longer have access.  :p

---

### Post by pevzi on 2009-08-29
> **ackanao said:**
> 
and specially this:
[http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2](http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2)

Hmm. OK, thank you for this information. If DX is already implemented in wine so it would be enough to run the most of games I think.

> **ackanao said:**
> 
hikarikore is right you only need few DX libraries and if you want to extract them use cabextract - it's in the repos just use: 

```
sudo apt-get install cabextract
``` (read man pages to see how to use it)


Yes, I know about it and earlier this way helped me to run some games. OK, maybe I'll try it again if something wouldn't work.

> **ackanao said:**
> 
@hikarikore
I have a suggestion - please make one sticky with explicit warning about DirectX because these questions will never stop and it's really annoying answering them all over again.


Yes, it would be nice and would help to avoid such silly questions like mine (: Sorry for it.
Thank you all.

---

### Post by ackanao on 2009-08-29
> **hikaricore said:**
> ...as I have stepped down from forum moderation and no longer have access.  :p

I didn't even notice that change - Although I'm a relatively new member I've visited this forum for almost 2 year now and I have nothing but respect for you; as far as I'm concerned, you'll always be an important Forum Staff member. :KS

> **hikaricore said:**
> This is a good idea, however you may want to ask YokoZar to add it to the WINE sticky

OK. I'll ask YokoZar about this - maybe i was a bit rude in my previous post but these guides about installing DirectX are all over the place and I think that this is a big issue that has to be addressed.

> **pevzi said:**
> Yes, it would be nice and would help to avoid such silly questions like mine (: Sorry for it.
Thank you all.

Don't worry about that you did nothing wrong - I was a bit rude and I'm sorry about that but this forum and Wine mailing list are full with these questions; when I google about Wine there's a whole bunch of guides suggesting installing DirectX and this is wrong in most cases.

---

### Post by bl33d on 2009-08-29
Actually installing DirectX is a good idea if you do it the right way. I always copy the system 32 folder, then install DirectX, and then paste the copied system 32 folder contents back into the original system 32 folder.

Works perfectly every time :)

---

### Post by ackanao on 2009-08-30
> **bl33d said:**
> Actually installing DirectX is a good idea if you do it the right way. I always copy the system 32 folder, then install DirectX, and then paste the copied system 32 folder contents back into the original system 32 folder.

Works perfectly every time :)

Do what you wish - i posted links to the official Wine documentation in my previous posts so you can read it or ignore it (it's your own choice).

I use Wine for years now and never had a need for full-blown DirectX installation - even an ancient versions of Wine works perfectly without "native overrides". If I understood you correctly you're using native system32 folder with your Wine setup - I have a simpler solution: Just use Windows instead.

---

### Post by hikaricore on 2009-08-30
I think he's trolling now... lol

---

### Post by bl33d on 2009-08-30
> **ackanao said:**
> Do what you wish - i posted links to the official Wine documentation in my previous posts so you can read it or ignore it (it's your own choice).

I use Wine for years now and never had a need for full-blown DirectX installation - even an ancient versions of Wine works perfectly without "native overrides". If I understood you correctly you're using native system32 folder with your Wine setup - I have a simpler solution: Just use Windows instead.

No I mean I copy the original, pure WINE system 32 folder, add a couple of .DLL's that are needed to install the DirectX 9.0C redistributable to the /windows/system32 folder, then install DirectX, and then copy & paste the contents of the copied WINE system32 back into /windows/system32. Like I said it works everytime.

Oh and hikaricore, no one is trolling so don't even try that little game.

---

### Post by YokoZar on 2009-09-09
> **bl33d said:**
> No I mean I copy the original, pure WINE system 32 folder, add a couple of .DLL's that are needed to install the DirectX 9.0C redistributable to the /windows/system32 folder, then install DirectX, and then copy & paste the contents of the copied WINE system32 back into /windows/system32. Like I said it works everytime.

Oh and hikaricore, no one is trolling so don't even try that little game.
All this does is replace any installed DirectX files with Wine supplied ones.  It works because you're basically deleting the DirectX installation you just made and getting standard Wine instead.

---

### Post by hikaricore on 2009-09-10
I tried to tell him this but he was a damn idiot.  :p

---

### Post by b1aq on 2009-09-10
> **YokoZar said:**
> All this does is replace any installed DirectX files with Wine supplied ones.  It works because you're basically deleting the DirectX installation you just made and getting standard Wine instead.

*claps*

Do you think that's maybe why I paste it back? It also means I can install all the d3dx9_xx.dll's without having to rely on winetricks, which can bork quite badly?

---

### Post by YokoZar on 2009-09-11
> **b1aq said:**
> *claps*

Do you think that's maybe why I paste it back? It also means I can install all the d3dx9_xx.dll's without having to rely on winetricks, which can bork quite badly?
How is winetricks is borking?  Have you reported that problem?

---

