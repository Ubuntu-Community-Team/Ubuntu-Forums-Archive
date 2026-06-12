---
title: "ssh key login doesn't work under newly created user"
date: 2011-07-21
forum: Server Platforms
---

### Post by FabianN on 2011-07-21
Hi all,

I'm running ubuntu server 11.04 and I am unable to login to a new user that I recently created. This is the 1st user that I have created, created using the "adduser" command (so, not including the user created at install).

I am able to ssh into the user created at install using password or key without any issues but I am unable to ssh into the newly created using a key (password works fine).

There are only a few things that are different between the two users(that I'm aware of), which are:

[LIST]
[*]Home directory was moved. When logged into the new user I can view ~/.ssh/authorized_keys and did place my public key there. I can also confirm that ~ points to the location I did intend to set this user's home folder, and just for safe measure I copied the .ssh folder to /home/*username*. (I can also confirm that the authorized_keys file is globally readable and so are directories it's contained in.

[*]The new users is not in all the same groups. The groups that are missing from the newly created user are: *_dialout cdrom plugdev users sambashare lpadmin_* (this is the only different in groups between the two users)
[/LIST]

Anyone able to help?

---

