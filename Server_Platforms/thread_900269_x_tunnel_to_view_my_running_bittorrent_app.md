---
title: "x tunnel to view my running bittorrent app"
date: 2008-08-25
forum: Server Platforms
---

### Post by 1jackjack on 2008-08-25
I have a server at home running ubuntu server 8.04 and utorrent on wine (one day I will upgrade to rtorrent). Currently, I remote desktop to my server to keep an eye on things, but this is very slow, and I recently discovered running applications through a ssh x tunnel i.e.

ssh -X user@server

Is it possible to load my running bittorrent app through the tunnel?

Cheers,
Jack

---

### Post by silverglade00 on 2008-08-25
I am pretty sure that you will want to use the 'screen' command to accomplish this, but I have not had a chance to play with it enough to tell you how to do it. You can start with 'man screen' to get started and I'm sure someone will come along who knows more about it.

---

### Post by 1jackjack on 2008-08-27
I'm afraid screen is just for command line apps...

---

### Post by Archmage on 2008-08-27
> **1jackjack said:**
> I'm afraid screen is just for command line apps...

Yes, it is. rtorrent and screen are a powerfull combination. But I'm afraid utorrent, wine and screen won't mix.

---

### Post by 1jackjack on 2008-08-27
@Archmage
Do you use rTorrent then? The only thing stopping me changing to that is the lack of a labels feature, so I can oversee my different trackers separately...

Cheers,
Jack

---

### Post by Archmage on 2008-08-28
> **1jackjack said:**
> @Archmage
Do you use rTorrent then? The only thing stopping me changing to that is the lack of a labels feature, so I can oversee my different trackers separately...

Yes, I'm using rtorrent by myself. Unfortunatly I don't understand exactly what you mean with "labels feature". I'm using rtorrent simply to drag the .torrents-files in one folder and than get the finished downloads later. Beside of that I'm not doing much with it. (Why should I, when it is working.)

---

