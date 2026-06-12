---
title: "How should I lock down an open ubuntu pc?"
date: 2007-02-14
forum: Server Platforms
---

### Post by sammydee on 2007-02-14
Hi.

Hopefully I will be setting up a Ubuntu box at school when I go back after half term. I want to leave it on and logged in all day so people can just sit down and have a play with it for half an hour or whatever and just see if they like it. It's just to demonstrate Ubuntu, and hopefully beryl and aiglx too.

I want to know how to completely lock it down, I highly doubt that there will be anybody who has either enough intent and know-how to compromise it, the people that know their stuff will be glad to see it there, and the people that don't know their stuff aren't a risk unless they accidently do something stupid.

I want something like two user accounts, admin and guest. It stays logged into guest most of the time. Guest has normal desktop priveleges, but CANNOT sudo and cannot cause any major problems.

I know I will probably have to edit the sudoers file to do this. How should I tackle that, and is there anything else I need to secure before allowing users free reign on the system? I'm hardly an expert on security, but I doubt there is much that can go wrong in this case?

Thanks
Sam

---

### Post by jtc on 2007-02-14
> **sammydee said:**
> Hi.
I want something like two user accounts, admin and guest. It stays logged into guest most of the time. Guest has normal desktop priveleges, but CANNOT sudo and cannot cause any major problems.
This shouldn't be a problem at all. Any account except the first one is created without any sudo-powers what so ever. If you manually want to give or take sudo-root-power the deciding factor is whatever a user belongs to the group admin or not.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sammydee on 2007-02-15
Thanks, that looks like exactly what I need.

Anything else I should watch out for? Users are able to go into preferences and mess around in there without any priveleges at all, anything major that could be messed up that I should watch out for?

I'm going to partition the disk to give me a backup partition and just create a disk snapshot which I can simply reload if it gets too broken, I really want to give people a free reign to fiddle around with it and see how it all works.

Sam

---

### Post by jtc on 2007-02-15
> **sammydee said:**
> Anything else I should watch out for? Users are able to go into preferences and mess around in there without any priveleges at all, anything major that could be messed up that I should watch out for?
Well, straight up I can think of three different kinds of potential problems.

[LIST=1]
[*] People accidently removing things from their start-menu etc
[*] Immaturities such as putting a pornographics pictures as wallpaper, or something in that direction.
[*] Someone beeing malious enough to install a keylogger or similiar, running as the current user, which I guess would be the same all the time.
[/LIST]
Problem one and two isn't really that critical and I guess you could always monitor the situation and see if sharper messures are neccesary. Number three could be bad thought, depending on what people use the computer for.

One solution, which would save you from having to lock down everything airtight is to simply have a script which removes the content of the homedir at every restart. That way any misstakes or "sabotage" will be gone and you'll have a fresh default everytime. If you then restart the computer now and then at least you'll minimize the potential problems.

---

### Post by sammydee on 2007-02-15
> **jtc said:**
> 
[LIST=1]
[*] People accidently removing things from their start-menu etc
[*] Immaturities such as putting a pornographics pictures as wallpaper, or something in that direction.
[*] Someone beeing malious enough to install a keylogger or similiar, running as the current user, which I guess would be the same all the time.
[/LIST]

This is the sort of thing I was thinking of. However, all internet access at our school goes through a fairly stringent whitelist proxy so finding pornographic images ets will be difficult, and I suspect that in a busy IT room anybody putting an image on from a thumbdrive or similar will be found out. I doubt there will be anybody malicious enough to install a keylogger or similar malware, all of the people that know how to do that would think it was pretty cool that there was a linux box at school. Worth bearing in mind though.

As for number one, this is my main concern.

> Problem one and two isn't really that critical and I guess you could always monitor the situation and see if sharper messures are neccesary. Number three could be bad thought, depending on what people use the computer for.

One solution, which would save you from having to lock down everything airtight is to simply have a script which removes the content of the homedir at every restart. That way any misstakes or "sabotage" will be gone and you'll have a fresh default everytime. If you then restart the computer now and then at least you'll minimize the potential problems.

That's a great thought, but a better idea (if possible) would be to have the home directory reset to a previous state each time the pc restarts, then preferences such as startup scripts which I put on there will be preserved.

How about this: Set up the preferences the way I want it to stay then CHMOD all the directories that I want to preserve in the home folder write only to the guest user. Then rm -f everything in the home directory with guest user permission every time you log out. This way anything that is changed will be deleted, and the guest user is unable to change anything permanently in the home folder.

Will this work?

Sam

---

### Post by sammydee on 2007-02-15
Another way of doing this perhaps would be to completely purge the entire home directory during startup, then restore the whole lot from a backup directory that is read only to all users except root. It would take a little wile but hopefully the pc will only be restarted once a day.

Is there any way of adding a little script like this to the startup procedure?

Sam

---

### Post by jtc on 2007-02-15
> **sammydee said:**
> Another way of doing this perhaps would be to completely purge the entire home directory during startup, then restore the whole lot from a backup directory that is read only to all users except root. It would take a little wile but hopefully the pc will only be restarted once a day.
I'd say that this would be the best and easiest solution. Will hardly take any time at all, since without documents and stuff their homedirectory takes up virtually almost no space at all.

> **sammydee said:**
> Is there any way of adding a little script like this to the startup procedure?
The easiest thing would probably be just to put the script inside /etc/rc.local

---

