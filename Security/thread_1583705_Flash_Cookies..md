---
title: "Flash Cookies."
date: 2010-09-28
forum: Security
---

### Post by zozza on 2010-09-28
I am a bit confused about Flash cookies.  My understanding is that they are located in ~/.macromedia.  

This is where they were located in  9.10 but when I upgraded to 10.04 the .macromedia folder never appeared.  I do use Flash from time to time so I would have thought I should have this folder.

I don't want Flash cookies but would like to know where they are (if there are any).  It seems strange to me that even though I use Flash sometimes there does not appear to be a folder that stores the cookies.

My concern is that Flash cookies are located somewhere else but I cannot find them.  

Any suggestions?  Thanks.

---

### Post by wacky_sung on 2010-09-28
Use Bleachbit to clear it for you.Beside that,it can help you to clear many type of junks as well.

---

### Post by Rubi1200 on 2010-09-28
Have you checked if there is a .adobe folder? They might be there.

I recommend BetterPrivacy for dealing with Flash cookies.

---

### Post by Jimtheplanner on 2010-09-28
Hi Guy's,

This is what your looking for [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html") 

You can adjust the controls to suit. When most folks find out about this its wow.....It collects that much data.......

Regards

Jim

---

### Post by mkvnmtr on 2010-09-28
The link in the above post to the flash manager controls  is one of the most important for your security on line that you will find. Be sure to check it out and set the controls for each computer you use.

---

### Post by BkkBonanza on 2010-09-29
I'm on 10.4 and have both a .macromedia and a .adobe. 

There is files that appear may be cookies at,

~/.adobe/Flash_Player/AssetCache/
and
~/.macromedia/Flash_Player/#SharedObjects/

I'm mostly sure you can delete files there you don't want. Looking at the file dates I notice that the .macromedia ones are the current new ones. They are directories, one for each web site.

It may depend more on what version of flash you have then what version of Ubuntu.

A nice way to view the contents of the cookie files is with this command,

**od -c -Ax filename**

Usually the content is encrypted/hashed so it doesn't visibly mean much.

---

### Post by zozza on 2010-09-29
Thanks for the advice.  I did have an .adobe directory but all its directories were empty.  

Is there anywhere else I wonder that Flash cookies could be stored?

---

### Post by james_mcl on 2011-10-16
Apologies for resurrecting a long dead thread, but there *is* another possible location. Look in

~/.gnash/SharedObjects/

---

### Post by lovinglinux on 2011-10-16
> **james_mcl said:**
> Apologies for resurrecting a long dead thread, but there *is* another possible location. Look in

~/.gnash/SharedObjects/

Another place is ~/.macromedia

However, you are indeed resurrecting the dead. Closed for necromancy.

---

