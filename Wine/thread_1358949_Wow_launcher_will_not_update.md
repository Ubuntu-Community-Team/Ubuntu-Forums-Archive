---
title: "Wow launcher will not update"
date: 2009-12-19
forum: Wine
---

### Post by psyboy55 on 2009-12-19
Im trying to get the world of warcraft launcher to update to the latest patch (3.3 i think.) I ran the launcher and it downloaded the new launcher. Now it only has the option to play and it does not patch. when i click play wow does not start up. when i directly run wow i can see im on patch "3.0.1 (8874) (release)" how do get to the latest patch?

---

### Post by YokoZar on 2009-12-19
If you run wow manually from the terminal and skip the launcher altogether it should patch and run fine.

---

### Post by Alatar1 on 2009-12-19
Browse yourself to home/yourusername/.wine./drive_c/program files/world of warcraft and run the game via WoW.exe NOT i repeat NOT launcher.exe, once your in the game login screen, on the bottom left un-check the box that says "show launcher".

DO NOT use the launcher, it locks you out of your WoW directory, has been doing so to EVERYONE on linux/wine since the last patch before 3.3, just do'nt use the launcher and all will be well

Oh and after it patches it will open the launcher by default, and lock your WoW folder again, youll have to go back in after patching to unlock it again, if you don't know how to unlock it,post back kthxbai

edit*****
you can aslo do it how yokozar stated, just be sure you doing it through WoW.exe and NOT launcher.exe, as i said it can and WILL lock you out.

---

### Post by psyboy55 on 2009-12-19
I now how to unlock my self out i've down it a million times. The problem i have is if i manually boot wow it wont patch, and if i run he launcher it wont patch. Can I manually patch some how?

---

### Post by YokoZar on 2009-12-19
> **psyboy55 said:**
> I now how to unlock my self out i've down it a million times. The problem i have is if i manually boot wow it wont patch, and if i run he launcher it wont patch. Can I manually patch some how?

I believe there are individual patch files you can download somewhere on the internet, yes.

---

### Post by Alatar1 on 2009-12-19
It won't patch if you run it manually thats odd... Ya i'm sure there are manual patch file. But to be sure tokeep the launcher disabled. it WILL lock you ALWAYS, DONT EVER EVER EVER use the launcher...EVER!!

---

### Post by hikaricore on 2009-12-20
This only seemed to start happening around the time that Windows 7 was released.
How much do you want to bet this bug is caused by some attempt to work properly with a new file persission system?

---

### Post by xwulf on 2009-12-21
I don't suggest using launcher either... to patch to 3.3 go to filefront and browse wow files and under "official patches" you can find the wow patches download them run them through wine and they'll install fine. afterward open wow through the .exe and all should be well. That's what I had to do.

---

