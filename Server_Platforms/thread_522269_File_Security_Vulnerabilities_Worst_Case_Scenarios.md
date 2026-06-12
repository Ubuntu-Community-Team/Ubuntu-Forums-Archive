---
title: "File Security Vulnerabilities: Worst Case Scenarios?"
date: 2007-08-10
forum: Server Platforms
---

### Post by Troubled on 2007-08-10
[SIZE="3"]Recently, I've been unfortunately communicating with some rather unsavory types of the 1337-hax0rz disposition, and I'm starting to get concerned about the safety of the personal files that I have stored on my Ubuntu system. These are files with photos and private information such as names and addresses which I fear are open to scrutiny.

My computer is not connected to the Internet 24-7, but I have communicated with these undesirables through HTTP, IRC, and telnet for some time. Could anyone give me a run-down on the worst case scenarios for my file security: what's the worst that someone could possibly do in cracking into my system while I'm connected to their server via an internet browser, an IRC client, and a telnet utility?

Don't be afraid to be creative; I'm sure that those script kiddies have plenty of time on their hands while they're on summer break.

Thanks,

-John[/SIZE]

---

### Post by codmate on 2007-08-10
It depends entirely on your system's configuration, what applications you have installed, and any vulnerabilities in said applications and configuration.

For instance: if you're running SSH on port 22, and your main account is the same as your IRC handle and your password is a dictionary word then you're extraordinarily vulnerable and probably have a rootkit installed.

What's the worst they can do?

Well - installing a rootkit that enables them to log in to your system as root whenever they want is nasty. Plus they can turn your box into their kiddie porn repository, use it to commit fraud, store other people's credit card info, use it to send trojans/spam.

Basically your worst nightmare.

If your machine is nicely secured I doubt you have to worry though.
Most script kiddies just move on to a more vulnerable target if they find a system that is even partially locked down.

---

### Post by Troubled on 2007-08-10
[size="3"]That sounds rather bad. I am running port 22 SSH, while my username/password is completely unrelated to my IRC nick. I've run chkrootkit and turned up nothing.
Through what means might a potential cracker install a malicious program onto my system? Does ssh allow remote file access/alteration?[/size]

---

### Post by bodhi.zazen on 2007-08-10
Yes, if you are running a ssh server the can can potentially access your box.

You can check you logs, but logs can be altered ...

My advice is to back up your data and re-install.

make a new user name and password

make a second user account without access to sudo for daily use.

read how to secure ssh if you use it :

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

[http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html](http://alblue.blogspot.com/2005/08/howto-ssh-logins-using-keys.html)

---

### Post by Troubled on 2007-08-10
[SIZE="3"]I don't actually run a SSH server, but I use putty to connect to ones possibly run by coders with ill-intent. Does that come with the same risks?

As to creating a second user, it would be nice to use a sudo-disabled account for internet access, but I use a wireless connection for my laptop and root level permissions are required to connect to a wireless network.
Any suggestions on how to overcome this obstacle, and how to identify possible Trojans?

Thanks for your help.[/SIZE]

---

### Post by bodhi.zazen on 2007-08-10
> **Troubled said:**
> [SIZE="3"]As to creating a second user, it would be nice to use a sudo-disabled account for internet access, but I use a wireless connection for my laptop and root level permissions are required to connect to a wireless network.
Any suggestions on how to overcome this obstacle, and how to identify possible Trojans?

Thanks for your help.[/SIZE]

You can put the command to start your wireless in 

/etc/rc.local

Or you can start your internet in a terminal:

su<user_with_admin_rights> #enter password #1
sudo <start internet> #enter password #2
exit
exit

---

