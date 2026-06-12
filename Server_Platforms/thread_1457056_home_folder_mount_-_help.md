---
title: "home folder mount - help"
date: 2010-04-18
forum: Server Platforms
---

### Post by macpraveen on 2010-04-18
Hi
I hope you people can help me on this.

Basically I am trying to setup a small network (for testing purposes) where 5 Ubuntu desktops (9.10) are connected to a Ubuntu Server (9.10) through a wireless router. Server is connected to router through lan. Clients are connected through netgear wireless pci adapter.

I am looking to create a roaming profile where the home folders are stored on the server and the clients authenticate using ldap. On authentication the home folder gets mounted.

I am done setting up LDAP on server using openLDAP and the client authentication is working pretty well.

Now I need the home folder to get mounted on login. I configured pam-mount on one of my client but i am unsuccessful. I see "CIFS VFS mount failed status -111" on /var/log/syslog

Can anyone pls clarify on these ?

- Should I need to install samba on the server for this setup? (this is total linux environment)

- If so, should samba and ldap talk to each other?

- Should I need create users and groups in ldap as well as in linux user accounts?

- Once ldap authenticates client, in terminal, i am not getting the logged in username displayed properly at username@machinename:$ prompt. I am getting sudo username displayed. what is wrong in this?

- and finally what is that cifs mount return status -111

Sorry for asking so many questions but I am new to linux and trying out a few options for my project.

Thanks
Praveen

---

### Post by macpraveen on 2010-04-18
any one pls?

---

