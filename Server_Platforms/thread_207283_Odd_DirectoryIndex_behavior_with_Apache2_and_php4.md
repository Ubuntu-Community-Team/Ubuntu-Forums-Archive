---
title: "Odd DirectoryIndex behavior with Apache2 and php4"
date: 2006-07-01
forum: Server Platforms
---

### Post by the_necroman on 2006-07-01
I've run into an odd problem I just can't seem to resolve.

I'm trying to setup gallery, and for the most part it works.  What I can't seem to resolve is accessing /gallery/.  It simply returns an oddly named phtml file with the contents of /gallery/index.php.

If I hit /gallery/index.php directly, the code gets executed.  It seems to only be a problem when DirectoryIndex kicks in.  I think it's simply a config issue because I have other apps that work fine.  HItting /blog/ executes index.php just fine.

I'm running apach2 and php4.  I've attached a copy of my virtual directory configuration, and I can post anything else that might be useful.

Thanks.

--
Dan

---

