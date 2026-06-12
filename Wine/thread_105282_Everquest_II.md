---
title: "Everquest II"
date: 2005-12-18
forum: Wine
---

### Post by Donnut on 2005-12-18
OK, I could find very little of this game in the forums, has anyone been succesful in running EQ2 under ubuntu?  I run WoW very nicely, but would like to run this one while staying "windows free"...

---

### Post by Brynster on 2005-12-18
Cedega doesn't yet support it, you could try wine but to the bet of my very limited knowledge it hasn't made the leap to Linux yet.


But don't whatever yo do take my word as fact.

---

### Post by joe_lace on 2006-06-27
Hate to bump an old thread but I was wondering if there was an update on this.

---

### Post by Perfex on 2006-06-27
[QUOTE=joe_lace]Hate to bump an old thread but I was wondering if there was an update on this.[/QUOTE]

I tryed once running it with wine from the install location on my harddrive that windows is running on, it started up the updater and proceeded to create tons in my home folder of files that already existed, thats as far as I got I quit mid into it.

but thats not even brining up the main screen yet so im not sure, personaly I dont think its worth the time, I played Everquest 1 for 2 years then jumped to Everquest 2 when it came out, played from launch untill about 2 months ago, it just got so repetative, and boring, was not like the enjoyment I had back in original Everquest.

