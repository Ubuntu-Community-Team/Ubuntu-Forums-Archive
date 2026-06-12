---
title: "Photoshop CS2"
date: 2009-02-14
forum: Wine
---

### Post by Littlejohn94 on 2009-02-14
Can someone please help me, when ever i open photoshop cs2.exe with wine it opens and it says please select your langauge, i click english and then it just disapears..does same thing with anyother language aswell. Please don't post things like just use GIMP etc. I am use to photoshop and would like to use that. Thanks.

---

### Post by Carl H on 2009-02-14
Open it from the command line and you'll get some error message back when it closes.

---

### Post by Littlejohn94 on 2009-02-14
I'm a noob, how would i open it in command line?:S

---

### Post by Carl H on 2009-02-14
You'll need to know what directory your Photoshop .exe file is in. In the file browser, select View Hidden Files, and look for the .wine directory. Go in there, and navigate  your way through (I'm guessing here) c_drive, Program Files, Adobe, PhotoShop, whatever, until you get to the one with the right exe file in it. 

From the Gnome menu panel, Applications -> Accessories -> Terminal  will get you a command prompt. 

You need to move the prompt through the directories to the one with the exe in. You don't have to type the whole lot in though, just type the first few letters of each directory and press TAB, it will complete it for you. If it doesn't, type a couple of extra letters in. 

So, assuming that it's in ".wine/c_drive/Program Files/Adobe/Photoshop", you'd type :-

**cd ".wi[TAB]/c_[TAB]/Pro[TAB]/Ado[TAB]/Pho[TAB]" **then press return. Remember the " at the start and the end. 

Type **pwd** to see what directory you're now in - this should be the one that you found at the start using the file browser.

Now type **ls *.exe **and the exe you want to run should be listed (There may be others as well). if it isn't, you're in the wrong directory! (Type **cd ~** to start again from the top)

Now type **wine cs2.exe **(assuming it's called cs2.exe) and Wine should run it. 

Keep an eye on this terminal window while Photoshop runs (and then crashes) and whatever appears there, copy it and paste it back in this thread. Hopefully somebody should be able to give you a clue as to the problem.

---

### Post by khelben1979 on 2009-02-14
I have read that installing DirectX 9.0c within the Wine program makes some Wine applications work where it normally wouldn't. You'll find the thread [here]("http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html").

Maybe it's worth a try?

---

### Post by hikaricore on 2009-02-14
> **khelben1979 said:**
> I have read that installing DirectX 9.0c within the Wine program makes some Wine applications work where it normally wouldn't. You'll find the thread [here]("http://www.wine-reviews.net/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html").

Maybe it's worth a try?

Please don't advise users to install directx under WINE.

There are few cases where this will do anything but harm and can be easily avoided by adding only a couple dll files.

---

### Post by khelben1979 on 2009-02-14
I see, I didn't know that.

---

### Post by Littlejohn94 on 2009-02-14
Carl the thing is i haven't even installed it yet.. I extracted the iso then right clicked on setup.exe and go open with Wine program loader or what ever it is and then it comes up with Adobe installer thingo and says Please select which language you would like to use i select one and then it just disappears :S

---

### Post by Littlejohn94 on 2009-02-14
nvm, i found what the problem was xD there was another folder and i went in that and there was another setup.exe, thanks for all your help guys.

---

