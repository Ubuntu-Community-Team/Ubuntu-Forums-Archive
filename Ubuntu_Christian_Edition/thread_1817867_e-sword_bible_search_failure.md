---
title: "e-sword bible search failure"
date: 2011-08-03
forum: Ubuntu Christian Edition
---

### Post by GlennW on 2011-08-03
I hope this thread is in the right place.

I am running Ubuntu 11.04. I have E-Sword 9.9.1 installed. The issue I have is that the Bible search function doesn't work. I can search on commentaries and dictionaries but not the Bible. Ctrl+s or highlighting a word/phrase of a verse (then right clicking and selecting Search) both produce a dialogue box with the search term but no items found. 

Changing Bible versions makes no difference. As far as I'm concerned the Bible search function is one of the things that has in past made E-Sword such a valuable tool.

Any thoughts?

---

### Post by david_kt on 2011-08-05
> **GlennW said:**
> I hope this thread is in the right place.

I am running Ubuntu 11.04. I have E-Sword 9.9.1 installed. The issue I have is that the Bible search function doesn't work. I can search on commentaries and dictionaries but not the Bible. Ctrl+s or highlighting a word/phrase of a verse (then right clicking and selecting Search) both produce a dialogue box with the search term but no items found. 

Changing Bible versions makes no difference. As far as I'm concerned the Bible search function is one of the things that has in past made E-Sword such a valuable tool.

Any thoughts?

Have you tried the installer at the first post of this thread:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

---

### Post by jonathonblake on 2011-08-05
> **GlennW said:**
>  I have E-Sword 9.9.1 installed. The issue I have is that the Bible search function doesn't work.

e-Sword 9.9.1 is incredibly fussy, when it comes to searching resources in general, and Bible resources in specific.

If the resource was not specifically created for e-Sword 9.x, search  probably will not work correctly. (*BeST 2.x* is the most reliable program for converting between *e-Sword Resource Format Specification 1* and *e-Sword Resource Format Specification 2*. Even then, its 50/50 that e-Sword will search the resource correctly.)

> Changing Bible versions makes no difference.

For a little bit more troubleshooting, are you using *Advanced Search*, or *Basic Search*? 

They have different points of failure.   
[LIST]
[*]*Advanced Search* is much picker about resources;
[*]*Basic Search* is much picker about search syntax;
[/LIST]

Other common issues are:
[LIST]
[*]The Active Bible in the Bible component, does not contain the content that is being searched for. (The version you are searching may have the content, but if the Active Bible in the Bible component does not have the content, your search may fail.);
[*]e-Sword does not recognize your Regex expression/search terms;
[*]e-Sword does not recognize your Boolean expression/search terms;
[*]You are searching content that uses a langauge, or writing system that e-Sword doesn't recognize;
[/LIST]

Once you get beyond basic Regex, e-Sword search results are unpredictable, usually returning a null result even though the syntax is correct, according to other regex engines.

jonathon

---

### Post by GlennW on 2011-08-06
Thanks for the input. This was the thread that I used for the E-Sword 9.9.1 install:

