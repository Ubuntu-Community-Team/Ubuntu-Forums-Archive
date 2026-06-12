---
title: "The &quot;broken sudo&quot; issue..."
date: 2007-03-08
forum: Server Platforms
---

### Post by Hopkins on 2007-03-08
I have been using the Ubuntu 6.06 LTS server at home over the last six months to run basic services (apache, vsftpd, freeciv, openssh).  (Note: these six months have been my first contact with Linux, so I'm still quite a noob!)  Twice, I have suffered from sudo "breaking".  Specifically, the main user was removed from the "admin" group in the /etc/group file.  I found [this handy site]("http://www.psychocats.net/ubuntu/sudo") that explained the problem to me and helped me to get the server up and running properly again.

The process is painless when I'm at home: restart in recovery mode, edit /etc/group and then restart normally.

However, this worries me because, if I'm not at home, I could be prevented from administering my own server.

Is this issue being looked into, or is it fully understood and there is some action I could take to avoid the problem?

---

### Post by dotman on 2007-03-08
Well as a precaution you may want to set the root password so if that were to happen, you can use su to gain admin access or simply log in as root through ssh. It's pretty easy to do and as long as you have a good password in mind, i think the risk is minimal.

```
you@comp:~$ sudo su
Password:(your user password)
root@comp:/home/you# passwd
Enter new UNIX password: (your super high security, uber complex password here) 
Retype new UNIX password: (and here)
passwd: password updated successfully
root@comp:/home/you# 
root@comp:/home/you# exit
you@comp:~$
```
If you are the paranoid type, you can restrict remote root access over ssh ([http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html)). In which case you would just ssh into your account and use the su command to gain root access.

---

### Post by Mr. C. on 2007-03-08
Perhaps I missed the "problem" mentioned on that link, but I didn't see any problem with sudo breaking.   Why do you phrase it as "sudo breaking", and not user misconfiguration?

Have you experienced the /etc/sudoers file being changed without your knowledge or intervention?

MrC

---

### Post by Hopkins on 2007-03-11
Thanks for your replies.  I hadn't considered enabling the root account - that should be a good safeguard.

Regarding "sudo breaking", Mr. C., it's true that it's a configuration issue.  "broken sudo" was the search string that gained me the link to _[the site I linked to]("http://www.psychocats.net/ubuntu/sudo")_ where the guy refers to it in a similar manner (have a look at that page for a full explaination of the problem).  /etc/sudoers was never the problem, it was just the /etc/group file that changed, removing my main user from the "admin" group.  This change to the /etc/group file was not made by me directly, it happened unexpectedly on both occasions, with the effect that I was locked out until I could enter recovery mode because the root account was not enabled.  There are no other users on this system, save a single user that my friends use for FTP via vsftpd.

Any ideas what could cause this?

---

### Post by Mr. C. on 2007-03-11
Not having seen exactly what software or packages were updated, or how /etc/groups was modified, it will likely be a pointless exercise to discover how things went wrong.

Better instead to be prepared for such mis-configurations in the future.  Give yourself SSH access, and just use "su" to become root to fix the problem.

I wouldn't worry much about it.  If you are concerned about such things happening in the future, keep backups for all your important files; restore as necessary after some rogue update performs unexpected surgery on your files.

MrC

---

