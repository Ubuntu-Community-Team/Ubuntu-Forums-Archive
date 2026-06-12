---
title: "How I can make my ubuntu-laptop remain silent until told otherwise?"
date: 2012-01-12
forum: Security
---

### Post by t.rei on 2012-01-12
Hi,

I'm using my laptop quite a lot in university surroundings. Now one thing that bugs me is: As soon as I turn it on and login in, there are numerous services trying to connect to all kinds of places in the web: ubuntuone, telepathy, gwibber, update, time, .... there is wlan defaulting to "get some connection" and bluetooth is available,too. Network shared folders exists that I didn't even know about and everyone in the room squeels with glee at a potential target for that new hack they came up with.

Now:

Is there an easy way to make the computer remain as quiet as absolutely possible as a default upon turning it on / waking it up / logging in.

I don't really need automatic features looking for current time, other peoples shares, all networks available, updates, ubuntuone or any other cloud service... besides turning off everything available in gnome-session-properties.

I really am not that well informed in these regards, but what would be the major "attention drawing" applications that I'd need to deactivate/remove or block?

Thanks.

---

### Post by Ms. Daisy on 2012-01-12
> **t.rei said:**
> I really am not that well informed in these regards... Because of the part I quoted I would first recommend that you read the basic security wiki.  [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

And to address your specific concern, I would recommend removing any applications you don't use.  That way only the applications you want will run, no extra noise.  As for updates, you can easily configure that to manually update instead of automatically.  If you're on the development release then I'm afraid I can't give you a tutorial beyond just finding update manager and changing the settings to be manual only.

You can manage permissions for the shared files. [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by t.rei on 2012-02-13
Update on this project:

I got quite a lot down to not-show-until-told-otherwise.

update-manager and file sharing and ubuntuone and all those 'services' were rather easy to figure out. 

Something disgusting I found was the amount of spam when starting firefox (blank page). 

I think I am slowly getting to the point where I can spot a switched-on-ubuntu just by the 'noise' it makes. XD

---

