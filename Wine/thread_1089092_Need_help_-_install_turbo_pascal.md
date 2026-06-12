---
title: "Need help - install turbo pascal"
date: 2009-03-06
forum: Wine
---

### Post by themacedonian on 2009-03-06
I have installed free pascal for ubuntu, fp working good but code for fp is diferently then turbo pascal ( compiler on windows ) 
Can i install turbo pascal compiler on wine and compile my code ? 
10x

---

### Post by cmay on 2009-03-06
you might. or try dosbox. in fact i have had turbo pascal on a old spare computer using freedos so i guess dosbox would be more optimal

---

### Post by themacedonian on 2009-03-06
Can i install turbo pascal on wine and compile my code ? 
If i can't, maybe have any tips with fp, i can change or edit this compiler to compile like turbo pascal. 
10x for reading me :)

---

### Post by DOS4dinner on 2009-03-08
Have you tried installing and compiling your code yet? (Nothing in your posts said so, so I had to ask). The only way you're going to find out is by testing it.

Now, which turbo Pascal is this? If it's the older-than-dirt ASCII-art no-thrills version, (As made freeware and downloadable from [here]("http://classicdosgames.com/utilities.html") at the bottom of the page--there's also a screenshot of it you can click on), it will run and compile code in DOSBox perfectly. Odds are it won't work in Wine if it is that version, as DOS programs don't have the best of luck in Wine.

If it is a newer windows version, you will just have to test it. Try some various Windows versions in winecfg if it doesn't work in one of the others. If it does work, odds are it will be able to compile your code.

As for getting Freepascal to work, it probably won't. Borland's Turbo Pascal probably has some extra pre-done non-standard functions in it that Freepascal can't do. I know there C++ compiler is like this, and I'd assume their pascal compiler would be the same. Of course, I have no experience with Pascal or its compilers, so I really have no clue if this applies to you.

Good luck though!

---

