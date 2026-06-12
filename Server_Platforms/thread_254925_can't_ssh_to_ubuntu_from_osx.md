---
title: "can't ssh to ubuntu from osx"
date: 2006-09-10
forum: Server Platforms
---

### Post by xale on 2006-09-10
I can't connect through from an osx machine to a ubuntu one.
- SSH works ok on OSX
- sshd is started on ubuntu
- i can locally ssh from ubuntu to ubuntu
- i get a timeout when trying to connect from osx to ubuntu.

Here some details:

ubuntu$ ifconfig -> 192.168.1.33

ubuntu$ ssh 192.168.1.33
--> ok

osx$ ifconfig -> 192.168.1.37

osx$ ssh server.#########.ch
--> ok

osx$ ssh 192.168.1.33
--> Connection reset by server

ubuntu$ tail -n 1 /var/log/auth.log | grep sshd
--> Sep 10 22:40:34 localhost sshd[6387]: fatal: Timeout before authentication for 192.168.1.37


The most strange thing is, that i can do some sftp (ftp over ssh) from the osx machine to the ubuntu one. But it's slow.



Does anybody know what's happening?

Any help is welcome!
a.l.e

---

### Post by Balut on 2006-09-10
Try ssh username@192.168.1.33 - replacing "username" with a local user on your ubuntu box.

---

### Post by xale on 2006-09-11
dear balut,

what do you mean with "a local user on your ubuntu box"?

i'm trying to connect as a user of the ubuntu box from another box running macosx.

and yes, i'm specifying the user i want to login with on ubuntu (with both user@ and -l user) and this user is fully selfdefined in the ubuntu box (no ldap or similar; and yes, i'm actually logged in with that user; and no, trying with another user doesn't work either; and no, i don't have any other linux boxes to try to login from; and yes, i can ssh from this ubuntu to this ubuntu... mmmh, i will try with an old windows box and post the results)

i don't want to sound rude, but i've spent almost two hours on the problem and tried to get help on #ubuntu, #ubuntu-de, #ubuntu-fr, and #ubuntu-it. from #ubuntu-de i've got several "good" tips, but they didn't solve my problem.

i've googled for several error messages and topics. found some similar errors, but no path to a solution to my problem either.

i'm using ssh, ubuntu and osx since years, and i've rebooted the machine :-)

i've posted this request on the server forum and not in the beginners beacause it doesn't seem to have an easy solution... even if, at the end, the solution will probably be quite simple, i fear that it needs some more advanced tip than "check if the ssh server is installed/running" (it is!) or define the name you want to login with.

from what i've read from different sources, the problem could be related with some ipv6 features. i've turned ipv6 off and now the dns works correctly, but ssh throug ssh is stil broken.

i'm still puzzled.
have a nice day.

a.l.e

---

### Post by xale on 2006-09-11
as i thought: i can login from a windows box!

and NO, it's not (only) an osX problem: i can login from the osX box to other ssh servers!

---

### Post by BoneKracker on 2006-09-11
look for incompatabilities in the two configurations

e.g.

- are they both talking the same protocol (ver 1 vs. ver 2; and related settings that allow or don't allow)
- dsa vs rsa encryption (and related settings that allow or don't allow)

---

### Post by xale on 2006-09-11
i didn't spot any compatibility...

in the attachments you can see my sshd_config file and the ssh_config from the osX box

---

### Post by BoneKracker on 2006-09-11
It was just a thought.  You'd want to look at the ssh configuration on the Mac too.  You might also want to check the software firewall on the Mac as well - if it's turned on, it could conceivably have port 22 closed.

Sorry I don't have the answer - just hoping to give you some possible directions to look.

---

### Post by xale on 2006-09-11
- the ssh_config.txt file is from the mac (openssh there, too)
- no firewall on none of the computers (ubuntu box can do sshd for itself and a windwos box! mac box can connect to other ssh servers)

i would be happy if someone could better post my request of help...

ciao a.l.e

---

### Post by bloodniece on 2006-09-11
Are you using little snitch?   RSA or DSA key change?

---

### Post by xale on 2006-09-11
i don't know: how can i check?

... sshd is installed with standard configuration from ubuntu; ssh is installed as it standard installed from osx.

ps.: you can see the two config files in the attachement in post above!

---

### Post by Balut on 2006-09-11
Try verbose mode: ssh -v 192.168.1.33
This may give some insight on where it is failing.

---

### Post by m_bridge on 2006-10-31
i'm having the same problem, i have 3 ubuntu pc and my mac laptop, 
while the ubuntu can happily connect eachothers, i cannot reach them through ssh from my mac.

```

[>bridge< ~/] ssh -v bridge@192.168.1.42
OpenSSH_4.2p1, OpenSSL 0.9.7i 14 Oct 2005
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to 192.168.1.42 [192.168.1.42] port 22.
debug1: Connection established.
debug1: identity file /Users/bridge/.ssh/id_rsa type 1
debug1: identity file /Users/bridge/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-5ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.2
debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: An invalid name was supplied
Cannot determine realm for numeric host address

debug1: An invalid name was supplied
A parameter was malformed
Validation error

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
Connection closed by 192.168.1.42

```
that's the output trying to connect to my new edgy installation
even stranger, i can reach that machine with no problems from outside the network (dynamic dns + forwarding 22 on my router)!

---

### Post by nixfaced on 2006-11-01
In my experience this sort of thing is caused by reverse-dns lookups timing out.  Just for kicks, on the machine running sshd, add an entry to your /etc/hosts containing the IP and name of the machine you're having a hard time connecting from (the format for doing so is provided by the localhost entry).

---

