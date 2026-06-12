---
title: "SSH only allowing logins if username = current local user"
date: 2010-07-14
forum: Security
---

### Post by Chromisdesigns on 2010-07-14
I have been trying to get SSH working on my Ubuntu install, in order to run secure VNC over SSH.  Had a bunch of strange problems documented in this thread:

[http://ubuntuforums.org/showthread.php?t=1530380](http://ubuntuforums.org/showthread.php?t=1530380)

But now I am at the point where I can indeed login remotely to Ubuntu, but ONLY if the username I login with is the same as the user currently logged in locally.  If I try to login remotely using any other username, the login is rejected.

Although I can probably live with that, for what I want to do, surely that's not the way it's intended to work???

What do I need to do to allow any of a specified list of users to use SSH to login from a remote client?

And, btw, thanks to those who replied to the previous thread.  My last serious use of Unix was back in the '70's, so I am, shall we say, a bit rusty and out-of-date.;)

Regards,

Bob

---

### Post by uRock on 2010-07-14
Have you install openssh-server?

---

### Post by bodhi.zazen on 2010-07-14
> **Chromisdesigns said:**
> I have been trying to get SSH working on my Ubuntu install, in order to run secure VNC over SSH.  Had a bunch of strange problems documented in this thread:

[http://ubuntuforums.org/showthread.php?t=1530380](http://ubuntuforums.org/showthread.php?t=1530380)

But now I am at the point where I can indeed login remotely to Ubuntu, but ONLY if the username I login with is the same as the user currently logged in locally.  If I try to login remotely using any other username, the login is rejected.

Although I can probably live with that, for what I want to do, surely that's not the way it's intended to work???

What do I need to do to allow any of a specified list of users to use SSH to login from a remote client?

And, btw, thanks to those who replied to the previous thread.  My last serious use of Unix was back in the '70's, so I am, shall we say, a bit rusty and out-of-date.;)

Regards,

Bob

Which login are you having a proble with ? SSH or VNC ?

I assume it is VNC and I would tell you there are different VNC servers. The Default, vino, shares a X session with the currently logged in user. They share the same session and if no one is logged in you can not connect via vnc.

Other vnc servers, freenx and vnc4server, use separate X sessions for each user.

My guess is you are wanting a different VNC server.

---

### Post by Chromisdesigns on 2010-07-14
> **uRock said:**
> Have you install openssh-server?
 
Yes, of course.
 
It's running, which is why I am able to connect via SSH at all.  My question now is why it only works with the same username as the current local user.

---

### Post by Chromisdesigns on 2010-07-14
> **bodhi.zazen said:**
> Which login are you having a proble with ? SSH or VNC ?
 
I assume it is VNC and I would tell you there are different VNC servers. The Default, vino, shares a X session with the currently logged in user. They share the same session and if no one is logged in you can not connect via vnc.
 
Other vnc servers, freenx and vnc4server, use separate X sessions for each user.
 
My guess is you are wanting a different VNC server.
 
 
Actually, VNC remote desktop works fine, it's the SSH server that's being picky about who it lets in! Although that is useful information about VNC. I haven't tried connecting with a differrent user in VNC, since it was working fine anyway.
 
I had a lot of problems getting in through SSH at all, to begin with. Now I have it to the point where I can login with a remote terminal client via SSH, as long as the users are the same. I haven't tried VNC over SSH together yet, as I don't have the correct remote client to do that at the moment. Thought I would get SSH working correctly first, so if there were a client problem, I'd know it wasn't due to SSH.
 
Where I am going with this is to allow my wife's iPad to tunnel in via SSH and use VNC on my pc. The VNC clients for iPad that are SSH capable are not the free ones, so before I paid money I wanted the server side working right. I have a free VNC client on the iPad that is working fine, but it does not use SSH.
 
Regards,
 
Bob

---

### Post by cdenley on 2010-07-14
I have never heard of anything like that. Any local users who may be logged in should have nothing to do with openssh-server. Post some more information. What version of ubuntu are you using? Are you sure the network simply isn't configured until you login? I think that was a problem in a previous version.

Post this output for when it works and when it doesn't. What error does it give you?
```

ssh -vvv myuser@myserver

```

