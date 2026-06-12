---
title: "Mix secure and insecure logins?"
date: 2008-06-01
forum: Security
---

### Post by aaulick on 2008-06-01
I would like to set up my system so that my little kids and visitors can have simple/no passwords to keep each other out, while administrator access (my wife and I) requires decent passwords.  The non-administrator accounts should be invisible to ssh/any other form of remote access.

It's easy to edit /etc/pam.d/common-password to remove password requirements generally for all users -- how do I set up different requirements for administrator/non-administrator?

It's easy to edit /etc/ssh/sshd_config to allow only administrators -- how do I generically disable non-administrator remote login by any service (smb/ftp/etc.etc.etc.) whether already running or added in the future?

---

### Post by HalPomeranz on 2008-06-01
> **aaulick said:**
> It's easy to edit /etc/pam.d/common-password to remove password requirements generally for all users -- how do I set up different requirements for administrator/non-administrator?

If there are user accounts you wish not to have a password, simply make sure that the second field of their /etc/shadow entry is empty.  They will be able to log in without providing a password.  I don't think this is a good idea, but it's your system.  Make sure they're not a member of the admin group or have any other sort of sudo access.

> **aaulick said:**
> It's easy to edit /etc/ssh/sshd_config to allow only administrators -- how do I generically disable non-administrator remote login by any service (smb/ftp/etc.etc.etc.) whether already running or added in the future?

Well, there's pam_deny, which allows you to specify a list of denied users.  The trick is that you're going to have to use it to block access to everything *but* the console login service (probably GDM).  This will require some careful PAM hackery in /etc/pam.d.

Note that all of the services you list above also have per-service user deny functionality (a separate SMB passwd file, /etc/ftpusers, etc, etc).  So you also have the option of configuring each remote login service individually as you turn it up.  This may be easier in the long run than having to maintain a highly customized PAM configuration.

---

### Post by aaulick on 2008-06-01
Thanks, HalPomeranz.  I wish it were simpler than that.  I can't have good passwords on the 5-year-old's account because she can't remember them and it takes her 10 minutes to type them in anyhow, and I can't leave it blank because then the three-year-old logs in and trashes all her stuff....

---

### Post by HalPomeranz on 2008-06-02
Oh, I see what you mean.  If you run the passwd command with root privileges you can set any password you want-- the normal strong passwords rules don't apply if you run the passwd command with root privs.  So just "sudo passwd <accountname>" to set a simpler password for "<accountname>".

---

