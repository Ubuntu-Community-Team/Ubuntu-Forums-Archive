---
title: "Ubuntu request for a media change"
date: 2010-04-10
forum: Server Platforms
---

### Post by ahounsome on 2010-04-10
Hope you can help. I've tried various releases of Ubuntu server on a box with twin hard drives which I'm mirroring (RAID 1). I run into an issue after partitioning when ubuntu asks for a media change. So its trying to find information from the CD which is not there. Presumably I need to get ubuntu to look for the information on the net?

---

### Post by Bachstelze on 2010-04-10
You probably have a cdrom line in your sources.list that you need to comment out or delete.

---

### Post by ahounsome on 2010-04-10
thanks for the quick response. I believe you're right but how do I do this as the OS is not setup?

---

### Post by Bachstelze on 2010-04-10
I'm not sure I understand your problem, then. What does the message say, exactly?

---

### Post by ahounsome on 2010-04-10
I am not with my server right now but the request is something like "please insert the CD {name of distro version}"

---

### Post by ahounsome on 2010-04-10
I think I've fixed it -
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
A mini CD installation forces all required files to be downloaded.

---

