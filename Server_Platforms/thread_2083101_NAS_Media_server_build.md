---
title: "NAS Media server build?"
date: 2012-11-11
forum: Server Platforms
---

### Post by bldgengineer on 2012-11-11
I'd like to build an linux based server that would serve my 3 htpcs(1 living room and 2 bedrooms) along with 2 laptops and my autocad/cs5 workstation. 

all htpcs and laptops are win7 home based and the workstation is win7 professional.

It should be able to stream HD movies to the htpcs as well as store items from the web as I download them from my laptop or workstation. My girlfriend uses the workstation for her photography and I use it for my cad drawings and such. The external hdds are getting a bit ridiculous and we'd like some easy redundancy for our work. I'd also like to have the ability to remotely connect to it if need be. I'd like to just build it and throw it in a closet in the house.

What would you guys recommend? I kind of have an idea what I need but would like to hear from the more experienced. Like:

Micro atx case
micro atx mobo
atom or i3 processor?
4 or 8gb of ram?
4) hdds 2 or 3 tb?
1) OS hdd. how large?
PSU size?
raid card or onboard raid sufficient?
OS - ubuntu server? freenas? other?

---

### Post by grunge09 on 2012-11-11
Save the money with the i3 and go with a AMD FX-4100 for $109 from newegg.com Or the AMD 965 for $99.

What OS?  Freenas is designed for a standalone file server, so it can't be used as a workstation.

You COULD install Ubuntu 12.10 Server and install ubuntu-desktop then cinnamonand use that instead of Unity.

Drives...2tb drives on eBay can be had for about 75 dollars each.  Start with 3 x 2tb in Raid 5.  Have a 60-120GB SSD boot drive.  You can always grow the raid 5 array later or add a hot spare drive.  

Adaptec makes a good 8 port raid controller, might get lucky and linux may see raid 5 setup from controller bios as one drive.  Usually not.

at least 8gb RAM.  

Motherboard that supports SATA III (970 or 990 series Asrock or Gigabyte are always good).  And HD's to match.  Green 2tb drives will be a little slow (but they are for data) and the SSD will be the OS Drive and run ok.  

Get a tall case, 2 Scythe 120mm 3200-3600 rpm case fans.  

Install Samba to share files across lan.  8 port gigabit switch (cheep on newegg).  

You can use WEBMIN to remotely administrate the pc.

Just my thoughts.  

Any other input?  Am I wrong?

---

### Post by Nilladar on 2012-11-12
I have used freenas, and it works perfect if you want a headless nas. In recent updates they added plugins, but in my opinion we're still buggy.

Currently I just have an old computer running Ubuntu12.04 server. Samba is installed; that will let you open files and play them on client pcs. If you need dlna I use minidlna since it is low resource. 

I have mine headless by ssh, since I have no desktop enviroment installed anyway. 

No hardware opinions, because like I said I just use an old computer using software RAID.

Hope this helps

---

### Post by papibe on 2012-11-12
Hi bldgengineer.

A few thoughts:

The specs look OK. A file server doesn't need too much hardware.

However, I would consider room to grow, so I would get a regular case that allow you to easily add more hard drives when needed.

If your HTPCs are computers, don't stream, use network shares instead (either samba or nfs).

If your HTPCs are wired, HD playback won't be a problem. If they are wireless, consider that unless they are close to the router, a regular G router won't cut it. You would need a wireless N router with a good signal.

Although FreeNAS is a valid alternative, I personally would go with a Linux server for two reasons:
[LIST]
[*]Better changes of a successful and painless installation because of much better hardware support.
[*]Once it is installed and working, you will start thinking in other services and possibilities for your server. Even though FreeNAS is not, by far, a one trick pony, any Linux server will be full of applications ready to use in its repositories.
[/LIST]
Even if 12.10 is available, 12.04 LTS would be a better choice for a server.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by kevinthecomputerguy on 2012-11-12
+1 low hardware needs on a file shares

I have a p3 450mhz (dual xeon) serving files, and a core i5 serving files, and i cant see a difference.

---

### Post by Vegan on 2012-11-12
I use a AMD sempron on my file server, a storage server is very undemanding in the extreme


:guitar::guitar::guitar:

---

