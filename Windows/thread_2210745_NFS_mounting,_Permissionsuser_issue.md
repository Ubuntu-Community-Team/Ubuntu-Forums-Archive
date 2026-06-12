---
title: "NFS mounting, Permissions/user issue"
date: 2014-03-12
forum: Windows
---

### Post by markosjal on 2014-03-12
Hello, I have been running Crystalbuntu (slimmed down ubuntu 12.04 for Apple TV 1 with XBMC) . Since xbmc runs as "root" user , files written by xbmc have owner root. I want to be able to maintain similar permissions whether files were written across network or local via xbmc. When I write files from a raspberry Pi , no matter what I try to do I can not seem to write files with owner "root" acroos network fron Raspberry Pi.

I have tried varios options on client and server side and I can not seem to get it right

I want to force files written by user pi on client to write as root on server so all files folders and permissions are consistent 

how must I do this?

my current server export
```

/home/atv/  *(rw,async,no_root_squash,no_subtree_check)

```

have tried also 
```

/home/atv/  *(rw,async,no_root_squash,no_subtree_check,anonuid=0)

```



My client /etc/fstab has (maybe I need to remove user option?)
```

192.168.1.2:/home/atv/.xbmc/addons                /home/pi/.xbmc/addons               nfs     _netdev,defaults,user,auto,noatime,intr   0 0
192.168.1.2:/home/atv/.xbmc/userdata/addon_data   /home/pi/.xbmc/userdata/addon_data  nfs     _netdev,defaults,user,auto,noatime,intr   0 0
192.168.1.2:/home/atv/Documents                   /home/pi/Documents                  nfs     _netdev,defaults,user,auto,noatime,intr   0 0
192.168.1.2:/home/atv/Downloads                   /home/pi/Downloads                  nfs     _netdev,defaults,user,auto,noatime,intr   0 0
192.168.1.2:/home/atv/Databases                   /home/pi/Databases                  nfs     _netdev,defaults,user,auto,noatime,intr   0 0
192.168.1.2:/home/atv/Videos                      /home/pi/Videos                     nfs     _netdev,defaults,user,auto,noatime,intr   0 0
192.168.1.2:/home/atv/Pictures                    /home/pi/Pictures                   nfs     _netdev,defaults,user,auto,noatime,intr   0 0
192.168.1.2:/home/atv/Music                       /home/pi/Music                      nfs     _netdev,defaults,user,auto,noatime,intr   0 0
192.168.1.2:/home/atv/.xbmc/userdata              /home/pi/.xbmc/shareduserdata       nfs     _netdev,defaults,user,auto,noatime,intr   0 0

```

---

### Post by howefield on 2014-03-12
Thread moved to the "*Other OS/Distro Support*" forum.

---

