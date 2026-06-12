---
title: "SSH Keys Problem"
date: 2017-07-21
forum: Security
---

### Post by CosmicFlux on 2017-07-21
Hi,

I can ssh into my Ubuntu 16.04 server using password authentication, but in the interests of hardening the security I want to use Public Key authentication. 

I have generated the keys on the client system and exported the public key from the SSH client to the authorized_keys file on the server.

When I log in remotely it says **Authentication Failed: Please Enter Password for User {my username}**

I have an encrypted **/home** so the keys have been moved to a directory on the system partition. I applied the necessary permissions and  updated the **sshd_config** file to point to the new location on the system partition.

Despite this, authentication fails.
[B][FONT=Courier New]
error: Received disconnect from xxx.xxx.x.xx port 42330:3: com.jcraft.jsch.JSchException: Auth fail [preauth]
Disconnected from xxx.xxx.x.xx port 42330 [preauth][/FONT][/B]

What am I missing?

CF

---

### Post by TheFu on 2017-07-21
You shouldn't need to move the keys somewhere odd.  ~/.ssh/ is where they are needed.

Did you use ssh-copy-id to push the public key to the server?  ssh is very particular about directory and file permissions.

I would put everything back the way it was - careful to get the permissions correct. Then start over with ssh-copy-id from the client machine.

If you aren't certain you can put things back, create a new userid on the server and start over with that.

```
$ ssh -vvvv userid@server
```
will provide verbose output and any issues should be clearly seen.

---

### Post by CosmicFlux on 2017-07-23
Hi,

Thanks for the reply.

The client machine is an Android tablet. I'm connecting to the server through an SSH application, not directly from the command line. The app has an option to generate keys and then send the public key to the server machine. I can access the system fine and dandy if I turn on password authentication, but if I want to access the server from beyond the LAN then I would much rather have a key-based authentication solution in place.

When I say I moved the keys to another location, what I meant was the **authorized_keys** file, which contains the public key sent from the tablet. The keys themselves are in [B]~/.ssh.
[/B]
I've tried removing - and purging - openssh and re-installing in order to reset, also re-creating ~/.ssh along with all necessary files. This includes regenerating new keys. 

I can connect interchangeably between my phone and tablet with no issues, the problem seems to be on the server itself. Neither device will connect when Public Key Authentication is set.

---

### Post by Habitual on 2017-07-23
[https://help.ubuntu.com/community/StricterDefaults](https://help.ubuntu.com/community/StricterDefaults)

---

### Post by HermanAB on 2017-07-24
Howdy,

If ssh won't connect, it is 99.999% of the time a permission issue.  SSH wants to have the keys and things locked down owner readable only.

---

### Post by copify on 2017-07-24
> **CosmicFlux said:**
> Hi,

I can ssh into my Ubuntu 16.04 server using password authentication, but in the interests of hardening the security I want to use Public Key authentication. 

I have generated the keys on the client system and exported the public key from the SSH client to the authorized_keys file on the server.

When I log in remotely it says **Authentication Failed: Please Enter Password for User {my username}**

I have an encrypted **/home** so the keys have been moved to a directory on the system partition. I applied the necessary permissions and updated the **sshd_config** file to point to the new location on the system partition.

Despite this, authentication fails.
[B][FONT=Courier New]
error: Received disconnect from xxx.xxx.x.xx port 42330:3: com.jcraft.jsch.JSchException: Auth fail [preauth]
Disconnected from xxx.xxx.x.xx port 42330 [preauth][/FONT][/B]

What am I missing?

CF

**[FONT=Courier New]Auth fail or blocked by firewall[/FONT]**

---

### Post by CosmicFlux on 2017-07-24
> **HermanAB said:**
> Howdy,

If ssh won't connect, it is 99.999% of the time a permission issue.  SSH wants to have the keys and things locked down owner readable only.

I have set all permissions, as per this:[ https://superuser.com/permissions-on-private-key-in-ssh-folder]("https://superuser.com/questions/215504/permissions-on-private-key-in-ssh-folder")

Problem persists.

**"Auth fail or blocked by firewall"**

Tried disabling the firewall, no joy.

Here is the message I'm getting under the **Authentication Failure** modal dialog:

> 
[FONT=Courier New]SSH_MSG_KEX_INIT[/FONT] sent
[FONT=Courier New]expecting SSH_MSG_KEX_ECDH_REPLY[/FONT]
[FONT=Courier New]ssh_rsa_verify:[/FONT] signature true
[FONT=Courier New]Host '**xxx.xxx.x.xx**' is known and matches the RSA host key[/FONT]
[FONT=Courier New]SSH_MSG_NEWKEYS[/FONT] received
[FONT=Courier New]SSH_MSG_SERVICE_REQUEST[/FONT] sent
S[FONT=Courier New]SH_MSG_SERVICE_ACCEPT[/FONT] received
[FONT=Courier New]Authentications that can continue:[/FONT] publickey, keybord-interactive, password
[FONT=Courier New]Next authentication method:[/FONT] publickey
[FONT=Courier New]DIsconnecting from[/FONT] xxx.xxx.x.xx port xxxxx


I'm beginning to get the feeling the encryption on the** /home/user** directory has something to do with this. I will try removing the encryption and see what that does.

---

### Post by TheFu on 2017-07-25
> **CosmicFlux said:**
>  I'm beginning to get the feeling the encryption on the** /home/user** directory has something to do with this. I will try removing the encryption and see what that does.

I ran with home directory encryption for about 6 months a few years ago.  No issues with ssh using keys. Nothing special was needed.  That was at least 2, perhaps 3 yrs ago. I have doubts that anything significantly changed with how the encryption is setup since then, but I don't know.

I soon realized that whole drive encryption  was more secure, faster, and allowed my normal backup solution to work, so I dumped HOME directory encryption.

---

### Post by CosmicFlux on 2017-07-26
> **TheFu said:**
> I ran with home directory encryption for about 6 months a few years ago.  No issues with ssh using keys. Nothing special was needed.  That was at least 2, perhaps 3 yrs ago. I have doubts that anything significantly changed with how the encryption is setup since then, but I don't know.

I soon realized that whole drive encryption  was more secure, faster, and allowed my normal backup solution to work, so I dumped HOME directory encryption.

You are indeed right. I managed to - somehow - get it working, even with encryption. Bit strange. I'm not sure what I did, but it's working. 

Thanks for all input guys, really appreciate it!

CF

---

