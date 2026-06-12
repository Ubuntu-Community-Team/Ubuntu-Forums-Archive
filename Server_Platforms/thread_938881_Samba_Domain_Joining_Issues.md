---
title: "Samba Domain Joining Issues"
date: 2008-10-05
forum: Server Platforms
---

### Post by ssavoy on 2008-10-05
Hi all,

I've installed Ubuntu server 8.04.1 here, and configured Samba for file sharing. It seems permissions and sharing is working just the way I want it to, but I can't seem to join Windows clients to the domain. 

When I enter the domain, it asks me for the username/password to join the domain, but then it gives me this error:

[IMG]https://dl.getdropbox.com/u/121069/NotFound.JPG[/IMG]

I've made sure to use the "sudo smbpasswd -a username" command for both root and my username. When trying to join using root, it says Access is Denied.

Otherwise permissions work fine if I'm just browsing shares.

---

### Post by Drezard on 2008-10-05
Samba is not an LDAP server! You need to look up installing Slapd/OpenLDAP with ubuntu then configure Samba with that.

Daniel

---

### Post by tbeehler on 2008-10-29
Does the user exist in the Samba database?  If not, you can add a user by using the command "smbpasswd -a username" without the quotes.

I assume that the user exists already on the Ubuntu machine as a regular user correct?

Also, I forget what group the user has to be off the top of my head, but I think the Savoy user has to have root level access to be able to add machines to the domain.  Don't quote me on that though.  It's late and my memory is a bit fuzzy. :)

Hope that helps you out!

---

### Post by uzi09 on 2009-01-30
Hey.

That particular error means that your machine is not added as a user on your domain controller.

Try the following command(s):
First you need to have a new group for machines:
```

sudo groupadd machines

```

Then add an account for the machine itself on your pdc (this supposes that you are using the passwd file for your samba users/passwords):
```
sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false machine_name_here$
```

Hope that works!

---

