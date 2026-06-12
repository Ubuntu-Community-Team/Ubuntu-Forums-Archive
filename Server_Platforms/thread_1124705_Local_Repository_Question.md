---
title: "Local Repository Question"
date: 2009-04-13
forum: Server Platforms
---

### Post by mosburn on 2009-04-13
I have a local repository set up so that I can ease the tax on the main servers and get some great speeds on the lan. With the forthcomming release of 9.04 is there something special that needs to be set so that update-manager will tell me that the new version is available on release day? I remember when Intrepid came out it would not let my users know that a new version is out and ready to be upgraded. 

Does anyone know how ubuntu tells update-manager that a new version is out and if I can replicate this process on my local repository?

Thanks

Michael

---

### Post by xris_xcess on 2009-04-14
Hi:

I can´t really answer your question per se, but I can think of maybe a different idea with similar results.

I have a server set up up apt-cacher-ng. It's an proxy server for apt and synaptic. Once up and running, just like with squid proxy, it caches requests for packages (debs and udebs as far as i can see).

Say you have 100 machines that regularly get an array of updates. The first one to get a particular update will max out at you internet conection speed. But the next client will get it straitght from the server at LAN speeds.

Now, you might not want clients to experience the initial delay... no problem, since you already have a mirror in place, I guess you already have some sort of updating/syncing mechanism (rsync or similar). You can easily complement the two together so that your server does the heavy lifting before the clients request an update.

All this with the added benefit of no interference with the built in update/notification tools that ubuntu ships with.

The only downside might be server load, since apt-cacher-ng uses (i believe) xinit.

---

### Post by mosburn on 2009-04-16
Hmm, I don't think that will work with apt-mirror. I think I may just have to play with tcpdump and update-manager -d to see what it is checking. The network that the hosts are on is a highly restricted one and it took quite some time to get the approvals to even build a repo out for them.

---

### Post by xris_xcess on 2009-04-16
I see...

Well maybe it just a file on the server that UM looks for and that has some basic config settings to apply. (new repos, etc.)

Have you looked/asked at the lauchpad site that cares for the update-manager pkg?

---

### Post by Thirtysixway on 2009-04-16
If your clients had 8.04 (Hardy) installed, the update manager won't alert them by default.  The LTS versions are set to only alert when a new LTS release comes out.  IE 6.06 => 8.04 => 10.04?

System > Administration > Software Sources > Updates(tab)

At the bottom you'll see Release Upgrade.  As long as that says normal, your client machines should tell that a new version of Ubuntu has been released.

---

