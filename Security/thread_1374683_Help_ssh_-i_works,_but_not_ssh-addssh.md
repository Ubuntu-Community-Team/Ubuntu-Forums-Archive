---
title: "Help: ssh -i works, but not ssh-add/ssh"
date: 2010-01-07
forum: Security
---

### Post by KeesM on 2010-01-07
Dear all,

I have a central file server running also ssh, and try to connect to it from the outside world using public key authorisation (final goal is to set up sshfs). Coming from a Windows background, I used to connect using PuTTY and WinSCP/FileZilla, which works great so the server is set up correctly, as is the fire wall, and the keys are valid.

I am fairly new in Ubuntu, but try to move from Windows to Linux.

When I do connect in Ubuntu 9.x using 'ssh -i <privatekeyfile> user@server', things work fine. When I first enter the keyfile using ssh-add, and then try to use 'ssh user@server', it does NOT work :( , and I get the error message:

[FONT="Courier New"]Permission denied (publickey,keyboard-interactive)[/FONT]

and in the message log on the server I see:

[FONT="Courier New"]Jan  6 11:15:14 NetDrive auth.err sshd[28392]: error: RSA_public_decrypt failed: error:0407006A:lib(4):func(112):reason(106)[/FONT]

Is there a difference using ssh -i versus ssh-add/ssh, or what else could be the reason for the connection refusal? Please keep in mind I am pretty much a beginner...

Thanks in advance,

---

### Post by Lars Noodén on 2010-01-07
> **KeesM said:**
> 
Is there a difference using ssh -i versus ssh-add/ssh, or what else could be the reason for the connection refusal? Please keep in mind I am pretty much a beginner...


Here are the two obvious things to check: 

1) Make sure the agent is running.  pgrep is an easy way:
```

# if an agent is running, the PID and name will be shown
$ pgrep -l ssh-agent
22353 ssh-agent

```

2) Make sure that the right key is loaded.  
```

ssh-add <privatekeyfile>

```

---

### Post by HDave on 2010-01-20
I've done this repeatedly on 9.10 and it doesn't work.  When I log back in the key is not there and "ssh-add -l" reports nothing.

This worked fine on 9.04.  Any ideas?

---

### Post by bodhi.zazen on 2010-01-20
> **HDave said:**
> I've done this repeatedly on 9.10 and it doesn't work.  When I log back in the key is not there and "ssh-add -l" reports nothing.

This worked fine on 9.04.  Any ideas?

It is working just fine for me on 9.10.

I am not sure, but I do not think ssh-add will not preserve your keys between sessions (I have never tried, I always clear my keys b4 I log out).

---

### Post by Lars Noodén on 2010-01-21
> **HDave said:**
> I've done this repeatedly on 9.10 and it doesn't work.  When I log back in the key is not there and "ssh-add -l" reports nothing.

This worked fine on 9.04.  Any ideas?

You probably had [keychain(1)](http://manpages.ubuntu.com/manpages/karmic/en/man1/keychain.1.html) for 9.04 and not 9.10.  keychain re-uses the ssh-agent and gpg-agent between logins.  Without keychain, the normal action is for the keys to be cleared because the agent is shutdown when you logout.  

I'm kind of assuming that logout does not necessarily mean shutting down the computer.   If you do not want to use keychain, you could find a way of having the system scripts start the agent for your user before you log in, so that it stays available after, also.  But then you have to find a way to pass the information about the agent and which socket it is using on to your desktop environment.

---

