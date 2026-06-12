---
title: "Ubuntu server wont allow uploading"
date: 2010-10-26
forum: Server Platforms
---

### Post by Cibico99 on 2010-10-26
I have my Ubuntu server 10.10 running. It worked fine at first, then i installed a gui on it, and now it wont let me upload to it with WinSCP or anything. I am running openSSh on it, any ideas?

---

### Post by Vegan on 2010-10-26
Error 1: Using a desktop

Solution: Format and start over and do not use a server for a desktop again

---

### Post by the_original_billq on 2010-10-26
> **Cibico99 said:**
> I have my Ubuntu server 10.10 running. It worked fine at first, then i installed a gui on it, and now it wont let me upload to it with WinSCP or anything. I am running openSSh on it, any ideas?

How did you "install a gui on it"?  (apt-get install gnome-desktop?)

See this: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI) for the right way, should you choose to do it.

What error do you get when you try the scp?

Is there anything in /var/log/messages on the server?  (do a tail -f /var/log/messages while trying the scp..)

Load Putty on your windows box and try doing an ssh terminal session to the server.  Does that work?  

Is sshd running on the server? (ps -ef|grep sshd)

You don't really say that you've tried debugging it at all, so these might be some first things to try...

-Bill

---

### Post by Cibico99 on 2010-10-26
I tried Putty, and I can log on, sshd is running, and WinSCP can login in but not upload, it gives me a permission denied error when uploading.

---

### Post by hawk2010 on 2010-10-27
You don't need to reinstall the OS. the issue is with permissions. can you tell me the output you get when you do ls -l /the-folder-path-the-user-is-logging-into

---

### Post by Cibico99 on 2010-10-28
Okay, so i just realized that I can upload to it, but only to the /home/user folder, which is where i log into. I figured it out though. i used "sudo passwd root", and set a password for the root user, and then i can log into the root user on the server and logon to it with WinSCP and upload anywhere. Thank you very much for your help.

---

### Post by hawk2010 on 2010-10-28
It is not a good security habit to log in as root! Use a low privilege account

---

