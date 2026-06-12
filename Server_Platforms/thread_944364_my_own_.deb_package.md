---
title: "my own .deb package"
date: 2008-10-11
forum: Server Platforms
---

### Post by chrisdeeley on 2008-10-11
I'm trying to compile my own deb package. So far its working but when i use dpkg --install mypackage.deb, it warns that the dependancies aren't installed but doesn't prompt the user to install them. It carries on and installs the package but obviously it doesn't work because the dependencies are missing.

My control file looks like this
Package: business-server
Version: 1.001
Priority: optional
Architecture: all
Essential: no
Depends: build-essential, gcc, libapr1, libaprutil1
Installed-Size: 1024
Maintainer: A Person [administrator@smallbusiness.local]
Description: The description can contain free-form text
.

Also in my postinst file, I can get it to prompt the user for questions or values but I was wondering how other packages mbring up the blue screen asking for user input.

Any help would be appreciated.

---

### Post by koenn on 2008-10-11
> **chrisdeeley said:**
> I'm trying to compile my own deb package. So far its working but when i use dpkg --install mypackage.deb, it warns that the dependancies aren't installed but doesn't prompt the user to install them. It carries on and installs the package but obviously it doesn't work because the dependencies are missing.

My control file looks like this
Package: business-server
Version: 1.001
Priority: optional
Architecture: all
Essential: no
Depends: build-essential, gcc, libapr1, libaprutil1
Installed-Size: 1024
Maintainer: A Person [administrator@smallbusiness.local]
Description: The description can contain free-form text
.

Also in my postinst file, I can get it to prompt the user for questions or values but I was wondering how other packages mbring up the blue screen asking for user input.

Any help would be appreciated.

dpkg -i will install dependencies only if they're present in the same directory as the package thet's being installed, i believe. So you could try that.
otoh, it's not something to worry about. obviously, dpkg can correctly read the dependencies from your control file, so it will work in real live as well.
you can simulate this by making your package available on a web server and add its uri to your apt sources list, then use apt to install it and get the dependencies satisfied.
(there's a little bit more to it, look at part 6 of this howto : [http://users.telenet.be/mydotcom/howto/linux/package.htm](http://users.telenet.be/mydotcom/howto/linux/package.htm))

for the user input in a postinst script : Debian uses a dedicated program orlibrary for this so that the script can use different interfaces (line-based text, dialog box text, ...) , provide OK, back and cancel buttons, and let it do common things such as test the input and prompt again if the input seems wrong, all without the maintainer (or you) having to hand-code this over and over again in the install scripts. 
I don't know what it is exactly, but you might find references to it in debian packaging manuals, howtos, and the likes.

---

