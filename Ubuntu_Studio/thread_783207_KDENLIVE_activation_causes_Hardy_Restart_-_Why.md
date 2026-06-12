---
title: "KDENLIVE activation causes Hardy Restart - Why?"
date: 2008-05-05
forum: Ubuntu Studio
---

### Post by lubeck on 2008-05-05
Subject says it all.  Anyone?
Thanks.

---

### Post by theophiles on 2008-05-07
I'm having this problem too. Weirdest of all, it only happens about 2/3 of the time. Last summer I used Kdenlive a great deal. Then came the professorial commitments of the academic year. I wanted to get back to making movies now that the academic year is over, but i am having trouble with kdenlive and have never been even able to figure out even the basics of cinelerra.

---

### Post by Creative2 on 2008-05-07
use blender... as movie editor

---

### Post by lubeck on 2008-05-08
FOUND FIX.  Per Kdenlive WIKI "Known Bugs" page, it seems by simply deleting the .config file at  /home/"youruser name"/.kde/share/config/kdenliverc  eliminates the strange behavior.  

Apparently, upgrades have a way of messing this file up--perhaps not upward compatible.  

To Creative2:  Thanks.  Have Blender, but like the straightforwardness of Kdenlive for most stuff.  I am also a bit simple minded and Blender is really "deep." :)

---

### Post by wkulecz on 2008-05-08
"I have problem X with application Y" 

Use application Z, is not really a very helpful response.

Kind of like, my car won't start -- go buy a Lexus!

--wally.

---

### Post by theophiles on 2008-05-08
> **lubeck said:**
> FOUND FIX.  Per Kdenlive WIKI "Known Bugs" page, it seems by simply deleting the .config file at  /home/"youruser name"/.kde/share/config/kdenliverc  eliminates the strange behavior.  

Apparently, upgrades have a way of messing this file up--perhaps not upward compatible.  

To Creative2:  Thanks.  Have Blender, but like the straightforwardness of Kdenlive for most stuff.  I am also a bit simple minded and Blender is really "deep." :)

Thank you so much it works like a dream now! \\:D/ I wonder what purpose that file served besides messing us up.

---

### Post by cbx332 on 2008-05-09
I tried this and I still have a really bad issue with KDEnLive.  It doesn't restart, but it just crashes loading a project.

