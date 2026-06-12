---
title: "Why does Wine have its own temp folders?"
date: 2008-12-09
forum: Wine
---

### Post by Endolith on 2008-12-09
.wine/drive_c/windows/temp was full of useless stuff.  Why doesn't Wine use the same tmp folder as Linux?  Is there a good reason for this?  Is there a good reason why Wine's temp folders aren't emptied regularly?

---

### Post by pietjanjaap on 2008-12-09
Because wine has nothing to do with linux. You are looking at the c drive, like in windows c drive. This is so that windows programs think this is windows.
If install more windows programs, you will see that there are more c drive's, that is because it is possible to install windows programms in separate c drive directory.

Wine simulate's windows so windows programs work.

---

### Post by Endolith on 2008-12-09
I know what .wine/drive_c is, but why isn't Wine's temp folder just a link to the /tmp folder?

---

### Post by hikaricore on 2008-12-09
> **Endolith said:**
> I know what .wine/drive_c is, but why isn't Wine's temp folder just a link to the /tmp folder?

If you don't like the way it is currently perhaps you should suggest this change to the WINE devs.

However WINE also stores useful files in the temp dir, including but not limited to the icons it extracts from some programs while installing them.
If you remove the contents of this folder (specifically the xpm files) you'll lose some of the pretty icons that WINE may have made in your menus and on your desktop.

---

### Post by asdfoo on 2008-12-09
> **hikaricore said:**
> If you don't like the way it is currently perhaps you should suggest this change to the WINE devs.

However WINE also stores useful files in the temp dir, including but not limited to the icons it extracts from some programs while installing them.
If you remove the contents of this folder (specifically the xpm files) you'll lose some of the pretty icons that WINE may have made in your menus and on your desktop.

hikaricore: [http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

One sensible reason you wouldn't use /tmp is because Wine uses prefixes under which everything for that prefix exists,  Registry, Programs, default drive (C:).  So it makes sense for any temporary files that programs create under Wine be specific to that prefix only.

Putting stuff under /tmp would be messier.  That said, if you want to change the location of the temporary directory it's just an environment variable, so conceivably if you _really_ wanted to put things under /tmp then you'd probably just modify TMP and TEMP.

---

### Post by hikaricore on 2008-12-09
Hi, I'll type out WINE how ever I damn well please.
I've seen folk posting that link everywhere and I'm quite tired of it.

Have a great day. ^_^

---

### Post by Endolith on 2008-12-09
> **hikaricore said:**
> If you don't like the way it is currently perhaps you should suggest this change to the WINE devs.

I didn't say I don't like the way it is; I asked *why *it is the way it is.  Maybe there's a good reason and it would be stupid to ask for it to be changed.
 
> However WINE also stores useful files in the temp dir, including but not limited to the icons it extracts from some programs while installing them.  If you remove the contents of this folder (specifically the xpm files) you'll lose some of the pretty icons that WINE may have made in your menus and on your desktop.Can you give some examples?  That seems like a strange place to store Desktop icons.
 
> **asdfoo said:**
> One sensible reason you wouldn't use /tmp is because Wine uses prefixes under which everything for that prefix exists, Registry, Programs, default drive (C:).  So it makes sense for any temporary files that programs create under Wine be specific to that prefix only.

What do you mean by "prefixes"?

---

### Post by asdfoo on 2008-12-10
> **Endolith said:**
> I didn't say I don't like the way it is; I asked *why *it is the way it is.  Maybe there's a good reason and it would be stupid to ask for it to be changed.
 
Can you give some examples?  That seems like a strange place to store Desktop icons.
 


What do you mean by "prefixes"?


Ah, wasn't sure if an explanation was required, but a Wine has a notion of a prefix which is like a self contained environment.  Your default prefix is ~/.wine

If you want to create a new prefix, then you set an environment variable called WINEPREFIX to the path you want to use for a prefix. eg:

WINEPREFIX=~/wine-testprefix wine notepad

Will be a distinct environment from your default prefix.  This can be useful for testing or keeping installed programs seperate, eg, I keep Battlefield 1942 in its own prefix, seperate from my testing, so I don't accidentally trash it.

---

