---
title: "Web based download manager"
date: 2010-02-01
forum: Server Platforms
---

### Post by psykro on 2010-02-01
I have installed 9.10 server on an old machine at home that I want to use purely for managing any software downloads.

I used to use the firefox add on DownThemAll on my ubuntu desktop environment so I am looking for a web based download manager for the server that has similar features (username/password restricted downloads, scheduling, pausing/restarting downloads) as DownThemAll.

I basically want to be able to add a bunch of downloads to a list and the server then downloads them. I need to be able to save a username/password combination for certain sites. I would also like to be able to see progress on the downloads and pause/resume them.

Any suggestions would be greatly appreciated.

I'm also not opposed to a download manager that runs on the server and I access via ssh, but web based would be preferred.

---

### Post by yogesh.girikumar on 2010-02-08
Hi,
       There are plenty of download managers available for Ubuntu that can be run from a remote location using ssh.
   You can try using curl, rsync, or wget depending on your usage and needs.
```
$ man curl
``````
$ man rsync
``````
$ man wget
```     In case you are downloading from Torrents, you can try using rtorrent. ([http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/))
       You can also check out the following download managers.

       d4x -> GUI based
axel -> CLI based
Freedownload manager -> GUI + Web interface + CLI
MLDonkey -> CLI + WEB interface
Shareaza -> CLI + web interface
       

See this wikipedia page for more information: [http://en.wikipedia.org/wiki/Comparison_of_download_managers](http://en.wikipedia.org/wiki/Comparison_of_download_managers)
       

Hope this helps,
Yogesh.

---

### Post by oguhhhacker on 2012-01-04
I can recomend this: [http://pyload.org/](http://pyload.org/)
You can even download Rapidshares with this!

---

### Post by psykro on 2012-01-04
> **oguhhhacker said:**
> I can recomend this: [http://pyload.org/](http://pyload.org/)
You can even download Rapidshares with this!

Thanks

---