Then run this remotely when you can't log in.
```

nc -z -v -w 5 myserver 22

```

While not logged in, try switching to a console (ctrl+alt+f1) and login. Do you have an internet connection?
```

ifconfig
nc -z -v -w 5 google.com 80

```
ctrl+alt+f7 should bring you back to the graphical login.

Post this output from your server immediately after you fail to use SSH?
```

tail /var/log/auth.log

```

---

### Post by anomie on 2010-07-14
[QUOTE=Chromisdesigns]But now I am at the point where I can indeed login remotely to Ubuntu, but ONLY if the username I login with is the same as the user currently logged in locally.  If I try to login remotely using any other username, the login is rejected.[/QUOTE]

I'd also be curious to see output from: 
```
$ sudo egrep -i 'allow|deny' /etc/ssh/sshd_config
```

The behavior you're describing is frankly pretty bizarre. Have you implemented any sort of drive / filesystem encryption by chance?

---

### Post by anomie on 2010-07-14
[QUOTE=cdenley]Are you sure the network simply isn't configured until you login?[/QUOTE]

That's an interesting point. 

@Chromisdesigns: when you say "If I try to login remotely using any other username, the login is rejected," what do you mean exactly? Are you even prompted for authentication credentials?

---

### Post by uRock on 2010-07-14
The OP means he/she can't connect to the machine unless someone is signed in to the account locally.

To the OP, When you set up the network manager did you check the box at the bottom of the screen(Available to all users) so that all accounts can use the same connection or do you have to give the keyring a password? If this box isn't checked, then this may be the problem.

---

### Post by anomie on 2010-07-14
That's not how I interpreted his comments, but we'll see. 

If he can't establish a TCP handshake (which the nc(1) tests would confirm), then it indeed points to a networking issue.

---

### Post by bodhi.zazen on 2010-07-14
> **cdenley said:**
> I have never heard of anything like that.

Well, it will not work in the OP is trying to log in as say root =)

But I agree, it sounds unusual and we need additional information.

---

### Post by Chromisdesigns on 2010-07-14
> **anomie said:**
> That's an interesting point. 
 
@Chromisdesigns: when you say "If I try to login remotely using any other username, the login is rejected," what do you mean exactly? Are you even prompted for authentication credentials?
 
The client I am using has the password stored locally before login is attempted.  With the users different, login is rejected.  Auth log shows the request coming in, and rejected as "unknown user".  What happens on the iPad client is the client prompts for the password again, it is assuming the stored one is wrong.  Entering the correct password again gives the same results.
 
When users are the same, it works flawlessly every time, with no change to the password stored in the local client.
 
There is definitely a network connection present -- when network is not active, remote client will not even identify the server and attempt to connect to it.  The error message on the remote client is different, in that case.

---

### Post by Chromisdesigns on 2010-07-14
@Cdenley:
 
"Then run this remotely when you can't log in."
 
Code:
nc -z -v -w 5 myserver 22
 
uhh...how could I run that remotely, given it won't let me in??? 
 
 
"Post this output from your server immediately after you fail to use SSH?"
 
Code:
tail /var/log/auth.log
 
 
Below is an example of auth log entries for failed request. This one is attempt to login via SSH to localhost by user not= current logged in user. Fails the same way for remote SSH access.
 
 
(I replaced actual user id in this post with "**dummy user name**")
 
Jul 13 19:20:28 ubuntu sshd[3974]: Invalid user **dummy user name** from 127.0.0.1
Jul 13 19:20:28 ubuntu sshd[3974]: Failed none for invalid user **dummy user name** from 127.0.0.1 port 34240 ssh2
Jul 13 19:20:50 ubuntu sshd[3974]: pam_unix(sshd:auth): check pass; user unknown
Jul 13 19:20:50 ubuntu sshd[3974]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost 
 
Once again, it fails if the users are not the same whether or not attempted SSH login is over the net or local on the same machine! Works both ways, too, if the users are the same.
 
 
This is Ubuntu 10.04, persistent live image installed on memory stick via Pendrive's installer.

---

### Post by anomie on 2010-07-14
I believe he meant to say, "run that locally". 

