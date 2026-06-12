---
title: "Openstack Horizon issues"
date: 2018-04-20
forum: Virtualisation
---

### Post by quartzeye on 2018-04-20
All,
  I am at a loss to resolve this issue.  I have a clean install of Openstack using LXD on a 16.04 VM using conjure-up.  The install had no issues and I followed the tutorial as well as matching instructions found on the internet.  I created an iptables rule to map the server ip to the Horizon dashboard but when I go to the Horizon dashboard and use the default credentials of u: admin p: openstack d: admin I get an invalid credentials error.  I even installed a desktop on the server and tried to access the dashboard from the server and got the same error when logging in.  I also rebuilt my VM from scratch and reinstalled Openstack three times with the same results.  These are the same steps I used a few months ago with the Pike release of Openstack and they worked then.

There must be something wrong in the setup of the Openstack environment that is not correctly configuring the credentials, the instructions are incomplete, or the UID/PWD/Domain listed as default is incorrect.  I am new to Openstack and I am trying to learn how to work with in the environment but if I cannot log in, I cannot learn.

Can anyone tell me how to fix this!

Set-up Links
[https://www.ubuntu.com/download/cloud/try-openstack](https://www.ubuntu.com/download/cloud/try-openstack)

and

[https://insights.ubuntu.com/2018/02/02/tutorial-install-single-server-openstack-with-conjure-up](https://insights.ubuntu.com/2018/02/02/tutorial-install-single-server-openstack-with-conjure-up)

Install Complete Screenshot
[IMG]/home/glzavert/Pictures/Selection_453.png[/IMG]

Iptables rule to get to the dashboard

sudo iptables -t nat -I PREROUTING -i ens33 -p TCP -d 192.168.62.50/32 --dport 80 -j DNAT --to-destination 10.42.107.103:80

Dashboard
[IMG]/home/glzavert/Pictures/Selection_454.png[/IMG]

---

### Post by quartzeye on 2018-04-20
So I figured it out, the domain is admin_domain.  The image shows the correct domain but doesn't display the "underbar".  That is a common issue with terminals, in the future,I would recommend using special characters that do not display consistently across termial emulators.

---

