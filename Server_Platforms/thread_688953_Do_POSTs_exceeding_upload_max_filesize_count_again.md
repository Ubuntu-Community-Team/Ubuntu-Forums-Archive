---
title: "Do POSTs exceeding upload_max_filesize count against bandwidth usage?"
date: 2008-02-05
forum: Server Platforms
---

### Post by Sporkman on 2008-02-05
I have file uploading mechanisms on my site, and the PHP upload_max_filesize is set to 5 MB, however occasionally someone comes along & tries to upload a file in the tens of megabytes all the way up to over a gigabyte... Do these count against my monthly bandwidth allotment, or is the transfer shut down before the transfer takes place?

---

### Post by soulresin on 2008-02-06
> **Sporkman said:**
> I have file uploading mechanisms on my site, and the PHP upload_max_filesize is set to 5 MB, however occasionally someone comes along & tries to upload a file in the tens of megabytes all the way up to over a gigabyte... Do these count against my monthly bandwidth allotment, or is the transfer shut down before the transfer takes place?

Not knowing the particular policies of your hosting, I'd say it probably counts towards your bandwidth.  The upload_max_filesize won't trigger the error until it's hit, and it won't get hit until that amount of data is actually sent to your server.

Tho, where I work we only charge for outgoing bandwidth, so like I said -- it depends on policy of your host.

---

### Post by Sporkman on 2008-02-07
Thanks, I'll check that out w/ my host service.

---

