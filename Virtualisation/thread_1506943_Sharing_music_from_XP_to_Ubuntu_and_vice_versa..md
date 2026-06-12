---
title: "Sharing music from XP to Ubuntu and vice versa."
date: 2010-06-10
forum: Virtualisation
---

### Post by Zaosyn on 2010-06-10
Hi guys right now I've installed VirtualBox and I have made Windows XP my guest. I've also installed the Zune software and my XP guest recognizes my Zune! Everything is great so far but I'm transferring all my music from my Zune onto my XP guest hoping I can access my music folder where all the transfered music is in on my XP guest through Ubuntu, thus listening to it through Ubuntu and not having to use XP when I want to listen to music.

I'm pretty sure there is a way via this "shared folder" option but it confuses me. Eventually what I would LIKE to do is get all my music from my XP guest and put it on my Ubuntu host and then when ever I download music I can just put it in a shared folder on my Ubuntu host that XP will recognize and automatically sync all the new music I've downloaded on Ubuntu to my Zune.

It sounds a little confusing but what I'm asking is so simple I might of made it sound too confusing. Does anyone have any idea how I would go about this? Thanks alot!

---

### Post by clblanchard on 2010-06-10
I think the easiest way would be to move the music to ubuntu and share it with the xp guest (bridged networking with Vbox).  This way you can have the music on ubuntu and only need xp to sync the zune.  

Make sure in settings you have the XP vm set to bridged networking and not NAT (this will give the vm an actual ip address on the network).  

Create a folder in ubuntu (ex. /home/yourname/Music)

right-click on the folder and select sharing options.

check the box that says "share this folder"

check the other two boxes "allow guest" and "allow create..."

if you don't have samba installed ubuntu will prompt you to install and then it will configure it for you.

In the xp guest you can go to network neighborhood and you should be able to see the shared folder.

copy the music to it and set your zune software to look there for the music so sync.

I think that should be what you need to do.

---

### Post by Zaosyn on 2010-06-11
Thank you so much! It worked flawlessly. Thanks again ):P

---

