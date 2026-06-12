---
title: "Connecting Remotely to Server from Windows/Mac Clients: FreeNX, x2go...."
date: 2016-03-25
forum: Server Platforms
---

### Post by c_xy on 2016-03-25
Hello, we are currently running Ubuntu 14.04 with Mate as the Desktop environment.

The server is:  dell poweredge r730 server

We wanted to know what would be the best options for multiple users to connect remotely to the server from Windows and Mac client machines.


We've used FreeNX in the past, but read about x2go. Are there advantages to using x2go vs Freenx in terms of: speed, graphics, etc. ?

Are there better free alternatives out there?

Does VMware do the same thing as FreeNX and x2go, or does it serve a different purpose?

Also, what about commercial products that do what FreeNx and x2go do, but might have more options?


Any suggestions/recommendations would help.

Thanks,


c.

---

### Post by volkswagner on 2016-03-25
For OSX clients I would use X-forwarding SSH access.

---

### Post by c_xy on 2016-03-25
Thank you for your response.

However, we want to have a GUI like interface when we login remotely per user. If we ssh -X, you can't access icons on a desktop like you would if you connect using nomachine.

c.

---

