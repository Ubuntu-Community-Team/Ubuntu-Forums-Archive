---
title: "Request: Wings3d and NVU"
date: 2005-04-26
forum: Ubuntu Backports
---

### Post by J.K.Makowka on 2005-04-26
[http://www.nvu.com/](http://www.nvu.com/)  Prerelease 1.0

[http://www.wings3d.com/](http://www.wings3d.com/) Both stable and development release would be great.

Thanks a lot.

---

### Post by jdong on 2005-04-26
I know no Nvu Debian packages exist yet. What about Wings3d?

---

### Post by J.K.Makowka on 2005-04-26
Ahh ok, you just port debian packges to ubuntu (should have read more carefully).

Wings3d is already in ubuntu, but a pretty old version.

How much work is it to create a .deb out of source or a binary installer?

---

### Post by jdong on 2005-04-26
Yes, most of these packages are already in Ubuntu or Debian, just at another version. I recompile to resolve library dependencies for the current stable Ubuntu. Ubuntu Extras, a Backports side project, worries about packages not in Ubuntu (but generally Debs are available)

If a Debian package already exists (even if it's old), updating it is usually a trivial task.

If a new package is to be made, unless it's a very simple console thing, I like to see it at least in Debian Experimental or Debian Sid, or Ubuntu's development branch.

I do not like creating brand-new packages, because I **KNOW** they won't be as high-quality as original genuine Debian :)

---

### Post by AgenT on 2005-05-20
A little late but I found a repository of[ Debian NVU packages]("http://packages.debian.org/unstable/web/nvu") on debian.org. Hope that helps.

---

### Post by jdong on 2005-05-20
Let's do it :)

---

### Post by AgenT on 2005-05-20
[QUOTE=jdong]Let's do it :)[/QUOTE]

YAY! \\:D/

Oh and... someone [fix those smilies]("http://ubuntuforums.org/showthread.php?t=34804")! ;-)

---

### Post by Pluby on 2005-06-04
NVU is pretty special in the web-development area, and I think will be a strong draw for anyone coming to Ubuntu. Perhaps it should be default-installed app, like OpenOffice? Because making a web page is slowly becoming something almost everyone needs to do.

In fact, when I first switched to Debian and Ubuntu, my biggest problem was finding an equivalent for Dreamweaver. There was nothing, and all references for "Web Development" basically pointed to Quanta and Bluefish... which indeed are the most sophisticated, but unfortunately not WYSIWYG, and thus nothing at all for the typical non-techie user I think Ubuntu wants to convince to try Linux.

NVU really hits the mark in that area -- everyone can feel instantly like they can make a real web page (not just some export from OpenOffice, etc.).

---

### Post by thephotoman on 2005-06-04
There's also a .deb in the Breezy repositories.

---

### Post by Pluby on 2005-08-09
Maybe there is a better way, but to get Nvu, I manually added this repository in menu Settings->Repositories:
Type: binary
URL: [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)
Distirubtions: hoary-backports
Sections: main universe multiverse restricted

Special note: Also, in my case, I had to do a "Force Version", because a Debian deb I put in earlier had messed things up a bit. 

Nvu is simply "a must", I really think it needs to be in the core distribution. Quanta, Bluefish, etc. are all great, probably more "powerful" in some esoteric sense... but ultimately, they simply aren't WYSIWYG, and thus not as useful for the average person.

---

