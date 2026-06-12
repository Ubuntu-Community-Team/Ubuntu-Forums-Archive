---
title: "I want to view my desktop during full screen games"
date: 2009-09-17
forum: Wine
---

### Post by Falc7 on 2009-09-17
When i play wine games they generally take up the whole screen, half life 2, and silent hill, and age of mythology are the ones i am thinking about. Is there some way to view my desktop without exiting the game? Like normally in windows you'd hit the windows key and the game would minimise, does kubuntu have an equivalent?

---

### Post by hikaricore on 2009-09-17
Depending on how the game uses "full screen" IE if it's just maximized or it's actually using a lower res and is holding the screen.
If the former is the case you can use keybindings in gnome/kde to switch desktops.
For example I'm playing a game on desktop 4 and i have my swtiching set to Ctrl+1-4.
I can hit Ctrl+1 , 2, or 3 to switch to a desktop the game isn't on, or I can hit Ctrl+4 to return to the game.
As I said depending on how the game is operating this may or may not work.
And you'll need to be mindful of ingame controls when setting your keybindings as the ctrl key may stick ingame after switching to a new desktop.

---

### Post by Bölvaður on 2009-09-17
> **hikaricore said:**
> 
For example I'm playing a game on desktop 4 and i have my swtiching set to Ctrl+1-4.

Yes but he probably needs to do Ctrl + Alt + &#8594; (right arrow key)

I on the other hand put my mouse in the bottom left corner... I guess it wont work for him though :(

---

### Post by Falc7 on 2009-09-18
I'm using kubuntu, how do i set those shortcuts up as none of them seem to be there by default :)

I thought it would be under the multiple desktops config section or input actions, but i didn't see it under either

---

### Post by hikaricore on 2009-09-18
I'm pretty sure it's under keyboard shortcuts but I'm not at home on my kde system atm.
Will update you on how to set them when I get out of work.  :p

---

### Post by beastrace91 on 2009-09-18
> **Falc7 said:**
>  Like normally in windows you'd hit the windows key and the game would minimise, does kubuntu have an equivalent?

I'd just like to point out that almost all full screen games I have played in Wine (CSS, TF2, WC3) are less than friendly when it comes to "alt-tabbing" - or changing from said full screen application to the desktop. Your mileage may very well vary from my own but I have found the best solution is running said full screen application in a "virtual desktop" or for best results a second X server (if you really still want it full screen with full desktop switching this is what you need to do). (the first is easy to setup the later takes a small bit of work)

~Jeff

---

### Post by hikaricore on 2009-09-18
Aye that's why I asked if was actual fullscreen or a maximised window taking up the full screen.

And for the OP to edit your keyboard shortcuts go into system setting from your kde menu and select Keyboard & Mouse.
Then select Global Shortcuts and choose KWin from the dropdown box to change desktop switching shortcuts.
If you're using desktop effects the location of this may vary, as I don't currently use them due to issues with my card I can't help you there.

---

### Post by Falc7 on 2009-09-18
> **hikaricore said:**
> Aye that's why I asked if was actual fullscreen or a maximised window taking up the full screen.

And for the OP to edit your keyboard shortcuts go into system setting from your kde menu and select Keyboard & Mouse.
Then select Global Shortcuts and choose KWin from the dropdown box to change desktop switching shortcuts.
If you're using desktop effects the location of this may vary, as I don't currently use them due to issues with my card I can't help you there.

Thanks this works. I am still getting used to KDE a little, as all the programs seem to show up in the taskbar on both desktops, is there a way to make it like gnome, where programs only show up in the taskbar on one desktop at a time? Anyway it works :D The resolution is a little muddled but nothing too bad.


> **beastrace91 said:**
> I'd just like to point out that almost all full screen games I have played in Wine (CSS, TF2, WC3) are less than friendly when it comes to "alt-tabbing" - or changing from said full screen application to the desktop. Your mileage may very well vary from my own but I have found the best solution is running said full screen application in a "virtual desktop" or for best results a second X server (if you really still want it full screen with full desktop switching this is what you need to do). (the first is easy to setup the later takes a small bit of work)

~Jeff

I'll try emulating a virtual desktop, and see how it goes :) thanks

---

### Post by hikaricore on 2009-09-18
> **Falc7 said:**
> Thanks this works. I am still getting used to KDE a little, as all the programs seem to show up in the taskbar on both desktops, is there a way to make it like gnome, where programs only show up in the taskbar on one desktop at a time? Anyway it works :D The resolution is a little muddled but nothing too bad.

Right click on your taskbar where there isn't a program already and select Task Manager Settings.
This will allow you to change the behavior of the tasks section of your bar.

---

### Post by WolfRage on 2009-10-22
Falc7 I just wanted to know what did you do to get AOM (Age of Mythology) to work on your system? I seem to have issues with the games frame rate per second, which causes the LAN play to lag for everyone else.

---

### Post by Falc7 on 2009-10-22
Yes i got it working, my problem wasen't due to FPS though, it was the ubuntu logging out, i solved it by creating a virtual desktop, so the game dosen't change th screen resolution.

---

### Post by WolfRage on 2009-10-22
Ok thanks I plan on using the virtual desktop on my next install attempt. Did you do anything else special besides this:
Copy "pidgen.dll" & "MFC45.dll" to sys32 folder.
Install AOM.
Install MSMXMLenu.msi
Install Version 1.10 patch.

---

### Post by Falc7 on 2009-10-22
Yep thats all i did, but i had to install MSMXMLenu.msi before i could install AOM. Everything runs flawlessly now, multiplayer LAN included

---

### Post by 8Kuula on 2009-10-22
I have used for HL2, CSS, Portal and L4D games fallowing method to get game to full screen and able to "alt+tab" to other programs/desktops.

I start game with -sw -noborder switches whitch starts game in windowed mode without borders. Fix resolution to max from game settings.

On HL2 and CSS -noborder switch won't work for some reason, do it work in windows? :P
So I have gone around that setting to excluding window decorations from Compiz Settings Manager there is Window Decoration selection and under that option Decoration windows: (any) & !(name=hl2.exe).

Other games like Wolfenstein for example I have gone around by adding in wine settings "add application" -> wolf2.exe and giving for it desktop size same as max resolution so its full screen. And from game options resolution to match. On games where can't get same resolution than on my screen I have played in window, lowered virtual desktop size to match games max resolution. Widescreen wanks image anyways then so it hurts my eyes ;)

P.S.
Damn Quake 4 (native) is hard locked focus or something, can't get that to "alt+tab" but that is other topic...

---

