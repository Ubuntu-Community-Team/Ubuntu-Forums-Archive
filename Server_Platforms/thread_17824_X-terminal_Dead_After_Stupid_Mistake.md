---
title: "X-terminal Dead After Stupid Mistake"
date: 2005-03-03
forum: Server Platforms
---

### Post by Jeffredo on 2005-03-03
Hello everyone.  They say a little knowledge is a dangerous thing and I'm living proof!  Being very new to Linux (two weeks) and not understanding the whole sudo/root thing well I was changing ownership of files outside of /home to my user name.  I chown'd /usr and now the x- terminal and Synaptic won't start  ("Failed to run /usr/bin/x-terminal-emulator as user root:").  I enabled a root password in recovery mode, but it won't work either.  I'm so ignorant I have no idea where to go from here (and it's probably and easy fix!).  If anyone can get me out of this mess I would really appreciate it!

---

### Post by JmSchanck on 2005-03-04
In changing the permission of those files to yourself, you've taken them away from root, so the easy fix is just to chown them back to root.

---

### Post by Jeffredo on 2005-03-04
It was really strange.  I went into recovery mode and did that, but it still wouldn't let me log in to a terminal or anything else.  Being it was a fresh install of Ubuntu I didn't have a lot invested in it yet, so I reinstalled it today and set up a root password and user password and learned that $sudo su; passwd  "" will let me do any software installation I want without trouble.

Thanks for the reply.  I have a lot to learn!  :lol: (I hope you all don't get tired of beginners like me!).

---

### Post by bored2k on 2005-03-04
[QUOTE=Jeffredo]It was really strange.  I went into recovery mode and did that, but it still wouldn't let me log in to a terminal or anything else.  Being it was a fresh install of Ubuntu I didn't have a lot invested in it yet, so I reinstalled it today and set up a root password and user password and learned that sudo su;passwrd "" will let me do any software installation I want without trouble.

Thanks for the reply.  I have a lot to learn!  :lol: (I hope you all don't get tired of beginners like me!).[/QUOTE]
[guide](http://www.ubuntuguide.com)

---

### Post by Marquis_de_Carabas on 2005-03-04
[QUOTE=bored2k][guide](http://www.ubuntuguide.com)[/QUOTE]

Your link's slightly wrong. It should be [http://www.ubuntuguide.org](http://www.ubuntuguide.org) not .com.

---

