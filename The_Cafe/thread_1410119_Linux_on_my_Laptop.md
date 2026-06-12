---
title: "Linux on my Laptop"
date: 2010-02-18
forum: The Cafe
---

### Post by civillian on 2010-02-18
Hi, as of writing I currently use solely windows 7, although before the release of windows 7 I used ubuntu entirely.

I'm looking to get back into it again, and my Laptop especially since windows 7 fails at reporting the battery life and I can't use it for more than half an hour before it shuts itself down (never did this with vista on it, which was installed previously), and on the old vista partition I want to install Linux again, in the hope It will get back to its hour and a bit battery life (still not great but it'll last a lecture that way, and I can get back tp typing notes!).

I was thinking about installing OpenSUSE after it got voted best linux distribution for laptops on Linux.com (I think) but I want a stripped version which I would make in susestudio, however I don't know what key things I should install for wireless, etc. everything else I can figure out but thats pretty much something I need out of the box.

However I also though about installing Ubuntu to the command line and then running a script (there is one in the ubuntuforums archives somewhere) to install a base system (wireless, gnome without the games etc and synaptic).

Any ideas? 
Thanks
Civ (returning Linux user)

---

### Post by undecim on 2010-02-18
> **C!V!NT said:**
> windows 7 fails at reporting the battery life and I can't use it for more than half an hour before it shuts itself down (never did this with vista on it, which was installed previously), and on the old vista partition I want to install Linux again, in the hope It will get back to its hour and a bit battery life (still not great but it'll last a lecture that way, and I can get back tp typing notes!).

Yikes... [http://tech.slashdot.org/story/10/02/03/0013257/Microsoft-Looking-Into-Windows-7-Battery-Failures](http://tech.slashdot.org/story/10/02/03/0013257/Microsoft-Looking-Into-Windows-7-Battery-Failures)

For that basic ubuntu install, how about [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by MasterNetra on 2010-02-18
> **undecim said:**
> Yikes... [http://tech.slashdot.org/story/10/02/03/0013257/Microsoft-Looking-Into-Windows-7-Battery-Failures](http://tech.slashdot.org/story/10/02/03/0013257/Microsoft-Looking-Into-Windows-7-Battery-Failures)

For that basic ubuntu install, how about [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Yikes indeed, come to think of it I think the RC version did that to my battery. I had always thought it was just age but now that I think about it. It was fine before I tested Windows 7 RC at the time but not after...lovely.

---

### Post by MichealH on 2010-02-18
You see MS cant do anything right mine goes down 1% every 15 seconds oh look I will last 35 mins on 
Vista: 2hrs! I have seen the TechNet forums and even a Microsoft Contributor has the same problem and ordered Microsoft to It and they havn't fixed it! Microsoft should stop developing this technology because we are humans and we have brains We know when to service the battery or not!

Go to Linux and I get 50 mins OMG Microsoft should buy these people with this problem and the ones who got the version (8,000,000 people) new Laptops with XP installed. I will grudge going back to Vista.

EDIT: I may of been a bit too harsh but I have to be harsh toward MS more: MS cant do anything right!

UPDATE: I was overreacting without checking the facts: [http://www.theregister.co.uk/2010/02/08/microsoft_on_windows_7_battery_complaints/](http://www.theregister.co.uk/2010/02/08/microsoft_on_windows_7_battery_complaints/)

---

### Post by civillian on 2010-02-18
> **undecim said:**
> For that basic ubuntu install, how about [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

That sounds ideal, any idea how I can install Gnome minus all the games and  stuff? Ideally I'd like to do an install, grab the apps I want and then that should be it!

Yikes indeed, its pretty bad, and a HUGE failure, considering that on the whole windows 7 is actually pretty good (apart from indecipherable error messages, it reminded my why I love linux so much!!), and unfortunately its required for my photo editing suite (Nikon's suite), so dualbooting is the way forwards for me!

Thanks for the replies people!

---

### Post by Simon17 on 2010-02-18
> **MichealH said:**
> 
UPDATE: I was overreacting without checking the facts: [http://www.theregister.co.uk/2010/02/08/microsoft_on_windows_7_battery_complaints/](http://www.theregister.co.uk/2010/02/08/microsoft_on_windows_7_battery_complaints/)

Extra! Extra! Read all about it! Some kid bashing Microsoft has no clue what he's talking about!

SERIOUSLY: Thanks for correcting yourself.

---

### Post by undecim on 2010-02-19
> **C!V!NT said:**
> any idea how I can install Gnome minus all the games and  stuff? Ideally I'd like to do an install, grab the apps I want and then that should be it!

the package "gnome-desktop-environment" I believe will install the gnome desktop without all those other apps. "gnome" will install the games, evolution, etc.

Though you will also want to either install a display manager (gdm package, or the more lightweight xdm package) or set up startx to start gnome-session

---

### Post by civillian on 2010-02-21
many thanks!

I tried vista again on the laptop, and the battery life is still poor, so there may well be a battery issue :S

Does anybody know if ubuntu has better (read: more configurable) power management than win7/Vista?

---

