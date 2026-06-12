---
title: "[SOLVED] Setting Apache2 Password"
date: 2008-08-04
forum: Server Platforms
---

### Post by archmage258 on 2008-08-04
Hi all,

I am running a Apache2 and am using mod-musicindex to share my music via my intranet.  I have been thinking about opening a port on my router to let me access my music from the internet but am concerned about security.  Is there some way for me to require internet users to be prompted for a password and intranet users just be let on?

Thanks!

---

### Post by bukwirm on 2008-08-04
You might want to start looking [here]("http://httpd.apache.org/docs/2.2/howto/auth.html").

---

### Post by archmage258 on 2008-08-04
Thanks for the quick response; unfortunately that is the page that I used to set up a test authentication page but I cannot find anywhere where it has instructions on how to auto-login (or just bypass the login) for a LAN account.

---

### Post by windependence on 2008-08-05
Save the password in your browser?

-Tim

---

### Post by hyper_ch on 2008-08-05
you could create an index.php page that will first require a login and after a successfull login show the directory listing. That's not "truly" safe as it can be circumvented. Best is to operate with .htaccess and auth.

---

### Post by archmage258 on 2008-08-05
Awesome; thanks for all the reply.  I'll give that a shot.

---

