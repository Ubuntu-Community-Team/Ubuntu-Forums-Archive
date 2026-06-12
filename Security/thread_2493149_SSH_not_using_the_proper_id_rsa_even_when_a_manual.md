---
title: "SSH not using the proper id_rsa even when a manually select it with -i"
date: 2023-12-05
forum: Security
---

### Post by GonZo on 2023-12-05
Recenlty I moved to Ubuntu 22.04 and I have this strange behaviour.

I've multiple id_rsa keys in my .ssh folder. For years I've been using them to connect to different servers but now I'm getting Denied Publickey errors

```
ssh -i ~/.ssh/id_rsa.ansible  ansible@xxxxxx.xxx.xxx
...
Received disconnect from xxxx.xxx.xxxx port 22:2: Too many authentication failures
```

the pair id_rsa.ansible and authorized_keys in xxx.xxx.xxx for ansible is correct. It works in other machines.

If I debug it with -vv I found that is trying to use a lot of different keys but last the one I manually selected

```
debug1: rekey in after 134217728 blocks
debug1: get_agent_identities: bound agent to hostkey
debug1: get_agent_identities: agent returned 10 keys
debug1: Will attempt key: /home/xxxxxxx/.ssh/id_rsa RSA SHA256:xxxxxx agent
debug1: Will attempt key: xxxx@xxxxxxxx RSA SHA256:xxxxxxxxx agent
debug1: Will attempt key: dumbuser RSA SHA256:6/OBGxxxxxxxxxxx agent
debug1: Will attempt key: xx@yyyyyyyyy   RSA SHA256:Pnl4qxxxxxxxxx agent
debug1: Will attempt key: xxxxxxxx RSA SHA256:Yy5gDAczPinIMb8nyvnodedxxxxxxx agent
debug1: Will attempt key: xxxxxxxxx@github.com RSA SHA256:GNb/Hlf89xxxxxxxx agent
......
debug1: Will attempt key: /home/xxxxxxxxxx/.ssh/id_rsa.ansible  explicit
debug2: pubkey_prepare: done
...
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/xxxxxx/.ssh/id_rsa RSA SHA256:xxxxxxxx agent
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Offering public key: xxxxx@xxxxxxxxxx.local RSA SHA256:rGEqV4DXxxxxxx agent
debug2: we sent a publickey packet, wait for reply
....
debug1: Offering public key: xxxxxx@github.com RSA SHA256:GNb/Hlf897xxxxxxxx agent
debug2: we sent a publickey packet, wait for reply
Received disconnect from 192.168.0.12 port 22:2: Too many authentication failures

```
after a few attemps the ssh server disconnects me for obvious reason...

Why is this happening? Is not just for one server, is every server. I've observed that same happens for filezilla, scp... and other ssh related services. Why is ssh priorizing other keys instead the one I manually selected?

---

### Post by TheFu on 2023-12-05
The minimum key length changed a few years ago.  Around 2017, we switched from using RSA keys to ed25519-based keys.  If you need to stay with RSA, use 4K keys.

If you are connecting to network devices, you'll need to look up which key types and lengths are require for each.

I honestly hope you aren't actually using 
```
$ ssh -i ~/.ssh/id_rsa.ansible  [email]ansible@xxxxxx.xxx.xxx[/email]
```
but have setup aliases for different connections and identities using the ~/.ssh/config file so you can say 
```
$ ssh foo
```
or scp or sftp or rsync or x2go or ... 50 other ssh-based tools
and have libssh pull the specifics from the ~/.ssh/config for each connection.  The manpage for this file which explains all the options is the manpage for the default ssh client config file ssh_config .... so **man ssh_config** is how to access that information.
```
NAME
     ssh_config — OpenSSH client configuration file

DESCRIPTION
     ssh(1) obtains configuration data from the following sources in the fol&#8208;
     lowing order:

           1.   command-line options
           2.   user's configuration file (~/.ssh/config)
           3.   system-wide configuration file (/etc/ssh/ssh_config)
...

```

Anyway, I think you'll need to create new ssh-keys of the new minimal length.  If it were me, I'd use ed25519 keys which have been preferred and get priority over RSA in recent libssh releases. And when you create them and put the public keys to the other systems, be certain the files each have the correct owner and permissions.  ssh-based tools are picky about that as well.  ssh-copy-id does what is needed automatically when transferring the public keys. If you aren't using that tool, you need to manually ensure everything is correct.

BTW, this really belongs in the "General" sub-forum, not "Chat".

---

### Post by GonZo on 2023-12-12
Thanks @TheFu for your kindly answer and sorry for not posting before. I use to config connections with ssh config file but also use some scripts that needs to emulate some other behaviours.

I will try what I found most interesting, update my old rsa keys and let you know if this solves the problem.

Regards

---

### Post by DuckHook on 2023-12-12
*Thread moved to **Security** as the more appropriate forum.*

---

### Post by aljames2 on 2023-12-12
+1 TheFu

I can add from my more limited experience, I had a  server once that wanted to use the id_ecdsa cipher to authenticate even  though I had set up a custom named ed25519 key-pair.

My fix was to, as suggested, use a ~/.ssh/config file.  I specified the IdentityFile I wanted used, and the HostKeyAlgorithm to use.  So it looks something like this:

```

Host bkpsrv
    User james
    HostName 192.168.10.231
    Port 34122
    IdentityFile ~/.ssh/kvmhst_ed25519
    HostKeyAlgorithms ssh-ed25519

```

---

