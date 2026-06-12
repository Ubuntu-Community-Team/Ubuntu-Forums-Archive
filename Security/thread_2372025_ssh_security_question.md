---
title: "ssh security question"
date: 2017-09-20
forum: Security
---

### Post by sonicwind on 2017-09-20
I'd like both Ubuntu computers on my home network to be able to share files. I've been reading about ssh, so I know how to do this.

My question is whether I really need to generate ssh keys, or am I good on a home network with just a really strong password?

Thanks. I appreciate any advice on this. Ubuntu 16.04 LTS

---

### Post by QIII on 2017-09-20
Hello!

Develop good habits at the outset.  Use keys.  Don't allow root login.  Change the default port.  Use fail2ban or similar.

There are some links to good resources [her]("https://help.ubuntu.com/community/SSH")e.

Cheers!

---

### Post by SeijiSensei on 2017-09-20
Keys will make your life much easier.  For instance, you can run automated backups at off-hours via rsync with keys.  You don't want to get up every morning at 2 am and type in a password.

---

### Post by HermanAB on 2017-09-22
The keys make things easier.  However, a key is not necessarily any better in practice than a 25 character password.  Both will keep attackers out.

---

### Post by kevin160 on 2017-09-30
Like HermanAB says, it isn't strictly necessary, especially on a private network.  I do it even on my home network because it makes life easier.  Do you want to type a long password or no password on a regular basis?  Quick ssh, scp, zfs send/receive, etc., etc.

---

### Post by HermanAB on 2017-10-01
The main thing is to always use very long passwords for everything.  A password should be a minimum of 12 characters and preferably much longer.  I was not joking about a 25 character password!

Never, ever, ever use kewl four character passwords, since some script kiddie will sooner or later show you just how uncool it actually is...

---

### Post by TheFu on 2017-10-01
Passwords of 16 characters and less are being completely hacked in less than 24 hrs these days.  20+ characters should be the minimum allowed.

ssh-keys make life easier.  After I get a login to a new system, the first thing I do is push my public ssh key there - 
```

$ ssh-copy-id userid@server
```
does it.  That's it. Done. Finished. How hard is that?  Takes about 10 seconds, since you will be prompted this 1 time for the login password.

Never be bothered again for a password from that client connecting using ssh, scp, sftp, rsync, rdiff-backup, or any tool built with libssh again.  ssh-key are 2K-4K in length - compare that to any password - basically, they are over 4000x better - and it really is an exponential function for those calculations, so 2**2K is more correct.

---

### Post by HermanAB on 2017-10-01
Not to burst your key bubble, but the thing I don't like about keys is that when your 'master' machine is compromised, the hacker can then access everything without even having to type in a password.  So, there are advantages and disadvantages to keys and you have to think about it for a minute before implementing it.  It is not necessarily the one true path to salvation.

---

### Post by TheFu on 2017-10-01
Of course, starting from a trivial setup is really just the beginning.

ssh-keys have passphrases or key files or gpg keys or a smartcard or .... .  This it up to each installation to deploy.  Security can be great or terrible.  ssh-keys can be centralized on an identity server for a company.  That box would be managed by professionals, but still a risk.  

Using the ssh-agent will allow control over how often the ssh-key file needs to be re-unlocked.  With U2F-based authentication, a HW device just needs to be plugged into the client machine to maintain the unlock for the keys, as needed.  Of course, then it comes down to an individual not leaving that in all the time for convenience or losing the FOB.  Smart cards built-into an ID could be better, provided the toilet requires the card for access.

But I'd say that using a 20 character password for remote access into any is still 2000x less secure than using a 2K ssh-key, even without a less-than-great passphrase.

---

### Post by sonicwind on 2017-10-01
Thanks for the responses and discussion.

What happens if I need to reinstall either Ubuntu system unexpectedly?

If it was the server computer, would I just reinstall openssh-server, and then send the public key to it again from the client?

If you had to reinstall the client, what do you do? Do you just delete the key on the server, reinstall openssh-client on the client and then send the new public key to the server? Would that work or is something else necessary?

---

### Post by TheFu on 2017-10-01
Backups would include the ssh-keys. No issue on either the client or the server, assuming backups are performed correctly. That means getting all the files, permissions, ownership, and ACLs, as needed.

I've been moving forward the same HOME since the mid-1990s.  Every few years, I'll re-generate ssh keys as new, better, crypto comes online for ssh.  Then I'll push those keys to the servers.  Sometimes, for high risk servers, I'll generate a separate key and configure that to be used in my ~/.ssh/config file for just that system.  In that way, having multiple keys becomes seamless to me during use, but I have control otherwise.

[https://www.yubico.com/why-yubico/for-business/computer-login/linux/](https://www.yubico.com/why-yubico/for-business/computer-login/linux/) - 2FA for ssh-key unlocking.
[https://www.yubico.com/support/knowledge-base/categories/articles/can-set-linux-system-use-u2f/](https://www.yubico.com/support/knowledge-base/categories/articles/can-set-linux-system-use-u2f/) - for U2F use.  Yubikey is just 1 of the U2F vendors.
Many git providers have supported U2F for almost 2 yrs now - which is over ssh.

---

### Post by SeijiSensei on 2017-10-02
The keys are stored in /home/username/.ssh.  If you back up your home directly, you'll back up the keys as well.

The only thing that will change is the new machine's signature.  The first time you connect to the new machine, the SSH client will complain that the identifier has changed.  After you accept the change, you shouldn't see any other issues.

---