[http://ubuntuforums.org/showthread.php?t=1524397]("http://ubuntuforums.org/showthread.php?t=1524397")

@david_kt there was no mention of a cabextract install so I didn't install it. 

@jonathan regarding searching I'm using only the basic search and at this point only single words without wild cards. I don't know how much more basic I can be. For instance, I search on "Eve" (without quotes) and the search box says 0 verses found. I can highlight the same word, right click on it and choose basic search and the results are the same.

Previous E-Sword installs were a bit trickier to install but worked so much better.

Are there any further details that I can furnish?

Thanks for your thoughts on this issue.

---

### Post by david_kt on 2011-08-06
> **GlennW said:**
> Thanks for the input. This was the thread that I used for the E-Sword 9.9.1 install:

[http://ubuntuforums.org/showthread.php?t=1524397]("http://ubuntuforums.org/showthread.php?t=1524397")

@david_kt there was no mention of a cabextract install so I didn't install it. 

Glen,
Try installer at the first post of this thread, after installing cabextract offcourse.

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

---

### Post by GlennW on 2011-08-08
> **david_kt said:**
> Glen,
Try installer at the first post of this thread, after installing cabextract offcourse.

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

Hi David,

I'm following your suggested thread and using the installer mentioned. However, after making sure that the installer in set to executable, running the installer program allows me to select the addons I'd like but will not run. Using System Monitor shows that the e-sword installer aborts almost immediately after launch. 

Any further suggestions?

Thanks.

---

### Post by david_kt on 2011-08-08
> **GlennW said:**
> Hi David,

I'm following your suggested thread and using the installer mentioned. However, after making sure that the installer in set to executable, running the installer program allows me to select the addons I'd like but will not run. Using System Monitor shows that the e-sword installer aborts almost immediately after launch. 

Any further suggestions?

Thanks.

Have you installed e-Sword using the installer?

DK

---

### Post by GlennW on 2011-08-09
> **david_kt said:**
> Have you installed e-Sword using the installer?

DK

Yes. I used the thread you suggested. Not to sound cheeky but is there a different installer?

---

### Post by david_kt on 2011-08-09
> **GlennW said:**
> Yes. I used the thread you suggested. Not to sound cheeky but is there a different installer?

No. But after you used the installer, do you still face bible search failure?

DK

---

### Post by GlennW on 2011-08-11
> **david_kt said:**
> No. But after you used the installer, do you still face bible search failure?

DK

Yes, the bible search continues to fail.....

---

### Post by david_kt on 2011-08-11
> **GlennW said:**
> Yes, the bible search continues to fail.....

Could you open terminal and issue below command:

env WINEPREFIX=$HOME/.wine_Esword wine "$HOME/.wine_Esword/drive_c/Program Files/e-Sword/e-Sword.exe"

After e-Sword start, do the bible search and and post the terminal output during bible search.

DK

---

### Post by jonathonblake on 2011-08-15
> **GlennW said:**
> For instance, I search on "Eve" (without quotes) and the search box says 0 verses found. I can highlight the same word, right click on it and choose basic search and the results are the same.

Does that happen with all Bibles?

jonathon

---

### Post by GlennW on 2011-08-15
> **david_kt said:**
> Could you open terminal and issue below command:

env WINEPREFIX=$HOME/.wine_Esword wine "$HOME/.wine_Esword/drive_c/Program Files/e-Sword/e-Sword.exe"

After e-Sword start, do the bible search and and post the terminal output during bible search.

DK

Hi David,

Sorry for taking so long to get back to you. I ran the above command from the terminal and it didn't work. What I did do is check the command issued when double clicking the icon. I took that command and issued it in the terminal. This is the output:

```
env WINEPREFIX="/home/glenn/.wine" wine C:\\windows\\command\\start.exe /Unix /home/glenn/.wine/dosdevices/c:/users/glenn/Start\ Menu/Programs/e-Sword/e-Sword.lnk
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3572614), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x358448c), stub!
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x359e3bc), stub!
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x3596c44), stub!
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x359e5cc), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x359e51c), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x359e524), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x359e51c), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x359e524), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x359e524), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a340c), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a08b4), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a083c), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a08b4), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a08b4), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a3444), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a3444), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a3444), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a3444), stub!
fixme:win:LockWindowUpdate (0x10060), partial stub!
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:win:LockWindowUpdate (0x10060), partial stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35a2414), stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEPictureImpl_Render Not quite correct implementation of rendering icons...
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35c4024), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35bc334), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35bc2e4), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x35bc2e4), stub!
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}


```

I think I'm more confused now than before. Thinking back, however, to the command you wanted me to run this is the output:

```
env WINEPREFIX=$HOME/.wine_Esword wine "$HOME/.wine_Esword/drive_c/Program Files/e-Sword/e-Sword.exe"
wine: cannot find '/home/glenn/.wine_Esword/drive_c/Program Files/e-Sword/e-Sword.exe'

```

---

### Post by david_kt on 2011-08-15
> **GlennW said:**
> Hi David,

Sorry for taking so long to get back to you. I ran the above command from the terminal and it didn't work. What I did do is check the command issued when double clicking the icon. I took that command and issued it in the terminal. This is the output:

```
env WINEPREFIX="/home/glenn/.wine" wine C:\\windows\\command\\start.exe /Unix /home/glenn/.wine/dosdevices/c:/users/glenn/Start\ Menu/Programs/e-Sword/e-Sword.lnk
```
I think I'm more confused now than before. Thinking back, however, to the command you wanted me to run this is the output:

```
env WINEPREFIX=$HOME/.wine_Esword wine "$HOME/.wine_Esword/drive_c/Program Files/e-Sword/e-Sword.exe"
wine: cannot find '/home/glenn/.wine_Esword/drive_c/Program Files/e-Sword/e-Sword.exe'

```

That means you have not used (or not successfully used) the installer yet. Please download the installer from here:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)


DK

---

### Post by GlennW on 2011-08-16
David,

I removed e-Sword and all its components. I went to your thread and followed everything. Finally, after a fresh install, it's working properly, with all search functions working as they should.

I thought I had earlier used your installer but must have skipped a step or corrupted something.

Thanks for your time and input into this issue.

Best regards.

---

