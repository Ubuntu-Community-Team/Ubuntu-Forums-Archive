---
title: "repository for code::blocks"
date: 2008-06-29
forum: Repositories &amp; Backports
---

### Post by Louis de Broglie on 2008-06-29
Hello ,

I downloaded code::blocks from here(64-bit version):

[http://www.codeblocks.org/downloads/5](http://www.codeblocks.org/downloads/5)

After that i extracted the tarball and installed the packages according to the dependencies. Now i click on the Applications -> Programming -> Code::Blocks IDE and nothing happens.:(

Then I saw something in the lower part of the download site:

> NOTE 2: The Ubuntu packages have been linked against wxGTK-2.8.7, which is not available in the default Ubuntu repositories.To successfully install these packages, you have to add the wxWidgets repository for Ubuntu in your /etc/apt/sources.list (e.g. deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main).

Can anyone explain this and help me run code::blocks perfectly?:)

---

### Post by Louis de Broglie on 2008-06-29
I have this 
deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main

repository in third-party software repository and enabled it. But when the repository reloads , this error occurs:

> 
W: GPG error: [http://apt.wxwidgets.org](http://apt.wxwidgets.org) gutsy-wx Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E0BCE7F53B087BC


---

### Post by Canis familiaris on 2008-06-29
Perhaps this post will help:
[http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418](http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418)

---

### Post by Louis de Broglie on 2008-06-29
Thanks a lot. It's working now:)

---

