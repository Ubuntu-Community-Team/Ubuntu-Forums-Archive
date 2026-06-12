---
title: "How to move your Wine &quot;C Drive&quot;"
date: 2009-05-27
forum: Wine
---

### Post by Nyken on 2009-05-27
Okay, read quite a few threads about how to do this, but none of them 
satisfactory, so I did some of my own experimenting. I'm writing each 
step down that works as I do them, so as to show that it should work for
you all.

First, open File Browser and press CTRL-h to unhide the contents 
of your Home directory.

Move the "drive_c" folder of your /home/user_name/.wine folder
to the alternate hard drive of your choice. Once it's there go to it's icon,
right click on it and chose to "Make Link." 

Third, remove the .wine folder from your Home directory so as to make this 
transition 100% clean. (I'm a bit obessive-compulsive about these things, but
I still recommend it.) You'll have to remove things as root. Some directories 
won't go quietly until they are emptied, so empty them as needs before
deleting the folders. 

Fourth, at this point, you should have no .wine folder at all. Now, at the
command line, run Winecfg and let it do it's thing. Close it when done.

Open your newly recreated .wine folder and rename the "drive_C" folder to
"drive_c1". You'll now want to put the link to your moved drive_c folder
in this new .wine folder and rename it "drive_c". This should, when you
go to Applications/Wine/Browse C:\ Drive take you to the "drive_c" folder
that you moved.

Lastly, go into the drive_c folder you moved and find and make a link to
the Program Files folder. Cut it. Go back to the .wine folder in your Home and 
rename the Program Files folder there to "Program Files1". Paste the link
and rename it "Program Files".

Once the links are established, you can remove the "c_drive1" folder from
your .wine folder. Wine will use those just fine.


Tried installing something simple like Note Tab Light off an old PC World CD 
to see where Wine would install programs installed after this fiasco and 
it properly found the moved drive_c Program Files folder. Everquest did so 
as well. :D
    

Hope this helps!

---

### Post by Nicolas.Perrault on 2010-04-04
Thanks Bud!

---

### Post by sonnet on 2012-12-28
I'm running KDE, and Dolphin file manager doesn't seem to have the option "make a link".
Does anyone knows how to solve this issue?

---

