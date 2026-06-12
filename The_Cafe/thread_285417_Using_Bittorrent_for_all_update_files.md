---
title: "Using Bittorrent for all update files"
date: 2006-10-26
forum: The Cafe
---

### Post by aprice2704 on 2006-10-26
Hi all, my first post here, hope I'm in the right place.

I was wondering if thought has been given to having the apt system run using bittorrent as a potential source even for single packages? This would take much of the load off the ubuntu servers and mirrors. I'd be delighted to have some of my bandwidth used for ubuntu packages.

I assume it would be quite safe if the torrent files were all obtained from trusted servers.

Regards

Andy

---

### Post by The Noble on 2006-10-26
Hypothetically it would work, and i think it would be great in the coming years of Ubuntu. I know Canonical is exploding into linux and is having amazing success, so even a 10% decrease would help.

---

### Post by maniacmusician on 2006-10-26
it sounds good at first, but how ideal is it really? the files are usually extremely small (except in times like this when there is mass upgrading), and torrenting those is not effective. And what happens when a newer version of a file comes out? will everyone that seeded the first time around download a new torrent?

It just seems odd. I suppose there's ways to work around it, but someone has to be willing to take the time to think about them. it certainly would help decrease the load on the servers. 

Also, how would things like port forwarding be dealt with? a lot of people use routers.

---

### Post by aprice2704 on 2006-10-26
@Noble: agreed.

@maniac: yes, I was pondering the 'many small files' issue myself, an obvious (to imagine, perhaps not to implement) solution would be to bundle files up into reasonably sized aggregations that go together. But I'm not sure its that much of an issue since BT sessions don't look like they have horrible overhead, though clearly larger than http. Since there would rapidly be a very large number of seeds available it would still be fast, if not that efficient in total bandwidth.

>...seeded the first time download a new torrent?<

yes, I would suggest that the torrents are what would be fetched from the central servers (perhaps in daily batches zipped together when got by scheduled update checks) those actually needed would be requested and then the contents of your package cache would be the shared files.

>Also, how would things like port forwarding be dealt with? a lot of people use routers.<

An issue to be sure, so the BT method would have to be an option. That said, I am behind a router and BT seems to both fetch and serve just fine without any port forwarding.

Of course the dist upgrade is what has set me thinking of this, but it could be helpful quite often when large, popular progs are updated.

:)

---

### Post by Polygon on 2006-10-27
this would be grand if it could actually be implemented. Im currently updating and its at the wonderful spped of 40-60 kb/s, a improvement of the 15-30 kb/s i was getting eariler with just vanilla archive.ubuntu.com 

yet when i downloaded the iso image, i was downloading at 400kb/s and i finished in like 18 minutes.

and you can have multiple files in one torrent download, so all they really have to do is include all of the ugprades in one torrent file and then you download it and then it does its thing with installing it.

---

### Post by aprice2704 on 2006-10-27
>>and you can have multiple files in one torrent download, so all they really have to do is include all of the ugprades in one torrent file and then you download it and then it does its thing with installing it.<<

Cool! That settles it then. BT updates make a lot of sense imo :)

---

### Post by maniacmusician on 2006-10-27
not yet....how would they know which upgrades a certain person needed? this would be efficient if there could be a .torrent generator, that gives you a .torrent file based on the packages you need.

---

### Post by aprice2704 on 2006-10-27
> **maniacmusician said:**
> not yet....how would they know which upgrades a certain person needed? this would be efficient if there could be a .torrent generator, that gives you a .torrent file based on the packages you need.

I would guess that if a file is in a torrent it does not have to be requested, so apt would just request the ones you need.

Not sure how well a torrent creator would work since it would generate more variations whereas bt works best if many people have the same file (I think)

:)

---

