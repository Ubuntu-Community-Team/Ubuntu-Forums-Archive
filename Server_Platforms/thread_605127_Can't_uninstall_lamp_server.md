---
title: "Can't uninstall lamp server"
date: 2007-11-06
forum: Server Platforms
---

### Post by mrblue182 on 2007-11-06
I have searched the forums far and wide for a similar problem, and have yet to find one, so here it goes.

I installed a lamp server using [this tutorial]("http://www.howtoforge.com/ubuntu_debian_lamp_server"). I then found out that xampp has a linux version (I used it on windows) and so I uninstalled my old lamp server (I apt-get remove --purge 'ed everything i downloaded) and then attempted to install the xampp server, but the xampp server couldn't be started because the old server was still up, I have no idea what to do now. Any help would be appreciated.

---

### Post by ardchoille42 on 2007-11-06
"lamp" is technically not a server.. it stands for [COLOR="Red"]L[/COLOR]inux [COLOR="Red"]A[/COLOR]pache [COLOR="Red"]M[/COLOR]ysql [COLOR="Red"]P[/COLOR]hp.

You can uninstall Apache, MySQL and Php and that would effectively remove those components, but there is no "lamp server" to remove.

---

### Post by mrblue182 on 2007-11-06
Yeah, I know that lamp means linux apache mysql and php, but i can't completely uninstall the server. When i try to browse to localhost, it get a 404 w/ this written at the bottom

Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at localhost Port 80

which leads me to believe that apache and php are still installed, even though i apt-get remove --purge 'ed them

---

### Post by mrblue182 on 2007-11-08
Okay, I fixed my problem. I no longer need help with this.

---

### Post by enchance on 2007-11-16
How were you able to fix it? I have the same problem.

---

### Post by armen_shlang on 2007-12-31
Yeah seriously man. I'm seeing alot of people who are having problem with this, incuding me. can you help us?

ardchoille42, you didn't say how to fix this problem.

---

### Post by pamepros on 2008-07-16
I have the same problem, can you tell us what you did to solve it? any of you...

---

### Post by mrblue182 on 2008-07-18
Sorry, forgot I even had this post. I uninstalled all of the items, but then I had to restart the computer. It was the first time in months I had to completely restart.

---

