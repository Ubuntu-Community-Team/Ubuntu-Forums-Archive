---
title: "can't open vmware server 1.0.7-10231 console"
date: 2008-09-19
forum: Virtualisation
---

### Post by Matt26 on 2008-09-19
i just upgraded my vmware server installation (on ubuntu 8.04) from 1.0.6 to the latest 1.0.7 build 10231... the installation completed successfully but now i can't open the vmware server console- when i try to, the console window will attempt to open (the window is visible on the task bar at the bottom of my screen) but then the window just disappears, nothing else happens!

when i run vmware server from the terminal this is what i get:
[B]/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
[/B]

any suggestions on how to fix this would be greatly appreciated.

thanks.

---

### Post by trmentry on 2008-09-19
Try this.

```

cd /usr/lib/vmware-server-console/lib/libgcc_s.so.1

sudo mv libgcc_s.so.1 libgcc_s.so.1.org

cd ../libpng12.so.0

sudo mv libpng12.so.0 libpng12.so.0.org

```

---

### Post by aguazz on 2008-09-20
Next steps solved this problem for me:

```
sudo ln -sf /usr/lib/gcc/i486-linux-gnu/4.2.3/libgcc_s.so /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1
sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0
```

---

### Post by Matt26 on 2008-09-20
thanks for the suggestions, i got my issue fixed using the steps at this link:

[http://radio.javaranch.com/davo/2008/06/18/1213791596327.html](http://radio.javaranch.com/davo/2008/06/18/1213791596327.html)

---

