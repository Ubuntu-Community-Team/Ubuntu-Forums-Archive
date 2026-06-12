---
title: "Dell server raid issue"
date: 2011-11-06
forum: Server Platforms
---

### Post by sangsterthegangster on 2011-11-06
I just bought this old Dell poweredge 2850 (this is my first server, so excuse me if this is a noob question), and when I tried to setup a hardware raid with Ubuntu server, I saw no option for it.
So then I tried going into my raid controllers bios to see if I could set one up there and still no luck.
I've looked around on google, I couldn't find anything on the subject!
It bios version is 'mptbios-5.06.06' and I was wondering if anyone knows anything about how to set this raid controller up or if someone could at least set me in the right direction. 

I have a software raid configured currently, however it seems to use up a lot more resources then I would like.
Does Ubuntu even support hardware raids with my controller? or do I configure raids with in the bios?
Please help,
Thanks

---

### Post by darkod on 2011-11-06
As far as I know there is no such thing as hardware raid which will be configured by the OS. That makes it software raid, right?
It's called hardware raid because separate hardware configures and controls it, in this case it should be the raid controller which 2850 should have unless it was removed.
Could it be disabled somehow?

For hardware raid you need to sort out how to create the array from the controller, it has nothing to do with Ubuntu. After that Ubuntu should be able to recognize the array and offer the option to use it.

---

### Post by sangsterthegangster on 2011-11-06
> **darkod said:**
> As far as I know there is no such thing as hardware raid which will be configured by the OS. That makes it software raid, right?
It's called hardware raid because separate hardware configures and controls it, in this case it should be the raid controller which 2850 should have unless it was removed.
Could it be disabled somehow?

For hardware raid you need to sort out how to create the array from the controller, it has nothing to do with Ubuntu. After that Ubuntu should be able to recognize the array and offer the option to use it.

Ok that's what I thought, I was just making sure I don't need drivers or something. the main problem is that I can't find how to configure my controller for a raid, the contollers BIOS doesn't seem to have any raid options. Is there a place that I could find documentation for it? I looked it up on Google several times and couldn't find any thing.

---

### Post by darkod on 2011-11-06
I have actually worked on 2850 few years ago in the UK but now I don't remember the exact steps.
One thing that you need to keep in mind: The raid configuration IS NOT in the BIOS of the motherboard.

The server should have Adaptec raid controller, and this is what you need to "open". For example, if on boot it says something like "press F2 to enter bios" soon after that it should say "press Fx or Ctrl + ? to enter raid controller, etc".

I don't remember the actual wording, don't hold my word on it. But entering the setup of the controller is different to entering the bios setup.

If you were entering in bios that might be why there are no raid options.

Look around while it boots again, and let us know.

Once you enter the controller the process is really intuitive, very simple to set up a new array.

---

### Post by volkswagner on 2011-11-06
Newbie with RAID here.

First find out as others mentioned what type of raid controller you have.

When booting up you should see a shortcut to enter the RAID controllers BIOS, not the system BIOS (like <ctr> + a, <ctr> + S, etc.).

If it is in fact an Adaptect be aware you may run into issues.  I'm installing on an adaptec with Intel chip now.  The Adaptec BIOS Raid configuration tool creates an odd name.  I am going to confirm, but you may need to fill the name up, or it will add blank space to the name (not good in Linux world).  Currently my Adaptect maxes out at 15 character name.  I hope it works here....

```
lspci
```


The above will show you what type of controller is installed.

---

### Post by rubylaser on 2011-11-06
mptbios-5.06.06 , this is an LSI based card.  It could support only RAID 0 and 1, or could support RAID 0/1/5/6/10, it totally depends on the card.  As volkswagner suggested, an lspci is probably the best thing to do next.

---

### Post by sangsterthegangster on 2011-11-06
Well, I know that I'm supposed to go into the raid controller's BIOS to configure the raid, I'm not that much of a noob lol, but when I went into the controllers BIOS it didn't give me any options for a raid. However the solution to my problem was actually within the motherboards BIOS (isn't that ironic?), I didn't have my raid controller enabled! It was set to another setting apparently using the same card. Now I am able to configure my raid. Noob mistake... 

thanks everyone who replied!

---

### Post by coffee412 on 2011-11-06
Dell Servers can be alot of fun. I had a Poweredge 4400 that I ran linux on. Ran for a long time. Called it dino.

What you have to do is get the service tag off the server. This is usually on a white sticker on the back somewhere. 

Go to the dell site and look it up and get the specs on what came in it. Then get the guilds on it. Changes are your going to configure it like said earlier. The bios of the raid card are entered into seperate from the system bios. Watch on boot up for the command to enter the controller bios.

---

### Post by bimmerd00d on 2011-12-13
Regardless of what has been said here, there IS an option in the BIOS for this.  Since the machine is RAID capable, it utilizes a RAID Key instead of an add-in card.  It is a PERC4i controller.  You need to go into the BIOS, and make sure the RAID controller is set to RAID, not SCSI like default.  If the RAID is working, you should see an option during boot to press CTRL+M to enter the RAID configuration, that's where you setup the array.  Also, you can pop open the cover and look next to the memory slots for the RAID key, it's about an inch and a half wide and is held in by some blue connectors.  There will also be a stick of RAM for the RAID controller on the vertical card on the right side (looking from the back), as well as a battery you may or may not see.  If you don't find the raid key, no worries.  Have a look on ebay and you can pick up a raid kit consisting of the raid key, memory, and battery for about $30 or so.  I just went through this last week and resurrected this server for use as a opendedup storage appliance for my VMWare vSphere cluster.

[http://en.community.dell.com/support-forums/servers/f/906/p/19326118/19672656.aspx](http://en.community.dell.com/support-forums/servers/f/906/p/19326118/19672656.aspx)

[img]http://www.darklab.rutgers.edu/MERCURY/t15/pe2850dell/td13-RaidKey-04_500px.jpg[/img]

Here is the BIOS option you are looking for, **make sure it says RAID enabled**, not SCSI enabled

credit:  [http://lists.us.dell.com/pipermail/linux-poweredge/2011-January/043982.html](http://lists.us.dell.com/pipermail/linux-poweredge/2011-January/043982.html)

[img]http://stuff.stroller.uk.eu.org/Poweredge%202850/RAID_screenshot.jpg[/img]

---

