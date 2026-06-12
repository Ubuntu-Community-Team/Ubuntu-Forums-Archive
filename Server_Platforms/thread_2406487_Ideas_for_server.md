---
title: "Ideas for server ??"
date: 2018-11-21
forum: Server Platforms
---

### Post by koen5 on 2018-11-21
Hey all

I currently have an ubuntu server configured that runs:

- Plex
- Nextcloud
- Samba
- apache2
- webmin (but I hardly use cause I SSH into my server for maintenance)

Nextcloud to share stuff with friends and ofc my plex map is samba shared over my home network to import movies.
Now I'm thinking of putting down a second server but I'm not really sure about what to put on it, I absolutely love tinkering around in the first one.

So my question is: what kind of stuff do you guys have running in your home labs ? Just wanna get some inspiration out of this !

---

### Post by TheFu on 2018-11-22
[https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign) has some ideas for you.

Please be certain that the webmin interface can only be reached using localhost connections, never over the internet.

Also, samba is a poor streaming tool.  If you can, use NFS for much better results.

If you don't have a backup server, you probably want one of those.

And I hope you are using virtualization to segment all these different services. Having all of them running under a single OS instance is a security nightmare.

---

### Post by Tadaen_Sylvermane on 2018-11-22
Mine includes an apt-caching proxy, transmission torrent server, file and media server (nfs), samba for the wife's windows computer for a few things, 2 minecraft servers, dhcp, dns, ltsp for media centers around the house, pxe boot installer server when I have to do an actual install, backup target for all machines in the house. Think that's it.

In my case my "server" is also my living room htpc, so direct boot to Kodi as well.


*EDIT* Agree on separating things via virtualization or containers. I don't because I'm lazy and my machine isn't open to the internet. But admittedly I do not do it correctly. I'm sure one of these days it will bite me.

---

