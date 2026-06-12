---
title: "Xserver 12.10"
date: 2012-09-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by EdGy28376 on 2012-09-07
I recently upgraded from a perfectly happy running 10.04 to 12.04. Some where in the process the X11 graphics broke. In an attempt to correct it I upgraded to 12.10.

I have a java applications that when I run it, it fails to open a X window. I get the error "Caused by: java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment". I have add the -Djava.awt.headless=true to over come that error. When I do that I get "Caused by: java.awt.HeadlessException".

I believe something was not upgraded properly as I have validated that the application works on a clean install with a virtual machine. The issue there is the network interface and latency.

Any ideas as to where it look would be deeply appreciated.

---

### Post by mips on 2012-09-07
Best bet is a fresh install.

---

### Post by critin on 2012-09-07
>  			 		   		 		 		I recently upgraded from a perfectly happy running 10.04 to 12.04.
Some where in the process the X11 graphics broke. In an attempt to correct it I upgraded to 12.10.

10.04 will be supported until April.   I suggest a fresh install of 12.04 if you really want to upgrade now.  I wonder how 12.10 got mixed in?  Be sure and don't use that one, it isn't ready for release.

---

