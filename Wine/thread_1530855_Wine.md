---
title: "Wine"
date: 2010-07-14
forum: Wine
---

### Post by malcmail on 2010-07-14
I wanted to get Spotify (for free - I'm tight!) to work on my ubuntu box. I tried to install WINE but it appears to have gone pear shaped.  When I do winecfg it gives the error messages along the lines of :
XError of failed request: XF86VidMode Disabled
and goes on a little more with similar.
 
If I try to install smthg with wine it gives the same error followed by:
 
WINE cannot find L"C:\\Windows\\system32\\spotify.exe"
 
I tried reinstalling the package but same problem.  Any ideas where now? Thanks in advance.

---

### Post by philinux on 2010-07-14
Moved to WINE forum.

---

### Post by malcmail on 2010-07-14
Couldnt find this forum originally - thanks Phil.
Having seen the sticky I presume this is an issue with graphics.  I dont have a specific graphics card in my Ubuntu box - just the onboard graphics options. 

Anyone any ideas where I should be going with this?  Wine 1.2 btw

EDIT
Full error message on attmpted installation
<code>
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  85
  Current serial number in output stream:  85
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  85
  Current serial number in output stream:  85
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  85
  Current serial number in output stream:  85
</code>

---

### Post by malcmail on 2010-07-14
SOLVED! AFter downloading all sorts of packages I found the answer. In case anyone else suffers heres what to do.

1. In terminal browse thr the hidden .wine folder.
2. Use vi to open user.reg
3. Chances are you are missing the following key
[Software\\Wine\\X11 Driver] xxxxxxxxxxxx
"UseXVidMode"="N"

The xxxx should be replaced by the number you see against adjacent keys.  Then it works a charm!

---

### Post by asdfoo on 2010-07-14
Editing the registry using a text editor is not recommended, it's a binary file managed by Wine internally.

Use regedit or a helper script like winetricks.

The original problem sounds like you might not have correct or full functioning video drivers?

---

### Post by malcmail on 2010-07-14
The problem is I'm told WINE is effectively run within itself so couldnt use any other windows based tools to fix it. It all looks safe and sound although now appear to have come across another problem!! The line was just missing - turns out a few ppl have had the same problem for some odd reason.

---

### Post by hikaricore on 2010-07-14
> **asdfoo said:**
> Editing the registry using a text editor is not recommended, it's a binary file managed by Wine internally.

Actually the .reg files are just plaintext, there's no reason you shouldn't be able to edit them with a text editor.

---

### Post by asdfoo on 2010-07-14
> **hikaricore said:**
> Actually the .reg files are just plaintext, there's no reason you shouldn't be able to edit them with a text editor.

No, they are binary files in the sense that their format is not guaranteed to be plain text, it's private and internal to Wine.  The public interface for modifying these files are through the win32 registry functions only, as regedit or reg.exe uses.

---

### Post by cogadh on 2010-07-14
I'm sorry, but you are completely wrong about the reg files. They are completely plain text and in fact there are occasions where Wine's own documentation says you can edit the files manually using a plain text editor (never a word processor). Granted, if you do type something wrong, it won't work, but Wine's "registry" is not like the real Windows registry that really can only be edited via regedit.

---

### Post by hikaricore on 2010-07-14
> **asdfoo said:**
> No, they are binary files in the sense that their format is not guaranteed to be plain text, it's private and internal to Wine.  The public interface for modifying these files are through the win32 registry functions only, as regedit or reg.exe uses.

Sorry but I'm right and you're the opposite:

[http://www.winehq.org/docs/wineusr-guide/using-regedit](http://www.winehq.org/docs/wineusr-guide/using-regedit)

> **Finally, unlike Windows, the Wine registry is written in plain text and can be changed using your favorite text editor.**

---

### Post by asdfoo on 2010-07-15
> **hikaricore said:**
> Sorry but I'm right and you're the opposite:

[http://www.winehq.org/docs/wineusr-guide/using-regedit](http://www.winehq.org/docs/wineusr-guide/using-regedit)

That's out of date.

see here: [http://wiki.winehq.org/FAQ#head-903eaf89ed775396f776438ec126ea9336828473](http://wiki.winehq.org/FAQ#head-903eaf89ed775396f776438ec126ea9336828473)

---

### Post by hikaricore on 2010-07-15
*sigh*

The context of that entry in the faq can be taken in several ways but only one is accurate.
Generally the idea is you "shouldn't" edit them with a text editor because the files are laid out in a specific manner.
As has been mentioned already if you edit them wrong it can and will cause problems.
This does not change the fact that the .reg files are in plaintext so stop trying to claim otherwise.

---

### Post by cogadh on 2010-07-15
Indeed, there is a huge difference between what is *recommended* to do and what you *actually* can do. If you are unfamiliar with Wine and its registry structure, by all means, use regedit, it is far safer for the novice. However, if you are already intimately familiar with Wine's registry or you have very specific editing instructions, go ahead and use a text editor. There is nothing about the file itself or its format that prevents you from doing that, you just need to be sure to use the correct syntax (so to speak) when editing it, just like when editing a simple script file.

---

### Post by Jamie White on 2010-11-02
I'm sorry but I have to bring this up again.
Regedit is next to useless for editing the registry for a lot of people, me for one. This is due to the fact that some stupid seemingly incurable bug stops you from renaming keys. And I don't mean just the preordained ones I mean newly created ones.
I'm absolutely at a loss for what to do. I tried all of the pseudo-mystical resizing the window suggested solutions. Nothing works.
So the only option I now have is to edit with gedit which, no doubt about it, is a cumbersome pain but, well, *it works*.

This should be standard. Wine should encourage editing this way. If they just made a faq for doing so, it wouldn't be risky anymore.

---

