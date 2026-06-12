---
title: "Old (intrepid) repositories"
date: 2010-12-03
forum: Server Platforms
---

### Post by whiskybar on 2010-12-03
Hi everyone,

I know it's kind of my fault but I have this problem. I have two machines running Intrepid. I should have upgraded them in due time but what's done is done. Now I need to install some packages there but the Intrepid is no longer supported - Intrepid repositories are no longer available.

What do you suggest, besides a complete reinstall of course? 

Is there an archive of old Ubuntu versions?

Thanks,
Jiri

---

### Post by snowpine on 2010-12-03
You can edit /etc/apt/sources.list and change your mirrors to 'old-releases.ubuntu.com'. This will allow you to install the old, outdated, unsupported applications from the Intrepid repositories. 

Of course I recommend upgrading to a supported release as soon as possible: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by whiskybar on 2010-12-04
Wow snowpine, this is exactly what I have been looking for. In fact, I needed that link about upgrading old releases too.

Thanks very much!

---

### Post by QBX on 2011-02-04
Thank you, this really helped me too.

---

