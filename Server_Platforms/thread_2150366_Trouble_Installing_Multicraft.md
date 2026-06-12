---
title: "Trouble Installing Multicraft"
date: 2013-05-31
forum: Server Platforms
---

### Post by TheMattVid on 2013-05-31
[FONT=Helvetica Neue]I have been following these directions to get Multicraft on my ubuntu VPS server by following the Linux directions:[/FONT]
[www.multicraft.org/site/page?view=install]("http://www.multicraft.org/site/page?view=install")

[FONT=Helvetica Neue]To continue, I need to initialize the database with:[/FONT]
[http://your.address/multicraft/](http://your.address/multicraft/)

[FONT=Helvetica Neue]The problem is, when I substitute "your.address" for the ip address of the VPS server, it just says that it cannot connect.[/FONT]

[FONT=Helvetica Neue]What am I doing incorrectly?[/FONT]

---

### Post by cj13579 on 2013-06-07
Perhaps these two instructions are in the wrong order:
> 
The setup script will tell you what to do next, here's a summary of that:
  -  Access the control panel under [http://your.address/multicraft/](http://your.address/multicraft/), it will start the front end installer
  -  Start the daemon (the setup script shows the command for that: "<multicraft dir>/bin/multicraft -v start")


Try starting the Multicraft daemon and then accessing the control panel through your browser.

---

