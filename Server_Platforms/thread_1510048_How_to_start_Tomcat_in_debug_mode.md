---
title: "How to start Tomcat in debug mode"
date: 2010-06-15
forum: Server Platforms
---

### Post by sureshatt on 2010-06-15
[LIST]
[*]Open a console
[*]Go to the tomcat home folder
[*]Issue following commands
[*]"set JPDA_ADDRESS=8000"
[*]"set JPDA_TRANSPORT=dt_socket"
[*]No go insdie the bin folder and issue the following comand
[*]"./catalina.sh jpda run"
[*]Thats all :)
[/LIST]

---