In any case, it's a moot point if you're seeing authentication attempts in your auth log. If you see those, this is not a network issue.

---

### Post by anomie on 2010-07-14
[QUOTE=Chromisdesigns]Jul 13 19:20:28 ubuntu sshd[3974]: Invalid user **dummy user name** from 127.0.0.1
Jul 13 19:20:28 ubuntu sshd[3974]: Failed none for invalid user **dummy user name** from 127.0.0.1 port 34240 ssh2
[/QUOTE]

Bingo. Your ssh client is jacked up. Can you reproduce the same problem from a different workstation? (i.e. Try this from a Linux or Windows workstation.)

---

### Post by Chromisdesigns on 2010-07-14
> **anomie said:**
> I'd also be curious to see output from: 
```
$ sudo egrep -i 'allow|deny' /etc/ssh/sshd_config
```
 
The behavior you're describing is frankly pretty bizarre. Have you implemented any sort of drive / filesystem encryption by chance?
 
 
There is no AllowUsers or DenyUsers section in sshd_config at all. As I understand it, that means any authorized user should be able to connect.
 
No drive or file encryption.  Straight stock install of 10.04 live image.

---

### Post by Chromisdesigns on 2010-07-14
> **anomie said:**
> Bingo. Your ssh client is jacked up. Can you reproduce the same problem from a different workstation? (i.e. Try this from a Linux or Windows workstation.)
 
 
You do understand that this happens when I try to login via SSH from the SAME machine using the Ubuntu client, right? just $ ssh -l [EMAIL="username@localhost"]username@localhost[/EMAIL] fails if users are not identical...
 
The iPad client fails or succeeds the same way as the client on the local machine.
 
I can try it from a client on another windows machine, but based on the above, I think the problem is server-side, not in the client.
 
Bob

---

### Post by anomie on 2010-07-14
Ah, I misunderstood your earlier post. I thought you were saying the string "**dummy user name**" was showing up in your log. (Now I see that you replaced that. Makes things a little confusing, IMO. :))

OK, given all the symptoms lumped together, it *seems* like sshd is simply unable to query your passwd file to confirm the existence of a user (unless that user is logged in). 

[quote=Chromisdesigns]This is Ubuntu 10.04, persistent live image installed on memory stick via Pendrive's installer.[/quote]

Perhaps this is related - I have no idea what mechanisms are in place for that live distro's incarnation (e.g. filesystem encryption?). Sorry, dunno. The diagnosis is straightforward enough, but the real, underlying cause less so.

---

### Post by Chromisdesigns on 2010-07-14
> **uRock said:**
> The OP means he/she can't connect to the machine unless someone is signed in to the account locally.

To the OP, When you set up the network manager did you check the box at the bottom of the screen(Available to all users) so that all accounts can use the same connection or do you have to give the keyring a password? If this box isn't checked, then this may be the problem.


@uRock -- You do indeed! :p  We are making progress, but not quite done...

This got me partway there.  It was not checked in network setup, and I did have to supply keyring password for logins.  I checked it, rebooted, and now am PARTWAY there:

I can now login to LOCALHOST (only) from the SSH client on the same machine, using a different username than the one currently signed in.  In other words, $ ssh -l somedifferentuser localhost now works fine!  It didn't before, showing exactly the same authentication error as trying it remotely.


HOWEVER, I still can't get in via SSH client from another machine on the net, unless I am already signed in locally with the same user (same as before):

