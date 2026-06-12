---
title: "Locking users in home directory"
date: 2007-03-29
forum: Server Platforms
---

### Post by dlichterman on 2007-03-29
Hello everyone.  Newbie here, just set up 6.10 server as a web server at school.  I just figured out how to do virtual hosting, and my next step was creating some more users with their own websites.  What I want to do is jail the users into their home directory.  I see that there is chroot, but don't know exactly where to go from there.  We will be using SSH and SFTP for file transfer not FTP.

Thanks
-Daniel

---

### Post by wayne_za on 2007-03-29
"Chrooted SSH HowTo"

Your users will be jailed in a specific directory which they will not be able to break out of.


see this how-to on the howtoforge page some useful stuff here!
[Howto]("http://www.howtoforge.com/chrooted_ssh_howto_debian")

---

### Post by wayne_za on 2007-03-30
Also see this link

[Jail users]("http://www.ubuntuforums.org/showthread.php?t=367573&highlight=jail")

---

