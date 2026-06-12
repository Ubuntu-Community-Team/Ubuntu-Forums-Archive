---
title: "[SOLVED] Downloading to remote machine"
date: 2007-07-29
forum: Server Platforms
---

### Post by p_quarles on 2007-07-29
I'm trying to figure out how to most efficiently use my file server (remote admin only) to download large files overnight. I tried two things, both of which are giving me some headaches.

1) The man page for SSH indicates that it's possible to include a command (in this case "sudo wget *url*") in the initial connection instructions, and that this should run the process on the remote machine and not in the shell. This didn't work for me. It printed the password prompt, but skipped right past it to the next line, wherein anything I entered was plain text. After that, I got a message saying the job was stopped. 

2) I used Webmin to schedule a download, which worked, but scrambled the filename. A .tar.gz file from Sourceforge was translated into a series of random numbers and letters. After I appended the appropriate extension, however, I was able to unpack it, and everything seemed to be intact. 

Basically I just want to be able to instruct my server to download a big file, then logout of the connection and shut down my desktop while it does this. Using Webmin to do this, and then renaming the file, apparently works, but I'm sure there's a less cumbersome way of doing this. 

I'm pretty certain I'm missing something obvious, and any insight into what this something might be is greatly appreciated.

---

### Post by cilynx on 2007-07-29
Using SSH to exicute a one-shot command on a remote host is a non-interactive process.  Basically, you can't do anything that requires you to enter anything.  Why do you need to run sudo on the fileserver?  Does the user that you are logging in as not have permission to write to the drive?

---

### Post by heimo on 2007-07-29
I'm  not quite sure if I understood you correctly, but here's my suggestion. SSH into the machine, execute wget with nohup, exit. That's how I'd do it. By the way, you shouldn't use root (sudo) to download anything as it's not neccessary. It's actually a security risk.
```
ssh myaccount@host
nohup wget http://url.where.ever/file.ext
exit (or ctrl+D)

```That leaves the wget downloading on the background and it won't stop when you exit because of "nohup" in front of it.

---

### Post by p_quarles on 2007-07-29
Thanks for the quick responses. 

@cylinx: Yes, in fact I was: trying to download to a Samba share owned by a different version of myself. Downloading it to the server's home directory (the default login dir), however, gave me the same error. 

@heimo: That worked beautifully. Exactly what I was looking for. Thanks much.

---

