---
title: "E-Sword installing other Bibles?? Hangs"
date: 2006-12-19
forum: Ubuntu Christian Edition
---

### Post by shane2peru on 2006-12-19
Does anyone else have this problem of installing Bibles on E-Sword running under wine?  It just hangs and gives me this error in the terminal:
```

fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub
fixme:richedit:RichEditANSIWndProc EM_FORMATRANGE: stub

```  and continues to run this error, until I stop it.  Any ideas?  E-Sword runs fine, I would just like to be able to install some more Bibles.

Shane

---

### Post by Darrious on 2006-12-19
Hmm....

Try this 
[B]

Add these lines to the [DllOverrides] section of ~/.wine.config:
"msi" = "native"
"msiexec.exe" = "native"
Then
Type wine setup752.exe to install e-Sword.
Type wine e-sword.exe in the installation directory to run e-Sword.[/B]

---

### Post by shane2peru on 2006-12-19
I added the two overrides in the library section when running ```
winecfg
```  it didn't seem to help.  I can run E-Sword, I just can't install extra Bibles.  That is when it locks up.  Thanks.

Shane

---

### Post by Darrious on 2006-12-19
It runs just fine for me. I will try to install extra bibles and see what it does.

---

### Post by shane2peru on 2006-12-19
ok, thanks! It seems to run well for me too.  I have only found one minor problem, it crashed on me while looking at Mat 2:11 and then clicking on the Matthew Henry Commentary.  If I went to another verse it was fine.  I was also using the Reina Valera Gómez Bible.  It was wierd.  If I used any other commentary it was fine.  I think just an odd error.

   However installing Bibles is my problem.

Shane

---

### Post by balloons on 2006-12-19
well if it helps... don't install the bibles. Simply copy them to the esword directory. They don't need to be installed. If the bible is in a exe format, install it on windows, then copy the file it creates in the esword directory to the wine esword directory. I just keep about 1 gb of resources on a cd, and point esword to it. Works great, no install needed.

---

### Post by shane2peru on 2006-12-19
Well, that is a solution, but I haven't booted into Windows in about a month.  There must be a fix to install these right from wine.  After all the program installed fine.  Doesn't make sense to me.  I did copy what I had in Windows over, that is how I got what I have, but I would like to install some new ones with out having to reboot, install, then reboot, then copy, then change permissions.  Kind of cumbersome.  If I get to a point where it is a must, I will.  Thanks.

Shane

I'm on the verge of letting Windows go, just a few hold ups.

---

### Post by Darrious on 2006-12-19
I actually had a tough decision when leaving Windows.

But I just said, "Linux is better of course." :D

---

### Post by shane2peru on 2006-12-20
> **Darrious said:**
> I actually had a tough decision when leaving Windows.

But I just said, "Linux is better of course." :D

I agree that Linux is better.  My problem is I use ACT! 6.0 which is a contact management program.  There is **NO EQUAL**  for it in Linux.  I have almost got it running under wine, just a few hang ups.

---

### Post by nello2012 on 2006-12-30
I placed the downloaded file in same directory as e-sword, run the exe file (e.g wine kjv.exe).  Afer it was successfully installed I run e-sword then went to option-resource-loation and change the location to where e-sword is. This worked for me. Please note that although location already points to the correct location you still have to do it again.

---

### Post by shane2peru on 2006-12-30
> **nello2012 said:**
> I placed the downloaded file in same directory as e-sword, run the exe file (e.g wine kjv.exe).  Afer it was successfully installed I run e-sword then went to option-resource-loation and change the location to where e-sword is. This worked for me. Please note that although location already points to the correct location you still have to do it again.

Hey thanks, that works!!!  Great.

Shane

---

### Post by oeb on 2007-01-07
I don't see any selections for .top files under options-resources-location.  Have you installed topical files within the e-Sword directory and then had them to work without further changes to settings such as those for the .bbl, .cmt, and .dct files shown under ...location?  Specifically, I'm interested in installing the topical file just posted to [http://www.e-swordfiles.com/files/McGee_J_Vernon_-_Thru_The_Bible_Notes_And_Outlines.exe](http://www.e-swordfiles.com/files/McGee_J_Vernon_-_Thru_The_Bible_Notes_And_Outlines.exe) but I'm reluctant to give it a try without first getting advice of some more versed in the use of wine than I am.  TIA, oeb

---

### Post by shane2peru on 2007-01-07
Top files work fine.  They are located in the commentary section.  Click on the Topic Notes, and at the bottom you can select what topic notes you want to read/look at.  Top files work fine for me.  You should be able to install them with out a problem as well, also if you have any problem you may need to save the file in the e-Sword directory in order to install it as has been stated in this post.

Shane

---

