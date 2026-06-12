---
title: "WoW install issues pulling out hair... now"
date: 2009-07-07
forum: Wine
---

### Post by xixpsychoxix on 2009-07-07
Ok, i apologize like five million times for yet ANOTHER WoW thread, but I am seriously pulling my hair out here. I have read every thread, every post, every everything that i could find on installing WoW on wine and it STILL doesnt work.  I installed the game from the internet and the installer crashed. I tried installing the game from the cd, it tried to do an online update, which crashed. finally i copied it from a windows partition, but the game will not start. It says "starting WoW.exe" at the bottom but then it just goes away. i have set all the options i could find that need to be set and am trying to find the wine WoW patches but can't. I installed from source code which did not work so i uninstalled then reinstalled from the repositories with the same results. It's not fair. I love ubuntu but i want to STRANGLE IT right now!!!

---

### Post by Rody on 2009-07-08
what happens when you run glxgears?

---

### Post by Hairybudda on 2009-07-08
Why don't you launch wine from the terminal and post the output so we at least know where it's crashing?

---

### Post by xixpsychoxix on 2009-07-08
umm im not quite sure what glxgears is... let me get that output here real quick and ill see.

here:

```

err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Program Files\\World of Warcraft\\WoW.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\World of Warcraft\\WoW.exe" failed, status c0000135

```

so looking at this i'm guessing i should look up "Missing OPENGL32.dll error" on google? Unless someone already knows what to do or this is a more specific issue?

---

### Post by NightMKoder on 2009-07-08
Mother of god, what did you do to your prefix?

rm -rf ~/.wine

and start over. Make sure you don't install anything funky. WoW is one of the apps where you don't need to tinker much at all.

---

### Post by jordonstyrk on 2009-07-20
alright im kind of in the same boat as you. i have done everything that [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) has instructed. i have tried both install off the cd's and from download. when i go to run the download it asks for username and password again, then im back to my desktop. when i try to run it off the cd's thru the terminal i get this errror 

wine: could not load L"C:\\windows\\system32\\install.exe": Module not found

please someone help. im as new with ubuntu as they come.
thanks

---

### Post by NightMKoder on 2009-07-20
> **jordonstyrk said:**
> alright im kind of in the same boat as you. i have done everything that [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) has instructed. i have tried both install off the cd's and from download. when i go to run the download it asks for username and password again, then im back to my desktop. when i try to run it off the cd's thru the terminal i get this errror 

wine: could not load L"C:\\windows\\system32\\install.exe": Module not found

please someone help. im as new with ubuntu as they come.
thanks

make sure you cd into the folder with the install.exe file. That message means that it can't find the file (install.exe).

EDIT: cd as in change directory, not CD.

---

### Post by dslreports_snakeoil on 2009-07-21
I have the same issue as you.  It was suggested to me to try this:

wine Wow.exe -opengl

un that from wherever you have WoW installed (e.g. /home/user/.wine/drive_c/Program Files/World of Warcraft)

Problem is, I haven't figured out how to do that.
My WOW hasn't created the WTF file yet, so I can't make any changes to the wtf file.

---

