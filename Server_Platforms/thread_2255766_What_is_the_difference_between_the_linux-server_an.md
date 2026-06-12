---
title: "What is the difference between the linux-server and linux-image-server kernels?"
date: 2014-12-07
forum: Server Platforms
---

### Post by David_Custer on 2014-12-07
[COLOR=#000000][FONT=Arial]I cannot find a recent definitive difference between [/FONT][/COLOR]**linux-server**[COLOR=#000000][FONT=Arial] and [/FONT][/COLOR]**linux-image-server**[COLOR=#000000][FONT=Arial]. I thought for sure this would be in the Ubuntu documentation, but I don't see it.[/FONT][/COLOR]

---

### Post by David_Custer on 2014-12-07
There are 45 views, and no responses. Did I ask this question incorrectly?

---

### Post by ian-weisser on 2014-12-07
Linux-image-server and linux-server were metapackages for server kernels back when server kernels were different from desktop kernels. The packages were dropped from the Ubuntu repositories after 14.04.

Linux-server generally is a metapackage that depends upon the latest server-specific kernel image, (often) kernel headers, and firmware files.
Linux-image-server generally is a subordinate metapackage that depends upon the latest server-specific kernel image and firmware files.
Generally, users should care only about the linux-server metapackage - linux-image-server gets pulled in as a dependency.

Example of dependencies from 10.04. Note the server-specific kernel dependency.

**linux-server** dependencies:
- linux-generic-pae
- *linux-image-server*
**linux-image-server** dependencies:
- linux-firmware
- linux-image-2.6.32-68-**server**
- linux-image-generic-pae


Example of dependencies from 12.04. The server-specific image has been replaced by server-specific headers:

**linux-server** dependencies:
- linux-generic-pae
- linux-headers-server
- *linux-image-server*
**linux-image-server** dependencies:
- linux-firmware
- linux-image-3.2.0-72-generic
- linux-image-generic-pae


Example of dependencies from 14.04. All server-specific references have been dropped, and both are simply transitional packages pointing to the latest kernel.

**linux-server** dependencies:
- linux-generic
**linux-image-server** dependencies:
- linux-image-generic

---

### Post by TheFu on 2014-12-07
> **David_Custer said:**
> There are 45 views, and no responses. Did I ask this question incorrectly?

Well - I looked, didn't understand the question, tried to figure it out, but in the end my 14.04 system didn't provide any clues, so I didn't have anything useful to say. 

It would have helped to specify "packages" somewhere in the question/title, however. That little keyword would have helped me **a bunch** - I considered whether you were asking about physical vs virtual servers possibly PXE booting an image ... couldn't tell for certain from the information in the question.

---

