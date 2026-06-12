---
title: "SSH Passphrase only asked once"
date: 2011-01-29
forum: Server Platforms
---

### Post by kpuz on 2011-01-29
Hello folks,
I am a noob who is playing around with setting up a home print/file server using Ubuntu Server 10.04. I have successfully setup the server and am now configuring the SSH server so I can control remotely. 

I have setup RSA keys with a passphrase as outlined in the SSH - Ubuntu Community Documentation. However, when I log in remotely I am only asked for the passphrase the first time. Any subsequent log-ins simply take a few seconds to connect without any passphrase request. After restarting my laptop (that I use to connect remotely), I am again asked for the passphrase only the first time and subsuquent logins are without a passphrase. 

I would like to know if this is normal and if there is a way to have passphrase requested on each login. Thanks in advance.

---

### Post by egpetrich on 2011-02-01
It's not clear from your post what SSH client you are using to connect to the server. (I'll also confess that I haven't recently read the documentation to which you refer.)

Since you are using keys and a passphrase, the behavior that you describe doesn't seem very surprising to me. The passphrase typically unlocks the key on the client side. There's an authentication agent in charge of maintaining the key (securely, one hopes) and exchanging authentication information with the server. When you restart the client computer, the authentication agent shuts down and has to be restarted, at which time you need to provide the passphrase again.

Can you elaborate on the client-side software that you are using?

---

### Post by kpuz on 2011-02-03
> **egpetrich said:**
> It's not clear from your post what SSH client you are using to connect to the server. (I'll also confess that I haven't recently read the documentation to which you refer.)

Since you are using keys and a passphrase, the behavior that you describe doesn't seem very surprising to me. The passphrase typically unlocks the key on the client side. There's an authentication agent in charge of maintaining the key (securely, one hopes) and exchanging authentication information with the server. When you restart the client computer, the authentication agent shuts down and has to be restarted, at which time you need to provide the passphrase again.

Can you elaborate on the client-side software that you are using?
Thanks for your reply. I am simply using the terminal to connect remotely to my server setup.

---

### Post by egpetrich on 2011-02-04
When you say you are "simply using the terminal", I'm going to assume that you mean that you are executing the command "ssh user@remotehost" from a terminal (e.g. xterm) running on another Linux machine. If this is not what you mean, then can you elaborate on what you are doing?

Authentication is an area of SSH that I'm not very clear on. I *think* that you have an authentication agent running (typically ssh-agent on Linux machines). Your GUI under Ubuntu may start the agent running automatically when you log in. I can't say with any confidence, since I don't use desktop Ubuntu.

The Linux agent program is named "ssh-agent". From your terminal, you should be able to see if you have an agent by executing the following command:
```
ssh-add -l
```
This command should list any identities that the agent is currently holding for you.
[LIST]
[*]If you were to execute this command after a system restart, I would expect it to show no keys.
[*]If there isn't an agent running, the command will complain that it can't find a connection to the agent.
[*]If you have already connected to the remote system, then I would expect to see the agent holding one key.
[/LIST]
Your goal appears to be to keep the agent from holding on to your identity key. According to the man page, the default is for the agent to hold your key forever.

If you can determine where the agent is starting (~/.xinitrc?), you can set the default timeout to something very small, such as
```
ssh-agent -t 5
```
(Keep any other options to ssh-agent that are already present.)
If you can't find the agent's startup command, then you may be stuck. I don't see a way to force ssh to pass a lifetime value to the agent. (You can specify a lifetime with the "ssh-add" command, but I think you'd have to do this every time. Not very convenient.)

- Eric Petrich

---

