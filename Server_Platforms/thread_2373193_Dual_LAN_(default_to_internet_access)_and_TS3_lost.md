---
title: "Dual LAN (default to internet access) and TS3 lost credentials - Mariadb issue?"
date: 2017-10-03
forum: Server Platforms
---

### Post by jambyc on 2017-10-03
Hi,

Recently I have reinstalled and imported Data Base ( and not only) for TS3 on my server 16.04 LTS and everything was fine untill most recent reboot.
Long story short I have reinstalled TS3 to use Mariadb and I had to import all databases for all other services.

After reboot all channels gone missing and it looks like TS3 itself using old database- the one I have imported from old database. I tend to believe somehow Mariadb didn't saved all channels into DB... but when I look into phpmyadmin all current users, including my own, are saved...!?

My credentials to TS3 as server admin has been lost for my gaming PC (which I used privilege key).

I tend to believe everything has to do with my recent dual LAN upgrade which is pointing to non internet access. 
Last week I have set up additional LAN connection for my home CCTV which hasn't got access to internet ( this is only for smb CCTV storage to reduce stress of main network and has it own router)
After reboot the default connection was for CCTV instead of the primary network.

Currently:
I have ticked in server connection GUI - Edit connections...-> CCTV (LAN)-> IPV4-> Routes... ->"Use this connection only for resources of this network" and at least I have access to the internet and all services.

At the moment all other services running OK and no data has been lost.

Or, is this DB privileges issue?

---

### Post by slickymaster on 2017-10-03
Thread moved to **Server Platforms** for a better fit

---