Here is the log extract showing successful connection when the users are the same, and refused connection when not the same users:  ( I've changed the real user names, for obvious reasons):


Jul 14 11:07:13 ubuntu sshd[4106]: pam_sm_authenticate: Called
Jul 14 11:07:13 ubuntu sshd[4106]: pam_sm_authenticate: username = [firstguy]
Jul 14 11:07:13 ubuntu sshd[4106]: Accepted password for firstguy from 10.0.0.4 port 51777 ssh2
Jul 14 11:07:13 ubuntu sshd[4106]: pam_unix(sshd:session): session opened for user firstguy by (uid=0)
Jul 14 11:07:33 ubuntu sshd[4168]: Received disconnect from 10.0.0.4: 11: 
Jul 14 11:07:33 ubuntu sshd[4106]: pam_unix(sshd:session): session closed for user firstguy
Jul 14 11:09:21 ubuntu sshd[4193]: Invalid user anotherguy from 10.0.0.4
Jul 14 11:09:21 ubuntu sshd[4193]: Failed none for invalid user anotherguy from 10.0.0.4 port 51780 ssh2
Jul 14 11:09:21 ubuntu sshd[4193]: pam_unix(sshd:auth): check pass; user unknown
Jul 14 11:09:21 ubuntu sshd[4193]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=nancys-ipad.local 
Jul 14 11:09:24 ubuntu sshd[4193]: Failed password for invalid user anotherguy from 10.0.0.4 port 51780 ssh2
Jul 14 11:09:46 ubuntu sshd[4196]: Invalid user anotherguy from 10.0.0.4
Jul 14 11:09:46 ubuntu sshd[4196]: Failed none for invalid user anotherguy from 10.0.0.4 port 51781 ssh2
Jul 14 11:09:46 ubuntu sshd[4196]: pam_unix(sshd:auth): check pass; user unknown
Jul 14 11:09:46 ubuntu sshd[4196]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=nancys-ipad.local 
Jul 14 11:09:48 ubuntu sshd[4196]: Failed password for invalid user anotherguy from 10.0.0.4 port 51781 ssh2

Any more ideas?  Your first one fixed the localhost problem, anyway!

Regards,

Bob

---

### Post by bodhi.zazen on 2010-07-14
Are you using wireless ?

At any rate, open Network Manager, and set the connection as available to all users.

Hard to find a screen shot, but see this:

[img]http://jintu.files.wordpress.com/2009/08/screenshot-4.png?w=450&h=453[/img]

See the little box at the bottom, "Available to all users" ? - use that option.

Someone will probably need to log in though unless you configure your wireless card outside of network manager.

---

### Post by Chromisdesigns on 2010-07-14
OK, an update to my reply to uRock above.  The situation is more complex than I thought.

I've done some more testing, and here are the current results.

I have two users, with the same priv's, one is the default user "ubuntu" and the other we'll call "otherguy".

"ubuntu" is able to login via SSH  on the same machine, using localhost, ie $ ssh -l ubuntu localhost.  This works fine.  It works regardless of whether the current signed-in user is ubuntu or otherguy.

"ubuntu" is also able to login remotely, from the iPad client on my LAN, again it doesn't matter whether the local user is ubuntu, otherguy, or if nobody at all is signed in locally.  The remote connection works fine, as long as the user = "ubuntu"

However, "otherguy" is not able to get in via SSH, whether attempted on the same machine or remotely.  Access fails the same way in either case, as shown in log file extracts posted before.

So I can't get in even locally with $ ssh -l otherguy localhost, regardless of who is already signed in -- fails if current local user is otherguy, also fails if current local user is ubuntu.

Yes, I am using wireless connections.  I did go back and check "allow all accounts to use connection" as suggested by "uRock".  Before that, I couldn't get connected even as "ubuntu" unless "ubuntu" was already signed on.

I don't understand what's going on with the differences between the user names.  I checked and made sure they both have the same priveleges.

Now what?  Obviously, I'd rather not be using "ubuntu" for remote access, as every ubuntu  install has that user.  But right now, it's the only one that works.

If it matters, I was signed on initially as "ubuntu" when the keyring was created and given a password.  Note that now I have "allow all users" checked in the network config, I am not asked for the keyring password anymore, regardless of who signs in.

Regards,

Bob

---

### Post by Chromisdesigns on 2010-07-14
> **anomie said:**
> Ah, I misunderstood your earlier post. I thought you were saying the string "**dummy user name**" was showing up in your log. (Now I see that you replaced that. Makes things a little confusing, IMO. :))

OK, given all the symptoms lumped together, it *seems* like sshd is simply unable to query your passwd file to confirm the existence of a user (unless that user is logged in). 



Perhaps this is related - I have no idea what mechanisms are in place for that live distro's incarnation (e.g. filesystem encryption?). Sorry, dunno. The diagnosis is straightforward enough, but the real, underlying cause less so.

