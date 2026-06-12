---
title: "Help Please vi editor -- how do I get out?"
date: 2010-07-28
forum: Server Platforms
---

### Post by youngros on 2010-07-28
Really trying to get this server to work and abandoned trying to do it with Xubuntu last night and installed Ubuntu server. But now I'm stuck on Samba again as I decided to use the vi editor to edit the smb.conf file and now I can't get out of it.
Big mistake will not use it again.

---

### Post by Arand on 2010-07-28
```
:wq
```There should be plenty of explanations of the standard vi commands out there, e.g. [http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)

- arand

---

### Post by youngros on 2010-07-28
Thanks..found some of the instructions confusing...ended logging out and back in again....now use nano

---

### Post by hudsonl on 2010-07-28
Don't give up totally on vi ... it's VERY powerful and guaranteed to be there even on the most minimalistic Linux distros.   

Take some time after the dust settles and learn the basics of vi ... you'll be glad you did.

The key thing to keep in mind is whether you are in "Command mode" or "Insert mode" and that the ESC key will take you back to command mode (where you can exit) and the letter "i" (when in command mode) will put you in Insert mode.

So ... if you stuck and just want out  ... hit ESC (even a couple times doesn't hurt) and you can then enter 

:wq  (write and quit ... save)

:q!     (quit without saving)

---

### Post by ruffEdgz on 2010-07-28
> **hudsonl said:**
> Don't give up totally on vi ... it's VERY powerful and guaranteed to be there even on the most minimalistic Linux distros.   

Take some time after the dust settles and learn the basics of vi ... you'll be glad you did.

The key thing to keep in mind is whether you are in "Command mode" or "Insert mode" and that the ESC key will take you back to command mode (where you can exit) and the letter "i" (when in command mode) will put you in Insert mode.

So ... if you stuck and just want out  ... hit ESC (even a couple times doesn't hurt) and you can then enter 

:wq  (write and quit ... save)

:q!     (quit without saving)

I agree with this comment. As much as nano is friendlier, vi and vim are just really powerful and can be found on almost every Linux distribution (lets say every linux distro I have used has 'vi' installed by default).

Glad you were able to get out and here is a graphical cheat sheet for using vi/vim: [CLICK HERE FOR CHEAT SHEET](http://blog.chinaunix.net/photo/50058_071115190844.gif)

---

