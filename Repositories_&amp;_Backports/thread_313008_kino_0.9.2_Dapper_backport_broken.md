---
title: "kino 0.9.2 Dapper backport broken?"
date: 2006-12-05
forum: Repositories &amp; Backports
---

### Post by finite9 on 2006-12-05
I have Kino 0.8 ni Dapper and it works fine for grabbing dv from firewire dv cam, but when i enabled the backport repo and installed kino 0.9.2 (to get it to recognise widescreen correctly), then I can no longer grab dv via firewire...it says that the ieee1394 module is not loaded.

At first I thought it was because it was pointing to the wrong device: Dapper is /dev/raw1394, whereas the default value in the Kino backport was something else entirely.  I changed it back to /dev/raw1394 but same error.

I am already starting Kino as sudo to get around the fact that permissions are not correct in Dapper for normal users when using /dev/raw1394, but the message is the same as you would get if you started Kino 0.8 as a normal user in Dapper.

Does anyone know what the problem is and how to workaround it?

---

