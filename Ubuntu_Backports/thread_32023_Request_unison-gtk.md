---
title: "Request: unison-gtk"
date: 2005-05-05
forum: Ubuntu Backports
---

### Post by hogweed on 2005-05-05
How about a backport of unison-gtk (and unison)? This is at 2.9 in Hoary, but Debian unstable has 2.10 -- the big difference, as far as I can see, is that the newer version uses gtk2. 

The unstable debs don't install correctly on a standard Hoary (Kubuntu) setup, and the source looks a bit complicated to me, as it includes source for windows and OS X as well.

The backports project is great, by the way -- I am not missing Gentoo *nearly* as much as I thought I would.

-- hogweed

---

### Post by jdong on 2005-05-05
Ok, Unison has a dependency (ocaml-nox) that I can't satisfy the specific version.

From the look of the changelog, it seems pretty important, too:

```

 * Transition to ocaml 3.08.3 ( Closes: #304124 )

```

Looking at the bug report, I don't want to force unison to compile against Hoary's current ocaml.

I need to check ocaml-nox and see if it's a library with reverse dependencies. If so, I can't really backport it because it'd break other packages. (sort of like upgrading gtk2 without revdep-rebuild ;) )

---

### Post by hogweed on 2005-05-06
Yikes. I guess I didn't catch that this was something quite so complicated in the errors that scrolled by. Thanks so much for looking into this so quickly.

-- hogweed

---

