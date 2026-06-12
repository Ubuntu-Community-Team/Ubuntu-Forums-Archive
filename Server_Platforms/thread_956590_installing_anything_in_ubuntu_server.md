---
title: "installing anything in ubuntu server"
date: 2008-10-23
forum: Server Platforms
---

### Post by adept_king on 2008-10-23
i have not internet connection on my ubuntu server yet.

installing anything in ubuntu server is not happening.

first of all, make is not included.  cant build my drivers to get my wireless card to work without it.  so...

i downloaded build-essential on another machine. i am unable to install it on ubuntu server.

[I]i type sudo install build-essential-11.3ubuntu1

and i get

install: missing destination file operand after 'build-essential-11.3ubuntu1'[/I]

i dont know where to tell ubuntu to install these things.  i thought they contained config files that tell linux where things are supposed to go.

i have a ubuntu desktop livecd and i could install so much from there if only i knew how.  i would love to have gcc, make and build-essential for starters, then maybe i could get to the point  where i can try and summon the mysterious spirits that cause internet to happen on this "ubuntu server."  i have to then figure out how to log onto a wep wireless connection, in order to install xubuntu.  

help appreciated.

---

### Post by lykwydchykyn on 2008-10-23
If you downloaded a .deb file, the command you're looking for is:
```

dpkg -i myfile.deb

```

However, that isn't going to help you, since build-essential is only a dummy package that depends on a list of other packages like gcc and so forth.  

When you do an APT install, the packages are cached to /var/cache/apt/archives.   So if you have another hardy machine, you could:
 - Do apt-get clean
 - apt-get -d install build-essential
 - copy the contents of /var/cache/apt/archives to the server
 - cd to the directory you copied the files to and run "dpkg -i *.deb"

Of course, if there are dependencies missing on the server that were already installed on the client, you'll have to grab those from the other workstation as well.  Seems like there's a snazzy program or script that does this process a whole lot more smoothly, but I can't recall it at the moment.

Best of luck!

---

### Post by stickboy2642 on 2008-10-23
Look at your /etc/apt/sources.list file.  Usually, the first line or 2 has a configuration that tells apt to look for the installation CD.  Normally these are commented out though.  This is my sources.lst file from a 7.10 server that shows you what the lines look like.  Simply remove the comment marks (#) from in front of the lines.  Save the file and then type apt-get update at the command line.  You will have to have the CD in the drive while updating:

**/etc/apt/sources.list**
```

# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

#deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

```

Hope this helps!

---

### Post by adept_king on 2008-10-23
that was great! etc/apt/sources.list

now if i can only unburn my lip that i burnt with spaghetti just now...

---

