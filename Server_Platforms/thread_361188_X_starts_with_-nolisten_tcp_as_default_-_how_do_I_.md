---
title: "X starts with -nolisten tcp as default - how do I allow exceptions?"
date: 2007-02-14
forum: Server Platforms
---

### Post by Saubazi on 2007-02-14
ps -ef | grep X tells me that X is started with nolisten tcp option. I turned it actually off from gdm.conf so I am wondering a bit why it is still on? 

I have some problems connecting to neighboring computers and exporting displays. 
I am able to connect to another linux machine and for example start xterm and it comes on
my display. If I do the same on an IBM machine I get "can't open display". I have tried with ssh -X option so I am bit lost.

Can I define local overrides to other machines - only place where I still found nolisten tcp option 
was in /etc/X11/xinit/xserverrc but I am a bit hesitant to switch it off what alternatives do I have?

---

### Post by gsgleason on 2007-12-14
I have the same issue on 7.10.  I changed the line:
DisallowTCP=true
to
DisallowTCP=false

I restart, but X still comes up with the -nolisten tcp option.

I've edited /etc/X11/xinit/xserverrc and removed the option there as well, but when I check the processes after a restart, it's still there.

Any input?

[edit] nevermind it did work.  I was restarting X but not gdm.

---

### Post by dougd on 2008-01-04
I also had the same issue and for me this is a show stopper as I could not get a display back from a HPUX 10.20 system that I use regularly.

What I found from my investigation is that the start script for kdm (/etc/init.d/kdm) checks for the text "Theme=@@@ToBeReplacedByDesktopBase@@@" in /etc/kde3/kdm/kdmrc and for the text "Wallpaper=default_blue.jpg" in /etc/kde3/kdm/backgroundrc. If these are both true then it runs the genkdmconf program which populates /etc/kde3/kdm/kdmrc with the nolisten tcp option.
I used Settings -> System Administration -> Login manager
from the kde menu to pull up "configure - KDE Control Module".
Under the "Background" tab there is a pull down menu to set the picture. I changed this to something other than the default  which changes the Wallpaper line in /etc/kde3/kdm/backgroundrc.
I then deleted the nolisten line from /etc/kde3/kdm/kdmrc and rebooted to restart kdm.
X no longer starts with the nolisten option.

I'm sure there must be a good reason for the logic in the kdm start script but it seems a little obscure to me.

---

### Post by kenjiru on 2008-01-13
I have the same question!

---

### Post by Saubazi on 2008-01-14
> **gsgleason said:**
> I have the same issue on 7.10.  I changed the line:
DisallowTCP=true
to
DisallowTCP=false

I restart, but X still comes up with the -nolisten tcp option.

I've edited /etc/X11/xinit/xserverrc and removed the option there as well, but when I check the processes after a restart, it's still there.

Any input?

[edit] nevermind it did work.  I was restarting X but not gdm.

I also changed this and now it seems that I am having more success with ssh -X command...I'll still have to test around a bit to make sure but at least I did not get the can't open terminal error anymore...

---

