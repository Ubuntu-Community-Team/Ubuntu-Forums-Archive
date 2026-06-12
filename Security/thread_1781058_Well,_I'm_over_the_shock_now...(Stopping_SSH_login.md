---
title: "Well, I'm over the shock now...(Stopping SSH logins)"
date: 2011-06-12
forum: Security
---

### Post by Thewhistlingwind on 2011-06-12
I just tried out SSH on my laptop, to find that it worked. Now for certain computers (Those not networked to the internet) I have no problem with SSH access. However, seeing that my laptop is on the net 24/7, being able to SSH in gave me a minor panic fit.

What steps would I take to disable SSH functionality? (Remove the daemon at startup?)

EDIT: Firewall stopped it after re-enabling, apparently it was off, I'm still confused though, isn't there a difference between client-ssh and server-ssh?
EDIT2: Removing startup daemon didn't work.
EDIT3: To be more clear, UFW is not enabled by default, I thought there were no listening services in default ubuntu, so I must have installed ssh-server at some point, whats the actual program called so I can remove it?

---

### Post by cariboo on 2011-06-13
The name of the ssh server is openssh-server, you can remove it using any of the usual suspects. The default install does have cups listening on port 631, on ip address 127.0.0.1

---

### Post by BkkBonanza on 2011-06-13
You can use 

sudo update-rc.d -f ssh remove

to disable ssh from starting at boot in case you want to enable it again later. But to remove it fully you can use,

sudo apt-get remove openssh-server

openssh-server is not installed in a default install so should not have been there unless you chose to install it at some point.

---

### Post by HermanAB on 2011-06-14
Howdy,

SSH is secure.  You only need to panick about it if you are in a habit of using short insecure passwords, in which case you should have your Geek license revoked.

---

