---
title: "SFTP understanding how keys work"
date: 2016-12-17
forum: Security
---

### Post by mooninite2 on 2016-12-17
I have a SFTP working but I'm not sure how to use keys so that I can disable passwords, and I'm not so sure I even have sshd_config set up properly. I'm looking for someone who can one-on-one with me and help be gain better understanding of how it works. 

Currently SFTP does work as I can access it through a file explorer on my phone and my Windows pc.

---

### Post by TheFu on 2016-12-17
[https://www.debian.org/devel/passwordlessssh](https://www.debian.org/devel/passwordlessssh)

Keys for sftp, scp, and ssh are the same. No difference. If ssh works with keys, then sftp will too, with the same setup.  
[https://www.youtube.com/watch?v=5Fcf-8LPvws](https://www.youtube.com/watch?v=5Fcf-8LPvws) - easy video to follow. Also, ignore all the "root" stuff. Don't use root with ssh ... ok, there might be 1 time every 3 yrs to use root with ssh.  Also, he typed too much - he should have used "command completion" - i.e. the {tab} to fill in commands and options.

For ssh security, there are a [few other things.]("http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures")  Check the security subforum for more.  

Can't help with your phone or Windows. Sorry.  There are probably videos about each of them.

---

### Post by mooninite2 on 2016-12-17
So the client, whatever system it's on, creates a key pair. Then I have to add the clients public key to my trusted keys. Am I getting this right so far?

---

### Post by TheFu on 2016-12-17
Almost.
Client makes a key-pair.  The public key is pushed to any server you like - 1 or 50. On Linux, we use ssh-copy-id to put it in the right place, with the correct permissions. ssh/sftp are picky about the public key file having permissions.  NEVER share the private key.  Don't confuse ssh-keys with gpg-keys. Same idea, different things.

---

### Post by mooninite2 on 2016-12-17
I've pasted the public key I generated into /.ssh/authorized_keys of the user I am trying to log on as. The format is as follows:


---- BEGIN SSH2 PUBLIC KEY ----
Comment: "imported-openssh-key"
Stuff
Stuff
Stuff
...
---- END SSH2 PUBLIC KEY ----

Does it need to be on one line? 

Does the comment in there need to be removed before putting the key in my authorized_keys?
(I'm pretty sure that it came from using puttygen to convert the priv key to use with filezilla)

---

