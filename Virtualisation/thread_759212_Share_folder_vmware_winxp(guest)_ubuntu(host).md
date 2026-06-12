---
title: "Share folder vmware winxp(guest) ubuntu(host)"
date: 2008-04-18
forum: Virtualisation
---

### Post by andradx on 2008-04-18
I'm writing this thread because it was a sticky issue I had and I searched the web a lot and from all the various solutions I found just one worked. When I tried to do the same to other machines, the forgotten bookmarked guide just couldn't be found so here it goes. (it is always useful to write the correct keywords in our google friend but oftenly it is quite hard to remember or input them)

If you're using a vmware-server and simply there is no setting option to enable a shared folder and if the usb devices just aren't recognized then there is a problem if you want to change files between your host and guest.

The solution for me was:
-installing samba

sudo apt-get install samba

run the command on your host terminal
 ifconfig | grep "inet addr:"
copy all the ips that are listed (probably the last one is enough, but I don't really know)

in the guest OS, winxp
run control panel->network options->lan(or whatsoever appears)->advanced->WINS

add all the ip addresses copied and enable
use netbios over tcp/ip

just share a folder on the windows network and enable other users permissions to change files

on your host go to places->network
there you'll find windows network and under the network name you defined for your guest there should appear the folder you just shared

shazam!!!you're done

I guess that adding all the ips would make all the users in the network able to change whatever files are in that folder. However in my case as I use it as a one way shared folder for specific files to program OMRON automates, not much warm can be done.

---

### Post by fjgaude on 2008-04-18
Yes, you can do it the way you have... there are other ways but with similar results. I've posted them a few times but not as a HOW-TO...

Shares are getting to be standard between Linux and Windows so many know how to do it. From Ubuntu it is good to make sure you have entered the Samba password:

```
sudo smbpasswd -a <name>
```

From there you have security from the quest to the host.

Thanks for sharing your way.

---

