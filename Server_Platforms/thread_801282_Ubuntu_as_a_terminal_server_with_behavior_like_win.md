---
title: "Ubuntu as a terminal server with behavior like windows remote desktop?"
date: 2008-05-20
forum: Server Platforms
---

### Post by airbornespent on 2008-05-20
How can I have Ubuntu setup as a terminal server where connections can be suspended and resumed from any computer?

A colleague and I need to set up a terminal server for us to remotely login to a GUI to work. He wants to use Windows server I want to use Ubuntu. 
His argument for Windows is the way in which remote desktop works: your session is persistent and no-matter what machine or where you login from, you get the same session.
I know X over SSH is not persistent. I have used NX for persistent connections, but, I've only gotten NX to remain persistent on one client machine at a time; when I disconnect from the NX server, I could login from that machine again and be where I left off. When I disconnect and login to the NX server from another machine with the same username, a NEW session is created!
How can I have Ubuntu setup as a terminal server where connections can be suspended and resumed from any computer?

---

### Post by bluefrog on 2008-05-20
Open a session on the server, enable remote desktop and then connect to it via vnc over ssh

---

