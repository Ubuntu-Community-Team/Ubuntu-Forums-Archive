---
title: "Band in a box 2006 - no sound"
date: 2008-12-31
forum: Wine
---

### Post by guayabound on 2008-12-31
I'm running BIAB 2006 thru WINE and it starts okay, but I cant get any sound to come out. I would love to get this up and running because its really one of the last apps I still use with windows.

I checked wine's sound config and its running thru ALSA and can generate sound when tested. I also tried started BIAB thru terminal and got the following:

fixme:win:SetLayeredWindowAttributes (0x10044,0x00000000,254,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10046,0x00000000,254,2): stub!
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 16/03/2008, dlt (d/m/y): 19/10/2008
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\pgjazz__.FOT",L"pgjazz__.ttf",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:win:LockWindowUpdate (0x10020), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x10020), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x10020), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\pgjazz__.FOT",L"pgjazz__.ttf",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\pgjazz__.FOT",L"pgjazz__.ttf",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\pgjazz__.FOT",L"pgjazz__.ttf",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\PGMUS.FOT",L"PGMUS.TTF",L"C:\\windows\\system32\\"): stub


And when I try to play a file terminal gives me this message repeatedly:

fixme:midi:midRecThread Sysex received but no buffer to store it!

Thanks,
Joe
Ubuntu 8.04

---

### Post by zivley on 2011-07-09
Damn it, I was so hoping to find an answer for this problem, this post is waiting for almost 3 years and nobody has anything to say about it???

---

### Post by markackerman8@gmail.com on 2013-03-04
> **zivley said:**
> Damn it, I was so hoping to find an answer for this problem, this post is waiting for almost 3 years and nobody has anything to say about it???

same issue here - areghhhh and nothing on the web

---

### Post by markackerman8@gmail.com on 2013-03-04
Solved

BIAB Settings
&#8728; Opt >> Midi/Audio driver setup
&#8227; Output is set to Wine Midi mapper

audio no works - fewwwwwwwww

[email]markackerman8@gmail.com[/email]

---

