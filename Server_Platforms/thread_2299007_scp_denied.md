---
title: "scp denied"
date: 2015-10-15
forum: Server Platforms
---

### Post by micahpage on 2015-10-15
I am trying to pass a zip over to my server via scp but i keep getting denied. I can ssh in fine via password

I did this setup
[https://help.ubuntu.com/14.04/serverguide/openssh-server.html](https://help.ubuntu.com/14.04/serverguide/openssh-server.html)

and after this i can ssh in without password

```
[COLOR=#000000]metulburr[/COLOR][COLOR=#000000]@[/COLOR][COLOR=#000000]ubuntu[/COLOR][COLOR=#000000]~[/COLOR][COLOR=#000000]$[/COLOR][COLOR=#000000]sudo[/COLOR][COLOR=#000000]scp[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]v[/COLOR][COLOR=#000000]plugin[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]zip[/COLOR][COLOR=#000000]metulburr[/COLOR][COLOR=#000000]@[/COLOR][COLOR=#000000]python[/COLOR][COLOR=#000000]-[/COLOR][COLOR=#000000]gaming[/COLOR][COLOR=#000000].[/COLOR][COLOR=#000000]com[/COLOR][COLOR=#000000]:/[/COLOR][COLOR=#000000]var[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]www[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]html[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]menu_test[/COLOR]Executing: program /usr/bin/ssh host python-gaming.com, user metulburr, command scp -v -t /var/www/html/menu_test
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options [COLOR=#0033CC]**for**[/COLOR] *
debug1: Connecting to python-gaming.com [198.199.80.192] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: identity file /root/.ssh/id_ed25519 type -1
debug1: identity file /root/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode [COLOR=#0033CC]**for**[/COLOR] protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3 pat OpenSSH_6.6.1* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none
debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA af:75:e9:f1:49:d0:b6:e2:30:09:59:4c:13:b5:64:b1
debug1: Host 'python-gaming.com' is known and matches the ECDSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can [COLOR=#0033CC]**continue**[/COLOR]: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Trying private key: /root/.ssh/id_ecdsa
debug1: Trying private key: /root/.ssh/id_ed25519
debug1: Next authentication method: password
metulburr@python-gaming.com's password: 
debug1: Authentication succeeded (password).
Authenticated to python-gaming.com ([198.199.80.192]:22).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: scp -v -t /var/www/html/menu_test
Sending file modes: C0640 32048 plugin.zip
Sink: C0640 32048 plugin.zip
scp: /var/www/html/menu_test/plugin.zip: Permission denied
metulburr@ubuntu ~  $ debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
Transferred: sent 2604, received 2328 bytes, in 0.2 seconds
Bytes per second: sent 13705.9, received 12253.2 [COLOR=#000000]debug1:[/COLOR][COLOR=#000000]Exit[/COLOR][COLOR=#000000]status[/COLOR][COLOR=#000000]1[/COLOR]
```

What else am i missing in order to allow me to scp to my server?

---

### Post by Lars Noodén on 2015-10-15
Try without sudo so that it uses your account's keys.

---

### Post by Lars Noodén on 2015-10-15
Also, over on python-gaming.com you will need write permissions to the directory (or file) named /var/www/html/menu_test, if that is where you are writing to.

If you are the only user then a simple chown will do the job.  If you are sharing write access, then you will need to work with group permissions instead.

---

### Post by micahpage on 2015-10-15
> [COLOR=#000000]Also, over on python-gaming.com you will need write permissions to the directory (or file) named /var/www/html/menu_test, if that is where you are writing to.[/COLOR]
wow i cannot beleive i forgot this step...thanks

---

### Post by SeijiSensei on 2015-10-15
```
sudoscp-vplugin
```
I assume the lack of a space after sudo was just a typo.  What happens if you use plain "scp"?

---

### Post by micahpage on 2015-10-15
i am not sure why, but pasting into code tags here it seems to squish the first line together...and i didnt catch it. 

scp without sudo did not work. I forgot to give permissions to the directory i was writing to. problem solved. thanks.

---

### Post by slickymaster on 2015-10-15
> **micahpage said:**
> i am not sure why, but pasting into code tags here it seems to squish the first line together...and i didnt catch it. 

scp without sudo did not work. I forgot to give permissions to the directory i was writing to. problem solved. thanks.

Here's how you [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") in the forums.

---

