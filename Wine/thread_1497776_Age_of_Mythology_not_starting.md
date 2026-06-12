---
title: "Age of Mythology not starting"
date: 2010-05-31
forum: Wine
---

### Post by BlackRat90 on 2010-05-31
I got the game and the extension to install fine, but when ever I go to run the game it starts, and then does nothing. It just sits in the start up loading screen for several minutes with no end in sight. 

My system is fast enough (about 4 gb of ram, and 2.8ghx duo processor) that it shouldn't be taking this long to load the game even in wine, but does anyone have any idea on why its not starting? or is it just being REALLY slow...

Both the Titans expansion and the main game don't start. I have let them be for over 5 minutes with out result.

Here's what i get when i try to run in the terminal:
> fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB: (0x13bf70)
fixme:msctf:LangBarMgr_ShowFloating STUB: (0x13bf70)
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x2005a, 0x136210): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x136210): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec80,0x00000000), stub!
fixme:msctf:LangBarMgr_GetShowFloatingStatus STUB: (0x13e9a8 )
fixme:msctf:LangBarMgr_ShowFloating STUB: (0x13e9a8 )


---

### Post by cogadh on 2010-05-31
Its probably the copy protection check failing. AoM uses SafeDisk copy protection, which does not work in Wine.

---

### Post by BlackRat90 on 2010-05-31
Any work around?

---

### Post by cogadh on 2010-05-31
You'll need to look for a cracked executable. Don't ask where or how to get one or how to use it once you have it, they are a legal grey area that is a taboo topic on these forums, so I'm afraid you are on your own in this. Remember, Google is your friend.

---

### Post by BlackRat90 on 2010-05-31
Indeed it is!
I ran across [this]("http://appdb.winehq.org/commentview.php?iAppId=1979&iVersionId=4776&iThreadId=35274") when i was doing some more digging...

I don't know how but it fixed it, of course after that i got another error, Wine just doesn't want me to play my games, it was an 'Initialization Failed'. a quick search of this and i found a fix (all you have to do is run it at a lower resolution), so i ran in 'video safe mode' this allowed me to start up the game with out problems and modify the resolution.

So far so good, but i have yet to actually play to game...ill posted solved when i do!

---

### Post by BlackRat90 on 2010-05-31
Well i got it to run! and it plays rather well.
The initialization problem had to do with the game not support wide screen monitors so i have to play in a windowed box, but it actually isnt that bad.

Thanks cogadh!

---

