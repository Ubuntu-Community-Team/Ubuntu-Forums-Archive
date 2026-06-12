---
title: "RemoteApp Server"
date: 2018-08-03
forum: Server Platforms
---

### Post by markeworth on 2018-08-03
[SIZE=2][FONT=arial]Hey everyone!

As many of you know on Windows Server you can publish installed software via the native RemoteApp role. And Parallels have Remote Application Server, which must be installed on any Windows Server for the same role. Also, I know about VMware [COLOR=#6A6A6A]**Horizon**[/COLOR][COLOR=#545454] 7 as a virtual desktop, but it's required a lot of resources.[/COLOR]

Is something like RemoteApp available for Linux servers? I'll be thankful if someone can give me some links to read or maybe to watch about RemoteApp solutions on Linux OS

Thanks a lot!
[/FONT][/SIZE]

---

### Post by LHammonds on 2018-08-03
Are you talking about publishing Linux applications or are you trying to find a way around licensing for serving Windows applications?  Because you can't.

Here are some remote desktop solutions but I don't think you are looking for full desktop:

[https://www.nomachine.com/](https://www.nomachine.com/)
[http://ltsp.org/](http://ltsp.org/)
[https://www.techrepublic.com/blog/tr-dojo/set-up-a-free-and-secure-terminal-server-with-linux/](https://www.techrepublic.com/blog/tr-dojo/set-up-a-free-and-secure-terminal-server-with-linux/)
[https://www.tecmint.com/guacamole-access-remote-linux-windows-machines-via-web-browser/](https://www.tecmint.com/guacamole-access-remote-linux-windows-machines-via-web-browser/)
 * Related: [https://stackoverflow.com/questions/37661274/guacamole-on-linux-rdp-single-application](https://stackoverflow.com/questions/37661274/guacamole-on-linux-rdp-single-application)

---

### Post by markeworth on 2018-08-03
Hey LHammonds!
I need some software to publish for example Libreoffice. We use Windows RemoteApp for 1S and MS Office atm. All documents available only on our servers. Like Google Docs but on personal servers :) Now we are looking for similar software on Linux server
Guacamole so close :) I'll try it. Thanks!

---

