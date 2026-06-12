---
title: "how to play games under linux"
date: 2009-01-26
forum: Wine
---

### Post by karimla131 on 2009-01-26
hi  i am new user in ubuntu but i begin to learn a lot of things and i decided to remove the windows but i couldn't so i can play any game 
so is there a way   to play windows games under ubuntu 8.10 
my graphics card is nvidia 
nvidia Ge-force 7300 LE
VBIOS Version :05.72.22.43.32
Memory: 256 up to 512 MB
 
i tried wine it just open the game and then close it 

      so is there is any advise for this
 

            thanks a lot and good luck 

                    kaeem

---

### Post by taurus on 2009-01-26
First of, what game are we talking here?

There is a gaming section (off site), [http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php), of the forum.

---

### Post by karimla131 on 2009-01-26
thank you for your fast replay 
then the games such as need for speed most wanted  
fifa 2005
pes2008

---

### Post by golusweet on 2009-01-26
You can install Windows games using Wine.

Go to add/remove ,and search for Wine,Install it.

Only compatible applications ,and games will work.

Check out the Wine app database [url]http://appdb.winehq.org/

Edit: You can try Cedega then though It's not free

http://www.cedega.com/

---

### Post by dardack on 2009-01-26
You also need the directx dll's.  what you should do is rune wine from a terminal so you can see the error message.  Like i run madden 08, from terminal wine /home/myname/Programs/Madden/mainapp.exe

You will probably need at least the mfc40.dll and the d3dx9_36.dll (i actually have 25-30 and 36) and both of these need to go in your ~/.wine/drive_c/windows/system32 directory.  Because like madden I'm pretty sure fifa only uses directx and not openGL.

---

### Post by karimla131 on 2009-01-26
so how should i install directx dll's , mfc40.dll and the d3dx9_36.dll an  on my ubuntu 
 i am sorry becouse i am new in ubuntu

---

### Post by dardack on 2009-01-26
No not most of them, just those 2 i mentioned usually will survice, you can find them online.  From wine's faq:

If you attempt to install Microsoft's DirectX, you will run into problems. It is not recommended nor supported by Wine HQ to attempt this. You can install the runtime, but it will not run. The runtime needs access to the Windows drivers, and Wine cannot access them for obvious reasons. The only native Microsoft DLLs that could be useful anyway are the d3dx9_xx.dll type ones, and these require you to accept Microsoft's license. Additionally these DLLs are now part of the Wine tree. So, as Wine improves these DLLs will only become less relevant.

So I guess they have since put mfc40.dll included (i used one from the internet tho myself) but you still might need the d3dx9_##.dll's.  I did for madden to run.  Again run wine in the terminal so you can see the error message.

---

### Post by karimla131 on 2009-01-26
i am so sorry but how can i run wine in the terminal so you can see the error message.

---

### Post by taurus on 2009-01-26
> **karimla131 said:**
> i am so sorry but how can i run wine in the terminal so you can see the error message.

Something like

```
wine *filename.exe*
```

---

### Post by dardack on 2009-01-26
> **karimla131 said:**
> i am so sorry but how can i run wine in the terminal so you can see the error message.


Applications->Accessories->Terminal

type wine /<path to exe>/filename.exe

---

### Post by karimla131 on 2009-01-26
whene i did it it open the game then say that error

fixme:win:EnumDisplayDevicesW ((null),0,0x32f3fc,0x00000000), stub!
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:mpeg3:MPEG3_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
fixme:adpcm:ADPCM_StreamSize misses the block header overhead
msadp32.c:277: cvtMMms16K: Assertion `*src <= 6' failed.
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithDataSegs
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:winmm:MMDRV_Exit Closing while ll-driver open

---

### Post by stchman on 2009-01-26
> **karimla131 said:**
> hi  i am new user in ubuntu but i begin to learn a lot of things and i decided to remove the windows but i couldn't so i can play any game 
so is there a way   to play windows games under ubuntu 8.10 
my graphics card is nvidia 
nvidia Ge-force 7300 LE
VBIOS Version :05.72.22.43.32
Memory: 256 up to 512 MB
 
i tried wine it just open the game and then close it 

      so is there is any advise for this
 

            thanks a lot and good luck 

                    kaeem

Not all Windows games play under WINE.  I recommend that if you are a gamer dual boot with Windows.

---

### Post by karimla131 on 2009-01-26
so is there not any thing to play games under ubuntu

---

### Post by Tibuda on 2009-01-26
> **karimla131 said:**
> so is there not any thing to play games under ubuntuyou missed a word in your sentence:> so is there not any thing to play **WINDOWS** games under ubuntu
But backing to the point: yes you can play some windows games in Ubuntu. You can try to install DirectX with [wine tricks]("http://wiki.winehq.org/winetricks"), but you won't be able to report wine bugs.

Check these links about the games you listed:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2577](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2577)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4464](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4464)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5860](http://appdb.winehq.org/objectManager.php?sClass=application&iId=5860)

---

### Post by stchman on 2009-01-27
> **karimla131 said:**
> so is there not any thing to play games under ubuntu

No I play plenty of Windows games under Ubuntu.  We are saying that WINE does not play 100% of them.

I find that the openGL games like Quake III, Doom III, etc. work very well.  It is when you try to play DirecX 9 or better that is becomes more problematic.

---

