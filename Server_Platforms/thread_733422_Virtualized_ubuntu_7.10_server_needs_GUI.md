---
title: "Virtualized ubuntu 7.10 server needs GUI"
date: 2008-03-23
forum: Server Platforms
---

### Post by fpellegrini on 2008-03-23
Ok,
I know a server should never need a GUI, BUT....
...my ruby on rails stack is on ubuntu 7.10, all is clean and fine until the day i need to add a new application (ruby on rails app) thet needs to access data stored in an IBM iSeries DB2.
In order to do that, IBM DB2 Connect Personal Edition must be installed on my server: this will allow connectivity to the IBM DB2 from ROR apps.
And here we have the surprise: the setup procedure for IBM DB2 Connect PE works only on a system with a GUI.
The problem would be simple to solve: go and install Gnome or KDE, but:  the ubuntu server is a virtualized server running under Vmware server, so where the GUI will run after installation?
:confused:
Please help me get out of this nightmare before I scratch the whole thing and sadly return to windows.#-o... (if you ask me to install DB2 by command line my answer will be: tell me how! It is undocumented, and if it is documented it is very well hidden...)

---

### Post by twright on 2008-03-23
you can try installing fluxbox (very lightweight + very few dependencies to mess up your server)
```
sudo apt-get install fluxbox
```

you can remotely use the gui via the vmware server client

the gui would run on the virtualized server

---

