---
title: "problem sharing an encfs non public folder with samba"
date: 2011-06-07
forum: Server Platforms
---

### Post by andyhe on 2011-06-07
hi,
maybe what I want to do just doesn't make sense (in which case you're welcome to point that out), but I would like a second opinion.
I've been trying to share a folder with samba. This folder is the decrypted version of an encfs encrypted folder. Mounting the decrypted folder on the server is done automatically on login using gnome-encfs. Exposing the folder locally works like a charm.
Now where I get stuck is trying to access the samba share from a client (even with smbclient on the server itself). I can see the share with smbclient -L:
 
 
[COLOR=seagreen]tijm64@tijm64-HTPC:~$ smbclient -L 192.168.1.100[/COLOR]
[COLOR=seagreen]Enter tijm64's password: [/COLOR]
[COLOR=seagreen]Domain=[TIJM64] OS=[Unix] Server=[Samba 3.4.7][/COLOR]
 
[COLOR=seagreen]    Sharename Type Comment[/COLOR]
[COLOR=seagreen]    --------- ---- -------[/COLOR]
[COLOR=seagreen]    Tijm64-HTPC Disk Tijm64 Home[/COLOR]
[COLOR=seagreen]    Tijm64-MEDIA Disk Tijm64 Home[/COLOR]
[COLOR=seagreen]    IPC$ IPC IPC Service (Samba Server 3.4.7)[/COLOR]
[COLOR=seagreen]Domain=[TIJM64] OS=[Unix] Server=[Samba 3.4.7][/COLOR]
 
[COLOR=seagreen]    Server Comment[/COLOR]
[COLOR=seagreen]    --------- -------[/COLOR]
[COLOR=seagreen]    TIJM64-HTPC domestic samba :-)[/COLOR]
 
[COLOR=seagreen]    Workgroup Master[/COLOR]
[COLOR=seagreen]    --------- -------[/COLOR]
[COLOR=seagreen]    TIJM64 [/COLOR]
 
 
Both Tijm64-HTPC and Tijm64-MEDIA are encfs encrypted folders, difference between the 2 shares is that Tijm64-HTPC is in fact a subfolder of en encrypted local homedir of user tijm64, marked public in encfs (since root can access it in a terminal, but not decrypt it, see also [http://www.linux.com/archive/feature/114147](http://www.linux.com/archive/feature/114147)). Tijm64-MEDIA on the other hand is also encrypted for user tijm64, but not a homedir, and not marked public.
 
Accessing both shares with smbclient gives the following result:
 
[COLOR=seagreen]tijm64@tijm64-HTPC:~$ smbclient //192.168.1.100/Tijm64-MEDIA -U tijm64 -W TIJM64 [/COLOR]
[COLOR=seagreen]Enter tijm64's password: [/COLOR]
[COLOR=seagreen]Domain=[TIJM64] OS=[Unix] Server=[Samba 3.4.7][/COLOR]
[COLOR=seagreen]tree connect failed: NT_STATUS_BAD_NETWORK_NAME[/COLOR]
[COLOR=seagreen]tijm64@tijm64-HTPC:~$ smbclient //192.168.1.100/Tijm64-HTPC -U tijm64 -W TIJM64 [/COLOR]
[COLOR=seagreen]Enter tijm64's password: [/COLOR]
[COLOR=seagreen]Domain=[TIJM64] OS=[Unix] Server=[Samba 3.4.7][/COLOR]
[COLOR=seagreen]smb: \> [/COLOR]
 
 
So: I can access Tijm64-HTPC (the public one), but not Tijm64-MEDIA.
 
I suspect (though I couldn't find a clear description of this limitation) that due to the fact that an encfs folder is not marked public, it will not be able to be shared through samba, since the samba daemon runs as root. 
 
My questions:
- Is my conclusion correct?
- what are my alternatives?
- Would sharing the encrypted version of the folder work, and then have it decrypted on the client side using encfs. 
- Can I mark an encfs folder as public and still automount it with gnome-encfs (I don't see how)?
- Any other (preferably simpler) options?
 
All input appreciated, if only to confirm my thoughts.
Andy

---

### Post by andyhe on 2011-06-07
By the way, here are the smb.conf definitions for the 2 shares (since one of the 2 works, and the defs are similar, I didn't bother pasting all of the conf file, should there be a need, just shout):


[COLOR="SeaGreen"][Tijm64-HTPC]

    comment = Tijm64 Home
    path = /home/tijm64/shares
    valid users = tijm64
    public = no
    writable = yes
    create mask = 0600

[Tijm64-MEDIA]

    comment = Tijm64 Home
    path = /data/tijm64/media
    valid users = tijm64
    public = no
    writable = yes
    create mask = 0600
[/COLOR]

---

### Post by andyhe on 2012-02-12
just for anyone choling on the same problem: here is where you might find a hint:
[http://forums.overclockers.com.au/showthread.php?t=662969](http://forums.overclockers.com.au/showthread.php?t=662969)

---

