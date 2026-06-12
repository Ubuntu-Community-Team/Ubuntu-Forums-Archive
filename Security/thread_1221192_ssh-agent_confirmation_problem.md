---
title: "ssh-agent confirmation problem"
date: 2009-07-23
forum: Security
---

### Post by 2e0spf on 2009-07-23
Hi,

I have been searching for quite some time for an answer to my problem and havnt found anything relevant so please excuse me if this has already been covered.

What i am trying to achieve is for ssh-agent to ask me to confirm usage of my private key before it logs me onto the remote server. I had this working very nicely in hardy by doing the following:

in gconf-editor unticking ssh in apps>gnome-keyring
then in a terminal:

```
ssh-add -c path.to.my.priv.key
```then when typing ssh remote.server.com a pop-up box would appear and if i pressed enter then it would go ahead and log me onto the remote server (without requiring a password) and if i clicked the cancel button or pressed esc then the agent wouldnt use my key and i would not be able to log onto the server. 

Unfortuantly on my nice shiny new install of Jaunty, when i run the ssh-add command i 
get the following:

```
me@laptop:~$ ssh-add -c_Private/id_dsa
Enter passphrase for /home/user/Private/id_dsa  (i type password here)
SSH_AGENT_FAILURE
Identity added:/home/user/Private/id_dsa (/home/user/Private/id_dsa)
me@laptop:~$
```and then when ssh'ing onto a remote server it just goes ahead and does it rather than checking with me first which is obviously quite a security risk. 

Anyone any ideas how i might resolve this?

Many thanks for your time,

Steve

---

### Post by c_wraith on 2009-07-23
> **2e0spf said:**
> when ssh'ing onto a remote server it just goes ahead and does it rather than checking with me first which is obviously quite a security risk.  Obviously?  Really?  That's...  not at all obvious.

  Exactly what risk is it exposing you to?  It's not like it sends your private key over the wire.  In fact, the big advantage to using public/private keypairs instead of passwords for authentication is that you never send your secret to anyone else.

---

### Post by 2e0spf on 2009-07-23
Because if my laptop gets hacked (yes, probably quite unlikely, but possible) i dont want 300+ servers to also get compromised...

---

### Post by aesis05401 on 2009-07-23
> **2e0spf said:**
> Because if my laptop gets hacked (yes, probably quite unlikely, but possible) i dont want 300+ servers to also get compromised...

Please update me if this info is out of date, but:

Anyone who achieves a priv escalation on your machine can immediately pwn ssh-agent (and pretty much everything else on your system) because ssh-agent relies on standard *nix permissions to keep the keyring safe.  

You original question about wanting to see a prompt is a valid one.  The only possible answer to your second post is to deploy AppArmor or run an SE setup to prevent priv escalations.  

So back on topic, does anyone know how to force a prompt from ssh-agent as per the OP first post.

---

### Post by bodhi.zazen on 2009-07-23
@aesis05401 : Your security example is circular.  Anyone who achieves a priv escalation on your machine can immediately pwn anything on the system.

Bug report (Debian) [http://www.nabble.com/Bug-493874:-ssh-add--c-reports-SSH_AGENT_FAILURE-and-doesn%27t-ask-for-confirmation-td18832956.html](http://www.nabble.com/Bug-493874:-ssh-add--c-reports-SSH_AGENT_FAILURE-and-doesn%27t-ask-for-confirmation-td18832956.html)

I would file a bug report with Ubuntu as well.

I will try this later tonight and see if I can give a better answer.

---

### Post by aesis05401 on 2009-07-23
> **bodhi.zazen said:**
> @aesis05401 : Your security example is circular.  Anyone who achieves a priv escalation on your machine can immediately pwn anything on the system.

bohdi - that was my point - that the OP wasn't asking a valid question with his second post because any priv escalation unrelated to ssh-agent would compromise ssh-agent.

I qualified what could be pwned with 'pretty much' because chrooted environments should be able to tolerate priv escalation without giving over access to the host, right?

That is how I am setting up my machine.  I started with LFS instructions and am now building little autonomous root points to run different apps.  Am I wasting my time?

---

### Post by bodhi.zazen on 2009-07-23
Depends on who you ask. IMO chroot jail can be broken out of and I would spend my time on apparmor or selinux. Depending on what you do with chroot, maintaining a chroot (updating apps) takes a ton of time. I used to run servers in a chroot, now I use OpenVZ for that. Running a user log in, with X, in a chroot, that would be a pain (yes it can be done).

vsftp can be easily configured to chroot users to $HOME , so really it depends on 

Freebsd has a robust chroot system.

At the end of the day chroot take a ton of time to set up and maintain.

---

### Post by aesis05401 on 2009-07-23
> **bodhi.zazen said:**
> *snip* ...At the end of the day chroot take a ton of time to set up and maintain.

To the OP, I am new to the security approaches bodhi.zazen mentions in the above post, but I can confirm chroot strategy takes a lot of time to maintain ;)

I hope the prompt issue is fixed in ssh-agent.  Good luck.

---

### Post by ngaur on 2012-10-16
> **c_wraith said:**
> Obviously?  Really?  That's...  not at all obvious.

  Exactly what risk is it exposing you to?  It's not like it sends your private key over the wire.  In fact, the big advantage to using public/private keypairs instead of passwords for authentication is that you never send your secret to anyone else.

2e0spf misrepresented the issue here, and the discussion got derailed.  Despite the age of this thread, I thought it worthwhile to correct the misconceptions here.

The problem with not confirming use of the agent is not about your own machine being compromised, but about your ssh-agent being forwarded over ssh to an intermediary, where anyone with access to your account orthe root account can easily make use of the connection to your ssh-agent, and connect to other servers as you so long as that agent connection is still alive.  

If you have confirmation enabled, then when someone tries to misuse your agent connection, you will see a confirmation dialog and have a chance to recognise that it is not supposed to be happening.

SSH agent forwarding is the way to go for things like copying files between remote servers, but you do need to be careful.  I don't like using agent forwarding for stepping through a bastion host though.  For that it's more secure (albeit more awkward) to use port forwarding to enable tunnelling an ssh connection from your desktop/laptop through the bastion host to the target host.

---

### Post by papibe on 2012-10-16
Please don't reply on old threads.

**Thread closed**.

---

### Post by lisati on 2012-10-16
A lot can change in three years. Thread closed.

From the [forum code of conduct]("http://ubuntuforums.org/index.php?page=policy"):
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

