---
title: "Jail SSH user's access to home dir."
date: 2010-09-17
forum: Server Platforms
---

### Post by Patrik89 on 2010-09-17
Hi.

I was under the impression that this would be an easy task to accomplish. However, after googling for a good while all I came up with was some rather weird and pseudo solution and not really a good way of doing it.

What is the reason this feature is not implemented into OpenSSH or any SSH in general? Is there a security threat?

I want to limit certain users (or groups) access to their home directory over both SSH and SFTP.

I recently came over an excellent script called lshell ([http://lshell.ghantoos.org/](http://lshell.ghantoos.org/)) which basically had every feature I needed and more. With lshell I can restrict users access globally and individually and limit their access to /home/"user" and/or to for example /etc, /bin and if they try to access / or anything else they are not allowed to they will get a warning and eventually get kicked out.

This is genius! But I wonder why no such thing is not supported official by ubuntu or OpenSSH? Is it on the list of "TODO" things or is there a good reason this is not a feature (and I should not use lshell..)?

Thanks in advance,
Patrik.

---

### Post by prshah on 2010-09-17
Hello,

thanks for the link on lshell. I have been looking for something like that for a while.

I have been trying to jail SFTP for a while as well, without success. I had to make some changes to a "subsystem" parameter in the /etc/ssh/sshd_config file, but ended up breaking SSH entirely. I look around and see if I can find the details on what I did.

In the meantime, I'll keep an eye on this, since I'm looking to do the same.

(think of this message as an over-sized "bump")

---

### Post by R.Bucky on 2010-09-21
Ubuntu already has built in user groups for limiting access to users. SSH users can be limited to their user directory, so can VSFTP or similar FTP applications. No need to use additional applications for something that is already built in.

---

### Post by prshah on 2010-09-21
> **R.Bucky said:**
> SSH users can be limited to their user directory, so can VSFTP or similar FTP applications. No need to use additional applications for something that is already built in.

Unfortunately not! When you set up SSH access, and then use sftp with either username/password and/or public-key authentication, you are dumped into "/" by default, NOT the relevant home directory!

While permissions still apply, and you can't really do anything (such as delete system files) there is still a concern that you can access files (as read only) which could be blocked by "jailing" or "chrooting" the sftp subsystem.

---

### Post by the_original_billq on 2010-09-21
Perhaps using a restricted shell is what you're looking for?  Check out the bash man page.  "bash -r" restricts you to $HOME.

$ bash -r
bash-3.2$ pwd
/home/bquayle
bash-3.2$ cd /
bash: cd: restricted
bash-3.2$

---

### Post by Patrik89 on 2010-09-27
Thanks for your inputs.

However, rbash doesn't really cut it. One could still browse and read every file on the server even though one is using "restricted bash".

I guess lshell is the way to go. I've been using it for a week or so now and really enjoy the script.

Lshell is also located in the official ubuntu repositories so I guess it is safe to use.

---

### Post by windsxs on 2010-10-13
The problam is quite clear, but unfortunately, it seems as noboty knows the answer...
How to make SFTP logged in users, to be jailed in thei home directory? By default, user can view upper directories e.g. admin users files or other users php scripts or enything else...

---

