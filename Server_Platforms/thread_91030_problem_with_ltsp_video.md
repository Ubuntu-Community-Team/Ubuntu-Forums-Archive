---
title: "problem with ltsp video"
date: 2005-11-16
forum: Server Platforms
---

### Post by ugus on 2005-11-16
hello

I installed in my house (P4 2.4G 512M Ram Gforce2) ubuntu with the ltsp server, it worked, then i came to work and installed it again (in a celeron1.7Gz 1Gram really old s3 video) and the thin client had a maximum resolution of 640x480, the thin client is the same machine in my house and my work, a dell p3 450MHz with an s3 savage video card, and i tried with a dell pentium 200 class machine, and it doesnt even load x

I donwloaded k12 linux, it worked, in the old pentium 200 it has a maximum resolution of 800x600 but its fine, anyway i know it can give 104x768 at 256 colors, but what I want is ubuntu because it's easier for the common user.

any suggestions?

augusto

---

### Post by petterah on 2005-11-20
Hi, check the ltsp docs at [COLOR="Blue"]www.ltsp.org[/COLOR]. There is a config file where to configure the X driver to use on each thin client, i think its vesa by default, but maybe a S3 will work better? ;)

---

