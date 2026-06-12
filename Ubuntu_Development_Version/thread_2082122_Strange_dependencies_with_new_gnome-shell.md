---
title: "Strange dependencies with new gnome-shell"
date: 2012-11-08
forum: Ubuntu Development Version
---

### Post by Harry33 on 2012-11-08
We have the new gnome-shell_3.6.1-3ubuntu1 in RR repo now.
That flavour is build against the new libcogl11 (instead of libcogl9).

Also new libclutter-1.0-0 (1.12.2-0ubuntu1) is build against libcogl11,
like libclutter-gtk-1.0-0 (1.4.0-1) too.

Well, one would expect that there were the related new mutter too.
However, the new version (3.6.1-1ubuntu1), which is build against libcogl11,
bears the new name libmutter0a (instead of libmutter0).
So it cannot be installed and the old lincogl9 thus cannot be removed.

One more time:
we need the package libmutter0, built against libcogl11 or a new gnome-shell built against libmutter0a.

---

### Post by sgage on 2012-11-08
> **Harry33 said:**
> We have the new gnome-shell_3.6.1-3ubuntu2 in RR repo now.
That flavour is build against the new libcogl11 (instead of libcogl9).

Also new libclutter-1.0-0 (1.12.2-0ubuntu1) is build against libcogl11,
like libclutter-gtk-1.0-0 (1.4.0-1) too.

Well, one would expect that there were the related new mutter too.
However, the new version (3.6.1-1ubuntu1), which is build against libcogl11,
bears the new name libmutter0a (instead of libmutter0).
So it cannot be installed and the old lincogl9 thus cannot be removed.

One more time:
we need the package libmutter0, built against libcogl11.

Just updated my sources, and I'm seeing 3.6.1-0ubuntu1.1

That's on the US Server. Let's check the Main Server...

Nope, same version there as well.

---

### Post by Harry33 on 2012-11-08
The second new Gnome-shell has been built: 3.6.1-3ubuntu2.

But it cannot be installed because of gir1.2-gnomedesktop-3.0.

> 
gnome-shell:
  Depends: gir1.2-gnomedesktop-3.0 (>=3.6.1) but 3.6.0.1-0ubuntu2 is to be installed


---

### Post by jbicha on 2012-11-08
Well this is why you shouldn't use -proposed with development release cycles any more. :)

Anyway, thanks for pointing out the problem. It should be resolved soon.

---

### Post by Harry33 on 2012-11-08
> **jbicha said:**
> Well this is why you shouldn't use -proposed with development release cycles any more. :)

Anyway, thanks for pointing out the problem. It should be resolved soon.

Jeremy, how could I have pointed this to you and other readers, If I hadn't enabled the proposed repo then?

I have no problems what so ever with this kind of development of packages.
I merely wanted to warn people not to try to force install new gnome-shell and mutter yet.

And yes I can see that new gnome-desktop3 (3.6.1-0ubuntu1)is in RR now.

---

### Post by jbicha on 2012-11-08
> **Harry33 said:**
> Jeremy, how could I have pointed this to you and other readers, If I hadn't enabled the proposed repo then?

I have no problems what so ever with this kind of development of packages.
I merely wanted to warn people not to try to force install new gnome-shell and mutter yet.

And yes I can see that new gnome-desktop3 (3.6.1-0ubuntu1)is in RR now.

Other readers shouldn't be using -proposed either.

We had figured out that gnome-desktop3 needed updating, but I didn't realize it was my fault for my gnome-shell upload until you posted. We don't yet have a pretty NBS tracker like we had for quantal and previous releases now that we don't have NBS problems in the archives any more (except in -proposed).

---

