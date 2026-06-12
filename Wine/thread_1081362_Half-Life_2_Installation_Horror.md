---
title: "Half-Life 2 Installation Horror"
date: 2009-02-26
forum: Wine
---

### Post by Junkieman on 2009-02-26
Hi all, so I would love to know how those who play HL2 in WINE got it to install. It's driving me nuts and I have run out of tricks to try!

I'm installing from original CD's, and someway into CD 2 I get this error:

```
Installation ended prematurely because of an error
``` :mad:

I tried the tutorial at [foxholeunderground.com]("http://www.foxholeunderground.com/serendipity/index.php?/archives/1-The-Ultimate-Counter-Strike-Source-Ubuntu-Installation-Guide.html"), both methods: Making a compiled DVD ISO, and installing from the CD's. I have tried all compatability combinations with WINE (98,2000,VISTA) and even updated MSIEXEC within WINE, no luck. 

I installed Steam fine and it's even logging in, but I just don't have the bandwidth to install HL2 through Steam. There is a much [older thread here]("http://ubuntuforums.org/showthread.php?t=807773&highlight=half+life+prematurely") but that was of no help unfortunately.

Following the instructions at [winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2890") only gets me this far...

I suspect it's an installer issue, damn msiexec! If only I can get it to install...

Is there anyone out there who successfully installed HL2 from the originals? Any tricks or help would make you a hero!

**Info**
Ubuntu 8.10 (intrepid)
Proc Intel core duo with 3GB of memory, Intel integrated video
WINE version 1.0.1

---

### Post by bjnueva8623 on 2009-02-28
I'm having the same exact problem. Hopefully someone can help. I'll let you know if I ever find a solution.

---

### Post by kidux on 2009-02-28
Forgive me, I haven't played PC games in a while, but what about installing it on Win in a VM or dual boot, then copy the installed directory to .wine?

---

### Post by ScarySquirrel on 2009-02-28
tinyXP partition + Wine

---

### Post by betrunkenaffe on 2009-02-28
I downloaded it using Steam.

---

### Post by aaronb on 2009-02-28
I think you can... 

1. Install steam and login.
2. Make sure it is not currently running (Exit out of it).
3. Manually copy the *.gcf files to your steamapps folder from the CD.
4. Start steam.
5. Attempt to run the game. Steam should decrypt the files and download any updates.

This will only work if its a legal copy and you have registered the CD key in steam already.

---

### Post by fmarier on 2009-03-01
Here's a way to manually install Half-Life 2 if the installer
won't let you go past the first CD.

1- Install using the installer until it fails
   (into the default directory -- C:\Program Files\Steam)

2- Copy all .cab files from all CDs into a temporary directory

3- Install the "cabextract" package and extract all of the game files:

  cabextract hlf2.CAB

4- Rename the files so that they look like this:

base source shared.gcf                   css.ico
base source shared materials.gcf         half-life 2 base content.gcf
base source shared models.gcf            hl2.ico1
base source shared sounds.gcf            Source Shared Securom.gcf
counterstrike source base content.gcf    winui.gcf
counterstrike source shared content.gcf

(note the dash in "half-life 2" and the spaces instead of underscores)

5- Start up Steam and go to the games tab, Half-Life should be in there

---

### Post by Junkieman on 2009-03-02
Thanks all for the comments everyone, aaronb and fmarier for the excellent ideas, I will try these out tonight! :)

---

### Post by Junkieman on 2009-03-02
Thanks to the previous 2 posters, I extracted the CAB files and placed them in ~/.wine/drive_c/Program Files/Valve/Steam/SteamApps, logged into Steam and clicked "Install". It seemed to pick up the files and start decrypting them (why oh why steam?!). 

After the decryption it listed HL2 as Installed, but only at 41%! It started downloading the rest. My guess is that it installed and the rest is HL updates that Steam is pulling down, so I can't even launch the game until that is done. Restarting Steam in offline mode still refuses to launch the game ](*,)

I'm not sure I can let it run through though, some of us have caps :p

Thanks anyways guys for the great help! I'll have to find a cracked version somewhere, since it's such a ballache getting the REAL version running!

---

### Post by ScarySquirrel on 2010-04-24
So, did it blend?

---

### Post by asdfoo on 2010-04-24
> **ScarySquirrel said:**
> So, did it blend?


why are you digging up an old thread? if you are trying to install the same software via cd why don't you just tell us what went wrong if anything?

99.9% of people install HL2 via steam anyway.

---

