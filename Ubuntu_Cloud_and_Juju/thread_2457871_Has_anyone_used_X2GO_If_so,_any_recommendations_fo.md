---
title: "Has anyone used X2GO? If so, any recommendations for settings to make it usable?!"
date: 2021-02-11
forum: Ubuntu Cloud and Juju
---

### Post by 42pjcqyy on 2021-02-11
Hi, I have a VPS running Ubuntu 20.04. I am working on a Mac here and using X2GO to get a GUI connection (over ssh). 
I have googled for hours and can't find anything about what settings to choose for compression (and connection) to speed up the GUI interaction. It is unusable due to being so slow. Does anyone know what settings are best or even where I can ask to find out?! 
thanks

---

### Post by TheFu on 2021-02-11
I don't know anything about a Mac or built-in limitations it probably has.
No need for an extra ssh - x2go uses the NX protocol, so ssh is built-into that already. Hope that's what you meant.

As for performance, there are a few things that matter. Let's think about these.
[LIST]
[*]Don't use Gnome3, use XFCE or LXQT DEs ... or better, use just a WM, no DE at all.
[*]sufficient CPU
[*]sufficient RAM
[*]sufficient bandwidth
[/LIST]

1 vCPU on a modern computer (any Core2 Duo or better since 2010), should be fine. I've used a 2-core Celerion in a Chromebook from 2012 happily.

2G RAM or more to run a GUI is needed.  Less than that and you should stay with text-only via ssh. I'm talking about the remote server RAM. GUIs are hogs.  Most of my servers only have 512MB or maybe 1G of RAM assigned.  No GUI on those.

As for bandwidth, I've used x2go from other continents and found it almost snappy.  I've seen a few things in the client-side controls which directly impact the bandwidth used.
* a reverse-channel for printer, file, and audio sharing.  Disable that.
* The size and type of images transferred. On a LAN, I've never modified it, but my LANs are all GigE with nearly GigE performance.  Over the internet, I force the image size to be 4k-png.
* There is a connection bandwidth setting - I always choose 1 less than whatever my bandwidth actually is.  Over the internet, choose ISDN.

I don't have the client running, so I didn't check the exact names, but those are the broad strokes for the settings.

Of course, any OSX limitations (not great X/Server) would be on your side.  I know the Linux and Windows implementations of the x2go client were good and stable.  For a few years, I used x2go from a Win7 machine all day long into a Linux desktop. Worked perfectly.

x2go should be 2-3x faster than other other remote desktop except the expensive commercial ones with hardware support.  I've seen 1080 video streamed over a remote desktop over 1,000 miles away with a Citrix solution on specialized client hardware.

Hope these things help.  I have noticed that 20.04 Ubuntu behaves funny with x2go. Even with ssh-key setup and working, the x2go client still demands a password. I should file a bug.

---

### Post by him610 on 2021-04-20
Yes, I have begun to use x2go only recently. I do not have any prior experience using it so I don't know how it used to behave. Many times, I read how you expounded on the usefulness of x2go, so I thought I would try it.

---

