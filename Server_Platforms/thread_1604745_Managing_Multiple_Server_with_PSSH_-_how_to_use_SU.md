---
title: "Managing Multiple Server with PSSH - how to use SUDO"
date: 2010-10-24
forum: Server Platforms
---

### Post by nicolasdiogo on 2010-10-24
hi folks,

i have a set of servers that i have to manage and i thougth that pssh (parallel-ssh) would be a great tool for the job.

Except that i can not see how to use that with 'sudo'

i can set password-less ssh between multiple servers for a given user.

but i can not see how to do administrative work if i can not call SUDO as it requires a password to be entered firstly.

any suggestions here please?


thanks in advancem,


Nicolas

---

### Post by abix_adam_pl on 2010-10-24
On every server you shoud modify /etc/sudoers via the command:

```
sudo visudo
```

The modified lines shoudl looks like this:

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: SETENV: ALL

```

That should help.

Adam

---

### Post by nicolasdiogo on 2010-10-24
thanks adam,

now we have a 'catch 22' situation.

how can i amend this file in all machines without being able to use sudo to modify and copy this file across.

besides, this solution does imply that users of the group admin can do anything without ever providing any password to be checked.

it seems a little too relaxed for me.

but it may be the only solution, if i can only figure on how to amend this file in all servers.


with regards,

Nicolas


> **abix_adam_pl said:**
> On every server you shoud modify /etc/sudoers via the command:

```
sudo visudo
```

The modified lines shoudl looks like this:

```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD: SETENV: ALL

```


---

### Post by abix_adam_pl on 2010-10-25
> **nicolasdiogo said:**
> thanks adam,
how can i amend this file in all machines without being able to use sudo to modify and copy this file across.


Sorry, the only solution I can imagine is to do for each one x:

```
ssh -l user -C some_machine_x
```
Then inside do: 
```
sudo visudo
logout
```

> **nicolasdiogo said:**
> thanks adam,
besides, this solution does imply that users of the group admin can do  anything without ever providing any password to be checked.

You can always create some other group, like:

```
sudo groupadd ssh_admin
sudo usermod your_login -g ssh_admin 

```

and then modify sudoers to gran NOPASSWD to ssh_admin group only.

Adam

---

### Post by koenn on 2010-10-25
enable the root account on your servers and setup key-based authentication ?

---

### Post by abix_adam_pl on 2010-10-25
koenn, You are right.

Just copy rsa keys to /root/.ssh directory and you can do :
```
ssh root@server command
```Best regards,
Adam

---

