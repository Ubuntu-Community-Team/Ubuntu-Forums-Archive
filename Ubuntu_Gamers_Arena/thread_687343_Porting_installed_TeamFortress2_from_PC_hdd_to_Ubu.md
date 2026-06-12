---
title: "Porting installed TeamFortress2 from PC hdd to Ubuntu"
date: 2008-02-04
forum: Ubuntu Gamers Arena
---

### Post by TommyPickles on 2008-02-04
Howdy all,

I have TeamFortress2 installed on my desktop PC.  I'd like to bring it over to my external hdd where I have installed Ubuntu (gutsy), so that I can then play it using Wine or Cedega on my HP NC6400 work laptop.

As I purchased OrangeBox via STEAM and I'm not a big fan of downloading gigs again, is there any way I can copy across the files and required registry settings to my Ubuntu hdd? Is the procedure the same\ whether I do so using Wine or Cedega? (if its different, I'll go down the Cedega path)

Much appreciated!

Cheers
Leon

---

### Post by TommyPickles on 2008-02-07
After a bit of digging around, here's the steps to port from PC to Linux if you've Steam downloaded.

On your PC, simply right-click the game of choice (say TF2), and select Backup Game. 

That aside, I've had troubles running Half-Life 2 and Counter-Strike on my HP nc6400 laptop (3 gig ram, 1.66 ghz Core 2 Duo).  If anyone knows how to get the sound working and best graphics setup, please let me know!

---

### Post by Roryking on 2008-02-20
Yes. Go to where Steam is installed on your windows partition (usually C:\Program Files\Steam\) and enter the "steamapps" folder. Theoretically, you can just copy/paste the steamapps folder to where you installed Steam on Wine (~/.wine/drive_c/Program files/Steam for me) and Steam will know what to do with the files. Alternatively you can just copy the .gcf and .ncf files and Steam will decompress them when you open the game, but you will then need to copy any custom maps you want to move from the respective game folders (also in steamapps, under the folder with your steam username). Please note that some games use more than one gcf, i.e. if you only move the TF2 file, Steam will try to download the "source shared content" gcf which comes out to an additional 2 or 3 GB.

---

