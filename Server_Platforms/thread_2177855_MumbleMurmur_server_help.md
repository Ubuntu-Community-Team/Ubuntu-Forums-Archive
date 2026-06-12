---
title: "Mumble/Murmur server help"
date: 2013-09-30
forum: Server Platforms
---

### Post by Eyeball114 on 2013-09-30
I had a mumble server running just fine on my home server today. The server went down and when I manually launched it a new mumble server popped up instead of the one that I have been using and is already configured. 

I started the server with murmurd as directed by someone else. I see now they were wrong. I decided to delete mumble and just start over

I did:
sudo  apt-get remove --purge mumble-server

But the server still ran. So Im thinking there is another instance of the server running somewhere but I can not locate it.
There is nothing about mumble in /var/log

Anyone know where another instance of mumble may be and how to get rid of it?

EDIT:

Oh also today I added 8gb more of ram and a dedicated network card. Could the card have caused the issue?

---

### Post by The Cog on 2013-09-30
The executable is /usr/sbin/murmurd so you can search for that:
```
ps -ef | grep murmurd
```
and if it's there, you should also see what ini file it used. You should be able to kill it with the command
```
sudo killall -9 murmurd
```

---

### Post by Eyeball114 on 2013-09-30
Worked great thank you so much!

---

