---
title: "Problems with ssh and github"
date: 2011-06-09
forum: Security
---

### Post by shawnhcorey on 2011-06-09
I trying to use ssh to connect to github but I can't.  I've set up a new RSA code but when I try to connect, I get:

```
$ ssh -v git@github.com
...
debug1: Host 'github.com' is known and matches the RSA host key.
debug1: Found key in /home/shawn/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/shawn/.ssh/id_rsa
debug1: Remote: Forced command: gerve shawnhcorey
debug1: Remote: Port forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Agent forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug1: Remote: Forced command: gerve shawnhcorey
debug1: Remote: Port forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Agent forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Authentication succeeded (publickey).
Authenticated to github.com ([207.97.227.239]:22).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_CA.UTF-8
PTY allocation request failed on channel 0

```

I've searched the web and found this as a possible solution but it didn't work:

```
rm -rf /dev/ptmx
mknod /dev/ptmx c 5 2
chmod 666 /dev/ptmx
umount /dev/pts
rm -rf /dev/pts
mkdir /dev/pts
mount /dev/pts

```

I also found a recommendation to add this to /etc/fstab:

```
# for ssh error: PTY allocation request failed on channel 0
none            /dev/pts        devpts  defaults        0       0

```

Which I did, rebooted, and it still doesn't work.

Any one have other suggestions?

---

### Post by webofunni on 2011-06-09
They are not allowing ssh access. see

[http://help.github.com/linux-set-up-git/](http://help.github.com/linux-set-up-git/)

see the last section 

```

Test everything out.
To make sure everything is working you&#8217;ll now SSH to GitHub. Don&#8217;t change the &#8220;git@github.com&#8221; part. That&#8217;s supposed to be there.

$ ssh git@github.comAttempts to ssh to github
Which should give you this:

The authenticity of host 'github.com (207.97.227.239)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?
Don&#8217;t worry, this is supposed to happen. Type &#8220;yes&#8221;.

PTY allocation request failed on channel 0
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.


```

---

### Post by shawnhcorey on 2011-06-09
The only part I get is PTY failed.  The ssh dies.  No messages.

---

### Post by webofunni on 2011-06-09
It seems they stopped printing that message :-)

It was working for me before, but now its the same as you. But I guess you will be able to sync your git. are you able to do that ?

---

### Post by shawnhcorey on 2011-06-09
> **webofunni said:**
> It seems they stopped printing that message :-)

It was working for me before, but now its the same as you. But I guess you will be able to sync your git. are you able to do that ?

I don't get any message, ssh dies.  No connection.

I get this:
```
Authenticated to github.com ([207.97.227.239]:22).
```

That should mean my git is valid.

---

### Post by webofunni on 2011-06-09
You are able to authenticate with the server, that is enough I guess. You need to contact them, if you need more info, because its their server and they manage ssh server. 

Try to add some code in to your git repo and see, if that works

---

### Post by shawnhcorey on 2011-06-09
> **webofunni said:**
> You are able to authenticate with the server, that is enough I guess. You need to contact them, if you need more info, because its their server and they manage ssh server. 

Try to add some code in to your git repo and see, if that works

I sent them a message yesterday but I have heard back.

I'll try using the repo but I'm not confident it will work.

---

### Post by webofunni on 2011-06-09
Try it and let us know, if it works or not

---

