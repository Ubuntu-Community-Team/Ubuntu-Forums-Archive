---
title: "Enable History on Unbuntu Server"
date: 2007-06-12
forum: Server Platforms
---

### Post by Shocm on 2007-06-12
Just curious, I am working on an Ubuntu Server and want to enable history on certain user accounts. Can someone point me in the right direction on how to do this.

---

### Post by Wardazo on 2007-06-12
Hi

Not quite sure what you mean. Many server actions are logged to the /var/log directory,like pages served by apache,  ssh login attempts, ftp server events... and much much more

Have a poke around there. You might find what you're looking for.

---

### Post by Shocm on 2007-06-12
Sorry, in re-reading my question I guess it doesn't make sense... OK when a user logs in and does a bunch of actions in bash it is recorder bash_history. Then they can run the command >history and see all the commands they've ran. Right now, the way Ubuntu Server is set up, once that user logs out and back in they loose the bash history. How can I enable it to stick around between log ins.  

Does that make a little more sense?

---

### Post by Wardazo on 2007-06-12
By default everyone's bash history is 500 lines. I mean you can always go back 500 commands. This continues accross sessions.

If you want to increase it for every user (say 1000 lines )then edit  /etc/bash.bashrc to include the following line at the end:

> export HISTSIZE=1000

This will take effect once your session is closed

You must restart your session. 

... to check that your history quota has indeed been increased:

> env



Each users's history is by default stored in their home directory. If you can sudo you have access to everyone's history.

---

