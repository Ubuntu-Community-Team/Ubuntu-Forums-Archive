---
title: "managing Linux"
date: 2012-02-05
forum: Server Platforms
---

### Post by Vegan on 2012-02-05
at the moment I manage my Ubuntu VM with webmin fine
i manage my windows vms with remote desktop fine
each can see the other, fine

so is there any remote desktop options for a windows client?

---

### Post by linuxpyro on 2012-02-05
Do you mean some sort of remote desktop client on Windows that you could use to look at the desktop of Ubuntu?  If so, just for use on your local LAN VNC is quick and easy.  You should be able to enable the VNC server on Ubuntu by going to the remote desktop section under the System menu.  There are lots of VNC viewers available for Windows, but in the past I've used TightVNC: [http://www.tightvnc.com/]("http://www.tightvnc.com/")

Note though that VNC doesn't do well on lower bandwidth links, so if you want remote desktop outside your LAN I'd recommend looking into the NoMachines Nx technology; there's an open source version of the server called freenx that I'd recommend looking into.

---

### Post by TheFu on 2012-02-06
Linuxpyro is right.

Sure. I'll assume you want to connect of the internet. That means you need network encryption.
* X/Windows over ssh.
* VNC over VPN/ssh
* NX using a NX client and FreeNX server.

If you really want to be light on the bandwidth, use ssh text interfaces.
If you want the next most efficient solution with built-in security, NX is about 10x more efficient than VNC IMHO.  VNC is fine over most broadband connections, but be certain you tunnel it inside a VPN or ssh connection.  X/Windows client/server will work over a WAN, but it will be really painful.

I use ssh about 99% of the time, but if I do need a desktop, then freenx server is pretty easy to setup on Ubuntu and there are clients for most full OSes.  NX is usable over an old modem connection if that's all you have.

I would encourage you to avoid the GUI and use the CLI more.

---

### Post by Mia1990 on 2012-02-06
Logmein is remote access tool from what they claim.I have never used it.I have a friend that has.You can check it out [here]("https://secure.logmein.com/welcome/access/fasteasy/16/?gclid=CPT4wonUiK4CFQVthwodvRVS3A&wt.srch=1&utpk=+remote%20+desktop&destination=/welcome/access/fasteasy/16/&originid=67490&ef_id=nGFPL2plKXAAAEPj:20120206055133:s")

---

