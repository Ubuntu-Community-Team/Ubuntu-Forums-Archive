---
title: "dansguardian blocking downloads"
date: 2008-05-19
forum: Ubuntu Christian Edition
---

### Post by Bnosidda on 2008-05-19
I can't install the .zip files for brushes for gimp and I really need some new brushes, is the a way to allow downloads from 1 site or allow downloads in general?

---

### Post by Eutaw on 2008-05-21
You may have to disable dansguardian to download (the e-Sword protocol requires it). If there is a work-around, somebody more experienced than I will have to show it to you.

---

### Post by Bnosidda on 2008-05-22
bump I really need help and if you could, is there a way to install flash player without going onto their site? like with the "apt-get install" command?

---

### Post by Bnosidda on 2008-05-23
Bump
 plzzzzzz

---

### Post by Eutaw on 2008-05-24
Simplest way is to disable to download, re-enable after

---

### Post by Bnosidda on 2008-05-25
When I disable it, it cuts off my internet connection

---

### Post by Eutaw on 2008-05-25
I haven't had that problem. Are you root? It shouldn't block you unless you're logged in under a secondary account. Or you may try using the liveCD, see if it lets you in.

---

### Post by tx-uturn on 2008-05-29
I don't remember the list, but /etc/dansguardian has filter lists.      You can either add you download site to the whitelist or figure out what filter is blocking and edit that one

---

### Post by funkydan2 on 2008-06-02
If you're using dansguardian at home or on your own computer, you probably don't want to categorically block any type of file download.

The files /etc/dansguardian/bannedmimetypelist and /etc/dansguardian/bannedextensionlist have a pretty restrictive list of files that dansguardian will block.

You may want to delete some (or all, like I have) of the lines in this file so that your downloads aren't blocked.

(Easiest way to do this would be to run 'gksu gedit /etc/dansguardian/bannedmimetypelist' ...)

---

