---
title: "Help setting up Web/Home media server"
date: 2011-03-12
forum: Server Platforms
---

### Post by thursdayy on 2011-03-12
I am looking to run a home media server that also lets me play around with a test development for my web programming.

What I want the server to do:

[LIST]
[*]Able to recognize on Mac (AFP)
[*]Able to recognize on Windows (SMB)
[*]Able to use the same user/pass to the same directory using either AFP or SMB
[LIST]
[*]For example, user1 has access to /home/user1/* when logging through AFP or SMB [same credentials] but also has access to a public share called /home/home that is public to anyone on the network with a user/password
[/LIST]
 
[*]Able to run FireFly Media Server for iTunes streaming
[*]Able to run SSH / SFTP to give remote access to a user's directory
[LIST]
[*]For example, user1 can remotely SSH/SFTP to /home/user1/* from the internet
[/LIST]
 
[*]Able to run SubVersion for version control
[*]Able to run Apache / MySQL/ PHP in conjunction with SubVersion
[/LIST]
So far, I have installed all of these packages separately but find it very hard to manage.  I was wondering if someone had an easier solution to this problem.  I basically want to set it up as a test development server with my home media needs.  Any guidance on this would be greatly appreciated

---

