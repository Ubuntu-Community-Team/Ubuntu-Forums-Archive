---
title: "Octave v on 19.04"
date: 2019-03-16
forum: Ubuntu Development Version
---

### Post by buzzmandt on 2019-03-16
Can someone on 19.04 dev tell me what version octave is in there please?

---

### Post by Smask on 2019-03-16
4.4.1-5

[URL="https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=octave"]https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=octave
[/URL]
Changes since Cosmic 18.10:

```
octave (4.4.1-5) unstable; urgency=medium

  [ Mike Miller ]
  * bison-3.3.patch: new patch from upstream, fixes FTBFS with bison 3.3
    (Closes: #923442)

 -- Sébastien Villemot <sebastien@debian.org>  Fri, 01 Mar 2019 10:16:21 +0100

octave (4.4.1-4) unstable; urgency=medium

  * Add libglu1-mesa-dev to Build-Depends. This is necessary to have
    OpenGL support on armel and armhf (on other archs, it is pulled in by
    qtbase5-dev). Thanks to Adrian Bunk (Closes: #918616)

 -- Sébastien Villemot <sebastien@debian.org>  Tue, 08 Jan 2019 10:30:45 +0100

octave (4.4.1-3) unstable; urgency=medium

  [ Rafael Laboissiere ]
  * d/README.Debian: Fix wording regarding the use of the "pkg install" command
  * d/README.Debian: Document the necessity of the "pkg load" command
    (Closes: 914373)
  * d/control: Bump Standards-Version to 4.3.0 (no changes needed)
  * Build-depend on debhelper-compat instead of using d/compat

  [ Mike Miller ]
  * Ensure that Octave includes important features
    - d/t/builtin-features: New test for builtin features.
    - d/t/control: Include builtin-features in autopkgtest suite.
    - d/rules: Call builtin-features after standard test suite.
    (Closes: #916979)

  [ Sébastien Villemot ]
  * unimplemented-functions.patch: update the list of unimplemented functions
    (Closes: #914391)

 -- Sébastien Villemot <sebastien@debian.org>  Sun, 06 Jan 2019 10:45:09 +0100

octave (4.4.1-2) unstable; urgency=medium

  [ Steffen Möller ]
  * Update metadata - added references to scientific software registries.

  [ Rafael Laboissiere ]
  * d/control: Bump Standards-Version to 4.2.1 (no changes needed)

 -- Sébastien Villemot <sebastien@debian.org>  Tue, 02 Oct 2018 10:12:52 +0200
```

---

