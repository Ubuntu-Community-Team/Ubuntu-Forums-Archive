---
title: "Looking to set up a home ftp/web server. Need distro advice."
date: 2009-10-25
forum: Server Platforms
---

### Post by Warpedflash on 2009-10-25
I have an old thin client that i have stuck a 80gb hdd into and plan on using it as a ftp/web server. the system has... limited resources none of which are upgradeable (par the hdd).

80gb IDE (i will partition this to 10 for system, 70 for files etc)
600mhz cpu
64mb ram
10/100 ethernet

I was wondering if ubuntu would be a sensible server distro to use for this? also if i do use ubuntu how much could i cut out? I only want to use it as a web server to give it a frontend to the ftp as my parents will also be using it and I figure they can manage to go to a web site to upload/view files whereas ftp may be beyond them.

So any suggestions? or would ubuntu server be sensible to use on it?

Thanks,
Warpedflash

---

### Post by volkswagner on 2009-10-25
I don't think you will have much joy with 64Meg RAM.  Large files may choke the system, ie files larger than 64meg.  With apache and other services running, you will be hitting swap space heavily.

You may want to start with with just FTP.

You can run FTP on FreeNAS, which may be lighter on resources.

---

### Post by gnuisancev3 on 2009-10-25
I've ran an email server, and an apache web server on a machine just slightly better than yours using ubuntu server out of my home for a while.    Do not install X, Gnome, GDM, etc.. just stick with plain ol Ubuntu Server and nothing more.  

As long as the website you use is pretty much straight HTML, maybe some low resource PHP, you should be fine.  You start getting into some heavy database CMS type stuff and it's not going to work out so well.  

It should handle FTP just fine.

I hope this is more for a personal project rather than anything you will NEED high availability of, b/c no matter what the OS i'd say the machine wouldn't cut it.

---

### Post by Warpedflash on 2009-10-25
> **volkswagner said:**
> I don't think you will have much joy with 64Meg RAM.  Large files may choke the system, ie files larger than 64meg.  With apache and other services running, you will be hitting swap space heavily.

You may want to start with with just FTP.

You can run FTP on FreeNAS, which may be lighter on resources.

I assumed it would be using swap space quite a bit so that dosent shock me.
I looked at freeNAS and was thinking of going in that direction as teh webpage is not rely high priority... thanks for the advice

> **gnuisancev3 said:**
> I've ran an email server, and an apache web server on a machine just slightly better than yours using ubuntu server out of my home for a while.    Do not install X, Gnome, GDM, etc.. just stick with plain ol Ubuntu Server and nothing more.  

As long as the website you use is pretty much straight HTML, maybe some low resource PHP, you should be fine.  You start getting into some heavy database CMS type stuff and it's not going to work out so well.  

It should handle FTP just fine.

I hope this is more for a personal project rather than anything you will NEED high availability of, b/c no matter what the OS i'd say the machine wouldn't cut it.

Yes its a personal project basically in case i forget any important uni work im going to have my uni folder backup to it each night then i can access it should i forget said work (at least that will be its function for about 6 months then my parents will get use of it as well when i move back home).

the site should be very basic html and php just blank page with a php password script so enter your user/pass and get access to your files as a listing.

Thanks for the advice both of you. i will try ubuntu server first i recon tehn if thats too slow go to freeNAS and just ftp it all

---

