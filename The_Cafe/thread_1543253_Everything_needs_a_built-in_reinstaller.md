---
title: "Everything needs a built-in reinstaller"
date: 2010-07-31
forum: The Cafe
---

### Post by chessnerd on 2010-07-31
I just spent 8 hours trying to get my Sansa View to sync with my Windows 7 install (using Windows Media Player 12). I didn't mean to because, until now, every time I plugged it in it would simply sync, no questions asked. 

Today, not so much.

I tried everything I could think of, but nothing worked. Every time I synced it would sync one new song and then stop cold. I had added nearly 1300 new audio files since the last sync so I wasn't about to waste my time connecting and reconnecting. I searched the net, tried various fixes. Nothing. 

In the end, I went on my View, went to the Format option, and wiped the whole thing. Obviously all the music and videos are gone now, but at least it's syncing again (currently at 39%) and should be up and running again in about half an hour.

It is true that I should never have had this problem, but these things happen from time to time with many software products (although the View has notoriously crappy firmware) so it is nice to see that SanDisk put in what amounts to a built-in reinstaller.

I think that this would be a nice feature for Windows and Linux. Have a software program that you could activate that would completely reinstall the system to the original settings. Sure, you'd need to run potentially months worth of updates afterwards, but it would definitely clean out any bugs the system had acquired.

---

### Post by Legendary_Bibo on 2010-07-31
> **chessnerd said:**
> I just spent 8 hours trying to get my Sansa View to sync with my Windows 7 install (using Windows Media Player 12). I didn't mean to because, until now, every time I plugged it in it would simply sync, no questions asked. 

Today, not so much.

I tried everything I could think of, but nothing worked. Every time I synced it would sync one new song and then stop cold. I had added nearly 1300 new audio files since the last sync so I wasn't about to waste my time connecting and reconnecting. I searched the net, tried various fixes. Nothing. 

In the end, I went on my View, went to the Format option, and wiped the whole thing. Obviously all the music and videos are gone now, but at least it's syncing again (currently at 39%) and should be up and running again in about half an hour.

It is true that I should never have had this problem, but these things happen from time to time with many software products (although the View has notoriously crappy firmware) so it is nice to see that SanDisk put in what amounts to a built-in reinstaller.

I think that this would be a nice feature for Windows and Linux. Have a software program that you could activate that would completely reinstall the system to the original settings. Sure, you'd need to run potentially months worth of updates afterwards, but it would definitely clean out any bugs the system had acquired.

Anything through Synaptic, Ubuntu software center, and debs have this feature already if I'm not mistaken.

---

### Post by chessnerd on 2010-07-31
> **Legendary_Bibo said:**
> Anything through Synaptic, Ubuntu software center, and debs have this feature already if I'm not mistaken.

Very true, and I've used this feature many times to fix parts of the OS. However, I'm talking about reinstalling everything. I guess you could just reinstall everything but that would take a while to do via Synaptic.

---

### Post by Legendary_Bibo on 2010-07-31
> **chessnerd said:**
> Very true, and I've used this feature many times to fix parts of the OS. However, I'm talking about reinstalling everything. I guess you could just reinstall everything but that would take a while to do via Synaptic.

I think a little change of synaptic would make that easier. What I have in mind is that when you click on a package it would show you everything else it would install like all the libs.

---

### Post by FuturePilot on 2010-07-31
> **Legendary_Bibo said:**
> I think a little change of synaptic would make that easier. What I have in mind is that when you click on a package it would show you everything else it would install like all the libs.

Unless I'm misunderstanding it already does exactly that.

---

### Post by Legendary_Bibo on 2010-07-31
> **FuturePilot said:**
> Unless I'm misunderstanding it already does exactly that.

When you go to install it. Does uninstalling something through synaptic also uninstall the dependencies?

---

### Post by FuturePilot on 2010-07-31
> **Legendary_Bibo said:**
> When you go to install it. Does uninstalling something through synaptic also uninstall the dependencies?

Not directly. Unneeded dependencies get marked as autoremovable. You can then use the status button to show all autoremovable packages and then easily remove them. 

```
sudo apt-get autoremove
```

also accomplishes the same thing.

---

### Post by chriswyatt on 2010-07-31
Windows has something useful for reinstalling system files that I've only discovered recently:

sfc /scannow

I've had to use it quite a bit on my virtualised Windows XP in VirtualBox, seems to like to corrupt a lot for some reason.

Then of course there is the complete reinstall you can do with Windows if things are really messed up.

That's one thing I love about the Debian package management system, you can choose to reinstall the files, or completely purge everything including the configuration files.  You could probably fix most problems this way.

---

