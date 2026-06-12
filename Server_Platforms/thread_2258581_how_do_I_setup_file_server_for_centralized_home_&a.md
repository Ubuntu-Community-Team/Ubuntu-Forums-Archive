---
title: "how do I setup file server for centralized home &amp; logins?"
date: 2014-12-28
forum: Server Platforms
---

### Post by EarlsFurniture on 2014-12-28
I'm looking to setup an office LAN accordingly:

server: 3.2ghz AMDx2 with 8GB RAM - as file/print server
clients: 8-10 machines that vary from 1.2ghz PIII with 1GB RAM to same machine as 'server' with 4GB RAM.

router: Cisco rvs4000
switch: d-link 24 port. (room for all machines, printers, wifi ap, and spares)

I want each user to be able to sit down at any client, choose their name from the greeter, and get their same desktop,settings,home directory (including bookmarks, email etc.) regardless of what machine they sit down to use.

Presently, all machines except 2 PIII's run Ubuntu 12.04.5, with the PIIIs running Xubuntu 12.04.1 (since it runs leaner and there are specific video issues on those machines with anything higher than the .1 release)

I understand there might be issues with settings on those Xubuntu machines, or with using centralized desktop settings if I don't have XFCE/Xubuntu installed on all clients. If there is a way around this or to deal with it other than installing full Ubuntu on these low-end machines, or moving to an all xubuntu network, I'd be grateful. (if it's just a matter of installing xubuntu-desktop on every Ubuntu machine, and then those users get xubuntu-desktop but everyone else gets ubuntu-desktop - that'll work for me - not sure it's possible to auto-select desktop type via the login?)

I DO NOT at this time need or want an application server. I just want users to be able to access their files and customized desktops from any physical client they use. (they all run the same applications anyway and I don't mind maintaining the separate machines)

I also don't think I want a thin-client setup since the server (just a PC - nothing special) probably would choke if trying to serve full ubuntu over the network, applications and all, to the various clients simultaneously.

There will also be some common file directories with various access levels to be shared via NFS.

I've searched high and dry for this and suspect I just don't know what to call it properly. The closest thing I can muster is 'centralized authentication' but I'm not sure that isn't something different entirely.

There's the additional issue that every user needs to run a windows-only app via vbox. If multiple simultaneous logins to XP via a single VM are possible that would be splendid for maintenance purposes, but I'm thinking it isn't from my reading so far. (and quit possibly a violation of the Windows license) This would be a case where I DO need to serve a single application to multiple users at the same time, but I could continue to live with maintaining multiple vm instances on each separate machine. (I thought about running these on the server and providing them via rdesktop, but I don't want to mire the server in mud, I do however use rdesktop to serve those vms to the PIIIs since they choke when running vbox)

Is any of this even possible with this level of hardware?

Or am I stuck with having users locked to specific machines to access their customized desktops? (that is, wallpapers, various user settings, home directories, bookmarks, and email)

Thanks in advance for any tips, pointers, links, etc.

---

### Post by MAFoElffen on 2014-12-29
This is just my perspective...

To get what you want, roaming profiles, the users would need to log into your server at login. The server would be the domain controller. Their home directories would be on that server. Each client machine would be set up the same to use the configs from their home directory. To be the same throughout, all would have to be setup to the lowest common denominator. 

That would mean either re-configuring all down to run Xubuntu or upgrade the video on the two machines, to be able to run Ubuntu. I think the first would be a step back, While the two using those two machines may be happier with better video. (Good name brand video cards can be had these days for under $50...)

That is the physical layer of that. The rest is how you want to go about it and the skill level of who is setting it up.

A simple to administer, low-end solution would be Zentyal Sever. Runs on Ubuntu Server core and is GUI. Not as secure, but easy to setup, administer and manage. From there you could set up your centralized login (NTP, Kereberos, LDAP), although that system leans towards more to Samba shares for print and file sharing. Since on top of Ubuntu Server core, NFS can be done on that server, but is not supported within their GUI. Cups support is their. Some login scripting may apply for the clients to pick up the server resource exports...

Of course you could do the same with Ubuntu Server, which would be more secure... but would all be commandline installs, config, admin and management.. (albiet other management tools such as webmin, etc...) Just the skill level should be a little higher to get it setup right.

---

### Post by EarlsFurniture on 2015-01-21
Thanks. I think that gets the basics out of the way. I've tried other video cards in the two lower-end machines, but sadly, they just can't perform with unity in any usable sense. I think it's more an issue of the processor (pentium III) than anything else. I guess I'll have to find another use for these boxes.

Having everyone run the same version of Ubuntu otherwise should not be a problem. I have no issues that I'm aware of handling the setup from CLI. (though at the moment, that shouldn't be too much of an issue since the 'server' is also my own workstation with a gui)

I can set up every employee with a user account on the server easy enough. My biggest hurdle right now is how do I set up a client so that it looks for users on the server, rather than the local machine? (via the login screen) I'll hazard a guess that somewhere along the way, I'll have to set up some sort of domain-controller/directory daemon on the server and that the clients will load something at startup that will accomplish the task, but I can't seem to find ANY documention on this magic, at least not described in any terms I'm thinking of.

Thanks again for your assistance, I'll keep looking and studying.

---