Anomie, please see my updated post, near the end of the thread.  It works for one user, but not for the other.  They have the same priveleges.  I'm thinking it has to do with the keyring, somehow.

---

### Post by cariboo on 2010-07-14
This might seem like a dumb question, but does "otherguy" have an account on the computer you are trying to log on to?

We might as well try to cover all the bases.

---

### Post by Chromisdesigns on 2010-07-14
> **cariboo907 said:**
> This might seem like a dumb question, but does "otherguy" have an account on the computer you are trying to log on to?
 
We might as well try to cover all the bases.
 
Yep.  And I can sign on as "otherguy" just fine, through the local signon menu, or swtich users to "otherguy".

---

### Post by bodhi.zazen on 2010-07-14
I suspect it has something to do with your network or network configuration and not ssh.

Can you try a wired connection or temporarily disable your wireless security (WEP/WPA).

Again, I advise you to configure your wireless network manually and not with Network Manager.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by Chromisdesigns on 2010-07-14
> **bodhi.zazen said:**
> I suspect it has something to do with your network or network configuration and not ssh.
 
Can you try a wired connection or temporarily disable your wireless security (WEP/WPA).
 
Again, I advise you to configure your wireless network manually and not with Network Manager.
 
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
 
Yes, I can try it on another machine that's on an ethernet connection.  You may be correct, I'm beginning to think it has something to do with the keyring config or setup.
 
I'll try it on the other machine and report back.
 
Bob

---

### Post by Chromisdesigns on 2010-07-14
> **bodhi.zazen said:**
> I suspect it has something to do with your network or network configuration and not ssh.

Can you try a wired connection or temporarily disable your wireless security (WEP/WPA).

Again, I advise you to configure your wireless network manually and not with Network Manager.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)


OK, I'm now running on a different PC, no wireless, ethernet connection to the router.  Some of the symptoms have changed, others not -- it's worse, not better, overall...


FIrst, there is still something weird going  on with the user accounts.  Same as before, only "ubuntu" can do a successful ssh -l username localhost.  "otherguy" fails, "ubuntu" works.  Again, doesn't matter who is signed in locally at the time on this machine.  I checked, again, and the both users have the exact same privileges.

However, remote connections now do not work at all.  Remote client just hangs when trying to connect, doesn't matter which user I try.  Eventually it times out.  Remote client is still wireless, but server is now wired.  I wonder if all this is still pointing to keyring, or maybe wireless config?  I have to say I'm surprised by this change, though.

I'm going to try it with a wireless connection, but on the new pc.  Suspect it will behave as it did on the original machine, though.

Regards,

Bob

---

### Post by bodhi.zazen on 2010-07-14
Are you using encrypted home partitions ? ssh keys ?

Can you post the full output of

```
ssh user@server -vv
```

Look at the output of ssh -vv with a working and broken user, both from  localhost and remote.

And check the logs (/var/log) on the server for any errors as well.

Other thoughts are -

What ssh server are you using ? We assume open-ssh, but are you using an  alternate ?

What authentication protocol are you using ? Just passwords, or keys ?

---

### Post by Chromisdesigns on 2010-07-14
> **bodhi.zazen said:**
> Are you using encrypted home partitions ? ssh keys ?

Can you post the full output of

```
ssh user@server -vv
```Look at the output of ssh -vv with a working and broken user, both from  localhost and remote.

And check the logs (/var/log) on the server for any errors as well.

Other thoughts are -

What ssh server are you using ? We assume open-ssh, but are you using an  alternate ?

What authentication protocol are you using ? Just passwords, or keys ?


No encryption.  Don't believe the remote client app uses ssh keys, only password. However, the one I will eventually use does use keys, preferably.

open-ssh is the server.  Results of good and failed logins posted below.  Cannot post results from the remote iPad client, don't have that ability on the client.  When it works, using "ubuntu" a normal session comes up.  Otherwise, the password prompt comes up again.  After several attempts, client reports failed authorization.

