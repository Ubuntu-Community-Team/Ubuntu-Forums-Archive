---
title: "Writing Mouse data to a file"
date: 2009-01-11
forum: System76 Support
---

### Post by maverick_ on 2009-01-11
I was wondering if its possible to read/print the data sent by USB MOUSE (dx, dy , Z-wheel & button status) directly to file instead of converting it into cursor movements or clicks for that matter.

 Has anyone ever done such a thing ? How does one find out which driver code is being used for the mouse connected, there seems to be many mouse related files floating around.

Please reply....

---

### Post by drewbenn on 2009-01-11
Does 'xev' fit your needs?  (You _might_ need to install 'x11-utils' to get it).  If you want to store what you do into a file, run 'typescript' before running 'xev'.

---

### Post by Lee_Machine on 2009-01-11
So your thinking the implications would be to write a script to tell the computer click here and there at this time?

The program you would use is called xev just go to terminal and type xev.

It tells you what button is being pressed, when, where(in pixels), and the hex code for that button. It similar to a tool you use when setting up a TV remote with lirc.


hope this helps.

---

### Post by maverick_ on 2009-01-11
Thanks alot guys... drewbenn & lee_machine, xev does help but this is not exactly what I'm looking for.

  I'm thinking on changing the mouse driver functionality to dump the raw mouse data into a logfile as & when it arrives rather than just reporting to cursor application.

Any Ideas ?

---

### Post by jdb on 2009-01-11
> **maverick_ said:**
> I was wondering if its possible to read/print the data sent by USB MOUSE (dx, dy , Z-wheel & button status) directly to file instead of converting it into cursor movements or clicks for that matter.

 Has anyone ever done such a thing ? How does one find out which driver code is being used for the mouse connected, there seems to be many mouse related files floating around.

Please reply....

sudo cat /dev/input/mice > mice.bin

ctl-c when you're done

jdb

---

