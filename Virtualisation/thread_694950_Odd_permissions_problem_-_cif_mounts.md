---
title: "Odd permissions problem - cif mounts"
date: 2008-02-12
forum: Virtualisation
---

### Post by rickbsgu on 2008-02-12
Ubuntu 7.10 on MacBook intel  under VMWare/Parallels (I've seen the same problem under both VM environments).

I've done cif (smb) mounts to a Mac share.  I can access the share perfectly from a Windows VM or a FreeBSD VM or an outside Windows machine.

Now, let's say I have a directory on the share with a couple of files in it:

srcdir/
  file1.txt
  file2.txt

And I want to copy that dir to some point on my share.  So, I do it like this:

cp -R (...)/srcdir (...)/dstdir

What happens is Ubuntu complains that it can't create the directory - permission denied.  But, when I look in the dstdir, the srcdir *is* created, but the files underneath aren't.

If I repeat the command, it then sees the directory is created, but then complains about the first file and permissions out, again.  But, it appears to copy the file.

If I repeat the command, again, it may or may not complain about permissions for the second file.

Eventually, after several iterations, it all gets copied down - with a lot of complaints along the way.

I've opened up the permissions completely, I've made myself part of the 'root' group, but it still does this.

Any thoughts *greatly* appreciated.

Thankx,
rickb

---

### Post by fjgaude on 2008-02-12
You have checked the permissions of the files created? Are they open to you?

Going root doesn't sound like a good way to go.

---

### Post by rickbsgu on 2008-02-13
Yeah, I've set and reset permissions - a+w on everything.

No va.

Currently playing with cifs.mount args to see if something there.

rickb

---

### Post by rickbsgu on 2008-02-14
Ok, have one answer.

On the Mac side, when you set up the share, you need to allow 'everyone' full access.  Apparently the Mac user isn't *quite* the same as the Linux user.

I'd like to fine tune this, since I really don't want 'everyone' access on the Mac shares, but that's what I had to do.

rickb

---

### Post by fjgaude on 2008-02-14
Send a bug report to Apple for your issues.

Peace!

---

