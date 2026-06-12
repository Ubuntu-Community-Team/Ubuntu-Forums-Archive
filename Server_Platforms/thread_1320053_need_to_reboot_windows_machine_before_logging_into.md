---
title: "need to reboot windows machine before logging into different share?"
date: 2009-11-08
forum: Server Platforms
---

### Post by mendo on 2009-11-08
i am setting up an ubuntu server, sans gui and have been configuring it remotely, via putty.

i have some shares setup via samba and am noticing that if i log into user1's share (home dir) from a winxp machine, i can't then log into user2's share (home dir) w/o rebooting the winxp machine first.

i can login to user1's share on winxp machine 1 and then login to user2's share from winxp machine 2 at the same time, but once i login to any share that requires authentication, i can't login to another share that requires authentication unless i reboot the windows box first.

what's up with that?

i am attempting to employ user security in samba.

while i'm at it - if i expect to have public (no password req'd) and secure (authenticated) shares on the same server, should i be using user or share security in samba.  this server is not a domain controller.  domains scare me.

please and thank you in advance.

---

### Post by Thirtysixway on 2009-11-09
On windows, are you logging of user1's account and logging into user2's account?

It sounds to me that you are trying to connect to two different samba shares with two different usernames/passwords. Are you using the "net use" command to mount the shares?

---

### Post by mendo on 2009-11-09
i am tyring to log into both samba share's from the same windows account.

you are correct in that i am trying to log into 2 samba shares w/2 user names & passwords.

i am not aware of the "net use" command.  i'm just using simple share definitions in the smb.conf file for public shares and i want my roommates to have secure home directories on the network.

is my method flawed?

thanks for your help.

---

