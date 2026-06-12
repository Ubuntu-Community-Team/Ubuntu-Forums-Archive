---
title: "Just *copying* an .so wrecked the system?"
date: 2013-01-17
forum: Server Platforms
---

### Post by floatingworld on 2013-01-17
So I was experimenting with my first-ever attempt to set up a chroot, fortunately working on a test 12.04 LTS server install.  I used bindfs to experimentally figure out which parts of the filesystem needed to be duplicated within my chroot directory and successfully got chroot launched with the application working properly.

bindfs takes up a fair chunk of memory and my production server is fairly limited memory-wise, so I umounted those folders and proceeded with trying to get it working by copying only the necessary files over to the chroot directory, using the approach described in the GNU documentation of running "ldd" on the executable to find out which libraries it needs.

I got half of them copied over and then got to the point of running this command:```
cp /lib/i386-linux-gnu/libdl.so.2 /my/chroot/dir/lib/i386-linux-gnu
```when the ssh connection dropped suddenly.  I went to the server's console and tried to log in but entering the username resulted in this error```
/bin/login: error while loading shared libraries: /lib/i386-linux-gnu/libdl.so.2: file too short
```and now during a reboot it hangs while running mountall with the same error about the same .so file.  Googling the error seems to indicate that the "too short" bit is a complaint that it doesn't see an [ELF]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format") header when it begins to load the file.

Since this is just a test server I don't really care about fixing the problem, I'm sure I'll find a workaround with a more conventional way of setting up a chroot, but what I'm really curious about is: **what happened?  How did simply copying this file apparently make it unreadable?**

---

### Post by floatingworld on 2013-01-18
Once I got into the system (via a Puppy Linux LiveCD... it's amazing how useless the Ubuntu "rescue mode" is) I found that .so files I'd copied were zero length and that [FONT="Courier New"]/my/chroot/dir/lib[/FONT] was empty.

So I figure that what must've happened is that I accidentally left the bindfs mount up for that directory (which had been pointing to [FONT="Courier New"]/lib[/FONT]) and so I was actually copying each file on top of itself, which must've erased them.  cp can normally recognize this and abort with an error but bindfs being involved must be what produced a different result.

---

