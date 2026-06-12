---
title: "Backgrounds are gone after installing gnome 3.6"
date: 2013-03-29
forum: Ubuntu Development Version
---

### Post by geovino on 2013-03-29
I've installed 13.04 and after installing gnome and then logging out and back into unity desktop, the backgrounds are gone. What happened? How do you get backgrounds back in unity and gnome?

---

### Post by ManamiVixen on 2013-03-29
Gnome 3.8 changed where the settings for wallpapers are stored. Unity dosen't look in that new place and so cannot work with the Gnome 3.8 repo ATM.

By the way, the Gnome ppa for Raring provides Gnome 3.8.

---

### Post by geovino on 2013-03-30
so gnome 3.6 doesn't work with unity in 13.04?

I reinstalled 13.04 and haven't thought of using gnome at this point... what is the ppa to install gnome 3.8?

---

### Post by ManamiVixen on 2013-03-30
No, the Gnome PPA for Raring provides 3.8. Raring by default uses Gnome 3.6. The no wallpapers is a bug that is being worked out, but most likely will never be fixed anytime soon unless either Canonical or The Gnome Foundation give in and support each other's desktops, which they won't. The Gnome 3 PPA though supports a pure Gnome desktop, no Unity installed. This will be the PPA people on Ubuntu Gnome Remix will be using to upgrade UGR in the comming month or so.

---

