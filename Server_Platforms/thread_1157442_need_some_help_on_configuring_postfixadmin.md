---
title: "need some help on configuring postfixadmin"
date: 2009-05-12
forum: Server Platforms
---

### Post by kustomjs on 2009-05-12
Hi Guys

I need some help on configuring postfixadmin I get to the setup page but everytime I try to create a superadmin I get this stupid error message"Setup password not specified correctly

If you want to use the password you entered as setup password, edit config.inc.php and set

$CONF['setup_password'] = '6349e9f396e9100370c15182f780f4f0:8885300cfaf8ec8fb7f76ff08de436bc28f41d2a';"


how can I fix that?

---

### Post by a9k3d on 2009-05-14
It's been a few months since I last setup a postfixadmin and I didn't encounter that setup variable nor is it in my config.inc.php. 

Have you manually edited the config.inc.php yet? I had to set all the DB related stuff like $CONF['database_password'] etc. 

It is absolutely critical that the DB connection works before trying to make superadmins. You may find php errors in /var/log/apache2/error.log that show the database problem.

---

