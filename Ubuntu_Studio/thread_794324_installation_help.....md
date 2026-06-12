---
title: "installation help...."
date: 2008-05-14
forum: Ubuntu Studio
---

### Post by boe-bots on 2008-05-14
okay.....so i downloaded rosegarden from sourceforge.......how do i "install" it so i can use it?

thanks

i'm problably just being stupid....

---

### Post by Stochastic on 2008-05-14
yup, that's a little silly to do.

Sourceforge will allow you to compile the package from source, but that's a bit tricky if you're new to linux.

What you want to do is download the rosegarden package from the Ubuntu repositories, these are pre-compiled binaries for your os.  You can do this a number of ways:
   - Open Main Menu -> System -> Administration -> Synaptic Package Manager and do a search for rosegarden.  Right-click the little box next to the rosegarden package, and select mark for installation.  Then click the apply button and watch it do it's magic.
   - Open a terminal and do ```
sudo apt-get install rosegarden
``` (to search for a package with apt do "apt-cache search rosegarden") this tool is quite powerful, but the command line can scare newbies.

Typically only programs not in the repos you'll need to download from sourceforge.

---

