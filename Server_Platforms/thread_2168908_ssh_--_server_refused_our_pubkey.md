---
title: "ssh -- server refused our pubkey"
date: 2013-08-19
forum: Server Platforms
---

### Post by kr6511292 on 2013-08-19
I chmod-ed 600 ~/.ssh/authorized_keys2 and 700 ~/.ssh with and without root, after restarting ssh everything works fine.  After I reboot, the file and folder revert their permissions and won't let me in.  I've never seen any problems like this before :confused: so this has totally left me confused.  Has anyone else ran into this before?

---

### Post by TheFu on 2013-08-20
Turn up the verbosity on your ssh command -vvvv and watch the logs on the other side too.  Also, I was under the impression that authorized_keys2 was deprecated for authorized_keys again.  root shouldn't own any files either.

Which userid are you using?  Coming in as root is **not** a best practice.  Many sshd_config files disable remote root.

---

### Post by CharlesA on 2013-08-21
> **TheFu said:**
> Turn up the verbosity on your ssh command -vvvv and watch the logs on the other side too.  Also, I was under the impression that authorized_keys2 was deprecated for authorized_keys again.  root shouldn't own any files either.

I think you nailed it. I've always used authorized_keys. Permissions are a huge thing as I lost access to my VPS because I forgot to chown the .ssh directory from root to the user I wanted to log in as and was left scratching my head until I checked something else and discovered the owner was incorrect.

> Which userid are you using?  Coming in as root is **not** a best practice.  Many sshd_config files disable remote root.

Agreed. There are some ways to login as root by using keys only, but so far I have been logging into a non root user and then su'ing to root if/when I need to.

---

### Post by kr6511292 on 2013-08-25
I reinstalled 13.04 just to rule out having been hacked and disabled the port 22 rule in my router.  I then setup key only auth again and disabled root logins and chmod'd the files as a normal user.  Everything was working fine for a few days and then my server stopped accepting the keys again.  I haven't tried -vvv yet, but I'll try with that later.

---

### Post by CharlesA on 2013-08-25
Check /var/log/auth.log after trying to connect via ssh and see what it says. Otherwise ssh -vvv might be helpful.

---

### Post by 1clue on 2013-08-25
What are the permissions on your ~ and ~/.ssh directories?

It's been awhile since I read what the details are, but I think if your $HOME is writable by somebody other than you, or if your .ssh directory is readable or writable by anyone but you then ssh refuses.  Or something.

Try chmod 700 ~/.ssh (non-recursive)

Sorry, just too lazy right now to look it up.

---

### Post by TheFu on 2013-08-26
> **kr6511292 said:**
> I reinstalled 13.04 just to rule out having been hacked and disabled the port 22 rule in my router.  I then setup key only auth again and disabled root logins and chmod'd the files as a normal user.  Everything was working fine for a few days and then my server stopped accepting the keys again.  I haven't tried -vvv yet, but I'll try with that later.

Until you turn on the verbosity and check the server side logs, we are pissing in the wind here.

---

