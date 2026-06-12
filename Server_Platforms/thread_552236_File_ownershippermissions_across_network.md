---
title: "File ownership/permissions across network"
date: 2007-09-16
forum: Server Platforms
---

### Post by pmorton on 2007-09-16
Can anyone help me out here?

 I have two ubuntu machines, Bill and Ben, and I'm using Samba to access one from the other. I set up a share on Bill and mount it on Ben. No problems there. 

The files/directory ownerships on Bill's share are originally  Ben:Ben; but when I copy the files  over from the share on Bill to the mountpoint on Ben, the ownerships  have mysteriously changed from Ben:Ben to Bill:Bill. 

So I try, as root, to change them back to Ben:Ben but I can neither do that nor change their access permissions; I get the error message:
"chown: changing ownership of `/home/<mountpoint>/<filename> : Permission denied.

There's obviously some principle I'm not getting, and I'd be grateful if someone could explain it.

---

### Post by pheeror on 2007-09-16
This is happening, because samba takes care about permission itself. Use NFS instead of samba. There's no need for samba in non-microsoft networks.

---

### Post by pmorton on 2007-09-16
> **pheeror said:**
> This is happening, because samba takes care about permission itself. Use NFS instead of samba. There's no need for samba in non-microsoft networks.

I'm using Samba because I have a mixed Linux/Windows network. I wondered if Samba was making the changes in ownership. Do you know how to control that? It seems like a strange default policy to me. I can do nothing with the files I've copied over.

---

