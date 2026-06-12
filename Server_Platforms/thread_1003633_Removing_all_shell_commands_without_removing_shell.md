---
title: "Removing all shell commands without removing shell"
date: 2008-12-06
forum: Server Platforms
---

### Post by jersak on 2008-12-06
Hi there,

I would like to know if its possible, and if it is, how to create an user who can login via SSH but cannot do anything else. This user should not be allowed to execute any commands in shell besides "exit" to close the SSH session.

I tried creating an user without access to shell or bash, but it didnt worked because when this user logged in via ssh, the session closed instantly after the logon.

I need this because im setting up a tunnel where people will login with putty via ssh to tunnel the applications, but i dont want them using putty to input commands in the shell.

Sorry if i cant explain me better, im really confused about this.

Regards

---

### Post by samosamo on 2008-12-06
You can limit a user to certain commands.  I don't exactly know how, but I read about it here: [http://arctic.org/~dean/rdiff-backup/unattended.html](http://arctic.org/~dean/rdiff-backup/unattended.html)

That page shows you how to limit a user to only perform backup commands.  Just to give you an idea on how it is done.

---

### Post by hictio on 2008-12-06
There are a couple of things you can do here.

If you don't want to offer any SSH access to the server that its going to work as the tunnel entry, you can simply run redir on that box, and use a redirection on a local port that will point to the remote SSH server.
The syntax will like this:
```

/path/to/redir --lport=xx22 --caddr=remote.IP.address --cport=22

```

The 'xx22' its a port that it is not being used by any app on the SSH gateway box.

[redir](http://www.linux.org/apps/AppId_865.html)


The other option might chrooting the SSH accounts that you are creating on the SSH gateway box, like this, for instance: [SFTP For Business Use](http://freshmeat.net/articles/view/1576/), using [rssh](http://freshmeat.net/projects/rssh/).

---

### Post by scorp123 on 2008-12-06
> **jersak said:**
> This user should not be allowed to execute any commands in shell besides "exit" to close the SSH session. I'd work with "Access Control Lists". So IMHO the steps would be:
[LIST]
[*]create a special user group for those users, e.g. "sshguests"
[*]every such user is member of that group and of that group only
[*]via ACL you block them access to any directories and binaries you don't want them to have access to
[*]result: they can't do much if you do it right (you should test this!). If they try and access anything their group has no access to they should get a "Access denied!" error message.
[/LIST]

As for ACL's and how to install and use them: please take a look here:
[http://tlug.dnho.net/?q=node/171](http://tlug.dnho.net/?q=node/171)

This tutorial is quite detailed. It was written ages ago for SUSE (before it was called "OpenSUSE" ...) but the commands shown in there are still valid as far as I can tell:
[http://www.suse.de/~agruen/acl/linux-acls/online/](http://www.suse.de/~agruen/acl/linux-acls/online/)

Please read that and make a note of the examples given on that page, e.g. how to use the "getfacl" and "setfacl" commands.

Please make sure you test this first on unimportant files ... just to make sure that you don't lock yourself out of your own system, OK? :)

---

### Post by adaptr on 2008-12-06
Just disable their shell and run the SSH tunnel as their login command.

---

### Post by random_mike on 2008-12-07
> **jersak said:**
> 
I need this because im setting up a tunnel where people will login with putty via ssh to tunnel the applications, but i dont want them using putty to input commands in the shell.

Sorry if i cant explain me better, im really confused about this.

Regards


If you need a tunnel you can use Plink to create a tunnel.
For example I have Windows users running rsync backup to our linux server with no shell "/bin/false" over ssh.

For example:
```
plink -v -ssh -2 -N -batch -L 873:localhost:873 -l USERNAME 10.1.1.1 -P 22 -pw *****
```

Tunnel ready and then they execute there rsync command.

Plink = a command-line interface to the PuTTY back ends
You find plink where you found putty.

---

### Post by jersak on 2008-12-07
> **random_mike said:**
> If you need a tunnel you can use Plink to create a tunnel.
For example I have Windows users running rsync backup to our linux server with no shell "/bin/false" over ssh.

For example:
```
plink -v -ssh -2 -N -batch -L 873:localhost:873 -l USERNAME 10.1.1.1 -P 22 -pw *****
```

Tunnel ready and then they execute there rsync command.

Plink = a command-line interface to the PuTTY back ends
You find plink where you found putty.

GREAT!!
This actually saved my day! Thank you SO MUCH!

PS: Is there someway to display a message when the user log in? Like an MOTD?

---

### Post by scorp123 on 2008-12-08
> **jersak said:**
> PS: Is there someway to display a message when the user log in? Like an MOTD? You could display a message before login upon creation of the SSH connection via **/etc/issue.net** .... You just have to uncomment this line in **/etc/ssh/sshd_config** (this is usually towards the end of that file):```
# Banner /etc/issue.net
``` ... remove the hash " # " on the beginnging of the line. Write something meaningful into /etc/issue.net and then restart your SSH. After that your users will get whatever you wrote into /etc/issue.net as a message when they establish a connection to that system.

See this thread here:
[http://ubuntuforums.org/showpost.php?p=4838239&postcount=10](http://ubuntuforums.org/showpost.php?p=4838239&postcount=10)

---

### Post by hictio on 2008-12-08
> **scorp123 said:**
> You could display a message before login upon creation of the SSH connection via **/etc/issue.net** .... You just have to uncomment this line in **/etc/ssh/sshd_config** (this is usually towards the end of that file):```
# Banner /etc/issue.net
``` ... remove the hash " # " on the beginnging of the line. Write something meaningful into /etc/issue.net and then restart your SSH. After that your users will get whatever you wrote into /etc/issue.net as a message when they establish a connection to that system.

See this thread here:
[http://ubuntuforums.org/showpost.php?p=4838239&postcount=10](http://ubuntuforums.org/showpost.php?p=4838239&postcount=10)

And, if you want to display exactly like a MOTD, after a successful login, then uncoment the line:

```

PrintMotd yes

```

on the /etc/ssh/sshd_config file.
You don't need to restart the SSHD daemon fro this change to become active, issuing a:

```

sudo /etc/init.d/sshd reload (ENTER)

```

is enough.

---

