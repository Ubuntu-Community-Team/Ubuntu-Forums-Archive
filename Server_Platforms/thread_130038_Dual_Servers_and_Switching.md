---
title: "Dual Servers and Switching"
date: 2006-02-15
forum: Server Platforms
---

### Post by Stryker777 on 2006-02-15
I have dual servers running.  Both full copies of each other.  
What I am wanting to do is figure out the best way to switch between them if the main goes down.
Any input would be great!
Here is the method i am currently working on just because I dont know anyone that has done it.

Im putting the control in my firewall server and having the script check the status of the both servers once per minute.  If the main server is not replying but the secondary is, the iptables forward entry gets changed so all requests to 22.22.22.22 get forwarded to 22.22.22.23 instead and it still continues running the checks.  When the main comes back up, the next scan will get a response and reset the entry so 22.22.22.22 goes to 22.22.22.22.

Is this doable or is there a better way?
Thanks

---

### Post by Stryker777 on 2006-02-16
Is anyone else running dual servers with one as a backup that gets automatically switched?  If so, what method or software are you using?
Thanks

---

