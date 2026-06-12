---
title: "pppoe"
date: 2010-10-14
forum: Server Platforms
---

### Post by expatCM on 2010-10-14
I use pppoe together with monit on my server to manage my adsl connection - I use the router in bridge mode to the server.

All was well until yesterday.  My ISP asked me to change my subscription package which I did.  The problem that appeared was that they needed to give me a new username and password.  I ran pppoeconf and the changes were made.

What happens now is that when I start up the server pppoe starts automatically (as part of the system startup) and connects to the Internet and then stops.  The connected DNS information is echoed to screen but the server loading halts.  I then have to press Ctrl-C and the server continues loading and at the very end of the process monit makes the Internet connection.  The process ends with the prompt to login to the server which is normal.

What I would like to work out is how to stop the pppoe process from starting half way through the server startup since it seems to me that monit can handle this.  Any ideas?

---

