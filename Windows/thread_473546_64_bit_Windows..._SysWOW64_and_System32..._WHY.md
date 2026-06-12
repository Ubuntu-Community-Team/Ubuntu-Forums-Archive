---
title: "64 bit Windows... SysWOW64 and System32... WHY?"
date: 2007-06-14
forum: Windows
---

### Post by cunawarit on 2007-06-14
I’ve had a 64 bit Windows 2003 Server for a couple of months and I’ve just noticed something.

The SysWOW64 and System32 directories. 

I assumed that System32 had 32 bit libraries, and SysWOW64 had 64 bit libraries. Safe assumption, right?

But no!

According to Wikipedia: 

"The operating system uses the %SystemRoot%\system32 directory for its 64-bit library and executable files. This is done for backwards compatibility reasons as many legacy applications are hardcoded to use that path. When executing 32-bit applications, WOW64 redirects requests for DLLs from that directory to %SystemRoot%\sysWOW64, which contains legacy libraries and executables."

Well, that’s consistent, and not back to front at all!!!

I’m not bashing, just surprised... What’s the Linux way?

---

### Post by Yoooder on 2007-06-21
lol, that's quaint.

Of course they're probably just following the logic of putting Shut Down in Start.  Or the oxymoron of "Microsoft Works."

*ducks ballistic chair from Redmond*

---

### Post by LukeCarrier on 2008-01-29
Yeah I've noticed this too. I don't get why they didn't just use a symbolic link (vista now has this technology so it wouldn't be hard to set up in older versions of windows) on the system32 folder to rthe new syswow64 folder, and had a folder called legacy or crap (as thats what it is) set up for all the old 32bit stuff.
 
Yeah, seems like a typical microsoft idea :P

---

