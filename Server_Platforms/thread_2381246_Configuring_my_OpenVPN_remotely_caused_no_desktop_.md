---
title: "Configuring my OpenVPN remotely caused no desktop GUI at reboot"
date: 2017-12-28
forum: Server Platforms
---

### Post by ericbowers on 2017-12-28
Hi, wondering if anyone has advice to offer. 

My Ubuntu 17.10 server's desktop was pretty much just fine before I went out out of town for the Christmas holiday. While away from home, I remoted into my machine to finish configuring my OpenVPN server and client configuration setup. 

My new issue I discovered upon returning home after Christmas and sitting down in front of my server was that it now reboots into the black, command line interface only, and to launch the Gnome GUI, I have to instruct it to do so by command line and authenticate. On the black command line screen, it gives me the following message, which I had never seen until returning home after finishing the OpenVPN config remotely over the holiday. 

[26. 483561] Could not find key with description [233fbca018e7a300]
[26. 483590] Could not find valid key in user session keyring for sig specified in mount option [233fbca018e7a300]
[26. 483618] Error parsing options; rc = [-2]

I just want to make it default back into the Wayland flavor desktop I had been using (I believe through Unity) by default at all reboots. 

I'm still relatively new to Linux and running my own personal server, started working on this file server project in October of this year.  Any advice on troubleshooting this desktop GUI problem is much appreciated.

---

### Post by TheFu on 2017-12-29
I'm confused about the entire "server" having a GUI.  Servers don't have GUIs.  You can have a desktop install, then add server processes to it.  
Some people install a server, then add a very light GUI, but those would be odd setups.

With 17.10, Wayland has become the default, so many things that the fringe users, like you and me, do haven't been tried yet. Wayland is replacing X11 and has many differences, failings, and great new features when compared to the 30 yr old X11.  You might know these things.  Remote GUIs aren't high on their list.

As for troubleshooting, I always create a new userid, then login as that to test any GUI issues. This often shows issues with a specific userid's configs, not the entire system.  You could just make a new HOME, if you like. Both are pretty easy if you have a solid understanding of Unix userids and how dumb they are.

If that fails to show anything different, I'd purge then reinstall the GUI I wanted.  Purging should remove any system-wide config files.  "remove" will not.

For technical people, openvpn is handy for non-desktop systems (android).  Generally, I prefer ssh and ssh-tunnels over openvpn.  The remote desktop solution I use is based on ssh too and it feels 2-3x faster than most other methods. It is x2go, though I haven't tried it with 17.10 - I'm an LTS-only guy.  Thank you for your service - bug testing non-LTS releases is a thankless job.

---

### Post by slickymaster on 2017-12-29
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2017-12-29
I copy/pasted the 2nd error message and it seems that error is related to having an encrypted HOME directory that isn't being decrypted through the expected session key manager.  I played with per-userid encrypted HOMEs over 5 yrs ago and found it didn't meet my needs (backups were broken for my setup), so I switched to full disk encryption under an LVM setup.  Both have issues and caveats for use.

Anyway - that's a hint this isn't a server issue and likely has NOTHING to do with openvpn at all.

---