Next, when I tried it on different computer with a wired connection, got same results for attempts at login to localhost.  However, remote client would not connect at all, for either user.  Don't know why. That machine had full connectivity, otherwise -- could go to internet, etc., and both users could sign on locally as normal.  Rebooted and tried it using a wireless connection, all results the same, either wired or wireless on that machine.

 I'm back on the original machine now, and remote client again works fine for user ubuntu.

Here is the result of a successful login to localhost using ssh ubuntu@localhost -vv:

ubuntu@ubuntu:~$ ssh ubuntu@localhost -vv
OpenSSH_5.3p1 Debian-3ubuntu3, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/ubuntu/.ssh/identity type -1
debug1: identity file /home/ubuntu/.ssh/id_rsa type -1
debug1: identity file /home/ubuntu/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu3
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu3
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 129/256
debug2: bits set: 482/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/ubuntu/.ssh/known_hosts:1
debug2: bits set: 498/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/ubuntu/.ssh/identity ((nil))
debug2: key: /home/ubuntu/.ssh/id_rsa ((nil))
debug2: key: /home/ubuntu/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ubuntu/.ssh/identity
debug1: Trying private key: /home/ubuntu/.ssh/id_rsa
debug1: Trying private key: /home/ubuntu/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
ubuntu@localhost's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug2: channel 0: request shell confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


Last login: Wed Jul 14 13:41:16 2010 from nancys-ipad.local
ubuntu@ubuntu:~$ 

*** note evidence that I successfully logged in before from iPad remote client, above ***

and here is same results using the other user:  (replaced actual username with "other")

ubuntu@ubuntu:~$ ssh other@localhost -vv
OpenSSH_5.3p1 Debian-3ubuntu3, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/ubuntu/.ssh/identity type -1
debug1: identity file /home/ubuntu/.ssh/id_rsa type -1
debug1: identity file /home/ubuntu/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu3
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu3
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 139/256
debug2: bits set: 508/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/ubuntu/.ssh/known_hosts:1
debug2: bits set: 517/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/ubuntu/.ssh/identity ((nil))
debug2: key: /home/ubuntu/.ssh/id_rsa ((nil))
debug2: key: /home/ubuntu/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/ubuntu/.ssh/identity
debug1: Trying private key: /home/ubuntu/.ssh/id_rsa
debug1: Trying private key: /home/ubuntu/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
other@localhost's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
other@localhost's password: 

*** as you can see, it fails to authenticate for "other" using correct password  ***


*** here is the auth log snippet, beginning when ubuntu login was accepted, and then "other" login denied


Jul 14 13:44:46 ubuntu sshd[4317]: Accepted password for ubuntu from 127.0.0.1 port 41309 ssh2
Jul 14 13:44:46 ubuntu sshd[4317]: pam_unix(sshd:session): session opened for user ubuntu by (uid=0)
Jul 14 13:46:58 ubuntu sshd[4382]: Received disconnect from 127.0.0.1: 11: disconnected by user
Jul 14 13:46:58 ubuntu sshd[4317]: pam_unix(sshd:session): session closed for user ubuntu
Jul 14 13:47:10 ubuntu sshd[4417]: Invalid user other from 127.0.0.1
Jul 14 13:47:10 ubuntu sshd[4417]: Failed none for invalid user other from 127.0.0.1 port 33831 ssh2
Jul 14 13:47:30 ubuntu sshd[4417]: pam_unix(sshd:auth): check pass; user unknown
Jul 14 13:47:30 ubuntu sshd[4417]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost 
Jul 14 13:47:32 ubuntu sshd[4417]: Failed password for invalid user other from 127.0.0.1 port 33831 ssh2

---

### Post by bodhi.zazen on 2010-07-14
Well that output suggest the user does not exist on your system.

> Failed password  for invalid user other from 127.0.0.1 port 33831 ssh2 		                   		  		  		  		  		 		 			 				

You would need to add a user "other" on your ssh server.

If the user exists on your ssh server, what are the permissions of /etc/passwd ?

---

### Post by Chromisdesigns on 2010-07-14
> **bodhi.zazen said:**
> Well that output suggest the user does not exist on your system.



You would need to add a user "other" on your ssh server.

If the user exists on your ssh server, what are the permissions of /etc/passwd ?


The actual user (not "other") exists -- I've been logged in as that user dozens of times, it just won't login over ssh.  Unlike "ubuntu".

