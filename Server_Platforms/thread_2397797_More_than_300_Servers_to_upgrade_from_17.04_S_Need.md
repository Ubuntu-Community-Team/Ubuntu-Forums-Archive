---
title: "More than 300 Servers to upgrade from 17.04 :S Need Help!"
date: 2018-08-03
forum: Server Platforms
---

### Post by jpelletier on 2018-08-03
Hi,

We have more than 300 Ubuntu Servers actually in the field (remote locations / customers) running Ubuntu Server 17.04 (16.04 LTS had drivers issue), it was absolutely impossible for us to upgrade them until today but now, 17.10 is not supported either! The sources.list file use all old-releases repositories

Executing the command ```
sudo do-release-upgrade
``` return the error: ```
An upgrade from 'zesty' to 'bionic' is not supported with this tool.
```

We want to upgrade to 18.04 LTS but from what I see, our only option is to reinstall and it's not really an option... Is there any way to do it without reinstalling, even if it's unofficial/unsupported?

Thanks a lot!

---

### Post by Autodave on 2018-08-03
Hopefully, someone else will give you a better answer, but as far as I know that will be impossible: youi will have to do fresh installs. And since 17.04 is no loner receiving security updates, you better get started immediately.

---

### Post by Tadaen_Sylvermane on 2018-08-03
The only option I can think of is to skip the do-release-upgrade tool and do it manually the debian way. Change sources.list to reflect the archived 17.04 repos, do an apt full-upgrade, reboot if needed. Then change sources.list to reflect 17.10 archived repos, do an apt-get dist-upgrade to 17.10 and reboot. Assuming that goes through, you should be able to upgrade to 18.04 without issue I'd guess. But no guarantees. Ubuntu uses do-release-upgrade for some reason, what I don't know.

I would test this on a vm first.

I'd fire whoever decided a non lts release was a good idea, then ignored updating it to keep it current personally. I don't know your deployment or business but this could potentially be negligence. Maybe I'm to harsh.

---

### Post by oldfred on 2018-08-03
Moved to server sub-form where those who know servers may be able to help.

Are all systems exactly the same hardware?
Do you you have test systems for the installs?

---

### Post by LHammonds on 2018-08-04
Sounds like the OS was installed on physical hardware and 17.10 was used because it had drivers that supported the physical hardware.

Am I correct in thinking that it wasn't possible to upgrade until recently because 18.04.1 LTS has the drivers you need?

Are all 300 servers uniquely configured or can do a fresh install of 18.04.1, then create an image of that and do a restore of that image at the target location?  I understand their might be data you need to backup/transfer on the old server but doing a prep'd image deploy might be the fastest way.

Depending on the scenario, you might even be able to pre-configure the image with the destination IP and pre-migrate the data before sending it out.

Keep in mind also that even if you can do an in-place upgrade of the OS, that does not mean the applications and config files will upgrade smoothly.  If they are all very similar, you can at least work out and document the changes that will need to be made for each one and avoid the embarrassing situation where you have extended downtime at a site while you scratch your head trying to troubleshoot an upgrade issue.

@Tadaen_Sylvermane, playing the blame game is a waste of time when solutions need to be found.  And you do not know the circumstances involved with the rollout.

LHammonds

---

### Post by Tadaen_Sylvermane on 2018-08-04
You are correct and i apologize. I just get so tired of poorly managed it departments. Stuff like this should never happen. Happens to often. My apologies,  it just frustrates me to no end.

---

### Post by barroncm on 2018-08-05
You could do a "step" upgrade, basically you upgrade to each release between where you are at and where you want to be. I dont have the instructions handy, but it will take you a long time on 300 servers but it is an option. I think @LHammonds idea is probably the most practical.

---

### Post by 1clue on 2018-08-05
Not going to try with the upgrade part, but you could systematically rebuild onto a new image.  It would go something like this:

[LIST=1]
[*]Get a list of expressly installed software for each box, with something like **aptitude search '~i!~M'**
[*]Determine which of these was simply a convenience install without configuration and which was important software requiring attention.
[*]Backup all relevant configuration files to a remote location, along with that list from step 1 (all of /etc is a good start, it's almost never big, and /var will surely have tidbits in there too but don't try to copy the whole thing.)
[*]Backup data files for the software, or in the case of database backups back them up the recommended way first, and then copy the backups to the remote location.
[*]Use a local test system to verify this approach will work with your setup.
[*]On the new (or test) system, install the packages from the list in step 1. Do so individually at least at first because a major upgrade changes the available and preinstalled packages. You need to catch anything that's significantly different.
[*]Investigate the important configuration differences. It's possible that simply copying the old config files/directories to the new system will work, but also very possibly you will need to migrate the files.
[/LIST]

