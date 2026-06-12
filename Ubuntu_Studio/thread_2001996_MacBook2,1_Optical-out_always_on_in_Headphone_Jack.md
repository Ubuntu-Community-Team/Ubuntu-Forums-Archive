---
title: "MacBook2,1 Optical-out always on in Headphone Jack...  Can't use headphones.  Help?"
date: 2012-06-11
forum: Ubuntu Studio
---

### Post by raintheory on 2012-06-11
Running 12.04.  

I can turn off the optical output and enable the normal heaphone output by inputting the following in terminal:  

```
amixer set IEC958 off
amixer set Speaker,1 on
```  

This does work for the current session at least.

I've put those commands in /etc/rc.local and made it executable.  However, the optical out comes on again on reboot and I have no analog headphone output.  

I should note that /etc/rc.local runs fine with the desired effect when I run it manually.

Any suggestions?  

----

[B]SOLVED! - What I was trying didn't work at boot because 'etc/rc.local' does it's thing *before* alsa is loaded.  

SOLUTION - I created a bash script in '~/.config/autostart' containing the commands, made it executable, and voila!  Worked like a charm![/B]

---