Now I wait for [Vanguard]("http://www.vanguardsoh.com/"), I will try to run that in wine, if not its dual boot into windows :(

---

### Post by joe_lace on 2006-06-27
I've been playing it for a while now and would like the ability to continue.  But the truth is, I haven't played it in a month and if I can't make it work I'm not going to sweat it.

---

### Post by dasuberdog on 2006-10-04
My buddies are back on EQ2 but I got rid off all of windows and all windows programs.  I'd like to check EQ2 out again.  Anyone have it running on Ubuntu yet?

thanks

---

### Post by rbhigday on 2006-12-27
I dont know but would like to know as I play it often and it one of the few remain programs that keeps me from totally converting to Ubuntu on all my pc's.

Need to see if I can run quicken home and business and msn messenger those are the 3 windows programs my wife or I need.

Off to search the forum a bit :D

---

### Post by mcgroo on 2007-09-24
try here:

[http://appdb.winehq.org/appview.php?iVersionId=358&iTestingId=11179](http://appdb.winehq.org/appview.php?iVersionId=358&iTestingId=11179)

---

### Post by Diacre on 2007-12-04
I don't know if it helps anyone but I found this post while I was searching today:
[http://forums.station.sony.com/eq2/posts/list.m?topic_id=396323]("http://forums.station.sony.com/eq2/posts/list.m?topic_id=396323")

---

### Post by MWeather on 2007-12-24
I can confirn that Everquest 2 works with Wine now. You need Wine version 0.9.49 or above. Follow the directions here: [http://appdb.winehq.org/appview.php?iVersionId=358](http://appdb.winehq.org/appview.php?iVersionId=358)

---

### Post by Faud on 2007-12-24
Yep, it works. If you have any questions feel free to post and I'll do my best to help you get it set up

---

### Post by fktt on 2007-12-30
whoo! good news, guess ill have to start converting my eq-no-lifing father! :D

---

### Post by cryptidan on 2007-12-31
Still having a problem with the font issue.  Been searching for solution to no avail.

The normal assorted forum threads (@everquest forums, and winedb), I haven't come up with anything yet.

-Followed the directions on Winedb explicitly.

-set up my video card perfectly.

-added r_font_ft 0 to:
eq2.ini...error
eq2_default.ini...error
eq2_recent.ini...error

-wine version .52, eq2 will not work, don't matter, i still have .51

Any ideas?

---

### Post by Faud on 2007-12-31
Make sure that you are starting EQ2 in windowed mode also are you starting the game with everquest2.exe and not EQ2. exe ? Also make sure after you run the patcher that you go back to your eqdefault.ini file and redo the font hack.

---

### Post by cryptidan on 2008-01-01
Ok went back and tried again, same results.

I started with the patcher, eq2.exe,  gecko thing came up, i chose cancel as per the instructions, patcher continued on normal course, opened correctly, did a little update, went to red play button.  Closed the patcher, added r_font_ft 0 to eq2_default.ini, then opened everquest2.exe, in windowed mode (cl_fullscreen false), to which i got the same reply about the font.

[IMG]http://i20.photobucket.com/albums/b231/Shayol420/Screenshot.png[/IMG]

---

### Post by Faud on 2008-01-01
This may sound stupid but until I can put some hours to look into this have you tried deleting your recent.ini file ? before starting and then adding the font thing to the last line of your default ini.
Here is what my default.ini looks like just so that you know.

cl_screenwidth 1024

cl_screenheight 768

cl_placeholder_base_lods 0

r_stats 0 

r_font_ft 0

cl_unload_resources_asynchronously 1

r_appearance_update_always_dist 25

cl_player_cache_dir logincache-us





cl_language English 

cl_fullscreen 0



cl_alert_once_each 1



cl_log_crashes true



r_graph_over_time 0



r_looteffect 0

r_spawneffect 0



sfx_volume 0.90

ambient_volume 0.90

music_volume 0.50

combat_music_volume 0.55

voice_volume 0.70

resident_sound_volume 0.75

I'll try and look more into it and Im gonna be honest, anytime Ive gotten that message it was because I didnt add the font hack to default.ini after a patch. But I'll keep looking.

PS I noticed in your above post that you had added the font hack to your eq2.ini file. You shouldnt have a eq2.ini file unless you are using a custom user interface. That could also be part of your problem. Ive only gotten eq2map and infocenter to work. All other UI mods have crased EQ2 for me. So you could also try deleteing your eq2.in file as well.

---

### Post by cryptidan on 2008-01-02
When I had copied over my eq2 install from windows, it did have a custom ui, i deleted that, but didnt delete the eq2.ini...

so went ahead and did what you suggested, deleted recent.ini, and eq2.ini, ran the patcher again, that went well, but hits the same error.  meh.

---

### Post by cryptidan on 2008-01-04
Ok font issue is fixed, but now i'm getting this:

Backtrace:
=>1 0x7bc44abc in ntdll (+0x34abc) (0x0034e1f4)
  2 0x011042ad in d3d9 (+0x342ad) (0x0034ea4c)
  3 0x010fae42 in d3d9 (+0x2ae42) (0x0034ee00)
  4 0x010fc445 in d3d9 (+0x2c445) (0x0034ee28)
  5 0x010f9f35 in d3d9 (+0x29f35) (0x0034f02c)
  6 0x010fa5dd in d3d9 (+0x2a5dd) (0x0034f144)
  7 0x008d2c2a in everquest2 (+0x4d2c2a) (0x0034f694)
  8 0x00405270 in everquest2 (+0x5270) (0x009ff17a)
  9 0x3b000001 (0x0ce9c78b)
  10 0x00000000 (0x00000000)
wine: Call from 0x11042ad to unimplemented function GDI32.dll.GdiEntry1, aborting
wine: Call from 0x11042ad to unimplemented function GDI32.dll.GdiEntry1, aborting
fixme:dbghelp:SymInitializeW what to do ??

read about, thought it was related to fullscreen, but thats set to false

When i run wine dxdiag.exe, i get a message: "Dxdiag has detected that there may have been a problem accessing Direct3D the last time this program was used" dunno if that has anything to do with it, either

---

### Post by Faud on 2008-01-05
How did you fix your font issue ?

---

### Post by cryptidan on 2008-01-05
> **Faud said:**
> How did you fix your font issue ?


Heh, well, after going thru and getting rid of all custom ui references, i noticed it was still doing it, and read up some more, until i found a post in winedb about using "winefile" in the terminal, opening up the Z:/ drive and double clicking on eq2.exe for patch, and everquest2.exe for game...

typing "wine explorer /desktop=eq2,1024x768 everquest2.exe" as per recommended by that instructions there will always get me the font error, where after going thru the z drive, I actually get the opening movie (which looks perfectly fine) but afterwards it goes to a black screen with just tiny slashes of color (which I am assuming is the log-in screen).

I set up all the .dll files in the winecfg libraries tab before installing directx 9, so thats alrite i guess...

and the little error log i posted is actually part of a much larger terminal log, just didnt want to post the whole thing, thats just what it says at the end.

---

### Post by Faud on 2008-01-05
Im confused about why you would install directX 9 though since WINE has direct X in it per the install instructions. There are some posters on the EQ2 comments that are active on winehq.org I'll look over there and see if I cant find something for the new issue.

---

### Post by cryptidan on 2008-01-05
Ok. started over. got rid of LinuxMint, and repartitioned with Ubuntu 7.10...went fine

Installed wine 0.9.51...went fine

Didn't mess with directx

Followed the directions to to T...went fine, but have to use "winefile" to double-click on the apps.

ran patcher...went fine

Added r_font_ft 0, changed fullscreen to 0...np

Much better results to say the least, but here's the problem now:

[IMG]http://i20.photobucket.com/albums/b231/Shayol420/Screenshot-1.png[/IMG]

That's where it stops. no login options.

---

### Post by Faud on 2008-01-06
Does the game crash or just stay there ? Do you have anything odd in your terminal ? and finally Gratz! on getting past your font error

---

### Post by cryptidan on 2008-01-06
Thanx for bearing with me...well what it does is go to that title screen, and just stays there, the music continues to play, though, so I'm not sure if its freezing or what.

terminal output is kinda long, put in as attachment.

---

### Post by Faud on 2008-01-06
Need the attachment

---

### Post by cryptidan on 2008-01-07
der...sorry, was a little tired last nite:oops:

---

### Post by Faud on 2008-01-07
Im wondering what your system specs are inc. your graphics cardand just making sure that you have alsa checked off in your audio tab in winecfg. I'll delve into your attachment tonight

Also make sure that direct rendering is working

```

glxinfo | grep direct

```

---

### Post by Faud on 2008-01-08
Ok, got home and everything in the terminal output looks normal to me, where you hang is where (as far as I know) the game should start attempting to load the default UI, BUT what strikes me is that if you just dont have a UI folder then I think the game crashes with a "you must patch error" and you are just hanging and not crashing. I wonder if it was having some trouble with your UI folder or if maybe when you deleted your UI folder from your windows partition there was like a 1024x768_<server>.ini file that was left over that its trying to read and cant...or I could be totally offbase. Either way, one day Im gonna see you playing this game on linux lol

---

### Post by cryptidan on 2008-01-08
> **Faud said:**
> Im wondering what your system specs are inc. your graphics cardand just making sure that you have alsa checked off in your audio tab in winecfg. I'll delve into your attachment tonight

Also make sure that direct rendering is working

```

glxinfo | grep direct

```

ok, I have an older computer
Hp Vectra vl420
1.8 ghz pent 4
250 gb hd

video card is ati radeon 9550 x1050

rendering, i got a "yes, alsa is checked, and to the "1024x768_<server>.ini file" files, i went thru and deleted them all.

there is a "<loginnname>_characters.ini" and a "original_uisettings.ini" though

---

### Post by casperinmd on 2008-01-10
Try deleting all of your *.ini files, re patch, fix eq2_default.ini with the r_font line and then run EQ again.

I have had my share of problems in the beginning, and am running on  an older system without issues. What you are seeing now is new, never seen that issue.

Have you tried left clicking a few times in the EQ splash screen?

For me, it is slow so I always out of habit click in there..sorta moves it along for me. Then type your login name, password, character name (case sensitive) and server name you play on. Then the UI should try to load.

---

### Post by cryptidan on 2008-01-12
> **casperinmd said:**
> Try deleting all of your *.ini files, re patch, fix eq2_default.ini with the r_font line and then run EQ again.

I have had my share of problems in the beginning, and am running on  an older system without issues. What you are seeing now is new, never seen that issue.

Have you tried left clicking a few times in the EQ splash screen?

For me, it is slow so I always out of habit click in there..sorta moves it along for me. Then type your login name, password, character name (case sensitive) and server name you play on. Then the UI should try to load.

ok did all that, then i left clicked on the screen, got like a click sound couple times like a broken record, screen shut down and i got this in the terminal:

Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  146 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x3800131
  Serial number of failed request:  2966
  Current serial number in output stream:  2966

says ati in there...has to be my vid card, eh?

---

### Post by javafiend on 2008-03-20
Has anyone got this running on a 64-bit system?  I noticed the Gentoo AMD64 version running Wine 0.9.52 was rated "Garbage".  Has anything changed with 0.9.57?

---

### Post by javafiend on 2008-03-20
I think I've done everything I'm supposed to to get this to run, but when I run EverQuest2.exe it acts like it's about to start, but then there is just a brief flash of a window opening and then closing.  Can anyone help?

His is the terminal output:
```

4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeHigh", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeLow", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bBeta", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bDebug", 0x34e4cc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x19cd08,L"dmime.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szPath", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szName", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bExists", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szVersion", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szAttributes", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szLanguageEnglish", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeHigh", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeLow", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bBeta", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bDebug", 0x34e4cc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x19cd08,L"dmloader.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szPath", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szName", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bExists", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szVersion", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szAttributes", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szLanguageEnglish", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeHigh", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeLow", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bBeta", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bDebug", 0x34e4cc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x19cd08,L"dmscript.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szPath", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szName", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bExists", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szVersion", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szAttributes", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szLanguageEnglish", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeHigh", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeLow", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bBeta", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bDebug", 0x34e4cc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x19cd08,L"dmstyle.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szPath", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szName", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bExists", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szVersion", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szAttributes", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szLanguageEnglish", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeHigh", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeLow", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bBeta", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bDebug", 0x34e4cc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x19cd08,L"dmsynth.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szPath", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szName", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bExists", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szVersion", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szAttributes", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szLanguageEnglish", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeHigh", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeLow", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bBeta", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bDebug", 0x34e4cc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x19cd08,L"dmusic.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szPath", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szName", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bExists", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szVersion", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szAttributes", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szLanguageEnglish", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeHigh", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeLow", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bBeta", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bDebug", 0x34e4cc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x19cd08,L"devenum.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szPath", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szName", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bExists", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szVersion", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szAttributes", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szLanguageEnglish", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeHigh", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeLow", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bBeta", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bDebug", 0x34e4cc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x19cd08,L"quartz.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szPath", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szName", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bExists", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szVersion", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szAttributes", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"szLanguageEnglish", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeHigh", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"dwFileTimeLow", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bBeta", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x19cd08, L"bDebug", 0x34e4cc)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x19c730, L"DxDiag_DirectXFiles", 0x19cd08)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1a11c0, L"0", 0x1a11e0)
fixme:win:EnumDisplayDevicesW ((null),0,0x34e92c,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"szDeviceName", 0x34e69c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"szDescription", 0x34e68c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34e06c,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"szDisplayMemoryLocalized", 0x34e67c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"szDisplayMemoryEnglish", 0x34e66c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"dwWidth", 0x34e65c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"dwHeight", 0x34e64c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"dwBpp", 0x34e63c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"szVendorId", 0x34e62c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"szDeviceId", 0x34e61c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"szKeyDeviceKey", 0x34e60c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a11e0, L"szKeyDeviceID", 0x34e5fc)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x19c730, L"DxDiag_DisplayDevices", 0x1a11c0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1a1958, L"DxDiag_SoundDevices", 0x1a1978)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x1a1958, L"DxDiag_SoundCaptureDevices", 0x1a19c8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x19c730, L"DxDiag_DirectSound", 0x1a1958)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x19c730, L"DxDiag_DirectMusic", 0x1a1a88)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x19c730, L"DxDiag_DirectInput", 0x1a1af0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x19c730, L"DxDiag_DirectPlay", 0x1a1b58)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x1a1eb0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1eb0, 1, 0x1a1ec8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1eb0, 1, 0x1a24e0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1eb0, 1, 0x1a3768)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1eb0, 1, 0x1a3b58)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1eb0, 1, 0x1a4140)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1eb0, 1, 0x1a4568)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1eb0, 1, 0x1a5ea0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1eb0, 1, 0x1a62f8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x1a1e88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x1a1e88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x1a1e90)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1e90, 1, 0x1a1ea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x1a1e58)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a1e58, 1, 0x1a1e70)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x1a20f8)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x1a66c8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a66c8, 1, 0x1a7458)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x1a66c8, 1, 0x1a7470)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szCatName", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidCat", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5ec)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szClsidFilter", 0x34e5ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"szName", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwMerit", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwInputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x1a1db8, L"dwOutputs", 0x34e5cc)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x19c730, L"DxDiag_DirectShowFilters", 0x1a1db8)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x19c730, L"DxDiag_SystemInfo", 0x34f130)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x19c750, L"dwDirectXVersionMajor", 0x34f10c)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x19c750, L"dwDirectXVersionMinor", 0x34f10c)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x19c750, L"szDirectXVersionLetter", 0x34f10c)
wine: Unhandled page fault on read access to 0x00000000 at address 0x7f97c3 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x007f97c3).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:007f97c3 ESP:0034c264 EBP:00000005 EFLAGS:00010202(   - 00      - -RI1)
 EAX:0034c274 EBX:04000500 ECX:00000000 EDX:00000500
 ESI:016b1e00 EDI:00010026
Stack dump:
0x0034c264:  0040e929 0034c274 00000000 00415501
0x0034c274:  00000000 04000500 0041568f 004159da
0x0034c284:  00000005 00010026 0034c2dc 7ee08ce4
0x0034c294:  00000001 00000115 00000001 7c015898
0x0034c2a4:  0034da50 0034c270 7c0158c1 7ede5bba
0x0034c2b4:  00010026 00000005 00000000 04000500
Backtrace:
=>1 0x007f97c3 in everquest2 (+0x3f97c3) (0x00000005)
  2 0x00000000 (0x00000000)
0x007f97c3: movl        0x0(%ecx),%eax
Modules:
Module  Address                 Debug info      Name (120 modules)
PE        350000-  3b8000       Deferred        js3250
PE        3c0000-  3c8000       Deferred        plc4
PE        3d0000-  3d6000       Deferred        plds4
PE        400000- 10e4000       Export          everquest2
PE      10000000-1063b000       Deferred        xul
PE      21100000-2118c000       Deferred        mss32
PE      30000000-30028000       Deferred        nspr4
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca3000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca3000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
ELF     7d1b6000-7db4e000       Deferred        libglcore.so.1
ELF     7db4e000-7dbe4000       Deferred        libgl.so.1
ELF     7dbe4000-7dc2e000       Deferred        dsound<elf>
  \-PE  7dbf0000-7dc2e000       \               dsound
ELF     7dc3d000-7dc51000       Deferred        avicap32<elf>
  \-PE  7dc40000-7dc51000       \               avicap32
ELF     7dc51000-7dc6f000       Deferred        devenum<elf>
  \-PE  7dc60000-7dc6f000       \               devenum
ELF     7dc6f000-7dcc5000       Deferred        ddraw<elf>
  \-PE  7dc80000-7dcc5000       \               ddraw
ELF     7dcc5000-7dcdf000       Deferred        dxdiagn<elf>
  \-PE  7dcd0000-7dcdf000       \               dxdiagn
ELF     7ddf0000-7de05000       Deferred        psapi<elf>
  \-PE  7de00000-7de05000       \               psapi
ELF     7de05000-7de4e000       Deferred        dbghelp<elf>
  \-PE  7de10000-7de4e000       \               dbghelp
ELF     7de4e000-7de9f000       Deferred        libgcrypt.so.11
ELF     7de9f000-7dea3000       Deferred        libgpg-error.so.0
ELF     7dea3000-7deb3000       Deferred        libtasn1.so.3
ELF     7deb3000-7deb5000       Deferred        libkeyutils.so.1
ELF     7deb5000-7dee3000       Deferred        libcrypt.so.1
ELF     7dee3000-7df53000       Deferred        libgnutls.so.13
ELF     7df53000-7df78000       Deferred        libk5crypto.so.3
ELF     7df78000-7e000000       Deferred        libkrb5.so.3
ELF     7e000000-7e029000       Deferred        libgssapi_krb5.so.2
ELF     7e029000-7e05e000       Deferred        libcups.so.2
ELF     7e05e000-7e073000       Deferred        midimap<elf>
  \-PE  7e060000-7e073000       \               midimap
ELF     7e073000-7e099000       Deferred        msacm32<elf>
  \-PE  7e080000-7e099000       \               msacm32
ELF     7e099000-7e0b1000       Deferred        msacm32<elf>
  \-PE  7e0a0000-7e0b1000       \               msacm32
ELF     7e0b1000-7e177000       Deferred        libasound.so.2
ELF     7e183000-7e185000       Deferred        libnvidia-tls.so.1
ELF     7e185000-7e1ba000       Deferred        winealsa<elf>
  \-PE  7e190000-7e1ba000       \               winealsa
ELF     7e20c000-7e23e000       Deferred        uxtheme<elf>
  \-PE  7e210000-7e23e000       \               uxtheme
ELF     7e23e000-7e247000       Deferred        libxcursor.so.1
ELF     7e247000-7e24c000       Deferred        libxfixes.so.3
ELF     7e24c000-7e24f000       Deferred        libxcomposite.so.1
ELF     7e24f000-7e255000       Deferred        libxrandr.so.2
ELF     7e255000-7e25d000       Deferred        libxrender.so.1
ELF     7e25d000-7e260000       Deferred        libxinerama.so.1
ELF     7e260000-7e265000       Deferred        libxdmcp.so.6
ELF     7e265000-7e268000       Deferred        libxau.so.6
ELF     7e268000-7e359000       Deferred        libx11.so.6
ELF     7e359000-7e367000       Deferred        libxext.so.6
ELF     7e368000-7e370000       Deferred        libkrb5support.so.0
ELF     7e370000-7e373000       Deferred        libcom_err.so.2
ELF     7e375000-7e404000       Deferred        winex11<elf>
  \-PE  7e380000-7e404000       \               winex11
ELF     7e46e000-7e48e000       Deferred        libexpat.so.1
ELF     7e48e000-7e4b9000       Deferred        libfontconfig.so.1
ELF     7e4c7000-7e4dc000       Deferred        libz.so.1
ELF     7e4dc000-7e54c000       Deferred        libfreetype.so.6
ELF     7e54c000-7e5ef000       Deferred        oleaut32<elf>
  \-PE  7e560000-7e5ef000       \               oleaut32
ELF     7e5ef000-7e60c000       Deferred        imm32<elf>
  \-PE  7e600000-7e60c000       \               imm32
ELF     7e60c000-7e704000       Deferred        wined3d<elf>
  \-PE  7e620000-7e704000       \               wined3d
ELF     7e704000-7e735000       Deferred        d3d9<elf>
  \-PE  7e710000-7e735000       \               d3d9
ELF     7e735000-7e7d6000       Deferred        comdlg32<elf>
  \-PE  7e740000-7e7d6000       \               comdlg32
ELF     7e7d6000-7e80b000       Deferred        winspool<elf>
  \-PE  7e7e0000-7e80b000       \               winspool
ELF     7e80b000-7e86a000       Deferred        rpcrt4<elf>
  \-PE  7e820000-7e86a000       \               rpcrt4
ELF     7e86a000-7e90d000       Deferred        ole32<elf>
  \-PE  7e880000-7e90d000       \               ole32
ELF     7e90d000-7e99a000       Deferred        winmm<elf>
  \-PE  7e920000-7e99a000       \               winmm
ELF     7e99a000-7e9ad000       Deferred        libresolv.so.2
ELF     7e9bb000-7e9d9000       Deferred        iphlpapi<elf>
  \-PE  7e9c0000-7e9d9000       \               iphlpapi
ELF     7e9d9000-7ea04000       Deferred        ws2_32<elf>
  \-PE  7e9e0000-7ea04000       \               ws2_32
ELF     7ea04000-7ea1d000       Deferred        wsock32<elf>
  \-PE  7ea10000-7ea1d000       \               wsock32
ELF     7ea1d000-7eade000       Deferred        comctl32<elf>
  \-PE  7ea30000-7eade000       \               comctl32
ELF     7eade000-7eb36000       Deferred        shlwapi<elf>
  \-PE  7eaf0000-7eb36000       \               shlwapi
ELF     7eb36000-7ec3d000       Deferred        shell32<elf>
  \-PE  7eb50000-7ec3d000       \               shell32
ELF     7ec3d000-7ec88000       Deferred        advapi32<elf>
  \-PE  7ec50000-7ec88000       \               advapi32
ELF     7ec88000-7ed20000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed20000       \               gdi32
ELF     7ed20000-7ee5e000       Deferred        user32<elf>
  \-PE  7ed40000-7ee5e000       \               user32
ELF     7ee5e000-7ee72000       Deferred        lz32<elf>
  \-PE  7ee60000-7ee72000       \               lz32
ELF     7ee72000-7ee8b000       Deferred        version<elf>
  \-PE  7ee80000-7ee8b000       \               version
ELF     7efaa000-7efb5000       Deferred        libnss_files.so.2
ELF     7efb5000-7efcd000       Deferred        libnsl.so.1
ELF     7efcd000-7eff2000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     f7c91000-f7c9a000       Deferred        libnss_compat.so.2
ELF     f7c9b000-f7c9f000       Deferred        libdl.so.2
ELF     f7c9f000-f7de9000       Deferred        libc.so.6
ELF     f7dea000-f7e02000       Deferred        libpthread.so.0
ELF     f7e10000-f7f24000       Deferred        libwine.so.1
ELF     f7f26000-f7f44000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Sony\EverQuest II\EverQuest2.exe
        00000012    0
        00000009    0 <==
0000000a 
        0000000b    0
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
00000010 
        00000011    0
Backtrace:
=>1 0x007f97c3 in everquest2 (+0x3f97c3) (0x00000005)
  2 0x00000000 (0x00000000)


```

---

### Post by javafiend on 2008-03-21
Can anyone help?  I'd really like to get playing again :(

---

### Post by issashu on 2008-03-25
Is anyone having program path problems? The soe launcher works great and patches everything as needed, but there is one problem I can't get rid of.
When I try to launch the game, it always wants to install and execute in my home dir. Not in a subfolder, but DIRECTLY in my main home dir. I tried copying the game from my windows desktop, so I can avoid the long download times. I run eq2.exe and the launcher starts, and downloads in the main home dir, ignoring my eq2 folder. I left it to run and logged in. Then it started downloading the whole game, again ignoring the 9 GB folder...
I tried all kind of tricks to make it run IN the game folder, but without luck. At the end this morning, I just trew the whole eq2 folder in my home dir, just to see if it works. The patcher started and recognised everything. The game didn't launch, but I didn't have time to track that problem. If the game work great, I juuuust might live with the homedir mess for a while, but would preffer to have an eq2 folder.

If I remember right, there was a way to set application paths in wine, but can't remember how.

P.S.: Forgot to say, I tried to install the game from the original 2 DVDs, but installer isn't working. It starts and shows a white window and nothing happens.

EDIT: Managed to get past the above problem, but now am facing the same as javafiend.

---

### Post by Eschia on 2008-12-03
I followed the font instructions for the EQ2.ini file, have wine 1.1.9, and Ubuntu hardy. My Nvidia card model is geforce 5200 FX (128MB). When I ran WinXP on this machine i was capable of running EQ2 using the high performance profile in the options. I'm not having the font issue. However I am having a graphical issue. When i load everquest2.exe I can hear the title music playing but i see a black screen for a long time then it turns solid white. Any idea?

---