That would be insanely tedious for 300 systems, but if you have any number of these systems which are significantly similar you could script everything except step 7. Leaving you with the hard/interesting stuff.

---

### Post by jpelletier on 2018-08-20
> **oldfred said:**
> Moved to server sub-form where those who know servers may be able to help.

Are all systems exactly the same hardware?
Do you you have test systems for the installs?

Yes, exactly same hardware and I have many tests systems, not a problem!

> **LHammonds said:**
> Sounds like the OS was installed on physical hardware and 17.10 was used because it had drivers that supported the physical hardware.

Am I correct in thinking that it wasn't possible to upgrade until recently because 18.04.1 LTS has the drivers you need?

Are all 300 servers uniquely configured or can do a fresh install of 18.04.1, then create an image of that and do a restore of that image at the target location? I understand their might be data you need to backup/transfer on the old server but doing a prep'd image deploy might be the fastest way.

Depending on the scenario, you might even be able to pre-configure the image with the destination IP and pre-migrate the data before sending it out.

Keep in mind also that even if you can do an in-place upgrade of the OS, that does not mean the applications and config files will upgrade smoothly. If they are all very similar, you can at least work out and document the changes that will need to be made for each one and avoid the embarrassing situation where you have extended downtime at a site while you scratch your head trying to troubleshoot an upgrade issue.

@Tadaen_Sylvermane, playing the blame game is a waste of time when solutions need to be found. And you do not know the circumstances involved with the rollout.

LHammonds

We had to use 17.04 because of drivers issues, and it was not possible because of many factors.
We do have a backup for every servers, and sending a USB key with an image is an option. Probably the best / safest way to do it in fact.
Most of the applications are ours se we will test everything and find the good procedure before doing it. Servers hardware are 100% identical


Thanks everyone for the help. We will send a configured image on a USB key and ask every location to update it. Will try to turn this into an opportunity to improve our base image.

---

### Post by LHammonds on 2018-08-20
If you can, please let us know how it goes and thanks for letting us know what method you ended up choosing.  This is good to know.

LHammonds

---

### Post by jpelletier on 2018-08-27
> **Tadaen_Sylvermane said:**
> The only option I can think of is to skip the do-release-upgrade tool and do it manually the debian way. Change sources.list to reflect the archived 17.04 repos, do an apt full-upgrade, reboot if needed. Then change sources.list to reflect 17.10 archived repos, do an apt-get dist-upgrade to 17.10 and reboot. Assuming that goes through, you should be able to upgrade to 18.04 without issue I'd guess. But no guarantees. Ubuntu uses do-release-upgrade for some reason, what I don't know.

It might be impossible send a usb key for some machines, fastest way would be to do this. Anyone know the difference between a do-release-upgrade and simply updating sources.list with 17.10 repo (old-releases) than upgrade ?

---

### Post by 1clue on 2018-08-27
> **jpelletier said:**
> It might be impossible send a usb key for some machines, fastest way would be to do this. Anyone know the difference between a do-release-upgrade and simply updating sources.list with 17.10 repo (old-releases) than upgrade ?

If your systems are actual server hardware and support remote consoles through IPMI or some other remote management process, you can insert your USB key on your workstation wherever you're at and it works the same as if it were on the server.

For example, I use SuperMicro hardware which supports IPMI 2.0. Most of that hardware has never had a connected keyboard, monitor or mouse from the day the board was installed into the box until today, and most likely will never have anything like that connected. IPMI supports remote console through a service processor right on the motherboard. I can insert CDROMs, USB keys, USB hard drives, keyboards, mice, whatever. I can cold boot or reset or anything else, and even control fan speed.

There may be other technology out there that works well enough, but I'm not familiar with it.

---

### Post by 1clue on 2018-08-27
I'd also like to ask you to double-check your upgrades.  I know you said from 17.04, but there's always an exception somebody forgot about sitting in the back of the server room. If you have any systems from an earlier distro, like 14.x or earlier, then DO NOT try to upgrade to something newer. Ubuntu made the switch from upstart to systemd right around then, and the changes are pretty much catastrophic to your existing install IMO.

---

