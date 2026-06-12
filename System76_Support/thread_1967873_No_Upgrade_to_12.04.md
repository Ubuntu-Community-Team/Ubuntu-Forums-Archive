---
title: "No Upgrade to 12.04"
date: 2012-04-28
forum: System76 Support
---

### Post by stangdaman on 2012-04-28
I'm currently running 10.04 LTS on my Pangolin and I had it set to only update releases when the newest LTS come out but I expected and upgrade this week and update manager doesn't seem to be doing that. Any ideas on why it might not be picking it up?

---

### Post by pqwoerituytrueiwoq on 2012-04-29
very good question mine is set the same way and it did not tell me about it either (not that i would accept it, at least not before i fully test it and can have it do anything i want it to that i could do before)
you can run "sudo apt-get dist-upgrade" and get it (should be able to anyway) you could update using a live cd/usb it should give a upgrade option during install

---

### Post by isantop on 2012-04-30
I would wait a week or so anyway for the servers to cool down. If that doesn't work, then the official update process is to press Alt+F2 and type in this command:

```
update-manager -d
```

This will have update manager check for a version upgrade.

---

### Post by stangdaman on 2012-04-30
Thanks guys

---

### Post by stangdaman on 2012-05-03
So I finally upgraded and I have a couple quick questions. I did try searching and didn't see any answers. Compiz doesn't seem to be working since I upgraded and I don't see the option to reset it. Was that done away with in this release?

---

### Post by isantop on 2012-05-03
> **stangdaman said:**
> So I finally upgraded and I have a couple quick questions. I did try searching and didn't see any answers. Compiz doesn't seem to be working since I upgraded and I don't see the option to reset it. Was that done away with in this release?

How can you tell it isn't working? What's happening instead?

---

### Post by stangdaman on 2012-05-04
I guess I don't know it's not working. I don't see any of the graphics I was accustomed to and I don't see the option for it in my system settings.

---

### Post by isantop on 2012-05-04
> **stangdaman said:**
> I guess I don't know it's not working. I don't see any of the graphics I was accustomed to and I don't see the option for it in my system settings.

Which graphics? Do you mean the "Applications    Places    System" menus at the top? Those are replaced with Unity.

If you're seeing anything on the screen at all, it's actually very likely that compiz is working fine.

---

### Post by stangdaman on 2012-05-08
I guess I'm talking about things like the cube when switching virtual desktops or the wobbly windows. Not a big deal I just don't see those. I see the system settings area but when I open it I don't see the options to enable any of those.

---

### Post by Zvezdica27 on 2012-05-09
hi,

you need to install CCSM, which is the config tool for compiz.

In there you have the cube and wobbly wins and all compiz or unity related stuff. I don't use it anymore, so I can't tell if it works, but the option to turn it on is in there.

CCSM is short for Compiz config settings manager, just sudo apt-get install compiz and then press tab to see packages and type and tab to complete the command (or google)

blaž

---

### Post by isantop on 2012-05-10
> **Zvezdica27 said:**
> hi,

you need to install CCSM, which is the config tool for compiz.

In there you have the cube and wobbly wins and all compiz or unity related stuff. I don't use it anymore, so I can't tell if it works, but the option to turn it on is in there.

CCSM is short for Compiz config settings manager, just sudo apt-get install compiz and then press tab to see packages and type and tab to complete the command (or google)

blaž

And, be very careful in CCSM, as it is possible to break the graphical environment using it.

---

