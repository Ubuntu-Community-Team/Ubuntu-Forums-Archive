---
title: "how to install plesk on 18.04 no gui"
date: 2020-09-07
forum: Server Platforms
---

### Post by math492m on 2020-09-07
hi so i was trying to install plesk on my server no gui

so i tried to follow this guide but it didnt work 
[https://docs.plesk.com/en-US/obsidian/deployment-guide/plesk-installation-and-upgrade-on-single-server/installing-plesk-using-installer-console/installing-plesk-for-linux-using-installer-console.76445/](https://docs.plesk.com/en-US/obsidian/deployment-guide/plesk-installation-and-upgrade-on-single-server/installing-plesk-using-installer-console/installing-plesk-for-linux-using-installer-console.76445/)

when i intered the first command it just returned "unable to resolve host address 'autoinstall.plesk.com'

what did i do wrong

---

### Post by darkod on 2020-09-07
No need for anything complicated to install plesk on ubuntu server.

Download the .deb file from the plesk website and then just install with:
```
sudo dpkg -i filename.deb
```

PS. Just to clarify, I was talking about installing Plex Media Server because that is what you would usually install on a server. That is very easy to do using the mentioned deb file.

---

### Post by math492m on 2020-09-08
[COLOR=#666666]#[/COLOR] wget https:[COLOR=#666666]//[/COLOR]autoinstall.plesk.com[COLOR=#666666]/[/COLOR]plesk[COLOR=#666666]-[/COLOR]installer
this command fails with "unable to resolve host address 'autoinstall.plesk.com'"

and aint .deb debian only?

---

### Post by darkod on 2020-09-08
Ubuntu is based on debian so .deb files work. And that is not the file I am talking about.

For example for plex media server on 64-bit OS use this:
```
wget https://downloads.plex.tv/plex-media-server-new/1.20.1.3252-a78fef9a9/debian/plexmediaserver_1.20.1.3252-a78fef9a9_amd64.deb
```

After that install that deb file.

You have various files depending on linux version on [https://www.plex.tv/media-server-downloads/](https://www.plex.tv/media-server-downloads/)

---

### Post by math492m on 2020-09-08
hmmmm plesk not plex

---

### Post by darkod on 2020-09-08
Yeap, sorry, my bad. :) I see it now...

If it complains about resolving the host then you have some dns issues on the machine where you are running the command. Try this first:
```
dig autoinstall.plesk.com
```

That should return the IP address and should show if dns is working correctly or not.

---

