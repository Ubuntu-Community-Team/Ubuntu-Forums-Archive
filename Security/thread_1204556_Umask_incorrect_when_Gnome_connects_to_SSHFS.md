---
title: "Umask incorrect when Gnome connects to SSHFS"
date: 2009-07-04
forum: Security
---

### Post by Lucky. on 2009-07-04
Hi guys.  This is a spinoff of the following thread:

[http://ubuntuforums.org/showthread.php?t=1203246](http://ubuntuforums.org/showthread.php?t=1203246)

However the original thread changed courses enough to where it seemed a new thread may better benefit people searching for a solution.

On both server and client, I changed my umask in /etc/profile to 007.

I am connecting to the server from the client using sshfs.

Using the command prompt, this works well.  Newly created files follow the mask for permissions (Not sure which if client or server's mask is used, but this is no worry).

If I use Gnome's "Connect To Server" on the client and select "SSH", I connect and am able to work just fine.  However the umask on both client and server is ignored, and it appears I get default 022 behavior.

Is there a way to achieve the correct umask and still use Gnome to connect?

---

### Post by scorp123 on 2009-07-05
> **Lucky. said:**
>  On both server and client, I changed my umask in /etc/profile to 007. I am connecting to the server from the client using sshfs. Using the command prompt, this works well. Yes, because your login goes via SSH, hence the profile will be executed and whatever settings are in there will thus become active.

> **Lucky. said:**
>  If I use Gnome's "Connect To Server" on the client and select "SSH", I connect and am able to work just fine.  However the umask on both client and server is ignored  Of course. What you have there is a **SFTP** connection that does not care about your /etc/profile and its settings ... it's a sub-protocol of SSH that has its own sub-section in **/etc/ssh/sshd_config** -- usually somewhere towards the bottom of that file.

What you need is this link:

[http://jeff.robbins.ws/articles/setting-the-umask-for-sftp-transactions](http://jeff.robbins.ws/articles/setting-the-umask-for-sftp-transactions)

Do what it says. Write your own wrapper-script (e.g. set the correct umask) and then let the script invoke sftp-server ... Modify sshd_config so it now points to the script and not to the sftp process directly anymore. Voila, done.

---

### Post by Lucky. on 2009-07-07
Indeed, this worked well.  Thank you kind sir for your help both here and in previous threads.  You are a scholar and a gentleman.

---

### Post by scorp123 on 2009-07-08
> **Lucky. said:**
> Indeed, this worked well.  Thank you kind sir for your help both here and in previous threads.  You are a scholar and a gentleman. You're welcome :KS

---

