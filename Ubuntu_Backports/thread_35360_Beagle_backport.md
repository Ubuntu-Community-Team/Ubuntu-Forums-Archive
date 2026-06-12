---
title: "Beagle backport"
date: 2005-05-18
forum: Ubuntu Backports
---

### Post by jdong on 2005-05-18
I packaged Beagle from Breezy Universe, but it seems to be a really crappy quality debianization. Most runtime dependencies (including mono, gtk-sharp, etc) are not there.

You'll need to apt-get install them separately, based on the error messages that the 'best' command gives at the terminal.

You need at least:
[list]
[*]mono   
[*]libgtk-cil   
[*]libgnome-cil   
[*]libdbus-cil   
[*]libmono-dev   
[*]libgecko-cil   
[*] 
[/list]

---

### Post by mongolito404 on 2005-05-19
I did install the beagle backport package following [instructions found on the Beagle Wiki](http://www.beaglewiki.org/index.php/UbuntuInstall).
When I try to run beagled it ends with what seems to be an unhandled exception about a not found System DLL (see attached files for stderr and stdout of a beagled --fg --debug).

Any idea of what I did wrong ?

---

### Post by jdong on 2005-05-19
As I've already stated, libmono-dev is necessary (which contains the missing so)

I find it strange how crappily dependencies were generated for this package.

---

### Post by Slo Mo Snail on 2005-06-04
For my beagle 0.0.10 packages you also need libgsf-cil

But I think that were all dependencies... if something doesn't work give me the backtrace

---

