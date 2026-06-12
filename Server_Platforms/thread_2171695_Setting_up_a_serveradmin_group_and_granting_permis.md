---
title: "Setting up a serveradmin group and granting permissions"
date: 2013-09-01
forum: Server Platforms
---

### Post by Stefan_Luksch on 2013-09-01
Hi community,


I've been trying to set up a server admin group which has the permission on two servers on my Ubuntu.
But setting that up blew my mind.. I hope you can give me somewhat like a tutorial for my problem.


Example:
The name of the group is **srvadmin**.
There are two servers on the OS which are created through "adduser **server1**" and "adduser **server2**" with their homes.
The administrative account which is created at the installation, called "**admin**", is in this **srvadmin **group via "*usermod -aG [groupname] [username]*".
This group **srvadmin **should have all the rights which **server1 **and **server2 **have in their homes.
(That means starting and stopping the server and configure their files.)

Would be kind if someone takes his time to explain me how set this up! :)

Thanks in advance
Stefan.

---

### Post by TheFu on 2013-09-01
What specific sorts of tasks will these people need?

If you need specific people to be able to manage servers, but want to limit what they can do, use **sudo** and the **sudoers** file. I'd done some really advanced stuff with sudoers - plus everything gets logged by individual.

If you need application-specific accounts, fine, but force people to remote in using their own credentials, then only allow a **sudo -u app-account** command.  It would be better to limit them to specific commands instead of providing a completely new account. sudo can handle that too - be certain to create aliases for the "approved" commands, so the users don't get too frustrated trying all sorts of things that do not work.
```
man sudo 
man sudoers
```
will explain the details. Edit the sudoers file with **visudo** - so the grammar can be checked.

Allowing users to have shared access to an account without logging every command is most definitely NOT a best practice.
Of course, you might have needs that I don't understand.

---

