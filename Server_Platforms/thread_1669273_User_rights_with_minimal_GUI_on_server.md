---
title: "User rights with minimal GUI on server"
date: 2011-01-17
forum: Server Platforms
---

### Post by danieleday on 2011-01-17
Being new to Ubuntu & Linux I am having some issues :)

I am trying to set up a simple home file-server for media and backups, using an old Atom board I had lying around and 1GB memory, so I don't want a full desktop. All goes well with installing server 10.10, using LVM for my data disk. However, I wanted some GUI tools since I am not familiar with the CLI, so I installed gdm, xorg, and gnome-core as suggested in some threads and forums.

So far so good, it boots into the Gnome desktop, but I can't get sudo access with anything (synaptic, gkedit, etc.) - always "incorrect password". I am fine from the console; I reset my user password, no luck; I set up another admin user, and that also works in console but not the desktop.
I have no idea where to go next and can't find anything that works in the forum! Help!

---

### Post by imbjr on 2011-01-17
> **danieleday said:**
> Being new to Ubuntu & Linux I am having some issues :)

I am trying to set up a simple home file-server for media and backups, using an old Atom board I had lying around and 1GB memory, so I don't want a full desktop. All goes well with installing server 10.10, using LVM for my data disk. However, I wanted some GUI tools since I am not familiar with the CLI, so I installed gdm, xorg, and gnome-core as suggested in some threads and forums.

So far so good, it boots into the Gnome desktop, but I can't get sudo access with anything (synaptic, gkedit, etc.) - always "incorrect password". I am fine from the console; I reset my user password, no luck; I set up another admin user, and that also works in console but not the desktop.
I have no idea where to go next and can't find anything that works in the forum! Help!

I use the same set-up as you for various reasons, and recently encountered the problem you describe - though I see you use Lucid, when I've only seen this happen in Maverick.

To fix this, at least for running synaptic, I edited the menu option to read:

 gksudo synaptic

Note too, you do need to use gksudo for GUI apps, not sudo.

---

### Post by BbUiDgZ on 2011-01-17
you might want to check out webmin
[http://webmin.com/](http://webmin.com/) 
its a web based gui for linux systems and has the advantage of working on anything with a web browser (remote administration from a windows system for example).

```

wget http://prdownloads.sourceforge.net/webadmin/webmin_1.530_all.deb
sudo dpkg -i webmin_1.530_all.deb #this will error due to dependencies
sudo apt-get install -f #will fix those dependencies

```

you can then access the web frontend via [https://IP-IN-HERE:10000](https://IP-IN-HERE:10000) (replace IP-IN-HERE with your machines IP)

---

### Post by danieleday on 2011-01-17
> **imbjr said:**
> I use the same set-up as you for various reasons, and recently encountered the problem you describe - though I see you use Lucid, when I've only seen this happen in Maverick.

To fix this, at least for running synaptic, I edited the menu option to read:

 gksudo synaptic

Note too, you do need to use gksudo for GUI apps, not sudo.


Perfect, thanks, that fixes 'er up. I see my desktop machine (10.04 lucid) set itself up to use gksu on its menu. Lots of tricks to Ubuntu...back in business now! (Actually, I used 10.10 Maverick for the server install, so it fits your experience)

---

### Post by danieleday on 2011-01-17
> **BbUiDgZ said:**
> you might want to check out webmin
[http://webmin.com/](http://webmin.com/) 
its a web based gui for linux systems and has the advantage of working on anything with a web browser (remote administration from a windows system for example).

```

wget http://prdownloads.sourceforge.net/webadmin/webmin_1.530_all.deb
sudo dpkg -i webmin_1.530_all.deb #this will error due to dependencies
sudo apt-get install -f #will fix those dependencies

```you can then access the web frontend via [https://IP-IN-HERE:10000](https://IP-IN-HERE:10000) (replace IP-IN-HERE with your machines IP)


Nice, thanks for the info and the instructions, that's very helpful. I'll give it a try before I copy my files over. I see from their website it covers everything I'd want to do; and I'm using a KVM right now while I set up, but this will work great when I move it to the back room and run it headless. Cheers.

---

