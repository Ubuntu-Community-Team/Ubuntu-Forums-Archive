---
title: "GUI Apps to Configure Server"
date: 2008-07-08
forum: Server Platforms
---

### Post by sjrlaw on 2008-07-08
I am new to Linux and have been experimenting with a workstation/server setup trying to configure different apps on the server.  Does anyone know of some good GUI apps for configuring server apps that I can run from the workstation through an SSH connection to the server?  The apps I need to tweak are:

web server
mail server
SAMBA
print server

Thanks!

---

### Post by windependence on 2008-07-08
Well you can and should admin these directly from the command line in your SSH session. Loading a GUI on the server is not recommended. that is why Ubuntu didn't do it in the first place. 

That being said, there are some browser based utilities you can use to get started, like Webmin. I would try not to depend on them though, because they might not always be there when you have a server crash or problem. Try to learn as much CLI as you can. Don't worry, we are all here to help you 24/7/365. If you have any questions about using the command line, please don't hesitate to ask. Also, there are tons of how-to's and tutorials out on the web. Google is your friend.

-Tim

---

### Post by sjrlaw on 2008-07-09
Thanks, Tim.  I get the impression that the configuration of server apps has a lot to do with editing text files and configuration files, am I right?  If so, I can see where a GUI text editor can do that thru an SSH session from the workstation, so a GUI isn't being run on the server.  As a newbie, I was hoping for more hand holding, like a GUI app on the workstation that would help to tweak configuration files on the server.  Is there such a thing?

---

### Post by wilbbe01 on 2008-07-09
If you have ubuntu on your desktop machine you could in theory go to the Places menu, click connect to server, choose ssh as the type, login as whatever user has access to the configuration files, open them with gedit on your desktop and then save them back via your graphically connected ssh funness.  Or if in windows you could use winscp copy the files over, edit them in notepad or something then copy them back.

To me it seems like it would be a lot easier to just use nano from a terminal window.  Log in to the server via ssh, type nano [name of file you are editing] and then use that.  Nano/pico are fairly easy to learn and I find are often easier and more efficient on using than any graphical things anyway.

---

### Post by hyper_ch on 2008-07-09
you can use sshfs to map a server directory onto your machine and then use your normal/preferred text editor

---

