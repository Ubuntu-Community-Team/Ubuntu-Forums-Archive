---
title: "transmission daemon start stop restart"
date: 2010-06-25
forum: Server Platforms
---

### Post by mchlor on 2010-06-25
System: lucid x86 server.

greetings

goal: install and run latest transmission-daemon with web rpc.

transmission-daemon 2.0 installed fine, rpc runs.  No problems  except one.  How do I get this to start automatically upon boot?  Transmission-daemon start/stop/restart script is already there(etc/init.d/).
?
thx

---

### Post by jbrown96 on 2010-06-25
If you can run ```
sudo service transmission status
``` and get back something besides "unrecognized service," then you should be able to do the following. Note that you may have to change transmission slightly in the above command. It should be whatever name is listed in /etc/init.d/

For example, openssh-server is called ssh and on some distros sshd. You have to mess around with it a little. This can help ```
sudo service --status-all
```

Once you find it, then you will need to install chkconfig ```
sudo apt-get install chkconfig
``` Then run ```
sudo chkconfig transmission on
``` substitute transmission if it is named differently.

---

### Post by mchlor on 2010-06-25
thank you for the reply,

transmission-daemon does not respond to services on request from chkconfig

```
insserv: exiting now without changing boot order!
/sbin/insserv failed, exit code 1
```

However manual start using the old ways, ```
sudo /etc/init.d/transmission-daemon start
``` works perfectly.

---

### Post by mchlor on 2010-06-25
Solved.  For future fellow n00bs.

answer : [http://www.debuntu.org/how-to-manage-services-with-update-rc.d]("http://www.debuntu.org/how-to-manage-services-with-update-rc.d")

---

