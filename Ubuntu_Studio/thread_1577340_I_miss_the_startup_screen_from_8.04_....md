---
title: "I miss the startup screen from 8.04 ..."
date: 2010-09-18
forum: Ubuntu Studio
---

### Post by Troon on 2010-09-18
Hi,

anyone know how to get the great looking 'ubuntu studio' splash screen (shows while machine boots) from 8.04 - its has a white bar that oscillates inside the 'ubuntu studio' text. i upgraded through 9 to 10.04 and now its a mess of wrong resolution and sections of the screen in the wrong place. basically its screwed


any ideas??

cheers

---

### Post by 23dornot23d on 2010-09-18
I wrote this little help page for myself ..... each time I set up a new system .... with Grub2 .... Lucid and later,
as I use it quite a lot ...... [LINK]("https://sites.google.com/site/linuxbootubuntu/")

The bit you need is setting the correct start size for your computer in Grub 

( as this is probably set a default of something like 640 x 480 .... )

So if you type [B]
xrandr[/B] 
as described in the write up ..... it should let you see what resolutions you have available ...... 

[COLOR=Red]You need to get this right otherwise you may not be able to boot properly[/COLOR]

Then go down to this line .... but put in the size that suits your screen ...... 
I think this will solve your problem then - every computer has different resolutions ...
so set this to whatever your display works ok with - 
( This alone will change the menu only .... to the new resolution .... for the full setup use the link above )

[B]gksudo gedit /etc/default/grub
set gfxmode=1440x900
[/B] 
Then its a case of following the instructions to set it up to work ......

Dont forget to 

[B]update-grub 
[/B] 
at the end

( Once you have this set right the other splash screen starts to look ok again )

---

