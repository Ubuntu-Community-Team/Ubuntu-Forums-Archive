---
title: "Is this a dependancy bug?"
date: 2012-05-14
forum: Server Platforms
---

### Post by alf5 on 2012-05-14
package "openjdk-7-jre-headless" does not include "shared-mime-info" package.

The "shared-mime-info" package is needed to make java programs that use java.nio.file.Files.probeContentType() work properly.  java.nio.* classes are included in "openjdk-7-jre-headless".

If it is not installed the function returns "text/plain" for .html, .js, .css, etc.. files.


I think "shared-mime-info" package should form part of the dependency of "openjdk-7-jre-headless".

---

