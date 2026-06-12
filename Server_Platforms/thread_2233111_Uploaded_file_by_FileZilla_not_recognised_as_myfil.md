---
title: "Uploaded file by FileZilla not recognised as myfile.sh"
date: 2014-07-06
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2014-07-06
Hi all

If I download myfile.sh file, via FileZilla, from a Ubuntu server, modify it on a Ubuntu desktop or server, and upload it back to the server, there is a warning, via a cronjob > /bin/sh: 1: /var/data/bin/myfile.sh: not found
The permissions of the modified myfile.sh are exactly as the original.

When I last physically visited the server, I needed to issue ```
dos2unix /var/data/bin/myfile.sh
```to enable the file to be recognised correctly.

So, any workaround that would enable remote modification of such files, please?

TIA

---

### Post by steeldriver on 2014-07-06
Try setting the Filezilla transfer mode to 'binary' instead of 'ASCII'

---

### Post by ChrisRChamberlain on 2014-07-07
steeldriver

Thanks for your reply.

Your suggestion worked - many thanks

---

