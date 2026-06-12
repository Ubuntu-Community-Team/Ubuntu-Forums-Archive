---
title: "No Synaptic/No sudo apt-get update"
date: 2012-02-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-02-17
Anyone else?

camel2@ubuntu:~$ sudo apt-get update
[sudo] password for camel2: 
N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
camel2@ubuntu:~$ 

Yet network/modem activity in high gear ... whats going on?

---

### Post by winh8r on 2012-02-17
Some other process is using it.

try running 

```
top
```

to see what else is running that could be affecting it.

---

### Post by ventrical on 2012-02-17
[I]I ran Update Manager, rebooted and now it works! 

top shows nothing.

[/I]

---

### Post by cortman on 2012-02-17
Rather than top, how about

```
ps -ef | grep apt
ps -ef | grep dpkg
```

Kill all returned processes (except the ps process itself, obviously)

> N: Ignoring file 'ppa_file.txt' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

What's this file doing in there?

---

### Post by ventrical on 2012-02-17
Thats a good question. The whole install with that prob has been through the mill .. but I like cleaning these things up.

Good eye.

---

### Post by cortman on 2012-02-17
Great! That's an alpha for you...

---

### Post by Ibidem on 2012-02-18
Is update mangler running?
Did you run apt-get <something> previously?

Also, sudo lsof|grep var| grep lock should list whatever has that file open.
sudo lsof|grep TCP for network connections, or use sudo nethogs <interface>

Once in a while, apt will crash and you need to reboot to get everything working (or rm the lock file).

---

### Post by ventrical on 2012-02-18
> **Ibidem said:**
> Is update mangler running?
Did you run apt-get <something> previously?

Also, sudo lsof|grep var| grep lock should list whatever has that file open.
sudo lsof|grep TCP for network connections, or use sudo nethogs <interface>

Once in a while, apt will crash and you need to reboot to get everything working (or rm the lock file).

  This all worked out well. It appears that it was only a small blip on the radar screen. For a moment I thought that Ubuntu was trying to put the squeeze on me, to be preapred and get ready for Update Manager option only with LTS release .. but that appears not to be so.  Nothing else was running in the background (or perhaps it was but was just not being reported).  Synaptic has been acting strange of late anyways so I  guess it's alpha par for the course :)

---

### Post by VinDSL on 2012-02-18
> **ventrical said:**
> Synaptic has been acting strange of late anyways so I  guess it's alpha par for the course :)
Yes, it is...

For a few days, the "Quick Filter" didn't work.

Now it works, but if I reload the PPAs before the quick filter is done indexing, Synaptic gives me the middle-finger and closes without an error dialog. Boom!  Gone!  

LoL!  :D

Oh, well, you just need to be patient at this stage of the game.

---

### Post by Harry33 on 2012-02-19
> **VinDSL said:**
> Yes, it is...

For a few days, the "Quick Filter" didn't work.

Now it works, but if I reload the PPAs before the quick filter is done indexing, Synaptic gives me the middle-finger and closes without an error dialog. Boom!  Gone!  

LoL!  :D

Oh, well, you just need to be patient at this stage of the game.

Yes I see this crashing quite often these days.
So that bug is still left.
If it irritates too much, you can of course downgrade to the last working version (0.75.5~exp4).

---

### Post by VinDSL on 2012-02-19
Just experienced more weirdness!

[LIST]
[*]Opened Synaptic.
[*]Reloaded the PPAs.
[*]Marked all upgrades.
[/LIST]

Two upgrades were listed... Flash & Flash Plugin.

Clicked Apply, and was greeted with two 404s (Bad IPs).

Tried this n' that.  Wasn't getting anywhere.

[LIST]
[*]Switched Download Server from "Main" to "Server for United States". 
[*]Clicked Apply.
[*]Synaptic downloaded the files and performed upgrades normally.
[/LIST]

Heh!  :)

---

### Post by ventrical on 2012-02-19
> **VinDSL said:**
> Just experienced more weirdness!

[LIST]
[*]Opened Synaptic.
[*]Reloaded the PPAs.
[*]Marked all upgrades.
[/LIST]

Two upgrades were listed... Flash & Flash Plugin.

Clicked Apply, and was greeted with two 404s (Bad IPs).

Tried this n' that.  Wasn't getting anywhere.

[LIST]
[*]Switched Download Server from "Main" to "Server for United States".
[*]Clicked Apply.
[*]Synaptic downloaded the files and performed upgrades normally.
[/LIST]

Heh!  :)
Thanks Vin..   I think the main servers are just overloaded or somthing.

---

