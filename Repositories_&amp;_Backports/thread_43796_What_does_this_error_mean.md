---
title: "What does this error mean?"
date: 2005-06-23
forum: Repositories &amp; Backports
---

### Post by last1 on 2005-06-23
Hi, I added this repository for latest releases of Ur-Quan Masters, and am trying to install the game. When I check the box to install in synaptic, I get this response:
uqm:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
  Depends: libvorbisfile3 (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: uqm-content but it is not going to be installed

Then it doesn't let me install it. What's that mean?

---

### Post by Lunde on 2005-06-23
[QUOTE=last1]Hi, I added this repository for latest releases of Ur-Quan Masters, and am trying to install the game. When I check the box to install in synaptic, I get this response:
uqm:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
  Depends: libvorbisfile3 (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: uqm-content but it is not going to be installed

Then it doesn't let me install it. What's that mean?[/QUOTE]
 Try adding some repositories, guide here:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Then try to install the packets you are missing first
$ sudo apt-get install packet_name

---

### Post by last1 on 2005-06-23
I've already added all those repositories, and installed all those packages though. That's what I don't get. I have libc6, libvorbisfile3, and libvorbis0a, and they're all the latest, most up-to-date. I've even tried re-installing those particular packages and then attempting the uqm package, but I still get the same errors. 

Perhaps I should explain what else I've tried. Earlier I tried going to the actual page of the repository and downloaded the .deb files, verified that I had installed the dependencies, and manually installed the packages with dselect using the option to disregard the dependecy errors it was giving me. The result was that the game installed, and worked quite well.  But then when I used apt-get or synaptic I'd get an error telling me about how uqm was causing dependency problems and that I'd have to uninstall uqm before I could proceed with using apt-get in a normal fashion.  

If somebody can tell me of a way to tell Synaptic to just stop worrying about these fake dependency problems and to just continue to function normally, I'll just install the packages manually like I did before, but as it is, I don't want to cripple my apt-get capabilities just so I can play this game.

---

### Post by TRAVISL on 2005-06-24
I'm also getting a very similar error when installing practically anything.  Here is the output I get when trying to install acrobat reader.
```

travis@Laptop:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acroread: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages
```
This happens with all kinds of other programs too any help would be great.
Travis

---

### Post by kxs on 2005-06-24
I get the same error when trying to install acroread. What to do?

---

### Post by jdong on 2005-06-24
Guys... you can't use marillat and other non-Ubuntu repositories. The packages are not designed for use with Ubuntu. Remove all your ftp.nerim.net and other non-Ubuntu, non-Backports repositories.

---

### Post by kxs on 2005-06-25
OK, but still... what to do with such error?

[QUOTE=last1]Hi, I added this repository for latest releases of Ur-Quan Masters, and am trying to install the game. When I check the box to install in synaptic, I get this response:
uqm:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
  Depends: libvorbisfile3 (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: uqm-content but it is not going to be installed[/QUOTE]

---

### Post by TRAVISL on 2005-06-26
[QUOTE=jdong]Guys... you can't use marillat and other non-Ubuntu repositories. The packages are not designed for use with Ubuntu. Remove all your ftp.nerim.net and other non-Ubuntu, non-Backports repositories.[/QUOTE]
Thanks that worked great.  My system is back to normal.
Travis

---

