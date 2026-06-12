---
title: "OpenVAS plugin problem"
date: 2009-09-17
forum: Security
---

### Post by thorosius on 2009-09-17
Hi,

I have just started using the OpenVAS-Client GUI. The problem is that for every scan I do it reloads the whole plugin database. Which takes about 7-8 minutes on my machine. I want it to just load it once. Is that possible. Am I missing some option.:confused:

---

### Post by shayno90 on 2012-01-09
> **thorosius said:**
> Hi,

I have just started using the OpenVAS-Client GUI. The problem is that for every scan I do it reloads the whole plugin database. Which takes about 7-8 minutes on my machine. I want it to just load it once. Is that possible. Am I missing some option.:confused:

I would run greenbone security assistant via http instead of the client by loading all the certificates and plugins before you can do any scan. When you openvas check setup, it will detail any potential errors. Run this:

test -e /var/lib/openvas/CA/cacert.pem || sudo openvas-mkcert -q
sudo openvas-nvt-sync --wget
test -e /var/lib/openvas/users/om || sudo openvas-mkcert-client -n om -i
sudo /etc/init.d/openvas-manager stop
sudo /etc/init.d/openvas-scanner stop
sudo touch sudo touch /var/lib/openvas/mgr/tasks.db
sudo chmod 600 /var/lib/openvas/mgr/tasks.db
sudo openvassd
sudo openvasmd --migrate
sudo openvasmd --rebuild
sudo killall openvassd
sleep 15
sudo /etc/init.d/openvas-scanner start
sudo /etc/init.d/openvas-manager start
sudo /etc/init.d/openvas-administrator restart
sudo gsad 

Ensure you have already setup an admin and user account, if not add this command before "sudo gsad":
test -e /var/lib/openvas/users/admin || sudo openvasad -c add_user -n admin -r Admin

---