### Post by jpelletier on 2018-08-27
It's not really servers, those are Intel NUC6CAY systems running in Kiosk mode and they were all deployed from the same Image. If an update goes wrong, I have a backup of all sensitive data from all systems.

Is it better to upgrade to 17.10 first using the sources.list method, than use the official do-release-upgrade to upgrade from 17.10 to 18.04 LTS ?? (Trying this method right now on a system)
 Or should I simply update from 17.04 to 18.04 with the sources.list method?

---

### Post by 1clue on 2018-08-27
do-release-upgrade has been reliable for quite some time AFAIK, with the exception of the switch to systemd from an upstart system. In that latter case there is just way too many changes to /etc for things to go well.

I'm pretty sure 17.10 is systemd, so you should be good. I'm not sure where Ubuntu made the switch, but I know 14.x is upstart and 16.x is, I believe, systemd.

That said, my personal inclination would be to do what I suggested earlier: For each system, collect the features required for the box (difference between minimal installer and running image, required software only -- not dependencies) and script the install of that software, as different from the stock software. That way you know what YOUR PEOPLE changed.

By that method, you have a quantitative process for building each box. This is, IMO, a very effective backup strategy which is a little more work but yields a better result at a future date.

---

### Post by jpelletier on 2018-08-28
Each box are identical and we already have documented all installed softwares / configurations so we can reinstall from a minimal installer. Every updates / modifications from the original images are scripted already. And we are using systemd so no problem!

Yesterday I did a test: 
17.04 -> 17.10 with update / upgrade after changing the sources.list (since do-release upgrade don't work)
17.10 -> 18.04LTS with do-release-upgrade

I don't know if it's better to do this, or:
17.04 -> 18.04LTS with update / upgrade after changing the sources.list , skipping 17.10 and never using do-release-upgrade

---

### Post by LHammonds on 2018-08-28
How bad would it be if you installed an 18.04 image, got it fully patched, installed all the various software and got it ready as a base image.  Then at each site, backup the data on the server, throw down the new image and restore the data?

If the systems are all identical, you only need to work out the "how-to" for backing up and restoring the data.

This would allow for a clean OS that has zero potential for "upgrade gotchas"

LHammonds

---

### Post by 1clue on 2018-08-28
> **LHammonds said:**
> How bad would it be if you installed an 18.04 image, got it fully patched, installed all the various software and got it ready as a base image.  Then at each site, backup the data on the server, throw down the new image and restore the data?

If the systems are all identical, you only need to work out the "how-to" for backing up and restoring the data.

This would allow for a clean OS that has zero potential for "upgrade gotchas"

LHammonds

There would still be configuration issues, but IMO this is the least potential of problems, and the least amount of actual work per server.

---

### Post by jpelletier on 2018-08-28
> **LHammonds said:**
> How bad would it be if you installed an 18.04 image, got it fully patched, installed all the various software and got it ready as a base image.  Then at each site, backup the data on the server, throw down the new image and restore the data?

If the systems are all identical, you only need to work out the "how-to" for backing up and restoring the data.

This would allow for a clean OS that has zero potential for "upgrade gotchas"

LHammonds

Will do that for as many system as we can, but every system is at a different location around Canada / USA so logistically it's a nightmare, and more important it's a lot of money! Our customers are non-technical end-users so we really have to send someone locally. For many systems, we will have to try an update since it's cheap and faster for us.

So knowing that I must upgrade some systems remotely :) Which option is the better?

