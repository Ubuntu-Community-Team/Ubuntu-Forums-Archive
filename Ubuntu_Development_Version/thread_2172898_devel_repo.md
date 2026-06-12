---
title: "devel repo"
date: 2013-09-06
forum: Ubuntu Development Version
---

### Post by cpatrick08 on 2013-09-06
I noticed at [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) they have a devel repos, could that mean we finally have a rolling ubuntu release!!!

---

### Post by grahammechanical on 2013-09-07
I doubt it. When 13.10 is officially released we may get a script that converts the saucy repositories to T code name repositories and then an update will begin the process of turning Saucy into T code name. This was discussed early on in the year. By running daily updates on the development branch and then converting to the next development branch we get what is almost a rolling release. Some of us have been doing this for a few years now.

We have been using this command

```
sudo sed -i 's/raring/saucy/g' /etc/apt/sources.list
```

That changed a Raring install into a Saucy development install. We will have to change the names to switch from Saucy to T code name.

Regards.

---

### Post by PaulW2U on 2013-09-07
> **grahammechanical said:**
> I doubt it.

Did you check the link?

The 'devel' options are definitely there and at the moment seem to point to Saucy. Presumably once Saucy is released then those links will point to the 'T' release meaning it won't be necessary to run any script or change any repository names on our PCs. At the end of each development cycle the links are simply changed to point to the next cycle.

I seem to remember the Technical Board choosing 'devel' as the name for the continuous development release in an IRC session, so may be this the start of that.

**Edit: **Initial IRC meeting log: [http://irclogs.ubuntu.com/2013/03/18/%23ubuntu-meeting.html#t21:00](http://irclogs.ubuntu.com/2013/03/18/%23ubuntu-meeting.html#t21:00)

---

### Post by craig10x on 2013-09-07
Hope this is the case...they did say they would be creating a "symlink" so you could roll into each new development with out changing the source lists....
I just upgraded from 13.04 to 13.10 and i would love to have that symlink command ready by the time Saucy is released...:D

If not, i think that rather that change the source lists (which i messed up badly the last time) i'd probably just do another upgrade from an early 14.04 daily build because for me i think there would be less of a chance of a major mess up...i was going to use another word but i don't think the moderators would permit it ;)

And i believe Paul is correct about them choosing the name "devel" (development) as the name for the continuous development release...i recall them mentioning that too...
perhaps what that is on that page is synching it all to the new name...

Notice on that linked page, that on the very bottom you see all the "saucy" repos and at the very top it is all duplicated but has "devel" instead...that is why it makes me wonder if that is synching the two together for the coming symlink...

Just a guess on my part....but doesn't it make you wonder? ;)

---

