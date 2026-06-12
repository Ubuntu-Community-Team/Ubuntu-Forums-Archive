---
title: "403 Forbidden - You don't have permission to access / on this server."
date: 2011-09-26
forum: Security
---

### Post by giolicious on 2011-09-26
Yesterday, i installed Ubuntu Server 11.04 on my home PC coz i wanted what its like to host my own site. :) Everything went well with the installation. The only problem i can't seem to solve right now is the error i get when viewing my site on the web.

I get this:
> Forbidden

You don't have permission to access / on this server.
Apache/2.2.17 (Ubuntu) Server at 192.168.1.101 Port 80

i have already tried using chmod 755 but i still have the error above. Weird thing though is **_i can view the site normally when a user is logged on the server_**.

Any ideas?

---

### Post by tgm4883 on 2011-09-27
> **giolicious said:**
> Yesterday, i installed Ubuntu Server 11.04 on my home PC coz i wanted what its like to host my own site. :) Everything went well with the installation. The only problem i can't seem to solve right now is the error i get when viewing my site on the web.

I get this:


i have already tried using chmod 755 but i still have the error above. Weird thing though is **_i can view the site normally when a user is logged on the server_**.

Any ideas?

Where are the files for your site stored on your computer? Are they in your home directory? Did you encrypt your home directory?

---

### Post by giolicious on 2011-09-28
files are located at /home/username/ and yes i have chosen to encrypt my home folder during the installation.

---

### Post by tgm4883 on 2011-09-28
> **giolicious said:**
> files are located at /home/username/ and yes i have chosen to encrypt my home folder during the installation.

That's the issue then. When no user is logged in, the files are encrypted. When you log in, they are no longer encrypted. Move them outside of the encrypted area.

---

