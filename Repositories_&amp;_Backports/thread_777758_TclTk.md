---
title: "Tcl/Tk"
date: 2008-05-01
forum: Repositories &amp; Backports
---

### Post by stvn_consult on 2008-05-01
Is there an easy way to install all the Tcl/Tk packages, widgets and libraries using Ubuntu?

Thanks

---

### Post by yellowbean on 2008-05-13
I've got a similar question. I was trying to help out a friend by testing his Tcl/Tk app on my machine. I installed tcl, tcl-dev, tcl8.4, tcl8.4-dev, tcllib, tk, tk-dev, tklib, tk8.4, and tk8.4-dev. Basically everything I could find in Synaptic that looked relevant. But it still gave me an error:
invalid command name "tk::canvas"

Shouldn't "canvas" come with the base tk install? I can't even run simple test scripts that I've found on the web. Similar errors like:
invalid command name "tk::frame"

Any ideas?

---

### Post by vbt123 on 2010-12-24
> **yellowbean said:**
> I've got a similar question. I was trying to help out a friend by testing his Tcl/Tk app on my machine. I installed tcl, tcl-dev, tcl8.4, tcl8.4-dev, tcllib, tk, tk-dev, tklib, tk8.4, and tk8.4-dev. Basically everything I could find in Synaptic that looked relevant. But it still gave me an error:
invalid command name "tk::canvas"

Shouldn't "canvas" come with the base tk install? I can't even run simple test scripts that I've found on the web. Similar errors like:
invalid command name "tk::frame"

Any ideas?

I suppose, you have enough packages.
Try to run your script using "wish" command:

wish file.tcl

It works for me.

---

