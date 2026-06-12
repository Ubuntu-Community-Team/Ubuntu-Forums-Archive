---
title: "Wine won't open any programs"
date: 2010-05-08
forum: Wine
---

### Post by Garoes on 2010-05-08
Hello,
Just to start i'd like to say that i'm new to ubuntu, i've been using it for 3 days.
Before 10.04 came out I was using the beta, Wine worked on the version I was on.
And now i've upgraded to 10.04 LTS ( I done a fresh install ) .
Everything is perfect expect when I installed wine, it seemed that programs won't run.
I tried running something I knew would work under wine, what i've ran before,
and on the window pannel it was saying "Opening Installwow.exe" Then I would wait , It never came up, all what happened was the window saying "Opening Installwow.exe" just closed itself down and didn't get anywhere.
Thanks in advance,
-Jonathan

---

### Post by Garoes on 2010-05-08
I tried reinstalling Wine.

---

### Post by Soulcage on 2010-05-08
Try right clicking on any .exe file and click properties then click on the open with tab and make sure it shows wine windows program loader, (if I have that right) if it doesn't then click add and find it in the list.

---

### Post by Zireth ZH on 2010-05-08
he just said he could open those programs before... unfortunately i dunno the fix... it happends to me too.. so im waiting for a pro to reply xD

---

### Post by Garoes on 2010-05-08
> **Soulcage said:**
> Try right clicking on any .exe file and click properties then click on the open with tab and make sure it shows wine windows program loader, (if I have that right) if it doesn't then click add and find it in the list.

sorry for the late reply, It was already set on wine, but thanks for telling me anyway.

---

### Post by Garoes on 2010-05-08
> **Zireth ZH said:**
> he just said he could open those programs before... unfortunately i dunno the fix... it happends to me too.. so im waiting for a pro to reply xD

Applications > Wine > Configure Wine >  Drives > Auto detect > Apply > Ok 
That's what I done to get it to work.

---

### Post by MichaelCooper on 2010-07-13
Come on guys....The problem is the "program" won't open. I just downloaded e-Sword and installed it with wine. This worked fine. After installing the program, it will not open when I click on it. 

I don't think the thread is asking how to open the executable. The question is why won't the program open after it's been installed. This has happened to me with 2 different programs 2 days in a row now. Everything installs, the program shows up in Wine, but will not open.

---

### Post by hikaricore on 2010-07-13
> **MichaelCooper said:**
> Come on guys....The problem is the "program" won't open. I just downloaded e-Sword and installed it with wine. This worked fine. After installing the program, it will not open when I click on it. 

I don't think the thread is asking how to open the executable. The question is why won't the program open after it's been installed. This has happened to me with 2 different programs 2 days in a row now. Everything installs, the program shows up in Wine, but will not open.

The problem is you don't seem know what you're doing, you didn't read the stickies on how to properly test and post an issue, you didn't check the wine appdb, and you seem generally unwilling to do more than click on things.
Depending on the software in question you may want to find a native alternative instead of resorting to using wine first thing, this might require some searching on your part try not to strain yourself.
Now try again and this time provide actual info, and in the future make your own thread as this one is unrelated to your specific problem.

---

### Post by helenawahlberg on 2010-11-05
Maybe you could try this

right click on the exe, choose "Properties",  "Open With" tab (or  something like it), click "Add", "Custom Command" at the bottom, and  type:
     

     wine %s 


exactly like that. Now all .exes should automatically open with Wine.

---

