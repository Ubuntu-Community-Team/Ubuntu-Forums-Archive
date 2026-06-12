---
title: "Apache-php"
date: 2008-09-14
forum: Server Platforms
---

### Post by captbaritone on 2008-09-14
I am running Ubuntu Server edition with the default LAMP installation. My problem is this:

When I request a .php file which executes a shell_exec(), the server will not process another php file until the shell command has finished processing. For example, I have a php script which executes zip and returns the binary file. Currently, this grinds my web server to a standstill until the zip command is finished executing. 

Any ideas how one might remedy this situation?

---

