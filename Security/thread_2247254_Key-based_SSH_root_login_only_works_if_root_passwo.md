---
title: "Key-based SSH root login only works if root password unlocked"
date: 2014-10-06
forum: Security
---

### Post by Samloops on 2014-10-06
I have an issue that I've not been able to find discussed elsewhere.  I'm now totally stumped and would really appreciate some direction.  I only seem to be able to SSH to root on a target machine using key-pair authorization if the root password on the target is set.  If the root password is locked on the target, key-pair authorization fails.

Specifically, I have two identical Ubuntu 14.04 servers (A and B).  I am setting up an automated rsync script that will occasionally clone A to B over SSH.  Consequently, I will need to set up SSH from A root to B root and would like to set this up as securely as possible.  I believe that I have RSA keys set up properly, having an A-generated private key in /root/.ssh on A and the associated public key in /root/.ssh/authorized_keys on B.  A and B's /root/.ssh directories are set to 700, and B's /root/.ssh/authorized_keys is set to 600.  

I have set B's sshd_config as follows:

PermitRootLogin without-password
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
 ChallengeResponseAuthentication no
UsePAM no

If I attempt to SSH from A's root to B's root account, key-pair authorization fails and I am asked for B's root password.  If I set a password for root on B with 'sudo passwd root', then SSH from A's root to B's root, key-pair authorization succeeds and I connect WITHOUT entering a password.  However, if I lock B's root password with <sudo passwd -l root>, then the key-pair authorization fails again and I am requested for B's root password when trying to connect.

This behavior seems contrary to anything I've read about how to successfully set up SSH for root access using Ubuntu.  My understanding is that for root access over SSH, setting up the keys and sshd_config properly is all that is required.  The root password on the target should be able to remain locked.  Interestingly, even if I set PermitRootLogin to yes, I still get the same behavior.

Any ideas what I may be doing incorrectly?

Thanks,
Sam
Kamloops, Canada

---

### Post by TheFu on 2014-10-06
Don't "lock" the account and it works here.  After all, the root account doesn't have a password on Ubuntu systems and it is meant to be accessed through sudo.

However, I don't actually use the "root" account, instead I create a new account (root223afssfsd - random), and set the uid to 0. Then use that HOME and ~/.ssh/ for remote connections (only for backups)

Depending on what you are really trying to accomplish, using a devop tool like ansible might be an option too. These understand non-root connections, then use sudo.

---

### Post by Samloops on 2014-10-06
My understanding is that the root password as shipped is already "locked": [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) . It looks like your approach in essence is to activate the root account under a new name to help hide it, and move its home.  As there are many ways to skin a cat in Linux, that would be one approach.  It seems like a work around for something that even in Ubuntu, should not need to be worked around however. 

Thanks for the suggestion.  If I can't find a means of achieving an SSH key-pair connection without activating root, then I may have to go with your plan and activate its equivalent.

Thanks,
Sam

---

### Post by TheFu on 2014-10-07
Not certain this is clear - the "root223afssfsd" account is an additional account, not a replacement.
Looked through my sshd settings - the only one that is different here is UsePAM - mine is set to yes.  That other account also does not have a password and is only accessible through ssh keys.

Besides that, I don't have any other ideas. Sorry.

---

### Post by steeldriver on 2014-10-07
I wonder if you need to explicitly set 'PasswordAuthentication no' when you set 'UsePAM no' - otherwise it's trying non PAM-based PasswordAuthentication (i.e. direct from the passwd/shadow files)? Just a guess.

---

### Post by TheFu on 2014-10-07
> **steeldriver said:**
> I wonder if you need to explicitly set 'PasswordAuthentication no' when you set 'UsePAM no' - otherwise it's trying non PAM-based PasswordAuthentication (i.e. direct from the passwd/shadow files)? Just a guess.

I know that PermitRootLogin = no prevents my setup from working (with NO other changes).  Didn't get backups for a few days due to that.

---

### Post by Samloops on 2014-10-07
OK... I think I have it working.  I'm still testing but steeldriver's  hint about PasswordAuthentication got me looking at the relationship  between PAM and other settings.  What seems to work is to set on B:

PermitRootLogin without-password
ChallengeResponseAuthentication no
PasswordAuthentication no (originally commented out)
UsePAM yes

This allows key-pair authentication SSH from A/root to B/root.   Excellent.  At the same time, A and B's root passwords are still locked  as they probably should be and no other users are involved.

In regards to setting up a new user, I was under the impression that  root's uid=0 and that creating another user with uid=0 basically just  replaces root's account name.  /root directory would still exist of  course, but not be the "home" of the new root user.  Maybe I'm wrong  here.  It just seems that there is a potential for some real confusion  down the line.  It is an interesting approach however.

I'll test some more and see if I can duplicate the set up on another set  of servers.  If it works, I'll get back and tag this thread as  solved... or get back with more questions!

Thanks for everyone's feedback.  

Sam

---

### Post by Samloops on 2014-10-07
It seems to be working quite well.  Just thought I would list my sshd_config parameters in case others need to set up key-pair authorization for root access and are having problems.  Anything not listed below is commented out in my sshd_config.  I've also set up key-pairs for normal users as well, so that all connections are through key-pair authorization.

Port 4117
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
UsePriviledgeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 1024
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin without-password
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRHosts yes
RHostsRSAAuthentication no
HostBasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication no
X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AcceptEnv LANG LC *
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes

Thanks again for all the input!

Sam

---

