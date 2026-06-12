---
title: "Samba: 1 of 3 shares showing"
date: 2011-10-29
forum: Server Platforms
---

### Post by derelict888 on 2011-10-29
I have run samba on my home server for over a year and recently 2 of my shares have gone missing (with no changes to samba. I have also verified the folders on the server are still there and I even set the permissions to 777 and blasted out the file/folder ownerships. Here is what smb.conf looks like for the shares;
```

[File_Vault]
        comment = Applications, ISOs, etc...
        path = /var/share/File_Vault
        guest ok = yes
        read only = no

[Media]
        comment = Media: music, videos, etc...
        path = /var/share/Media
        guest ok = yes
        read only = no

[Offline_Files]
        comment = Share for offline files
        path = /var/share/Offline_Files
        guest ok = yes
        read only = no

```

Of the 3 only Offline_Files appears on my Win7 desktop when I navigate to \\[server_IP], any ideas?

---

### Post by derelict888 on 2011-10-29
I guess I should also say that I recently re-installed Win7 on my desktop. The LAN says its part of a "home" network type and I have already set the workgroup to the workgroup of my samba share and restarted.

---

### Post by volkswagner on 2011-10-29
Just a shot in the dark here.

The only difference I see with your shares are that the two non working shares have non alpha-numeric characters in the description.

Perhaps remove the commas and periods in the description and restart samba.

---

### Post by dapperdanny77 on 2011-10-30
can you please post the output of

testparm -v 


this shows your complete config

---

