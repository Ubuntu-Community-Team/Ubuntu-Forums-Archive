---
title: "Is this a virus?"
date: 2011-10-16
forum: Security
---

### Post by grimofoz on 2011-10-16
Yesterday I downloaded the 11.10 alternate iso (64 bit) with bit torrent to my existing Natty installation, then set it up on a new partition; no probs.
but then something peculiar happened to my Natty installation. It suddenly declared the disk was full. I did a search and discovered in the lib folder one file libnss-mdns4.so.2 was listed as 8TB.
I have 2 500gb hard drives in RAID1.
I went to synaptic and removed the file, then checked my drive space. Back up to 28gb free. So I reinstalled it and checked again, down to 16gb. 
The file's only supposed to be 156kb or so.
I completely removed the file and checked again. This time 8gb free space and dropping to nothing as I watched. did another search, now in the proc folder a file named kcore is listed as 128TB
I've done a file check with disk utility and with clam av and fslint. nothing.
Any ideas?

---

### Post by Dangertux on 2011-10-17
> **grimofoz said:**
> Yesterday I downloaded the 11.10 alternate iso (64 bit) with bit torrent to my existing Natty installation, then set it up on a new partition; no probs.
but then something peculiar happened to my Natty installation. It suddenly declared the disk was full. I did a search and discovered in the lib folder one file libnss-mdns4.so.2 was listed as 8TB.
I have 2 500gb hard drives in RAID1.
I went to synaptic and removed the file, then checked my drive space. Back up to 28gb free. So I reinstalled it and checked again, down to 16gb. 
The file's only supposed to be 156kb or so.
I completely removed the file and checked again. This time 8gb free space and dropping to nothing as I watched. did another search, now in the proc folder a file named kcore is listed as 128TB
I've done a file check with disk utility and with clam av and fslint. nothing.
Any ideas?

Here is information about nss-mdns : [http://0pointer.de/lennart/projects/nss-mdns/](http://0pointer.de/lennart/projects/nss-mdns/)

I would however say that it being an 8TB file is rather suspicious, although in this case I would not say it's indication of anything malicious. Most likely improper hardware configuration.

Hope that helps.

---

### Post by MonolithImmortal on 2011-10-18
> **Dangertux said:**
> Most likely improper hardware configuration.

Probably this.

---

### Post by grimofoz on 2011-10-18
I googled proc kcore and discovered I'm not the first to suffer this peculiar malady, particularly in 64 bit, but few answers. Apparently kcore is some sort of 'virtual' file, and should be about zero in size. It's only the label that swells to 128TB.
Unfortunately, Ubuntu classic believes the label and -like a boy who has eaten too much- refuses to play. Interestingly, Unity doesn't seem to care.
Perhaps because Unity acts like it's stuffed at the best of times?
Needless to say, I'm using my new 11.10 installation. From having upgrade problems ever since Breezy, I always run 3 installations; LTS, recent and latest. I would have to say this has been the best and most painless so far, although I still don't like Unity, and for some reason it will only boot from recovery.
At least the 'resume normal boot' option goes straight to the splash page, instead of having to startx in a command line.
And why is there no power options any more? It refuses to 'wake up'.

---

