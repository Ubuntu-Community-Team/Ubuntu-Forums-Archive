---
title: "ldap"
date: 2009-07-10
forum: Server Platforms
---

### Post by xandrex on 2009-07-10
Hello,

I am trying to install ldap on my new ubuntu server [I]Jaunty but I don't have an internet connection.  I was able to ftp the .deb slap and ldap-utils files onto the server.  When I run a dpkg -i  slapd_2.4.15-1ubuntu3_amd64.deb, it comes up with a gui asking me for the admin password, i put it in, then it fails and goes back to the prompt.  It says it is missing dependencies.

I guesss my questions is, what is the best way to install this ldap server without an internet connection?

Thank you,
[/I]

---

### Post by xandrex on 2009-07-14
No ones got nothing huh?

---

### Post by Cheesemill on 2009-07-14
Take a look at [Keryx]("http://keryxproject.org/")

---

### Post by giggins on 2009-07-14
You might have foobar'd the config or openldap's database. Try using this:

```
sudo dpkg-reconfigure slapd
```Then follow the prompts. If that doesn't work, maybe something else is broken. You can try this:

```
sudo cp -r /etc/ldap/slapd.d /etc/ldap/slapd.d_broken
sudo apt-get purge slapd
sudo dpkg -i slapd_2.4.15-1ubuntu3_amd64.deb
```

---

