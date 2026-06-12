---
title: "Server setup help for the slow-witted"
date: 2008-06-02
forum: Server Platforms
---

### Post by Geoff Muller on 2008-06-02
[FONT="Trebuchet MS"]Hi

I'm relatively new to Ubuntu, but love the potential to cut loose the MS shackles. Trouble is, I'm spending every waking hour trying to keep a business solvent in hard times, and I'm not as sharp in the learning department as I was in my distant youth.

Part of the business is photography and we've amassed a quintillion images in unsafe distributed places across the network. I've just bought a basic server box and a couple of 750 Gb discs and want to engineer - initially at least - just a fileserver on a RAID1 setup for peace of mind and general access.

I have Googled until I'm weary, and have unearthed a huge range of guides and helps, but nothing that doesn't seem to require a familiarity and expertise beyond my current state.

Apologies for possibly duplicating other requests for help, but I'd love some (straightforward) guidance from those ITK.

Thanks[/FONT]

---

### Post by mlapaglia on 2008-06-02
Are you using software or hardware RAID?

If hardware, grab a copy of the Ubuntu 8.04 server and install, I believe it's very straight forward, because the installer will only see one hard drive (assuming you have your BIOS configured correctly to work with the RAID card.

If software, [http://knowledge76.com/index.php/Ubuntu_Server_Install_With_Software_RAID](http://knowledge76.com/index.php/Ubuntu_Server_Install_With_Software_RAID)

As for setting up a network share, Ubuntu 8.04 has made this extremely easy. Right click the folders you want to share and select "sharing options" and use that accordingly. After the services have been installed, log out and back in (setting up the permissions I think) and then you can enable all the shares you need.

EDIT: What kind of a file server do you want? SSH, Samba, etc?

---

### Post by Geoff Muller on 2008-06-02
[FONT="Trebuchet MS"][/FONT]
**mlapaglia**

Thanks for that. In answer to your q's:

Software RAID (I picked up one of those cheap Econel server units from ebuyer that, while the (sparse) documentation leads one to believe it has hardware RAID support, in fact seems to be without it).

I think I've stumbled upon the linked knowledge 76 article before, but I also came across another, describing a slightly different set-up procedure with dual partitions on both discs and the ability to boot into either, should one or other disc fail. I may not have grasped all of it as well as I might.

"*EDIT: What kind of a file server do you want? SSH, Samba, etc?"*

I'm guessing at Samba, but will happily take advice - so long as the other machines on the network (XP and Vista mostly, but with migratory intentions for some to Ubuntu) can access and store files, then I'll be happy for now. The proto-administrator learning curve will have to wait a while.

---

### Post by rickyjones on 2008-06-02
> **Geoff Muller said:**
> [FONT="Trebuchet MS"][/FONT]
**mlapaglia**

Thanks for that. In answer to your q's:

Software RAID (I picked up one of those cheap Econel server units from ebuyer that, while the (sparse) documentation leads one to believe it has hardware RAID support, in fact seems to be without it).

I think I've stumbled upon the linked knowledge 76 article before, but I also came across another, describing a slightly different set-up procedure with dual partitions on both discs and the ability to boot into either, should one or other disc fail. I may not have grasped all of it as well as I might.

"*EDIT: What kind of a file server do you want? SSH, Samba, etc?"*

I'm guessing at Samba, but will happily take advice - so long as the other machines on the network (XP and Vista mostly, but with migratory intentions for some to Ubuntu) can access and store files, then I'll be happy for now. The proto-administrator learning curve will have to wait a while.

Samba is what you'll be using to do the filesharing. Please feel free to ask me questions if you would like help configuring it. For the most part SAMBA is pretty straight forward. It does take a little work to get it fully configured, however.

I recommend using SSH to administer the server in addition to Webmin. 

Have a great day!

Sincerely,
Richard

---

### Post by Geoff Muller on 2008-06-02
Thanks

Currently the machine has decided it needs to rebuild a disc (not sure why, as it hasn't done much yet, but I'm not up to arguing with a BIOS).

Once that has completed, I intend to put all the disc settings in the BIOS back to defaults, re-install 8.04 server (I'll put the GUI on as well, because I haven't done the other thing much since using VAX and GEC machines back in the 80's), and then hopefully implement RAID through Ubuntu.

I'll gladly take you up on the Samba help when I get to that stage.

---

### Post by hyper_ch on 2008-06-02
if you want a basic setup, then samba is very simple....

---

### Post by Geoff Muller on 2008-06-02
> **hyper_ch said:**
> if you want a basic setup, then samba is very simple....

That's what people tell me... I'll hopefully find out soon!

---

### Post by hyper_ch on 2008-06-02
it depends on your needs...

I have made myself a really simple configuration for samba.

---

### Post by rickyjones on 2008-06-03
> **hyper_ch said:**
> it depends on your needs...

I have made myself a really simple configuration for samba.

Years ago before I had any idea on how to really configure SAMBA I found the most basic config file ever. Set the NETBIOS name, and a share with no passwords. Simple as that. I still have that config running at a customer site right now.

-Richard

---

### Post by Geoff Muller on 2008-06-03
> **rickyjones said:**
> Years ago before I had any idea on how to really configure SAMBA I found the most basic config file ever. Set the NETBIOS name, and a share with no passwords. Simple as that. I still have that config running at a customer site right now.

-Richard

Richard

That sounds spot on, complexity-wise - I'm really only looking for very simple functionality at this stage.

I'm still waiting for the bl***y BIOS to finish rebuilding one of the drives (what that actually entails I don't know), then I'll get my installing trousers on.

I'm guessing that the best approach will be to ignore the Fujitsu-Siemens setup discs that came with the unit (it all seems to be biased towards Win server OS's) and set everything through 8.04 server (OS followed by GUI then configure SAMBA?). Or will I need to sort the RAID out in BIOS before the OS goes on? As it doesn't have a hardware RAID, I'm not sure what that will achieve (sorry, showing my ignorance again).