ubuntu@ubuntu:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
messagebus:x:102:107::/var/run/dbus:/bin/false
avahi-autoipd:x:103:110:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:104:111:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
couchdb:x:105:113:CouchDB Administrator,,,:/var/lib/couchdb:/bin/bash
speech-dispatcher:x:106:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
usbmux:x:107:46:usbmux daemon,,,:/home/usbmux:/bin/false
haldaemon:x:108:114:Hardware abstraction layer,,,:/var/run/hald:/bin/false
kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:110:115:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:111:117:RealtimeKit,,,:/proc:/bin/false
saned:x:112:118::/home/saned:/bin/false
hplip:x:113:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:114:120:Gnome Display Manager:/var/lib/gdm:/bin/false
ubuntu:x:999:999:Live session user,,,:/home/ubuntu:/bin/bash
sshd:x:115:65534::/var/run/sshd:/usr/sbin/nologin
other:x:1000:1000:other,,,,:/home/other:/bin/bash   *** note: here is the "other" user ***
ubuntu@ubuntu:~$ 


*** note, again I have changed the actual other username to "other" in above results. 

sshd:x:115:65534::/var/run/sshd:/usr/sbin/nologin  *** this line looks suspicious, though...***

BTW, I now have a VNC over SSH client on the iPad, and it behaves identically, both in shell mode and in VNC mode.  So long as the client user = "ubuntu", everything works.  I am using password auth, not keys, at the moment.  One note -- the first time I logged in with the new client, I had to enter the keyring password on the local server before it would connect.  Since then, it goes right in.

Regards,

Bob

---

### Post by Chromisdesigns on 2010-07-14
> **bodhi.zazen said:**
> Well that output suggest the user does not exist on your system.



You would need to add a user "other" on your ssh server.

If the user exists on your ssh server, what are the permissions of /etc/passwd ?

other@ubuntu:~$ ls -l /etc/passwd
-rw-r--r-- 1 root root 1810 2010-07-14 08:09 /etc/passwd
other@ubuntu:~$ 


Here are the permissions for the "other" user.

---

### Post by cariboo on 2010-07-14
never mind

---

### Post by Chromisdesigns on 2010-07-18
FIXED -- I found the problem, and you are NOT going to believe what it was:

If the full user name and the short user name are not the same, SSH login fails.

If the full user name and short user name are the same, SSH works correctly.

That's it -- end of story.

I suspect this is either a bug, period, or perhaps a bug in the GUI user admin tools, which may be getting confused about which version of the user name to write where.

In any case, it has nothing to do with the "ubuntu" user, depends strictly on whether you change the short name to something different from the long user name when adding the user (using the GUI tools)!

Geez!:D

---

### Post by bodhi.zazen on 2010-07-18
> **Chromisdesigns said:**
> FIXED -- I found the problem, and you are NOT going to believe what it was:

If the full user name and the short user name are not the same, SSH login fails.

If the full user name and short user name are the same, SSH works correctly.

That's it -- end of story.

I suspect this is either a bug, period, or perhaps a bug in the GUI user admin tools, which may be getting confused about which version of the user name to write where.

In any case, it has nothing to do with the "ubuntu" user, depends strictly on whether you change the short name to something different from the long user name when adding the user (using the GUI tools)!

Geez!:D

That is a new on on me ...

Thank you for posting the solution.

---

### Post by BiGNoRm6969 on 2010-07-24
I have the SAME problem.

I created my user using the command line with "useradd".

I am not sure to understand what you means by 

"If the full user name and the short user name are not the same, SSH login fails.

If the full user name and short user name are the same, SSH works correctly."

My username is "dummy" and the full name is "Testing User". Are your referring to that?

I am unable to log with ssh on the user "dummy"

---

### Post by Chromisdesigns on 2010-07-24
> **BiGNoRm6969 said:**
> I have the SAME problem.
 
I created my user using the command line with "useradd".
 
I am not sure to understand what you means by 
 
"If the full user name and the short user name are not the same, SSH login fails.
 
If the full user name and short user name are the same, SSH works correctly."
 
My username is "dummy" and the full name is "Testing User". Are your referring to that?
 
