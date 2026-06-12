---
title: "VirtualBox Flask Server / Ubuntu 16.04 32-bit / Server stops responding periodically"
date: 2020-09-24
forum: Virtualisation
---

### Post by fstephane on 2020-09-24
I'm not sure where to post this since I don't really know if this is an issue with Flask, VirtualBox (6.0) or Ubuntu (16.04 LTS). Please let me know if this isn't an appropriate place to post.

_Intro_
My company installs Ubuntu VMs for our clients that run a local Flask web server on their system. I know Flask is not meant to be used for production, but each individual server handles about 15 users max (and often just 1 or 2) and often only one or two users at a time. So far it's been working well for dozens of clients over several months.

_Problem_
[COLOR=#242729][FONT=Arial][FONT=arial][SIZE=2]We have a couple of clients where the application becomes inaccessible in users' browsers after a certain period of time. I can SSH to the VM and see that the flask service still seems to be running without issue. But the users are not able to connect to the IP address and port of the VM via their browser like they could before (eg. *http://<vm_ip>:<port_number>*).
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=arial][SIZE=2]Restarting the service doesn't resolve the issue, but restarting the entire VM does resolve it.
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=arial][SIZE=2]The VM network adapter is set to "NAT" and it serves the Flask app on the same IP address as the host machine. When the app becomes inaccessible, I'm not able to connect to the application on the host machine using either *http://<vm_ip>:<port_number>* or *http://localhost:<port_number>*. We have this same configuration on many client systems and it works without issue for all other clients.
[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][FONT=arial][SIZE=2]Nothing should change in the application configuration when the VM restarts. All networking and port settings are static. So something is clearly getting hung up. Since the application output doesn't show anything off and the flask service seems to restart fine internally, I'm guessing the issue is with Ubuntu or VirtualBox (or something on the client machine/network).[/SIZE][/FONT][/FONT][/COLOR]

_Questions_
I'm wondering if anyone has had this issue before, where they have a working Flask server that runs very reliably in most cases, but have an instance that periodically stops responding after a certain amount of time even though the VM is accessible and flask appears to be running fine internally? Does anyone know why this might happen?

I apologize for lack of details and logs - our access to the client machine is limited

Any help or suggestions would be much appreciated!

---

### Post by TheFu on 2020-09-24
Ubuntu 16.04 support ends in about 6 months.  It is well passed time to move to a different release - really should have moved 2 yrs ago so the customers can do their migrations as well.

Virtualbox shouldn't be used for production needs.  Use KVM for virtual machines or perhaps Xen.  KVM is maintained as part of the Linux kernel, by the kernel team. It is rock solid and it used by enterprises around the world.  Do you use Amazon EC2?  That's KVM.

i've never used flask. No opinion about that. For less than 20 users, pretty much anything framework should be fine, provided the back-end DBMS isn't a toy and is ACID compliant like Postgresql.

For any troubleshooting, you'll need logs.  Create a script and include this script in all your deployments that will grab all the config files and logs from the last day, tgz them into 1 file that the client can email to you.  You don't want direct access to client machines, ever.  If your company sets up the machines, take the same tgz on the last day just before leaving so you can bill time+materials when the clients screws with the configs.  Just push your configs back and bill them 4 hours for the trouble.

Again - don't use virtualbox and don't use 16.04 anymore.  Today, deployments should be on 20.04.

---