Geoff

---

### Post by rickyjones on 2008-06-03
> **Geoff Muller said:**
> Richard

That sounds spot on, complexity-wise - I'm really only looking for very simple functionality at this stage.

I'm still waiting for the bl***y BIOS to finish rebuilding one of the drives (what that actually entails I don't know), then I'll get my installing trousers on.

I'm guessing that the best approach will be to ignore the Fujitsu-Siemens setup discs that came with the unit (it all seems to be biased towards Win server OS's) and set everything through 8.04 server (OS followed by GUI then configure SAMBA?). Or will I need to sort the RAID out in BIOS before the OS goes on? As it doesn't have a hardware RAID, I'm not sure what that will achieve (sorry, showing my ignorance again).

Geoff

I'm no expert in configuring the RAID array but it all depends on how you want it. It sounds like the BIOS is controlling the RAID right now. When you begin the installation and you get to the hard drive portion you'll see either one drive, or many drives. If you see many drives then Ubuntu does NOT support your internal hardware RAID. If that is the case I would disable it and use Software RAID provided by Ubuntu. 

Then install the OS.
Then install the GUI if you'd like. (I personally do because I find the graphical environment more useful)
Then configure basic server settings (static IP, hostname, etc...).
Then install and configure SAMBA.

-Richard

---

### Post by hyper_ch on 2008-06-03
I use this:

```

[global]
workgroup = ARBEITSGRUPPE
hosts deny = 10.0.0.1

[exchange]
comment = Exchange
path = /home/hyper/Exchange
force user = hyper
force group = hyper
read only = No

[apps]
comment = Apps
path = /home/hyper/Apps

[movies]
comment = movies
path = /home/hyper/Movies

[music]
comment = music
path = /home/hyper/Music

```

Replace ARBEITSGRUPPE with your windows workgroup name.
Replace 10.0.0.1 with your router's IP address
Relace "hyper" with your username and change also paths ;)

And the rest adjust as you want.

Then add users to samba (they must be existing system users). Assuming your username is rickyjones on your linux computer run then:
```

sudo smbpasswd -a rickyjones

```
And enter a password. That one can differ from your actualy user login on the machine.

And finally, to be sure, restart samba:
```

sudo /etc/init.d/samba restart

```

Now browse from the windows machines to your linux machine and use "rickyjones" and the password as login credentials.

---

### Post by Geoff Muller on 2008-06-03
Thanks both

The rebuild has currently inched its painful way to 93%, so I hope to get to grips with the installation issues this evening or tomorrow am.

I'll be sure to let you know how it goes... and doubtless be on here again asking daft questions!

---

### Post by rickyjones on 2008-06-03
> **hyper_ch said:**
> I use this:

```

[global]
workgroup = ARBEITSGRUPPE
hosts deny = 10.0.0.1

[exchange]
comment = Exchange
path = /home/hyper/Exchange
force user = hyper
force group = hyper
read only = No

[apps]
comment = Apps
path = /home/hyper/Apps

[movies]
comment = movies
path = /home/hyper/Movies

[music]
comment = music
path = /home/hyper/Music

```

Replace ARBEITSGRUPPE with your windows workgroup name.
Replace 10.0.0.1 with your router's IP address
Relace "hyper" with your username and change also paths ;)

And the rest adjust as you want.

Then add users to samba (they must be existing system users). Assuming your username is rickyjones on your linux computer run then:
```

sudo smbpasswd -a rickyjones

```
And enter a password. That one can differ from your actualy user login on the machine.

And finally, to be sure, restart samba:
```

sudo /etc/init.d/samba restart

```

Now browse from the windows machines to your linux machine and use "rickyjones" and the password as login credentials.

Excellent write up! Very similar to what I have at a customer site. Wish I had enabled remote access so I could grab that file!

---

### Post by Geoff Muller on 2008-06-06
OK, I won't pretend it was all plain sailing, but, thanks largely to the advice I've received here, I now have a RAID1 Ubuntu server with Samba file serving all set up and currently absorbing our image library.

A few sticky moments, and the odd struggle with syntax, but stage one is definitely sorted. When time allows I'll have a look at stuff like mail servers and even web hosting, so I'll doubtless be back, but for now... thanks a lot chaps.

Geoff

PS Any recommendations for a 'bible' of Ubuntu/Linux commands to have next to the machine? I generally end up with so many tabs open  that I forget where I've been...

---

### Post by hyper_ch on 2008-06-06
[http://www.psychocats.net](http://www.psychocats.net)
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)
[https://wiki.ubuntu.com](https://wiki.ubuntu.com)
[http://www.ubuntuforums.org](http://www.ubuntuforums.org)
[http://www.google.com](http://www.google.com)

---

### Post by Geoff Muller on 2008-06-06
Ta

Oh well, I suppose that's only 5 tabs to start with....!!!

---

