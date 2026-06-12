---
title: "Backup exec RALUS"
date: 2007-01-03
forum: Server Platforms
---

### Post by dhoffman on 2007-01-03
:confused: I am trying to get backup exec ver 10 remote agent for linux to run.  I have managed to get it installed by converting the two rpm packages to deb packages with alein. I learned how to do that from the forums. When I try to start it, it fails.  In the beremote.service.log the following appears:

/opt/VRTSralua/bin/beremote: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file:  No such file or directory

I am new to Ubuntu and linux and am up against a brick wall at this point.  Any help  would be greatly appreciated.

---

### Post by yebo29 on 2007-01-03
It seems like those libraries are not installed, or you (the app) do not have permissions to those files (least likely).

Binaries will do that to you, me thinks. They were compiled using a certain system setup.

Is there a way that perhaps you could get the source code and compile it for your system?

That way it will tell you what's missing and/or its dependencies. You'll know what you need to install then.

FYI, that file is in /usr/lib on my system, I am running Edgy 6.10.

---

### Post by dhoffman on 2007-01-03
:confused: Thanks for the reply.  I'm not sure of what files I am looking for.  According to the Synaptic Package manager Libstdc++5 and Libstdc++6 is installed.  I reinstalled them just to make sure but the same error appears.  What files do I need to look for to make sure there are installed. If they aren't installed where can I get them and will it interferr with my current install if I install them.

Please excuse my ignorance with linux but this is my first try at using it as everything I have done before is has been on windows platform.

---

### Post by dhoffman on 2007-01-03
:) I was able to get the remote agent started.  I had to install the libstdc++2.10-glibc2.2 package which does contain the libstdc++-libc6.2-2.so.3 shared library.

---

### Post by yebo29 on 2007-01-04
:p SWEET! Good job, dude!

---

### Post by JingTu on 2007-06-25
I'm new to this forum.  I have installed RALUS 11d agent on my Ubuntu box.  I used alien to convert the two rpm packages to .deb packages and then installed these packages with dpkg.  I then modified /etc/VRTSralus/ralus.cfg file to include my BE server.  I also changed ndmp port in /etc/services file on my linux box and on the backup server.  I started agent manually and recycled services on the backup server.  But my linux box is not showing on the BE admin GUI under "Unix Agent".  I applied the license key to my backup server before starting all these.  What am I missing?  The backup server is running BE10.0, my understading is that RALUS 11d should work with 10.0

Thanks so much for your reply!

---