### Post by geovino on 2013-03-31
So it looks like you can't use unity and gnome on the same install without breaking the background wallpaper. Until they fix the bug, I'll forget about installing gnome. :(

---

### Post by zika on 2013-03-31
> **geovino said:**
> So it looks like you can't use unity and gnome on the same install without breaking the background wallpaper. Until they fix the bug, I'll forget about installing gnome. :(I've done **tons** of work (for my real-life job) these days just on Gnome&(occasionally)Unity and did not even notice that background is broken, except finding way of making black BG stick (in thread about G3.8 PPA)... Is BG really so important that someone could abstain of using Ubuntu just because of that...? Not preaching,, just being curious on a break of doing stuff... Or breaking stuff, who knows, Monday will show...

---

### Post by mc4man on 2013-03-31
Can't really see why Ubuntu would need to keep the Desktop active, doesn't seem to fit in with the grand convergence, though maybe they have a use for it.
If they don't, most people will get used to it, some won't..
(atm Hud on panel items is non-functional without Desktop focus & maybe a few other minor issues

---

### Post by EgoGratis on 2013-03-31
I added PPA because i wanted to test new Classic Mode and i noticed wallpaper does not work anymore in Unity or GNOME Classic Mode. It is interesting while logging out for one second wallpaper is shown and it might be related to the fact LightDM greeter still shows the wallpaper correctly.

Anyway if Classic Mode will get GNOME devs attention and will be treated as "standalone DE" not related and bend to GS paradigm in 2 to 4 dev cycles we could get something useful and fun to use again on the desktop and GS on tablet for example. About the wallpaper issue it would be nice if this would be fixed because icons on desktop + working wallpaper is something that will be used for foreseeable future and it Unity (next) on desktop would not want to provide this anymore this could still be the problem for GNOME Shell/Classic Mode.

---

### Post by mc4man on 2013-03-31
> **EgoGratis said:**
> I added PPA because i wanted to test new Classic Mode and i noticed wallpaper does not work anymore in Unity or GNOME Classic Mode. It is interesting while logging out for one second wallpaper is shown and it might be related to the fact LightDM greeter still shows the wallpaper correctly.

You could take a look at these 3, not sure if gdm works better or not, no longer have that install
[http://ubuntuforums.org/showthread.php?t=2121738&p=12578411&viewfull=1#post12578411](http://ubuntuforums.org/showthread.php?t=2121738&p=12578411&viewfull=1#post12578411)
[http://ubuntuforums.org/showthread.php?t=2121738&p=12578717&viewfull=1#post12578717](http://ubuntuforums.org/showthread.php?t=2121738&p=12578717&viewfull=1#post12578717)
[http://ubuntuforums.org/showthread.php?t=2121738&p=12580016&viewfull=1#post12580016](http://ubuntuforums.org/showthread.php?t=2121738&p=12580016&viewfull=1#post12580016)

If inclined look for/report a bug to ppa or upstream if a gnome issue

---

### Post by EgoGratis on 2013-03-31
> Gnome 3.8 changed where the settings for wallpapers are stored. Unity  dosen't look in that new place and so cannot work with the Gnome 3.8  repo ATM.

If this is true then i guess the problem will be solved not later than in Ubuntu using GNOME 3.8 and because of that i will not investigate this further i just wanted to test new GNOME Classic Mode because GS is not something i would like to use on desktop for now and Classic Mode is not there yet but i do see a lot of potential!

For Ubuntu 13.04 i look forward to use Unity + Compiz because it's fun pair to use it and it works nicely and probably Compiz will be replaced with something else in Unity Next and in GNOME 3 Classic Mode it doesn't work anymore with Compiz... That said i will enjoy and use default Ubuntu 13.04 for now because i think currently this is the most optimal solution for me and i like cool new features like for example better animation support in "aero snap" in Ubuntu 13.04 and will hope for the best outcome in the future.

---

### Post by clayt0njknight on 2013-04-24
> **EgoGratis said:**
> If this is true then i guess the problem will be solved not later than in Ubuntu using GNOME 3.8 and because of that i will not investigate this further i just wanted to test new GNOME Classic Mode because GS is not something i would like to use on desktop for now and Classic Mode is not there yet but i do see a lot of potential!

For Ubuntu 13.04 i look forward to use Unity + Compiz because it's fun pair to use it and it works nicely and probably Compiz will be replaced with something else in Unity Next and in GNOME 3 Classic Mode it doesn't work anymore with Compiz... That said i will enjoy and use default Ubuntu 13.04 for now because i think currently this is the most optimal solution for me and i like cool new features like for example better animation support in "aero snap" in Ubuntu 13.04 and will hope for the best outcome in the future.

I've actually found the bug lies in the process for the file manager to handle the desktop.  If you download Gnome-Tweak-Tool, open and click the "Desktop" selection on the left, then simply switch off the top option, all is well.

Unfortunately, in doing so, you no longer have desktop icons, even if they are enabled.  But at least you get your wallpaper back! 

This issue has reared it's ugly head again in Gnome 3.8 under Ubuntu 13.04 beta it seems... :(

---

### Post by EgoGratis on 2013-04-24
Thank for the effort but i must say:

> Unfortunately, in doing so, you no longer have desktop icons, even if  they are enabled.  But at least you get your wallpaper back!

No. 

That would not work for me i need my wallpaper and icons on the desktop and i hope it will stay these way for at least another decade.

---

### Post by giorsat on 2013-04-25
I have installed gnome remix with gnome ppa enabled (that means I have only gnome 3.8 installed) and I have a missing wallpaper problem too. I can see only when I go to activities otherwise I got a white wallpaper. very annoying. plus, if i create a new user, it has a normal wallpaper. so my question is. how can i delete / reset the settings in my gnome user account so that the system sees it as a new user (hopefully getting the wallpaper workin again....)

---

### Post by markbl on 2013-04-26
> **EgoGratis said:**
> 
That would not work for me i need my wallpaper and icons on the desktop and i hope it will stay these way for at least another decade.
If you turn off file manager managing desktop via gnome-tweak-tool then you still get the wallpaper, you just don't get folders and icons on your desktop.

Personally, I believe that people who think they need stuff on their desktop are not thinking clearly. The desktop is a sub-optimal window which can not be raised, sorted, moved, etc. People think they need it **only** because they had it on windows 95 etc. They don't need it and will work more effectively without it. Just click on the Files/Nautlus icon in your dash/launcher and you have all the power of the file manager in one or more windows.

---

### Post by Varemenos on 2013-04-26
Just turn it off and back on again. It will load the wallpaper (not sure if it will stick after you go back to unity and back though)

---

### Post by Malac on 2013-04-29
I tried changing the desktop from tweak tool and it seems the jpg files in /usr/share/backgrounds work but not the png files.

Try using jpg's or converting your png images to jpg.

I'm using 13.04 and Gnome Shell 3.8.2

Hope this helps.

EDIT: Just checked this and on my set up jpg's and even png work as backgrounds if they are 2048 x 1357. The original width of Ubuntu png was 2560 x 1600

---

### Post by bmwerks on 2013-04-30
try this in terminal

gsettings set org.gnome.settings-daemon.plugins.background active true

or what i did was to use dconf editor and followed the series of expandable tabs starting with "org" then "gnome settings" and so on from the command above and then activated the option.

....basically its like the background is off and this turns it back on.

---

### Post by EgoGratis on 2013-04-30
> **markbl said:**
> If you turn off file manager managing desktop via gnome-tweak-tool then you still get the wallpaper, you just don't get folders and icons on your desktop.

Personally, I believe that people who think they need stuff on their desktop are not thinking clearly. The desktop is a sub-optimal window which can not be raised, sorted, moved, etc. People think they need it **only** because they had it on windows 95 etc. They don't need it and will work more effectively without it. Just click on the Files/Nautlus icon in your dash/launcher and you have all the power of the file manager in one or more windows.

You do in what you personally believe works best for you and i am fine with that but i will do in what i personaly believe is the best for me and what i and billions of people are doing for decades. Just because small group of people don't like majority of desktop users put files and folders on the desktop doesn't in any way mean majority of desktop users should do what small group of people personally believe.

In order to personally convince majority of desktop users to stop using desktop icons one must make better replacement and "turning desktop icons off" feature is clearly not it. W95 used this paradigm yes but it was invented before that and not by Microsoft.

When somebody smart enough will come up with better paradigm then majority of users will probably use it for next few decades and that is about it. Current paradigm works best with icons on the desktop and by turning them off you are doing it wrong but OK if it works for you...

---

### Post by Malac on 2013-05-01
> **markbl said:**
> If you turn off file manager managing desktop via gnome-tweak-tool then you still get the wallpaper, you just don't get folders and icons on your desktop.

Personally, I believe that people who think they need stuff on their desktop are not thinking clearly. The desktop is a sub-optimal window which can not be raised, sorted, moved, etc. People think they need it **only** because they had it on windows 95 etc. They don't need it and will work more effectively without it. Just click on the Files/Nautlus icon in your dash/launcher and you have all the power of the file manager in one or more windows.

So hang on instead of just being able to click on one icon on my desktop I have to:
 1/. Open a menu 
2/. Navigate to a file manager shortcut
3/. Then click on that shortcut which opens my Home folder
4/. Then navigate to the file I wanted to open in the first place. (which may be amongst quite a few others).
5/. Then finally click on that file and I've accomplished in five operations what I could by clicking once on a launcher or file on my Desktop.

You obviously don't work on multiple projects at once, each with multiple files in different directories.

Yes the Desktop hasn't got the features of a "proper" window it is a "scratch" area if you like where you put your most used launchers and/or files until you don't need them any more then put them away. You used to be able to sort it until they started mucking about with it but you can still do it manually just grab the icon and move it where you want it.
Exactly like working at a real desk you move things about put it out of the way but still handy then when you're done it goes in a drawer or is filed in a cabinet or shredded :-)

The Desktop concept saves valuable seconds which over a working week or year soon adds up.

As previous poster said though each to there own and what ever works for you.

---

### Post by markbl on 2013-05-01
> **Malac said:**
> 
The Desktop concept saves valuable seconds which over a working week or year soon adds up.
No it doesn't. Actually it is losing valuable seconds. You just think you are more efficient keeping the same desktop you had with Windows 95 because it is human nature to be resilient to change. I could easily debate your points but it won't "click" until you work it out for yourself. We have moved on since that 90's windows desktop analogy to a real desk.

The desktop should be a blank slate over which app windows (including file manager windows) are placed and switched between. If you think you need a "show desktop" function, or a desktop trash icon (lol), then you are doing it wrong.

---

### Post by cariboo on 2013-05-01
> **markbl said:**
> No it doesn't. Actually it is losing valuable seconds. You just think you are more efficient keeping the same desktop you had with Windows 95 because it is human nature to be resilient to change. I could easily debate your points but it won't "click" until you work it out for yourself. We have moved on since that 90's windows desktop analogy to a real desk.

The desktop should be a blank slate over which app windows (including file manager windows) are placed and switched between. If you think you need a "show desktop" function, or a desktop trash icon (lol), then you are doing it wrong.

I actually I think this is what is wrong with both Unity, and Gnome-shell, the designers think that their way is the best way to do things, without even thinking about the different ways different people use their computers. My personal preference is to not have any extra icons on the desktop, and has been for years, but just because that's the way I use my system doesn't mean that everyone should use theirs the same way.

Hopefully eventual OS designers will see the error of their ways, and come to realize that not everyone is a new user, or a developer.

---

### Post by mc4man on 2013-05-01
> **markbl said:**
> 
...
Personally, I believe that people who think they need stuff on their desktop are not thinking clearly...
Don't think it goes that deep. People simply prefer things, in this case many like a 'Desktop' (folder) that can have a changeable custom background, limited specific context menu where they can place & access stuff.

> **markbl said:**
> 
 If you think you need a "show desktop" function, or a desktop trash icon (lol), then you are doing it wrong.
Likely not what users would be missing with no Desktop, even if so, certainly not "wrong" on their part.

---

### Post by kevpan815 on 2013-05-01
> **cariboo907 said:**
> I actually I think this is what is wrong with both Unity, and Gnome-shell, the designers think that their way is the best way to do things, without even thinking about the different ways different people use their computers. My personal preference is to not have any extra icons on the desktop, and has been for years, but just because that's the way I use my system doesn't mean that everyone should use theirs the same way.

Hopefully eventual OS designers will see the error of their ways, and come to realize that not everyone is a new user, or a developer.

With the Unity Interface it's easy to remove all of it from your Desktop, just Right-Click Un-Dock from Launcher. I do it all the time. :-)

---

### Post by EgoGratis on 2013-05-02
> **markbl said:**
> No it doesn't. Actually it is losing valuable seconds. You just think you are more efficient keeping the same desktop you had with Windows 95 because it is human nature to be resilient to change. I could easily debate your points but it won't "click" until you work it out for yourself. We have moved on since that 90's windows desktop analogy to a real desk.

The desktop should be a blank slate over which app windows (including file manager windows) are placed and switched between. If you think you need a "show desktop" function, or a desktop trash icon (lol), then you are doing it wrong.

It has nothing to do with W95 it just works better than current alternatives and that is about it. Some users will always try to do it differently and that is OK but for majority of users this desktop concept/paradigm/metaphor invented before W95 currently works best. There is no real alternative to convince majority of users on desktop ATM and yes "turn off desktop icons" is clearly not it. Your solution is in no way more productive in the end it's just personal preference to have empty desktop and to use file manager every time you need to access some file or folder but majority of users i assure you don't see it like that.

---

### Post by Malac on 2013-05-04
> **markbl said:**
> Actually it is losing valuable seconds. You just think you are more efficient keeping the same desktop you had with Windows 95.
No, I've actually timed it, time and motion and all that. :-)

> **markbl said:**
> If you think you need a "show desktop" function, or a desktop trash icon (lol), 
Don't have "Show Desktop" shortcut or ever use the key combo.
I don't even use Trash at all everything is "Shift-Delete"'d. If I'm deleting something I don't want it back again.

> **markbl said:**
> then you are doing it wrong.
For your way of working which is comfortable for you.

As for the "Windows95" way of working. I started out computer use in the DOS/CPM days doing machine code before moving to C programming on Unix(yes Unix not Linux) I am not set in my ways and still hand code a lot for programs as GUI just adds too much kludge. I'm not some Desktop evangelist, I just believe it has it's place as a scratch area when working on multiple files in multiple programs and/or multiple projects at once. If you are only working in one program with one or two files then you don't need the Desktop as a scratch area but otherwise it saves time..........for me. :-)

---

### Post by x2l2 on 2013-07-16
> **bmwerks said:**
> try this in terminal

gsettings set org.gnome.settings-daemon.plugins.background active true

or what i did was to use dconf editor and followed the series of expandable tabs starting with "org" then "gnome settings" and so on from the command above and then activated the option.

....basically its like the background is off and this turns it back on.

THANKS thats works for me

---

