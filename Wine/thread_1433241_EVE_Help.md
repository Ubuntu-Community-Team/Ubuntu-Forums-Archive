---
title: "EVE Help"
date: 2010-03-18
forum: Wine
---

### Post by drklunk on 2010-03-18
Now, I havent downloaded EVE yet but I will need some help configuring for it as the other two MMOs Ive tried to configure (GW and Perfect World) have both been laggy and, primarily, unplayable by my standards. 

Im on a laptop with ATI graphics and one of those fancy dual core AMDs. The graphics card shares memory with the 4gigs of ram and Im also on high-speed-ish DSL. The lag i experienced in both mentioned games is from the graphics as far as I can tell. 

Could anyone point me in the right direction to find out how to fully and properly configure Wine to play EVE Online? My drivers are all up to date as far as I know and I believe it just to my inability to properly set up Wine

---

### Post by Toffeeapple on 2010-03-19
I've found Eve to run pretty much flawlessly of late, but then I do have a decent Nvidia card. I get a good constant 60fps, there is a bit of stutter when first undocking or entering a system but I seem to recall that happening in windows too.

I think [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18563") is where you are going to find the best info on all things Eve and Wine, apart from ensuring you have some fonts installed (corefonts with winetricks does the trick) there isn't much that needs to be tweaked.

---

### Post by drklunk on 2010-03-19
Thanks man, yeah I saw elsewhere about the fonts and got them installed. Just sucks Ive got ATI, hopefully itll run alright

*edit*
Anyone mind explaining this to me?:
Ubuntu-9.10 has a known problem starting Eve-Online. This is a known issue specific to Ubuntu-9.10, and is not a problem with Wine. The workaround includes editting the prefs.ini file found in the Eve Online program folder. Edit "bitsCancelled=1" to "bitsCancelled=0".
   

This short script will also automate this function at Eve startup runtime:
   perl -pi -e 's/bitsCancelled=1/bitsCancelled=0/' "$HOME/.wine/drive_c/users/$USER/Local Settings/Application Data/CCP/EVE/c_program_files_ccp_eve_tranquility/settings/prefs.ini" && wine explorer /desktop=0,1680x1050 "C:\Program Files\CCP\EVE\eve.exe" & 
   

 Here is another using sed instead:
   sed -i -e '/bitsCancelled/ s/1/0/' prefs.ini && wine explorer /desktop=0,1680x1050 "C:\Program Files\CCP\EVE\eve.exe" & 
   

Thanks to N3o and Ilya Konovalovfor creating these scripts from the work-around I found along with others on the Eve Online Linux forums. 




I dont know how to do that stuff or what it is talking about.

---

### Post by Toffeeapple on 2010-03-19
There is an easier way, at least I think it is anyway.

In the folder found here.. (providing you haven't installed eve in it's own prefix or installed it with playonlinux or something)

"home/WHAT EVER YOUR USER NAME IS/.wine/drive_c/users/WHAT EVER YOUR USER NAME IS/Local Settings/Application Data/CCP/EVE/c_program_files_ccp_eve_tranquility/settings/"

is a file called 'prefs.ini'

add the line "bitsCancelled=0" without the quotes to that file if it's not already there and if it is make sure it is set to "0" again without the quotes.. run the game, set the preferences to how ever you like them within the game, exit the game go back to that file and make sure the 0 is still a 0 and then make the file read only...

That's what  I did anyway and it works just fine.

---

### Post by achelis on 2010-03-19
I don't know why it has to be done, but all the scripts does is editing the file:
```
.wine/drive_c/users/<username>/Local Settings/Application Data/CCP/EVE/c_program_files_ccp_eve_tranquility/settings/prefs.ini
```

Changing the line:
bitsCancelled=1
to
bitsCancelled=0

The scripts are simply there because it's easier than having to do it by hand :)

I don't know much about perl, but sed is a nice little tool where you can match patterns and substitute them for something else.

Say you have a file 'animal' with the line dog in it. The following sed program will then output cat.
```
sed -e 's/dog/cat/' animal
```

The -i simply tells sed to do replace in-place, that is not output it on the screen, but rather change the file. 
If you want to learn more about sed you can look here:[http://www.grymoire.com/Unix/Sed.html]("http://www.grymoire.com/Unix/Sed.html")

---

### Post by drklunk on 2010-03-19
Excellent guys, got it to work, thank you! Now just to resub and see how well it actually performs 0.o

*edit*
The game crashed when I tried to undock? Hmm...

---

### Post by Toffeeapple on 2010-03-20
Try disabling sound from within the game settings, or another thing is to rename the folder... 'Jukebox' to something else.

Found here..

home/WHAT EVER YOUR USER NAME IS/.wine/drive_c/Program Files/CCP/EVE/res/Audio/Jukebox

See if either of those two things help.

---

### Post by drklunk on 2010-03-20
Alright, Ill be giving that a shot. I wouldnt mind not having sound in the game at all since I listen to music while playing anyway. 

I followed this guide to configuring: [http://www.eve-search.com/thread/1007680/page/1](http://www.eve-search.com/thread/1007680/page/1)
I like having it as a window rather than taking up the whole screen but have issues with the resolution since the bottom tool bar covers a portion of the window. Is there a way to hide the bottom tool bar while its not in use or am I better off setting it to windowed mode within the game?

Also, Im having an issue with the prefs.ini. When I set it to "read only" itll work once or twice, then never again after that. I have to go through and redo the whole process. Any suggestions?

Thank you all for the help, much appreciated!

*edit*
If I were to use the sed method, would this be the proper code?:
sed -e 's/bitsCancelled=1/bitsCancelled=0/' prefs.ini 
Another issue Im having, none of the objects load. No ships, stations, planets, nothing except stars/suns. Any suggestions?

---

