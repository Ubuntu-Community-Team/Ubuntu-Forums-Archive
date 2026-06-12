---
title: "Way to speed up WINE load?"
date: 2010-06-17
forum: Wine
---

### Post by dpatel on 2010-06-17
Hi -

I am using Wine 1.1.42 in Ubuntu 10.04. I have MS Office 2003 installed. But I have a couple of issues:

- The first time I open one of the Office suite (e.g. Word) it can take 15-20secs to open. Thereafter it maybe 5-6secs. Is there a way to speed up the loading?

- I also find that when opening a file in Powerpoint takes a long time (even small files).

Can you help please?

---

### Post by ghostborg on 2010-06-17
Just a suggestion, and I'm sure you are using MS 2003 for a specific reason, but try OpenOffice and set your default file save to either MSOffice 2003 or 2007/XP. I have found most programs under Wine have some quirk. You could also try VirtualBox.

---

### Post by asdfoo on 2010-06-17
> **dpatel said:**
> Hi -

I am using Wine 1.1.42 in Ubuntu 10.04. I have MS Office 2003 installed. But I have a couple of issues:

- The first time I open one of the Office suite (e.g. Word) it can take 15-20secs to open. Thereafter it maybe 5-6secs. Is there a way to speed up the loading?

- I also find that when opening a file in Powerpoint takes a long time (even small files).

Can you help please?

1.  Wine has to go through a startup procedure, if it's not already running this takes some time.

2. Some fixes went into Wine which made some programs work but slowed down Microsoft Office, a solution is yet to be found but with any luck it'll be addressed soon.

ps. 1.1.42 is some months old, 1.2-rc3 was released 1 week ago.

---

### Post by dpatel on 2010-06-17
Thanks for the replies.

@asdfoo: Is there a way to have WINE load at startup and stay running? I'm guessing no...

And why would it load faster second time - does WINE stay in memory or is there some sort of prefetch/preload going on?

I'll try 1.2 - are the same MS Office related regressions you mentioned in 1.2-rc3? Do you know which version does not have these regressions?

Sorry for all the questions!!

---

### Post by Zireth ZH on 2010-06-17
linux loads all applications slower the first time.. after that first time u dun even have to wait a second...

---

### Post by asdfoo on 2010-06-17
I sometimes start wine's notepad, but I think the command "wineserver -p" is designed to start wine in the background and not exit.   Normally it exits after 4-5 seconds if no windows application is running I think.

---

### Post by dpatel on 2010-06-18
OK, I'll try it out. Thanks for the help...

---

