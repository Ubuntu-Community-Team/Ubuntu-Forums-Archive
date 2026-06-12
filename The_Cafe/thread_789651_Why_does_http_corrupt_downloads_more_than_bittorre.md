---
title: "Why does http corrupt downloads more than bittorrent?"
date: 2008-05-10
forum: The Cafe
---

### Post by akiratheoni on 2008-05-10
When people are asked to use Bittorrent instead of http for Linux ISOs, it's for two reasons: 1.) it's easier on the servers and you get better speeds if more people connect to it, and 2.) it corrupts far less often than http.

I already know #1. But just as the title says, why does http corrupt more often than bittorrent?

---

### Post by swoll1980 on 2008-05-10
bittorrent stores the file in packets (512kb I think) if a packet is corrupt it discards it and downloads another. http downloads the entire file as a whole so if there is a corrupt piece the whole file is worthless

---

### Post by LaRoza on 2008-05-10
> **swoll1980 said:**
> bittorrent stores the file in packets (512kb I think) if a packet is corrupt it discards it and downloads another. http downloads the entire file as a whole so if there is a corrupt piece the whole file is worthless

Not quite, http transfers packets also, but it is a different protocol than bittorrent.

---

### Post by spupy on 2008-05-10
The hash of the downloaded torrent is checked?

---

### Post by Joeb454 on 2008-05-10
I've often seen my torrent download count exceed the file size (sometimes by up to 40-50Mb, though I then tend to see around 7 banned IP's for sending corrupt data :p).

That said - sometimes HTTP downloads go far quicker for me than torrents.

---

### Post by the yawner on 2008-05-10
I think it has to do with how the packets received are assembled into a file. In http, once you stopped a download in progress the file is considered complete. This happens not only with actual file downloads, but also with viewing websites. Some websites get missing parts and images and you'll have to do a refresh just to complete it.

On the other hand, bittorrent expects that the packets received can be any part of the file, whicever part is available from the seeders. Thus it has to maintain a check of the file's completeness.

---

### Post by CSMatt on 2008-05-10
BitTorrent creates a SHA1 hash of the file and automatically checks each piece of the file against that hash for integrity.  With HTTP and FTP this has to be done manually, and the uploader has to manually provide a hash for the downloaders to check against.

---

### Post by Foster Grant on 2008-05-11
> **akiratheoni said:**
> When people are asked to use Bittorrent instead of http for Linux ISOs, it's for two reasons: 1.) it's easier on the servers and you get better speeds if more people connect to it, and 2.) it corrupts far less often than http.

I already know #1. But just as the title says, why does http corrupt more often than bittorrent?

I've had many, many more problems with corrupted ISOs via torrent than via HTTP/FTP, and for the most part I've found torrents to be far slower than HTTP/FTP downloads.

Then again, thanks to my cable company I have a download channel wide enough to drive two wreckers through side-by-side (they just upgraded their download speed again). :)

---

