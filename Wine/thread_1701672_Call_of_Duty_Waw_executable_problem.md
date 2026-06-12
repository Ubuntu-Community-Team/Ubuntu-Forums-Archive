---
title: "Call of Duty Waw executable problem"
date: 2011-03-06
forum: Wine
---

### Post by mclizardman on 2011-03-06
I am trying to run cod waw through wine, but i can't make any of the folders into executables because its read only. How do I get around this? Thanks.

---

### Post by mclizardman on 2011-03-07
Bump

---

### Post by xtremesupremacy3 on 2011-03-07
what do you mean? 

Making folders executable??

are you trying to just run an exe file?

---

### Post by howefield on 2011-03-07
Moved to the "*Wine*" forum.

---

### Post by mclizardman on 2011-03-07
> **xtremesupremacy3 said:**
> what do you mean? 

Making folders executable??

are you trying to just run an exe file?
Umm, yes. Isn't that what you are supposed to do? Right click on the file, properties, then select allow running as executable. Is is incorrect? I am going off the website........

---

### Post by xtremesupremacy3 on 2011-03-07
well what I usually do is I insert a DVD for instance and use the terminal to go to that directory ('cd /media/<NAME OF CD>')

Then i type 'ls' to show whats on the cd and look for the setup file...then to execute it (and any .exe files with wine) i just type 'wine startup.exe'.

The rule basically is...find the exe file and run it with command 'wine'...or right click on it and select 'open with Wine Program'.

But have you tried PlayOnLinux?

If not, I recommend looking into it. You get a list of games, then select the game you want to install and click install...it loads a little install script and does all the hard work for you, giving you more time to play, less to mess about

---

### Post by mclizardman on 2011-03-07
When I enter the name of the DVD (CODWAW) it says no such file or directory....

---

### Post by xtremesupremacy3 on 2011-03-07
okay well lets see if its in the correct folder as it is on mine.

type in the following in a terminal:
```
cd /media
```

once there type
```
ls
```

This should hopefully show the name of the DVD you seen before.
If so, type in but DON't hit enter yet:
```
cd C
```

then hit the TAB button.

If all goes well, it should complete the command for you, then hit enter

then type ls again and look for the setup file which can then be run with the wine command.

If you haven't used Winetricks yet, then I do recommend PlayOnLinux as it is going to save you a lot of headaches. It will mean installing different codecs, fonts, libraries etc, that don't come standard with Wine which POL will install for you.

It's just something worth considering

---

### Post by mclizardman on 2011-03-07
Wow, you are awesome. Setup started right up when I followed your directions. Too bad I can't find my installation code. Lol, anyway thanks, I will use these instructions for other games I have in mind. Thanks again!!!!

---

