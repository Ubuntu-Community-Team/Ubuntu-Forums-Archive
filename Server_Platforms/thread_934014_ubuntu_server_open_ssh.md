---
title: "ubuntu server open ssh"
date: 2008-09-30
forum: Server Platforms
---

### Post by nvysel24 on 2008-09-30
just had a quick ? since im a nub at this but what is the command to add a user to open ssh. and when i add them how can i set their permissions

---

### Post by bluefrog on 2008-09-30
unless specifically told (man sshd_config) all users of your system can ssh in.

also: [http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

---

### Post by nvysel24 on 2008-09-30
ok well i got the adduser command down now...i jus need help logging in. this ubuntu server is a virtual machine w/ the open ssh
so i open up putty put in the ip of the server and it asks to login when i log in it says access denied!?!!? ive created a test user w/ password testing and i tried my sudo account so yeah... i would ask my friend tony right now but hes not online :(

---

### Post by cariboo on 2008-09-30
Did you also create the new user on the server?

Jim

---

### Post by nvysel24 on 2008-09-30
no i actually did not want to create users for them to access the actual computer. i want them to access open ssh so i can have a proxy. by tunneling into it

---

### Post by lazyart on 2008-09-30
so what user name and password are you using to connect with?  You need an account on the server to log in with...

---

### Post by nvysel24 on 2008-09-30
well my u- david p-Powerof10tothemax!
and i tried that and it said access denied i even tried creating a serperate account u- test p- testing
still nothing do u have to create special accounts for the open ssh ?

---

### Post by Iowan on 2008-10-01
You can use SSH to log in to the server as a server user - meaning the user must (already) have an account on the server. SSH (by itself) does not have users (or accounts). Is that shedding light - or adding to confusion?

---

### Post by windependence on 2008-10-02
Iowan is correct here, you must have an account on the server to be able to log on to it, so you will have to add a user to your server to be able to get in.

-Tim

---