I am unable to log with ssh on the user "dummy"
 
Yes, precisely.  If both names were "dummy" you would have no problem logging into SSH.
 
If they are different, you get hosed!

---

### Post by CharlesA on 2010-07-24
Wow. I've not heard of that before. Thanks for posting the solution.

---

### Post by BiGNoRm6969 on 2010-07-25
Still does not work for me..

---

### Post by Chromisdesigns on 2010-07-25
> **BiGNoRm6969 said:**
> Still does not work for me..
 
check and make sure ssh server is running.  Then, if so, can you login as "ubuntu"?
 
i.e.  ssh -l ubuntu localhost
 
If so, then you know ssh is working to some degree.  If not, then SSH is probably hosed up, unless you modified the ubuntu account / user some way.
 
If you can get it as ubuntu, then create a new user "newguy".  Make the short and long names the same.
 
Can newguy get in with ssh -l newguy localhost  ?
 
If not, check your sshd_config file to make sure you don't have something strange with allow/deny user sections.

---

### Post by oomar on 2010-07-25
i may have missed something but its not true at all if the username and full name of a user are different that SSH login fails...


I have the full name as Logan N Collins and the user is logan and I can login fine...

---

### Post by Chromisdesigns on 2010-07-25
> **oomar said:**
> i may have missed something but its not true at all if the username and full name of a user are different that SSH login fails...
 
 
I have the full name as Logan N Collins and the user is logan and I can login fine...
 
 
The bug may be treating them as the same since the long name is space-separated. I didn't try this example. It definitely fails if they are not the same initial string, i.e. "Joe_blow" and "mack".
 
I'm pretty sure, but can't remember for certain, that it will fail if the two names are "joe_blow" and "joe"
 
The space separator may be a special case where it works.

---

### Post by oomar on 2010-07-25
> **Chromisdesigns said:**
> The bug may be treating them as the same since the long name is space-separated.  I didn't try this example.  It definitely fails if they are not the same initial string, i.e.   "Joe_blow" and "mack".

No i saw that and was responding to it. I'm curious to the validity of it. My SSH user that I use has a full name of Logan N Collins. But the short name is logan. and i can use ssh with it just fine. Or perhaps thats not truly what the full and short names of the user is? But to my understanding that doesn't make sense. Idk I'm a little confused.

EDIT: ok thats not the part i meant to quote... you edited yours before i replied lol

---

### Post by cdenley on 2010-07-26
```

cdenley@ubuntu:~$ ssh mack@192.168.0.136
mack@192.168.0.136's password: 
Linux vmware 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

mack@vmware:~$ getent passwd mack
mack:x:1001:1001:joe_blow,,,:/home/mack:/bin/bash
mack@vmware:~$ apt-cache policy openssh-server
openssh-server:
  Installed: 1:5.3p1-3ubuntu4
  Candidate: 1:5.3p1-3ubuntu4
  Version table:
 *** 1:5.3p1-3ubuntu4 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/main Packages
        100 /var/lib/dpkg/status
     1:5.3p1-3ubuntu3 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages

```

---

### Post by Chromisdesigns on 2010-07-26
> **cdenley said:**
> ```

cdenley@ubuntu:~$ ssh mack@192.168.0.136
mack@192.168.0.136's password: 
Linux vmware 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS
 
Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/
 
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
 
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
 
mack@vmware:~$ getent passwd mack
mack:x:1001:1001:joe_blow,,,:/home/mack:/bin/bash
mack@vmware:~$ apt-cache policy openssh-server
openssh-server:
  Installed: 1:5.3p1-3ubuntu4
  Candidate: 1:5.3p1-3ubuntu4
  Version table:
 *** 1:5.3p1-3ubuntu4 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/main Packages
        100 /var/lib/dpkg/status
     1:5.3p1-3ubuntu3 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/main Packages

```
 
 
Interesting. I don't know what to tell you, except it fails on my machine under these conditions! I was using longer user names, though -- I'll have to experiment further to see if the length makes a difference. Hard to see how it could, though, given Ubuntu user names can be up to 32 chars.
 
I'll post back results of the experiments in a day or two.

---

