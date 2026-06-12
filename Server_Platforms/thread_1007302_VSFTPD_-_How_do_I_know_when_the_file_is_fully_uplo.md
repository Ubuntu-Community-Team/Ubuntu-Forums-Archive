---
title: "VSFTPD - How do I know when the file is fully uploaded"
date: 2008-12-10
forum: Server Platforms
---

### Post by Wardazo on 2008-12-10
Hi

I have a client who will send a very large file via ftp to my server. My server is running VSFTPD.

When a large test file is uploaded, the file becomes listed immediately even though it is incomplete.(I want to send it off to Amazon's s3 as soon as it is complete.)

How do I know when it is complete if I don't know the file size, and the client will not tell me when it is complete.

I think there's probably a really simple answer that I'm missing somewhere.

Thanks

Ward

---

### Post by cdenley on 2008-12-10
What you want is the HiddenStores option in proftpd.
[http://www.proftpd.org/docs/directives/linked/config_ref_HiddenStores.html](http://www.proftpd.org/docs/directives/linked/config_ref_HiddenStores.html)
Unfortunately, vsftpd doesn't seem to have an option like that.

[http://ubuntuforums.org/showthread.php?t=465859](http://ubuntuforums.org/showthread.php?t=465859)

---

