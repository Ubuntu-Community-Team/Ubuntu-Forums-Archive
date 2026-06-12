---
title: "Any virtual machines able to burn a dvd ?"
date: 2008-10-17
forum: Virtualisation
---

### Post by Drakkor on 2008-10-17
I have VirtualBox with a virtual XP running inside Ubuntu Hardy,but if I try to burn something,it can't find my dvd burner. Any ideas ? Thanks :)

---

### Post by gali98 on 2008-10-17
In virtualbox there is an option called "dvd passthrough" or something similar. I am not sure exactly where the setting is, and I never got it to work good (but that was a year ago...) but that is what is supposed to make it work.
I suggest searching google for that option. The virtualbox forums has some good stuff too.
Kory

---

### Post by stinger30au on 2008-10-18
save the file your trying to burn as an .iso file and then install the addons s/w and share a directory between your virtual xp and ubuntu

save the .iso file to the shared directory and then fireup K3B and burn the .iso to cd/dvd and your good to go


i do it all the time, works like a charm

---

### Post by Drakkor on 2008-10-18
> install the addons s/w and share a directory between your virtual xp and ubuntu
Sorry,  could you be a little more detailed as to how one would accomplish this baffling feat ? .lol :)

---

### Post by gali98 on 2008-10-18
On the addons part,
in the hardware menu in virtualbox (its not really called that... if you have the virtual machine open, it is the second menu.)
At the bottom is says something like (install Guest Additions)
This will open a cd in the virtual machine. Just run the installer on the cd. you will probably need to restart afterward.
I don't really know where to go from there.
I know in the machine settings (When the virtual machine is turned off, the main virtual bo window. Click on the machine then click on the settings.)
there is a place for share machine folders.
That's all I can help you with.
Kory

---

