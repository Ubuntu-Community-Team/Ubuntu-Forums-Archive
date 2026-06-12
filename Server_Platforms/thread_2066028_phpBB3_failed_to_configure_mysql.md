---
title: "phpBB3 failed to configure mysql"
date: 2012-10-03
forum: Server Platforms
---

### Post by Ironlenny on 2012-10-03
I guess this is what I get for trying to setup phpBB while giving plasma.

I tried installing phpBB3 with mysql. That failed because I set the wrong root mysql password. I went ahead and install phpBB, telling dbconfig to ignore errors. After trying to rest the password manually, I just purged mysql. After installing mysql properly I tried purging and reinstalling phpbb. It doesn't ask for the root password, nor does it try to setup a 'phpbb' user or database. How can I get it to do that?

---

### Post by Ironlenny on 2012-10-03
I needed to purge dbconfig-common and then reinstall.

---

