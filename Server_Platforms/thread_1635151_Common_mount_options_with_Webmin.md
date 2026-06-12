---
title: "Common mount options with Webmin"
date: 2010-12-01
forum: Server Platforms
---

### Post by molinus on 2010-12-01
I am using Webmin to manage an internal server.  When it comes to mounts, I have a question about each choice available for mounting the following filesystem directories: 
    /
    /boot
    /home
    assorted directories for sharing with Samba

Here are the mount options:
    Read-only?
    Allow device files?
    Disallow setuid programs?
    Avoid updating last access times?
    Buffer writes to filesystem?
    Allow execution of binaries?
    Allow users to mount this filesystem?

I can find no documentation that is clear about what options to apply. 
I found a nice comprehensive site with security-related info:

[http://www.linuxtopia.org/online_books/linux_administrators_security_guide/02_Linux_Installation.html]("http://www.linuxtopia.org/online_books/linux_administrators_security_guide/02_Linux_Installation.html")

that seems to make sense, but when I followed the recommended security settings for /, /boot & /home, the whole system was screwed up and it took me 2 days to recover. :frown:

Can anyone point me in the right direction?

Thanks in advance.

---

### Post by stphnlee on 2010-12-08
I found a useful book about Webmin for free in Google Books. It's called "Managing Linux Systems with Webmin" by Jamie Cameron. I haven't looked for the answer to your specific question in there, but I remember that there are lots of useful tips.

---

