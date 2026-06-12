---
title: "Lost Sudo Privileges"
date: 2009-03-01
forum: Security
---

### Post by rmccarri on 2009-03-01
Hi,
I went to update my Ubuntu 8.10 desktop this evening and I ran into an error message.  As it turned out, my main user account had somehow been removed from the admin group.  Has anyone heard about this happening before, or should I be concerned that someone has gotten into my computer.  It's running a LAMP server that is open to the web.
Thanks!
Rob

---

### Post by bodhi.zazen on 2009-03-02
It usually happens whey you change your groups from the command line.

What is the output of ```
groups
``` ?

To fix it , boot to recovery mode and add your user back in the admin group.

I usually do this by manually editing /etc/groups and /etc/passwd

And while you are there you can look to see if any unauthorized changes have been made, unexpected users, etc.

If you have been compromised, I suggest you image the HD for forensics and re-install.

---

### Post by rmccarri on 2009-03-02
Hi, thanks for the info!  I was able to fix it right away without resorting to booting in recovery mode as I have su configured.

I rarely use this computer locally, so I guess that I hadn't noticed that this had happened when I added my user to the www-data group over SSH a couple of weeks ago.

---

### Post by cdenley on 2009-03-02
> **rmccarri said:**
> Hi, thanks for the info!  I was able to fix it right away without resorting to booting in recovery mode as I have su configured.

I rarely use this computer locally, so I guess that I hadn't noticed that this had happened when I added my user to the www-data group over SSH a couple of weeks ago.

If you are using ssh and set a root password, I hope you at least disabled root logins in /etc/ssh/sshd_config and used a very strong password. The root account has no valid password by default for a very good reason.

---

### Post by rmccarri on 2009-03-02
Yes, I have disabled root login over ssh and have a very strong password.  I also have SSH restricted to three failed login attempts.

---

