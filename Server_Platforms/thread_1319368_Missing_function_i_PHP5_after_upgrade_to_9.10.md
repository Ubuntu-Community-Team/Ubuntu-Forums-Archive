---
title: "Missing function i PHP5 after upgrade to 9.10"
date: 2009-11-08
forum: Server Platforms
---

### Post by niha64 on 2009-11-08
I've just upgrade a pc from version 9.04 (32 bit) (Just clikked get it in Synaptic). Most functions and applications is working fine, so I made a fresh install of the 9.10 x64 version on another pc.

When PHP5 scripts uses the GD function imagerotate I get an FATAL Error function not found. Other functions from the GD libary eg. imagecreatefromjpeg and imagejpeg works fine on both machines.

The scripts with imagerotate worked fine under 8.10 x64 and 9.04 32bit. 

I've tried to uninstall/update/install php5-gd through apt-get, but this does not change the situation.

Does anybody know a way to downgrade the php5-gd libary to the version from 8.10?

---

