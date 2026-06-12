---
title: "Local/server link"
date: 2018-08-08
forum: Server Platforms
---

### Post by warmango on 2018-08-08
So, here is my setup. I have a Ubuntu 18 desktop that I'm using as a web server. And I have Ubuntu 16 WSL on my windows laptop, and I use a program called MobaXTerm to auto login to WSL, and I have my SSH keys configured.

What I want to be able to do, is have a system where I have a local copy of my web page on my laptop located at /mnt/c/ApacheServer_Uby and then have it automatically sync with my serves web page at /home/nuse_wepage, which is where I have my web page files stored.

Are there programs out there that can. Do this For free? Or am I gonna have to use a script?

If I have to use a script like Git to do it, I wouldn't mind, I would prefer automatic 2way sync.

---

### Post by LHammonds on 2018-08-08
If they can see each other on the same network and they trust each other, you should be able to use rsync to keep the files sync'd between them.  

You could setup rsync to run in a script and schedule it via crontab to execute on a regular basis or run it manually.  You could even add logic to the script to see if the remote machine is on your network (can ping the IP) and only issue the rsync command if online.

LHammonds

---

### Post by warmango on 2018-08-08
> **LHammonds said:**
> If they can see each other on the same network and they trust each other, you should be able to use rsync to keep the files sync'd between them. 

You could setup rsync to run in a script and schedule it via crontab to execute on a regular basis or run it manually. You could even add logic to the script to see if the remote machine is on your network (can ping the IP) and only issue the rsync command if online.

LHammonds

I am sometimes AWAY from my Server at my home, but i do have it accessable via a webpage from dynu.com with all the ports needed to be fowarded, and if need be, i can foward a few more ports. I can easily ssh with port 8022,

---

### Post by LHammonds on 2018-08-08
> **warmango said:**
> I am sometimes AWAY from my Server at my home, but i do have it accessable via a webpage from dynu.com
Ah, a bit of crucial information there.  You are wanting to access the server and sync to it while on the local area network (LAN) as well as from the Internet.

Since you are already running a web server and it is accessible from the outside, you might want to look into NextCloud (it is like Dropbox).  You could install the NextCloud web/sync service on your web server and setup a mount point to your web server and associate it to your NextCloud account.  Then on your laptop, you can setup the NextCloud client to sync the web server folder and set the target to your laptop where your website is located.  Once you have the account and client configured correctly, it should keep the folders automatically in sync.  When your laptop can hit the Internet, it will connect to your NextCloud server and begin the sync.

I would use a specific account for this website folder so there is no chance of it accidentally syncing other files if you start using it for other things.

Make sure you configure it to use SSL to your data is encrypted during transfers.

LHammonds

---

