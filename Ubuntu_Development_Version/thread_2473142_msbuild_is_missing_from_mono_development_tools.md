---
title: "msbuild is missing from mono development tools"
date: 2022-03-25
forum: Ubuntu Development Version
---

### Post by stephen-mcconnel on 2022-03-25
msbuild is missing from mono-devel or as a separate package.  The xbuild included with mono-devel has been deprecated for years, and will not build the project I am trying to get to package for jammy.
In the past, my organization has provided our own mono and msbuild packages with various bugfixes that we had made which weren't yet released in mono stable.  We really don't have the resources to continue doing this since all of our bugfixes have been accepted upstream.
The msbuild package I've gotten from the mono project claims to be released under the MIT license, so I don't understand why it can't be shipped with jammy.

---

