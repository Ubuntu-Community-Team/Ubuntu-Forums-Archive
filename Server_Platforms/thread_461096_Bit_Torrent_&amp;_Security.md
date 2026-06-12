---
title: "Bit Torrent &amp; Security"
date: 2007-06-01
forum: Server Platforms
---

### Post by Sunforge on 2007-06-01
You can call me a paranoid old git but are there any security implications for sharing files under bit torrent? I'm pretty clear on the copyright side of things.

I'm running Ubuntu Feisty using a standard desktop installation.

A second question would be - are there better torrent client/server apps out there? I'm using the torrent client that comes with Ubuntu.

---

### Post by modulok on 2007-06-01
I use torrentflux...its great if you setup DDNS if you want to control your torrents when you are not at  your server.

---

### Post by murlidhar on 2007-06-01
you can use qbittorrent. just google it. it is steady and fast too and under active development.

---

### Post by az on 2007-06-01
Whatever client you use, pick one that is free-libre open source.  I would not trust a binary-only bittorrent application running on my box.

The fact that it's FLOSS does not in of itself guarantee that it is not spying on you, but it would certainly be a lot harder to accomplish.

Other than that, I would probably avoid running anything that can make my computer too vulnerable on the box running the bittorrent client.  For example, I would avoid running an ssh server (or worse still, a vnc server).  If I absolutely had to I would restrict traffic to known hosts and pick a really strong password.

---

