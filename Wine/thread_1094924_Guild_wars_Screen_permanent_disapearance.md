---
title: "Guild wars Screen permanent disapearance ?"
date: 2009-03-13
forum: Wine
---

### Post by killpotts on 2009-03-13
Alright, this is a very confusing problem and I have no idea how it happened. Guild Wars has alway ran fine for the past few days I have had ubuntu ( 8.10 ) installed. Now all of the sudden something odd has happened to it.

This is basically what I did:

-I launched GW in a workspace, then switched to another workspace while it was loading.
-While GW was loading, I opened up system monitor in the other workspace.
-In system manager, I ended a few programs I was no longer using at the time ( Firefox, Mplayer ) and set GW to high priority.
-GW disappeared. The screen vanished, but it remained in system manager. 
-I ended the process and reloaded GW, figuring that GW crashed.
-It loaded...but with NO SCREEN. Not a black screen, not a clear screen, but no screen. I can hear the music and everything playing in the background as if it was minimized, but there is no screen and alt+tab does not list it. Basically, its there, and its running with music, but it is only listed in system manager and exists with no screen. It cannot be switched too either.
-Logging out/Restarting does not remedy the issue
-Trying to run it via virtual destop does not resolve the issue either.
-Changing the Registry values as listed on Guild Wars page in wine HQ doesn't change anything either.
-All the things listed in the sticky ( different Windows versions, ect. ) don't fix anything either. 

This is what running in Terminal gets me:

```

fixme:win:EnumDisplayDevicesW ((null),0,0x32eb54,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e258,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32_FLOAT
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x36c0818,0x36c0778): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e87c0,0x36c07b0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e87c0,0x36c07b0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e87c0,0x36c07b0): stub


```

*I had recently installed 3DS MAX 7 trial version just before this started to happen. 
* I am using 1.1.16
* I am using the Nvidia accelerated graphics driver  ( V.177 )

SO...any ideas how something like this could possibly happen or how to fix it ? I suspect that the program is actually running somewhere, but trapped in some bizarre process I am not familiar with. The only thing I know how to do to switch to programs is "Continue process" in system manager and alt-tab to it.

---

### Post by killpotts on 2009-03-13
I just tried deleting the Arenanet keys in regedit, and even that didn't work. :(

---

### Post by mttman on 2009-03-13
i have a similar problem too. but mine is that GW is telling me i don't have the most recent drivers for my graphics card. i just updated to version 1.1.16 but i was running in version 1.0.1 and didn't have this problem but did have a problem with guild wars running slow. i think this might be a problem with version 1.1.16. does anyone know?

---

### Post by killpotts on 2009-03-13
Alright, I managed to fix it. I will post how I did it now in case anyone else gets the same problem:

-EDIT: actually, all you need to do is replace your GW.dat file. I would reccomend keeping a backup of GW.dat for this reason.

---

