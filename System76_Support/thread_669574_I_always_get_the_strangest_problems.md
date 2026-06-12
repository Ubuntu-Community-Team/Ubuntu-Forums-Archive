---
title: "I always get the strangest problems"
date: 2008-01-16
forum: System76 Support
---

### Post by Squish on 2008-01-16
Well, my gdm has seemed to switch to the debian default
I can only log into failsafe terminals
And the system76 restore didnt do anything...

Foreseable problems:
- I installed kde4 along side ubuntu,
- My computer froze, and had to do a manual restart. After that it wouldnt boot up anything at all, which... ughhh... forced me to do about 3 manual restarts(that is, holding the power button down) before I could even see the bios again. 

Ughh, what caused this freeze in the first place was a pain in the but bug that kept happening to me - The wireless IP would change, and I would HAVE to restart the computer to connect to it. If I tried going into the network settings, it would cause all my applications to not start, not even terminal, folders, taskmanager, or the shuttdown menu. It wasnt frozen, but I couldnt open anything. This happens to me about once a day, and I suspect it was because of the wireless router changing IP's on me. Whether it was the router that wouldnt allow me to reconnect, or ubuntu... I dont know. It happened to the mac downstairs as well, 
But not the 4 microsofts in the house.... go figure

I just want my gdm back, and my gnome...
Right now im running konsole off the failsafe, and with multiple tabs, I am running metacity, and firefox to get this message out to you.

Even when I select gnome or kde4 off the debian gdm, it always gives me the failsafe terminal.

i dont want to reinstall either....

---

### Post by thomasaaron on 2008-01-16
You had to do three hard restarts to just get to the BIOS? You get into the bios from the manufacturing splash screen. Did you have to restart to get to that splash screen? If so, that sounds like a hardware issue, not a gnome/kde issue?
But perhaps I'm misunderstanding.

If that is no the case, did you try to '--purge remove' kde and '--reinstall install' the gnome desktop?

---

### Post by Squish on 2008-01-16
I was scared, cause it was the manufactures splash screen that I couldnt get. At first I thought it might be a harddrive issue... but I detect no problems with file integrety.

Ive had the problem slightly before, because when the computer seizes up like I said with the wifi problem, It doesnt do a complete restart... and I had to do a alt-ctrl del 

But never have I had to do it 3 times.
I will try the command though, let you know how it goes.

---

### Post by Squish on 2008-01-16
sorry, I do not seem to understand the commands you gave me. could you be a bit more thorough?

---

### Post by thomasaaron on 2008-01-17
Sure. 

Sorry, when I get in a rush I stop making any sense at all!

This should remove KDE:
```
sudo apt-get remove kubuntu-desktop
```
This should re-install Gnome
```
sudo apt-get --reinstall install gnome-desktop
```

If I were you, I'd do a good backup first. Just in case...](*,)

---

### Post by Squish on 2008-01-22
Thanks.

What ended up happening, is that, I didnt have to remove either, but I dont start with a gdm anymore...

Funny how it is. but i actually prefer it.
Gives me something to play around in if I am bored.


I am still suffering from the same annoyance though, that is:
At random times, my wireless kicks out, wont reconnect, and seems to hang everything on my system... it wont even allow it to do a proper restart.
How can I diagnose what is happening?

---

### Post by thomasaaron on 2008-01-23
For the wireless problem, check out this thread:
[http://ubuntuforums.org/showthread.php?t=643028&highlight=wireless](http://ubuntuforums.org/showthread.php?t=643028&highlight=wireless)

---

### Post by Squish on 2008-01-31
*Bump*

Well weird issue now


I can connect to my router wirelessly... but I cannot access the internet. I also seem to have an extra connection in my connection manager that wasnt there before... 2 ethernets, a modem, and now this weird Ipvwhatsit thing...
The manager is giving me 4 bars... but no internet access. its weird.
I dont mind doing a reinstall... Ive been thinking of beta testing hardy. I had fun beta testing before so it cool. Backing up files is no problem, I just need to find a way to keep my deluge torrent list in tact. I have over 100 torrents, and it took me like 7 hours to get all of em.
anyways, either or solution is fine.
This issue is so strange though... I wish I could understand just what is going on here...?

It stopped working after I restarted. My computer is a bit fickle though, so it doesnt surprise me. lol, it doesnt even give me a gdm anymore - straight to commandline. Funny that I actually prefer it that way

---

### Post by thomasaaron on 2008-01-31
It doesn't give you gdm anymore? That is pretty hosed. (Somebody's been tinkering with their configurations, no? :lolflag:)

Run:
sudo dpkg-reconfigure xserver-xorg

choose *ALL* defaults from start to finish, except:
* choose nvidia for the driver if you have an nvidia machine, or intel as the driver if you don't have an nvidia machine.
* choose all available resolutions
* choose "Advanced" and then keep selecting defaults.

Did that get gdm back up?

If not, give me a call. You might need to restore your system. I say that because it is beginning to sound like it would take less time than figuring out all of the problems.

---

### Post by Squish on 2008-02-01
Dude, I just want my internet back...
The GDM crash was caused by the internet bug freezing my system, and making me force restart the darn thing. After that it gave me a debian gdm, and it would log me into a suspicious session where none of my folders or files existed., so I uninstalled kde4 and everything, and it gave me the command line. I can start the gdm fine, its just not on my startlist or whatever.

I guess it was partly kde4, but mostly it was that darn bug. At least for once it wasnt completely my doing:lolflag:

What would I need to reinstall if I want to default my internet settings?

Also note, internet is a top priority, because my method of connecting is currently by running a live cd, meaning I cant really do anything else until that is done.
If I updated to Hardy Alpha 3, would that fix it?

---

### Post by Squish on 2008-02-01
So I decided going back was the best thing to do.
Heres what I did:

Basically heres what happened. When you blacklist something, the item also seems to appear in the blacklist file, that is in modprobe.d, so not only did I have to delete the blacklist-ipw~~~~, but I had to go into that file, and make sure it didnt blacklist it as well (I think).
So I did that, and then went to the module, and added the original back in.

The other module confused my computer as it would seem, and thought that I had a lan. It could not connect to the internet wireslessly, only the modem.


So this workaround simply is not acceptable in my terms. I followed it to a tee, and no luck


BUT I AM HAPPY I FIGURED IT OUT!:KS Gold star for me!!!

---

