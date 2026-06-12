---
title: "[SOLVED] Hot to enable root login on vsftpd?"
date: 2007-10-15
forum: Server Platforms
---

### Post by victorbrca on 2007-10-15
Hi all,

  How can I enable root login to my vsftpd? 

  I know this is a security issue, but I'll be limiting root access from my network only on "hosts.deny" and "hosts.allow" after.

Thanks,

Vic.

---

### Post by Brazen on 2007-10-15
I think it would be easier, and better, to find another way to do what you are wanting to do (such as configuring permissions or groups, but it depends on your reason for wanting this).

Now, you have 3 choices:

1) Whine and moan because I didn't give you the answer that you want (most choose this option), 2) follow this advice, explaining what you are actually trying to accomplish so someone can help, or 3) explain why you need root login so people don't constantly repeat what I just said.

---

### Post by victorbrca on 2007-10-16
> **Brazen said:**
> "...1) Whine and moan because I didn't give you the answer that you want (most choose this option).."

hehe, no whining!! :)  I'm already thanked someone took the time to read...

I have a web/ftp server on my dmz (different subnet than my LAN). I also have 3 users on the same server:
- anonymous (for downloads)
- ftp privileged (for few ppl)
- main server user (for myself)

I would like to have full access to the server so I can upload any file to any folder. I can't have the option "local_root=/" because of the two other users. So I was thinking on enabling root login and limit it to my LAN subnet for security. That's all...  :-k

Any better way of doing this? Thanks!!

Vic

---

### Post by netlogic on 2007-10-16
> **victorbrca said:**
> 

Any better way of doing this? Thanks!!

Vic

You should use ssh. If the speed is the concern, ftp to the user directory, and use the root privilege to move the files. If someone see your root password, or brut force in, your machine will be owned.

---

### Post by TheReaper on 2007-10-16
On Linux Clients you can use SSHFS to mount the remote filesystem over SSH into a directory -- highly secure, highly comfortable.

Alternative on Windows Clients: WinSCP.

greets

---

### Post by victorbrca on 2007-10-16
> **netlogic said:**
> You should use ssh. If the speed is the concern, ftp to the user directory, and use the root privilege to move the files. If someone see your root password, or brut force in, your machine will be owned.

Speed is not a problem as this will all be done internally. The main thing is acquiring full write access.

> **TheReaper said:**
> On Linux Clients you can use SSHFS to mount the remote filesystem over SSH into a directory -- highly secure, highly comfortable.

Alternative on Windows Clients: WinSCP.

greets

Is there a way to give sshfs login full access. I installed and am able to create, upload and delete files on _almost_ all folders.

Thanks,

Vic.

---

### Post by victorbrca on 2007-10-16
I just found something that I think will do the job for me. 

I can use nautilus for ssh and have the user's complete access. All I have to do is put "ssh://user@sshserver" on the address line and I'm good.   :D

Thanks,

Vic.

---

