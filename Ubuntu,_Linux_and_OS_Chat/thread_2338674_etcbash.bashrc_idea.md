---
title: "etc/bash.bashrc idea"
date: 2016-09-30
forum: Ubuntu, Linux and OS Chat
---

### Post by jeff.sadowski on 2016-09-30
create a /etc/bash.bashrc.d directory with files of format [0-9][0-9]-packagename-version
ie: 50-cuda-8.0
so that paths can be added in order using the number
and add the necessary code in /etc/bash.bashrc to use it

maybe have paths in its own maybe a /etc/bash.bashrc.path and  /etc/bash.bashrc.path.d 
directory sections as well to make it easier for .bashrc  files to pick and choose paths.

downsides more paths add slowness for shells looking for said programs and 
slowness to autocompletes as well

upside programs can add their paths to the path by adding a file in 
/etc/bash.bashrc.d/ without editing the /etc/bash.bashrc file

Just thought I'd put those ideas out there.

---

### Post by DuckHook on 2016-10-01
Not a support topic.

*Thread moved to **Ubuntu, Linux and OS Chat** as the more appropriate forum.*

---

