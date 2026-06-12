---
title: "Availability of FLAC 1.1.4?"
date: 2007-07-09
forum: Repositories &amp; Backports
---

### Post by Roobert on 2007-07-09
I should have posted this post to this forum:

Does anyone know why flac 1.1.4 hasn't trickled it's way into the repositories yet, or when/if we may expect it on Feisty? Installing it myself looks pretty daunting, as I have to uninstall half my applications because of a dependency on libflac.

What if I just uninstall the flac command-line package in Synaptic, then compile and install the source for flac 1.1.4 myself? Will this also update libflac, liboggflac, libflac-dev, etc.?

~ Eric.

---

### Post by mlind on 2007-07-09
Gutsy has the newer flac already, and I reckon you're going to get flac 1.1.4 as backport only for feisty. Although you should request the package to be backported first in Ubuntu's [bugtracker]("https://bugs.launchpad.net/feisty-backports").

Applications need to be built against the newer libflac to have any benefit of using it and none of the feisty's packages are. You can have both libflac7 (1.1.3) and libflac8 (1.1.4) installed at same time though.

Is there any particular reason you need newer flac?

---

### Post by Roobert on 2007-07-09
I wanted to be able to incorporate whatever bugfixes are present in flac 1.1.4 so that Sound Juicer may take advantage of them. Sound Juicer uses a gstreamer pipeline which calls libflac.  And I just want the latest and greatest. 

~ Eric.

---

### Post by mlind on 2007-07-09
> **Roobert said:**
> I wanted to be able to incorporate whatever bugfixes are present in flac 1.1.4 so that Sound Juicer may take advantage of them. Sound Juicer uses a gstreamer pipeline which calls libflac.  And I just want the latest and greatest. 

~ Eric.

you would need to rebuild gstreamer0.10-plugins-good against newer flac to get this done. If you really want latest and greatest, install current Ubuntu development version (gutsy) which includes both.

---

