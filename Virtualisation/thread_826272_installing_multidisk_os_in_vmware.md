---
title: "installing multidisk os in vmware"
date: 2008-06-11
forum: Virtualisation
---

### Post by greenbag on 2008-06-11
ok...

installed VMware Workstation v6.0.3, and got past the:


```
run installer until you get to where it asks to run vmware-config.pl

then:

   1.  cd /usr/lib/vmware/modules/source
   2. sudo cp vmmon.tar vmmon.tar.orig
   3. sudo tar xvf vmmon.tar
   4. cd vmmon-only/include/
   5. sudo vi vcpuset.h
   6. change line 74 from: #include “asm/bitops.h” to: #include “linux/bitops.h”
   7. rm vmmon.tar
   8. sudo tar cvf vmmon.tar vmmon-only/
   9. sudo rm -rf vmmon-only/
  10. sudo vmware-config.pl
```

That went fine...

Now, trying top install xp mce, 2 cd's. First cd runs fine, but when it asks for 2nd cd, I put in... but says it's the wrong cd(?). I didn't have this problem with vm installed in an xp host, running suse as guest. That was a few cd's itself, but installed fine.

Is it just a setting somewhere?


Thanks   :)


gb

---

### Post by greenbag on 2008-06-11
should have mentioned, after inserting second cd, it's still registering as the first cd

---

### Post by greenbag on 2008-06-12
fixed it...

Right clicked the cd icon at the bottom right of the vm window, and disconnected the cd drive. Then right clicked the cd icon on desktop and chose eject. Inserted 2nd cd, and waited until cd's window popped open, then closed it. I them right clicked tje vm window's cd icon again, and re-connected... it read it right away and continued the install  :)

---

