---
title: "Ubuntu MAAS login NOT working"
date: 2015-07-24
forum: Virtualisation
---

### Post by haripriya2 on 2015-07-24
I installed ubuntu maas in a vagrant box and did the port forwarding setup.
On accessing the web interface only nodes link is available.

I also have the pxe images not found warning in the UI. Tried to import PXE images and was completed but still the warning message persists and no other links available.

I did some research and found something can be done by logging in here  : [https://maas.ubuntu.com/docs/maascli.html#cli](https://maas.ubuntu.com/docs/maascli.html#cli).

My web UI is similar to one in the above link.
They asked to login to API using 
maas login <profile-name> <hostname> <key>

[COLOR=#222222][FONT=Verdana]But I am getting unknown command login.[/FONT][/COLOR]Then I tried with maas-cli login <profile-name> <hostname> <key> and I am getting error saying connection refused. 


```
vagrant@precise32:~$ maas-cli login root http://localhost:8081/MAAS/api/1.0/auth vNjxR3wUuesrFkakLu:Kbxr5YHsSQkZy6mtLP:Bk4Wq3QzWrmTg6LvGe83j4uBzTvUmar7
usage: /usr/lib/python2.7/dist-packages/maascli/__main__.py [-h] COMMAND ...
/usr/lib/python2.7/dist-packages/maascli/__main__.py: error: [Errno 111] Connection refused





```


Am I doing something wrong? please help me..

My goal is to setup a node and use maas API to do its powercycle.

My host machine is ubuntu 14.04

---

### Post by haripriya2 on 2015-08-04
This was a usage issue.

Fixed this by correcting the API URL.

The URL should be [http://localhost/MAAS/api/1.0](http://localhost/MAAS/api/1.0) (no need of port - which we set to access MAAS UI from outside. Since we are trying login inside maas box port is not needed).

Usage will be : maas login <profilename> [http://localhost/MAAS/api/1.0](http://localhost/MAAS/api/1.0) <key>

You will be logged in with a new profilename <profilename>

---

