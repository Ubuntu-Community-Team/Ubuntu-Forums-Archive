---
title: "MySQL all of a sudden won't login?"
date: 2012-09-22
forum: Server Platforms
---

### Post by cesar98026 on 2012-09-22
Today I woke up and tried checking my email. Guess what? It didn't work. I've got it traced to the SQL database, it turns out I can't log in from PhpmyAdmin(error #1045) but I can log in on the CLI. I have a mail server running Postfix, Courier and MySQL. It's a production server, so I need help [I][B]fast.:confused: 
[/B][/I]

---

### Post by Ms. Daisy on 2012-09-23
So the MySQL database is directly facing the web then?

---

### Post by cesar98026 on 2012-09-23
I don't think so. The network name is localhost.

---

### Post by sffvba[e0rt on 2012-09-23
*Thread moved to **Server Platforms**.*


404

---

### Post by cesar98026 on 2012-09-27
I've narrowed it down to phpmyadmin and roundcube webmail. PHP can connect to the database just fine but phpmyadmin still displays error #1045 and roundcube says the username/password is incorrect.:guitar:

---

### Post by d4m1r on 2012-09-28
Are phpmyadmin/roundcube using the same username you manually tried logging in with? Try changing the users password on the account and see if it fixes it for both.

---