[http://www.progbox.co.uk/wordpress/?p=538](http://www.progbox.co.uk/wordpress/?p=538)
[http://www.progbox.co.uk/wordpress/?p=539](http://www.progbox.co.uk/wordpress/?p=539)

Please can someone help

---

### Post by theophiles on 2008-05-09
something to note is that this process MUST BE REDONE every single time you update your system . . . sigh.

---

### Post by theophiles on 2008-05-09
> **theophiles said:**
> something to note is that this process MUST BE REDONE every single time you update your system . . . sigh.

No, it has to be redone more often than that. Every time KDENLIVE is started, it creates kdenliverc again. So, when I want to restart it, I can't. 

I am also now having the afore mentioned problem of KDENLIVE shutting down.

---

### Post by jurgen32 on 2008-05-23
Hey there.
I had the same prob.
And I think i've got the solution.

Startup kubuntu.
Then before you start Kdenlive you have to edit the Kdenlive config file.

Open Konsole (Kmenu-System-Konsole).
Type or copy/paste:
[COLOR="Red"]*sudo kate /home/user/.kde/share/config/kdenliverc*[/COLOR]

go to the end of the file and outmark this two lines:

[COLOR="Red"][I][Unmanaged Settings]
videoprofile=pal_dv[/I]
[/COLOR]
Like this:

[I][COLOR="Red"]#[Unmanaged Settings]
#videoprofile=pal_dv[/COLOR][/I]

And then of course save the file again.
Now you can close Konsole and try Kdenlive.

I don't know why but er is something wrong with the preselect of the videoprofile.
I'll hope this wil work for you guys because Kdenlive is a great tool!!
I also hope this answer wil be simpel enough for new kubuntu users.

Good luck,
Jurgen

---

### Post by jurgen32 on 2008-05-24
Oke... Jurgen, think again.
After restarting kubuntu i've got the same old problem again.
One discovery is that if I start Kdenlive as root ther seams no problems.

---

### Post by jurgen32 on 2008-06-28
Oke, I've found a new solution... I hope.
Now I tested it for a while and Kdenlive is still working.
I found this topic [http://www.progbox.co.uk/wordpress/?p=540]("http://www.progbox.co.uk/wordpress/?p=540")
I quote:
[I]Excuse my bad english

If you have a NVidia and Ubuntu Hardy Heron, the crash of Kdenlive is due a missconfiguration of the last Nvidia driver in Heron by default.

The solution:

Edit the xorg.conf
sudo gedit /etc/X11/xorg.conf

Add this line to the Device Section
Option “UseCompositeWrapper” “True”

Add this at the end of the file
Section “Extensions”
Option “Composite” “Enable”
EndSection

Reset the X server (Ctrl+Alt+Backspace)
You can run the Kdenlive without it crashes… enjoy it!
Greetings from Spain![/I]

This is what I did. But it did'nt work because when you copy and past it the quotation marks are not good, so you have to type it for your self.
A other thing is that I did not fill in the second  part (the lines that have to be put on the end of the file).

[SIZE="4"]_Now I wil explain this for people who are new with Kubuntu/Ubuntu._[/SIZE]

Open:
**Menu/System/Konsole** (under KDE) 
**Apllications/Accessories/Terminal** (under Gnome)

Type: 
***sudo kate /etc/X11/xorg.conf*** (use kate for KDE and gedit for Gnome)
Give your password
Kate/gedit will open the file.
First make a backup of this file by going to the top of the file and press ***save as***
You can give a new name: ***xorg.confbackup***

Than edit the file.
Search for this line: ***Section "Device"***
This is how it could look like:

[B][I]Section "Device"
	            Identifier	"Configured Video Device"
                    Boardname	"NVIDIA GeForce 8 Series"
	            Busid	"PCI:1:0:0"
                    Driver	"nvidia"
	            Screen	0
	            Vendorname	"NVIDIA"
	            Option	"NoLogo"	"True"
	            [COLOR="Red"]Option 		"UseCompositeWrapper" "True"[/COLOR]
EndSection[/I][/B]

The red line is the one you have to put in the file.
You have to type the red line by hand.
After this you go to the top of the file and press again ***save as***
Save the file under the proper name: ***xorg.conf***
Now you have to restart your session ***ctrl+alt+backspace*** and if everything is going well you can login with your password again....
Hopefully Kdenlive will work now.
[SIZE="4"][U]
If for some reason your not able to start a new session:[/U][/SIZE]
Try restarting your computer first and if that does not work do the following steps:
Restart your computer.
Press ***Esc*** as soon as possible.
Now you can choose what you want to do.
Choose the second option from above (the one with the recovery mode).
Enter.
In the recovery menu you choose for root.
Type: ***nano /etc/X11/xorg.confbackup***
Than you have to save it as ***xorg.conf*** again like this:
***Ctrl + o*** delete the word backup (with backspace) 
enter and confirm with **yes**
Exit ***Ctrl + x***
type ***reboot***


I hope this is easy for everybody.

Jurgen

---

### Post by ujwal10101 on 2008-07-09
Thanks a lot Jurgen for finding the solution and presenting it in a newb-friendly way :). Worked like a charm.

---

### Post by mike1212 on 2008-08-05
I'm having trouble with the solution listed above.  When I do:

     sudo gedit /etc/x11/xorg.conf

it opens xorg.conf, but the file is blank.  Am I doing something wrong?  Maybe something to do with permissions?

Note: I'm trying to get kdenlive to work (it crashes when I start the program).  I've got a new laptop from system76, ubuntu 8.04, nvidia.

Thanks!

---

### Post by swisscow on 2008-08-06
> **mike1212 said:**
> I'm having trouble with the solution listed above.  When I do:

     sudo gedit /etc/x11/xorg.conf

it opens xorg.conf, but the file is blank.  Am I doing something wrong?  Maybe something to do with permissions?

Note: I'm trying to get kdenlive to work (it crashes when I start the program).  I've got a new laptop from system76, ubuntu 8.04, nvidia.

Thanks!

replace the x11 with X11 (capital X)

---

### Post by lubeck on 2008-08-14
FINAL FIX I FOUND WITH HARDY - Works for me, at least:

First, clearly the file discussed above, "kdenliverc" is somehow indeed the culprit in this crashing.  In my case, I delete it, start up Kdenlive, and sometimes it works, sometime it crashes.
[B]
Here is the fix that finally worked well for me, for some unknown reason that I am sure a genius can explain. [/B] Perhaps it will work for you:

1. Delete "kdenliverc" as noted above (entries above advise where to locate it)
2. START Kdenlive.  If it crashes, immediately go to the "kdenliverc" file using Text Editor and you will note it only has a couple lines (4 in my case.  For me, the last two lines were [NewStuff] and a web address under it.) 

Comment out the last two lines using a "# " as a prefix, save it, and then re-start Kdenlive. 

For some reason, this allows a normal config file to be created ...a much larger config file if you inspect it ... and my Kdenlive was fine thereafter.  Weird.  Worked perfectly on two of my machines.

WARNING: Someone in another post recommended modifying 'xorg.conf' for Nvidia systems.  I cannot recommend.  Can result in system issues.  This approach resulted in complete devastation of my X11 display parameters and display behavior, which I had to rebuild.

---

