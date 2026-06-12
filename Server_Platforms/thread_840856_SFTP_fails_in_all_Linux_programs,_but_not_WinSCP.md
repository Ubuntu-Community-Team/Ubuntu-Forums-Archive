---
title: "SFTP fails in all Linux programs, but not WinSCP"
date: 2008-06-25
forum: Server Platforms
---

### Post by altonbr on 2008-06-25
Using Ubuntu 8.04/GNOME 2.22, I can not get sftp to work for the life of me.

FileZilla [3.0.7.1-0ubuntu3]
gFTP [2.0.18-17ubuntu1]
sftp (on the command line)
Nautilus [1:2.22.3-0ubuntu2]

They all fail to connect to this one server on port 22 via SFTP.

The one program that succeeds in connecting, through Wine and on Windows, is WinSCP 4.0.7 and 4.1.4. Unfortunately, WinSCP is a little buggy through Wine so I can't use it in Linux.

I can SSH to it successfully however. It seems to be the only Linux program that works...

FileZilla
> Status:	Connecting to $DOMAIN:22...
Response:	fzSftp started
Command:	open "$USERNAME@$DOMAIN" 22
Command:	Pass: **********
Status:	Connected to $DOMAIN
Error:	Could not connect to server

gFTP
> Opening SSH connection to $DOMAIN
Running program ssh -e none -l $USERNAME -p 22 $DOMAIN -s sftp
3: Protocol Initialization
$USERNAME@$DOMAIN's password: *********
Request for subsystem 'sftp' failed on channel 0

Error: Could not read from socket: Connection reset by peer
Disconnecting from site $DOMAIN

sftp
> sftp $USERNAME@$DOMAIN
Connecting to $DOMAIN...
$USERNAME@$DOMAIN's password: *********
Request for subsystem 'sftp' failed on channel 0
Couldn't read packet: Connection reset by peer

Nautilus
> sftp://$USERNAME@$DOMAIN:22
(Dailogue: "Enter your password: " **********)
Couldn't display "sftp://$USERNAME@$DOMAIN/".
Error: Error reading from unix: Input/output error
Please select another viewer and try again.

WinSCP
> Searching for host...
Connectiong to host...
Authenticating...
Using username "$USERNAME"
(Dailogue: "Password: " **********)
Authenticated.
Starting the session.
Reading remote directory...

---

### Post by RealPSL on 2008-06-25
If I remember well WinSCP is smart enough to drop back to using scp if sftp fails. You might want to make sure that the target systems have the sftp subsystem enabled.

---

### Post by altonbr on 2008-06-26
> **RealPSL said:**
> If I remember well WinSCP is smart enough to drop back to using scp if sftp fails. You might want to make sure that the target systems have the sftp subsystem enabled.

Hmm, looks like SCP is available but SFTP is not on this shared host. What can I do from a Linux client perspective so I don't have to reboot into Windows just to use WinSCP?

---

### Post by MJN on 2008-06-26
It might be worth speaking to your provider as the SFTP subsystem is a relatively straightforward (not to mention standard, albeit not default) extension to SSH from v2. They may be able/willing to enable it with little persuasion.
 
In direct answer to your question though there must be a suitable SCP client available on Linux but this is not my sphere of experience so will have to let others make suggestions.
 
Mathew

---

### Post by hyper_ch on 2008-06-26
what about konqueror? as address enter:
```

fish://user@remote

```

---

### Post by altonbr on 2008-06-27
> **MJN said:**
> It might be worth speaking to your provider as the SFTP subsystem is a relatively straightforward (not to mention standard, albeit not default) extension to SSH from v2. They may be able/willing to enable it with little persuasion.
 
In direct answer to your question though there must be a suitable SCP client available on Linux but this is not my sphere of experience so will have to let others make suggestions.
 
Mathew

Yes, I know how rediculous it is that they don't provide SFTP. They didn't provide rsync by default either and had to persuade them with a week-full of e-mails to get them to install it.

I'll do my best for SFTP now!

I'm just frustrated there is no LinSCP, or a port of WinSCP to Linux...

> **hyper_ch said:**
> what about konqueror? as address enter:
```

fish://user@remote

```

I don't use KDE, but I'm installing the packages and trying it now.

Edit: OMG, fish:// works! I thought it was a joke at first since I'ver never heard of it!

After KDE4, why am I even using GNOME!?

Thank you, thank you, thank you!

---

### Post by hyper_ch on 2008-06-27
you know what, konqui is also multi-pane... just right-click on the bottom bar and select "split vertically/horizontally"... I normally have a layout like this:

```

-----------------------------
|             |             |
|             |             |
|             |             |
|             |             |
|             |-------------|
|             |             |
|             |             |
|             |             |
|             |             |
-----------------------------

```

---

### Post by deeflex on 2009-01-11
Here's a neat solution: ```
sudo gftp
``` . 

Didn't want to install KDE which eats a lot of memory ;).

---

