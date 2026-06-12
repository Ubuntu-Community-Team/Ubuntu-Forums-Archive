---
title: "no &quot;Synchronize on Ubuntu One&quot; menu item"
date: 2010-05-30
forum: Ubuntu One (CLOSED)
---

### Post by jonas.arnout on 2010-05-30
Hi

from what i've read the way to sync folders is to right click on them and select Synchronize on Ubuntu One. all very well, but i dont have the menuitem.

an other way to go, though i think its the old one is to drag them into Ubuntu One, a folder in my homedirectory.

m currently using ubuntu 10.04 netbook remix and my system is up to date

I can manualy upload files to ubuntu one, but not entire folders.

I have my netbook added as a divice on ubuntu one and it says "Syncronisation in process..."

u1sdtool --list-folders returns No folders

u1sdtool --list-shared returns
Shared list:
  id=c364c6d5-342f-4722-81d0-c710315aa8a2 name=Jonas **accepted=False** access_level=View to= path=/home/jonas/Ubuntu One

**so how do i add "Synchronize on Ubuntu One" menu item when i right click a folder?**

thx

edit:
one more thing: i do have the menu item Share on Ubuntu One... but when i select myself it still doesnt upload.

---

### Post by duanedesign on 2010-06-01
The option to synchronize folders is only available for folders in your $HOME directory. Are the folders you are trying to sync in your $HOME?

Currently you can only upload files through the webUI not entire folders.

---

### Post by jonas.arnout on 2010-06-01
thank you for your reply.

here is what i did wrong in the first place

i dragged the folder into ubuntu one, the folder in my homedir
after it didnt upload to the u1 servers i went on the internet and found out i was to right click it but i clicked it while it was still in the ubuntu one folder. (hence only share on U1 was found)

when i click a folder outside of the ubuntu one folder i get the sync on u1 menu item

so i moved the folders outside of the u1 folder and it works like a charm.

i found out that syncing by merly placing a link (and not moving the files to the ubuntu one folder ) will get U1 to sync those folders too? it seemed in developement at the time. is that feature done, cuz it didnt work for me.

as an idea to help u with the folder uploading thing for the webaccess of U1: take a look at how Gmail (and wave) handles attatchments. there u can select multiple files (but no folders) to upload at the same time, without selecting each file seperatly. m not sure how it works exactly but i do know that u need to have google gears installed for it to work.

thx again for helping me fix this problem

---

### Post by tlinuxx on 2010-06-22
It seems difficult to delete user-defined folder via web interface"one.ubuntu.com"

---