This
[COLOR=#000000]17.04 -> 17.10 with update / upgrade after changing the sources.list (since do-release upgrade don't work)[/COLOR]
[COLOR=#000000]17.10 -> 18.04LTS with do-release-upgrade[/COLOR]

[COLOR=#000000]Or:[/COLOR]
[COLOR=#000000]17.04 -> 18.04LTS with update / upgrade after changing the sources.list , skipping 17.10 and never using do-release-upgrade
[/COLOR]
If a system upgrade fail, we have the Plan B (which is Plan A ... reinstalling image hehe)

Thanks again for the help!

---

### Post by LHammonds on 2018-08-28
Well, I cannot give you any advice on in-place upgrades as I never do them.  But I would make sure they have something onsite so they restore it to the way it was prior to upgrade and/or have the new base image ready to rollout as a potential secondary option...but a restore would be much faster to get back online without specialized help onsite.

Maybe do the in-place upgrades for as many as possible, then for any sites that had to do restores, send onsite tech to lay down the base 18.04 image.  However, that would mean you would have a mixed environment at this point.  Some with older OS residuals and others with fresh base install.

**EDIT:** For future rollouts of hardware, you might consider having two separate drives(partitions) (like a switch) where one contains the active boot partition/OS and another that can contain an offline copy of a new base image.  The active system could be configured to pull down new images and just modify the boot process to point to the other OS when time to upgrade.  Then the active OS can later update the other OS image the next time.  I thought about designing a system like this in the past but for desktop images.  New desktop images would be pushed to the active-running OS and stored on the system, upon next boot, the newest image would be activated.  But I never got further than the idea since we cannot rollout Linux as a desktop yet (too many Windows-required apps).

LHammonds

---

### Post by 1clue on 2018-08-28
A lot of the time I sit and wonder about the advisability of datacenters. And service processors on server hardware. And the expense of that server hardware.

And then a situation like this comes up and I see the light.

This discussion has gone around in circles for awhile.

If all the systems were in the same datacenter then it would be manageable.
If the systems were server hardware with a true remote console like IPMI2, then it would be manageable.

As it is, the hardware is scattered around everywhere, with no knowledgeable IT staff at most of the sites.

If the do-release-upgrade doesn't work then the site in question is down until some knowledgeable IT staff can get there, get familiar with the system and the process being attempted and figure out what happened.
If you go with a reinstall then you need the IT staff on-site because you lack service processors.

The only thing I can guess would be to have one spare server. Choose the system, install a replacement, get it working. Send the server to the appropriate site. Someone there unplugs the old one and plugs in the new one. Assuming everything works or is manageable to fix, they send that spare back which becomes the upgrade to site #2 and so on.

That's going to be outrageously expensive and outrageously time consuming. You're looking at a few years to do the upgrade.

---

### Post by 1clue on 2018-08-28
The other highly improbable course I can think of is to set up servers in a datacenter with VPN access.

Configure server 1 with new or spare hardware at the datacenter. When it's running get the users at site 1 to start using the datacenter hardware. Site 1 sends their server to the datacenter.
Configure server 2 with a new image on the hardware at the datacenter which came from site 1. When it's running get the users on site 2 to use the datacenter hardware. Site 2 sends their server to the datacenter.
Configure server N with a new image on the hardware at the datacenter  which came from site N-1. When it's running get the users on site N to use  the datacenter hardware. Site N sends their server to the datacenter.

The process could work in parallel to get reasonable speed. There could be some number of experts working on this system, and each could have some number of servers in their loop, so that shipping time does not unnecessarily extend the process and your upgraders stay busy.

While this is at least as expensive as any of the other approaches I can think of, you are now poised for future upgrades by having a relatively small number of skilled people who manage all the hardware and have physical access.

---

### Post by 1clue on 2018-08-28
One thing we don't know is what sort of load these servers have, or what the layout is. To me I would investigate hardware reduction, to get a few pieces of really good hardware to replace a bunch of less capable systems. If your server hardware is web-based you could use virtual hosts to get some number of sites into a single piece of hardware.

You could use virtualization to further improve your hardware costs and system maintainability. If we were talking about upgrading 300 web sites on 30 VMs on 5 or 6 hosts it would be an entirely different discussion and no big deal. Not only that, you could do future maintenance with close to zero downtime.

---

### Post by LHammonds on 2018-08-29
> **1clue said:**
> One thing we don't know is what sort of load these servers have, or what the layout is. To me I would investigate hardware reduction, to get a few pieces of really good hardware to replace a bunch of less capable systems. If your server hardware is web-based you could use virtual hosts to get some number of sites into a single piece of hardware.

You could use virtualization to further improve your hardware costs and system maintainability. If we were talking about upgrading 300 web sites on 30 VMs on 5 or 6 hosts it would be an entirely different discussion and no big deal. Not only that, you could do future maintenance with close to zero downtime.

This was already explained here:

> **jpelletier said:**
> It's  not really servers, those are  [Intel  NUC6CAY](https://www.intel.com/content/www/us/en/products/boards-kits/nuc/mini-pcs/nuc6cays.html) systems running in Kiosk mode

> **jpelletier said:**
> We  had to use 17.04 because of drivers issues, and it was not possible  because of many factors.

So I seriously doubt this  touch-based system can be run remotely from a VM at a datacenter.  I'm  also sure they do not want the headache involved with useless systems if  any of the 300 remote sites have connection problems.  Kiosk  applications typically can run and work remotely even without a network  cable plugged in (and cache data until a connection can be  re-established).

LHammonds

---

### Post by jpelletier on 2018-08-29
> **LHammonds said:**
> This was already explained here:

So I seriously doubt this  touch-based system can be run remotely from a VM at a datacenter.  I'm  also sure they do not want the headache involved with useless systems if  any of the 300 remote sites have connection problems.  Kiosk  applications typically can run and work remotely even without a network  cable plugged in (and cache data until a connection can be  re-established).

LHammonds

Exactly, we don't have any data centers... they are small Kiosk (monitoring systems) used by end-users, like you and me. Some systems are installed in container running on generator somewhere in the middle of the forest.... seriously!

---

### Post by jpelletier on 2018-08-29
> **LHammonds said:**
> 
**EDIT:** For future rollouts of hardware, you might consider having two separate drives(partitions) (like a switch) where one contains the active boot partition/OS and another that can contain an offline copy of a new base image.  The active system could be configured to pull down new images and just modify the boot process to point to the other OS when time to upgrade.  Then the active OS can later update the other OS image the next time.  I thought about designing a system like this in the past but for desktop images.  New desktop images would be pushed to the active-running OS and stored on the system, upon next boot, the newest image would be activated.  But I never got further than the idea since we cannot rollout Linux as a desktop yet (too many Windows-required apps).

LHammonds

I like your idea! But we should be running 18.04LTS for a while now. For our apps, we use containerization

---

### Post by 1clue on 2018-08-29
Yeah, I remembered "nuc" but somehow missed "kiosk." My bad.

So what we actually have is 300 very lightly loaded systems which pretty much must be upgraded on site.

---

### Post by 1clue on 2018-08-29
So if they're all pretty much identical, how about this:

[LIST=1]
[*] Get 10 hard drives and a spare NUC.
[*]Install a drive in the NUC.
[*]Install 18.04 on the drive, including that specific NUC's site-specific data.
[*]Send the drive to the site.
[*]Start on the next drive/site while you're waiting.
[*]Somebody there swaps hard drives and sends you back the old one.
[*]You have 10 drives rolling through, so you're busy all the time while drives are in the mail.
[/LIST]

---

### Post by oldfred on 2018-08-29
One step further, get 10 spare Nucs. And configure them & ship entire system. 
Changing HDD may require someone more technical.

You probably have some one nearby most of the Kiosks to plug them in & ship older one back for reconfiguration. Shipping cost has to be lot less than sending someone to all 300 locations.

But if you are paying, I am available to go to all 300 locations.  
But may want to stay in area for a day or two, and maybe take spouse with so it is  a long paid vacation. :)

---

### Post by jpelletier on 2018-08-30
> **oldfred said:**
> One step further, get 10 spare Nucs. And configure them & ship entire system. 
Changing HDD may require someone more technical.

You probably have some one nearby most of the Kiosks to plug them in & ship older one back for reconfiguration. Shipping cost has to be lot less than sending someone to all 300 locations.

But if you are paying, I am available to go to all 300 locations.  
But may want to stay in area for a day or two, and maybe take spouse with so it is  a long paid vacation. :)

Haha thanks for the offer :P

---

### Post by TheFu on 2018-08-31
Figure I'd chime in. Not really with much new.

FedEx can solve many problems.   I've used them to deploy and maintain 22K remote, sometimes-connected, systems.  We purchased 10% spares just to handle failures due to heat and vibration. Initially, the connections were over a packet network, no IP, so pushing data wasn't possible.  Even after deploying private-networking to the 1000+ locations, patching was a pain. 

For 300, you just need a few spares to send out first which can be swapped  by a local, generic, IT person, assuming a video showing how to replace the whole system for onsite person isn't possible.

BTW, if the systems aren't networked at all, then there really aren't any added risks by not patching.  I'd wait until there was a failure to swap them out or do it slowly, say 30 in a month, so any issues get the hands-on help needed. Plus, the field people will happily help each other out, so if you start with 10 locations and get their feedback, the process can be improved with each step.

Back at the main location, I'd have an image that was maintained by a devops tool like Ansible and definitely using containers will make life easier.  

 In theory, snaps would be good, but there appears to be more overhead with those and people are still running into problems with some that aren't 100% self-contained.  Honestly, I'd wait at least a few more months before using 18.04 unless you are absolutely positive all is well.  There are still enough *issues* being reported that it concerns me.

But we are fair away from the problem and only you know the best solution.  Nothing has humbled me more than the unexpected situations that come up in the field.

---

