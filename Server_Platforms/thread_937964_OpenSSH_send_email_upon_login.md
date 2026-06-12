---
title: "OpenSSH send email upon login"
date: 2008-10-04
forum: Server Platforms
---

### Post by Shwick2 on 2008-10-04
Ubuntu 8.04

How would I send an email every time someone logs into openssh?  I'm using mailx and my ISP as a SMTP server.

Also I'd like to log/see what failed passwords were rather than just seeing "Failed password for invalid user asdf from 192.168.0.100 port 4304 ssh2" in auth.log.

---

### Post by pdwerryhouse on 2008-10-04
A simple way would be to add some code to /etc/profile:

```
echo "User logged in" | mailx -s "Login alert" address@example.com
```

This would send an email upon all logins (ssh or console), and it would also do this when someone runs "su -" successfully, which might be annoying.

Another option might be to look at sshd's *ForceCommand* option, along with the SSH_ORIGINAL_COMMAND environment variable (ie, set this to a script which sends the mail, and then runs the shell).

---

### Post by Shwick2 on 2008-10-05
I now receive an email whenever anyone logs into ssh, I added a call to the email script in /etc/bash.bashrc.

When I login using psftp.exe an email isn't sent though.  Is it worth it sending an email for psftp, or is sftp not a security risk.  How would I go about doing this?

---

### Post by pdwerryhouse on 2008-10-06
as sftp isn't logging in interactively, it doesn't source the /etc/bash.bashrc file.

I'm not entirely sure whether it's worth sending email at all. You might find that you get the email so often, that you start ignoring it.

---

### Post by Shwick2 on 2008-10-06
I don't care how many emails I receive, I just care how much damage can be caused if someone logs into sftp without me knowing.

If the damage can be significant, then I need to know what file I can call a send-email script from.

Logging in via sftp doesn't give you too much permissions, like I don't think they could take a password file and try to crack it or anything.

---

### Post by Masuran on 2008-10-06
> **Shwick2 said:**
> When I login using psftp.exe an email isn't sent though.  Is it worth it sending an email for psftp, or is sftp not a security risk.  How would I go about doing this?

I don't think it's worth sending a mail whenever someone connects using the SFTP protocol, since it's 'just' FTP. 
If you're worried about the security risk you should try to limit as much access from the users that can FTP to your server.

---

### Post by lykwydchykyn on 2008-10-07
Depending on the use scenarios and the way the system is setup, SFTP could be an attack vector.  Although you can't run commands or sudo, you can read and write files the user can read and write.

For instance, if a user's account is compromised, a modified .bashrc could be uploaded containing malicious commands, or modified (read: rootkit) binaries could be stashed in ~/bin (if you use user bin directories), as a sort of "land mine" for the actual user to trigger on their next session.  Or someone could just be nasty and wipe out the user's files.

It really just depends on how paranoid you want to be.

---

### Post by Shwick2 on 2008-10-07
I'm probably not going to send an email for sftp.  I can't image hackers and script kiddies thinking, "omg time to hack sftp instead of ssh its not as obvious how to trigger scripts upon login!".

So how do you trigger scripts upon sftp login if it doesn't go through bash.bashrc.

---

