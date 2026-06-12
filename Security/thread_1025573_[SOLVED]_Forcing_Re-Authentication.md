---
title: "[SOLVED] Forcing Re-Authentication"
date: 2008-12-30
forum: Security
---

### Post by Kissell on 2008-12-30
I've got a nicely encrypted data partition on a server, but unfortunately it needs to be on and unlocked all the time so that clients can connect to it.  The encryption is great if the physical box is compromized, but it doesn't do anything to help if the client location is compromized.

Now, say a client connects via SFTP and has a drive mounted, and then they leave their office and leave the computer on, my server can be compromized by their negligence.  I can't trust them to even put screen saver passwords on their computers, security is too much trouble for them.

So what I would really love, is a way to kill their connections if they're idle...  I don't mind them being logged in for days straight, that's fine, as long as they're transfering a file...  but if their SSH session is just sittle their idle, I want to automatically kill it after it's been idle for like 15 minutes...  With the intent that on their end, they'd just try to use it again and it'd start a new session and ask them for their password again.  Can someone help me out with that?  It needs to be a server-side config (I can't trust the client-side), like something in sshd_config, but I haven't seen anything about how to do this.

---

### Post by kidders on 2008-12-31
Hi there,

Afaik OpenSSH doesn't allow idle timeouts to be set server-side. Support for that feature would assume that clients *have* to prompt for a password when re-initiating a timed out connection, which would be a very impractical constraint to impose.

> **Kissell said:**
> The encryption is great if the physical box is compromized, but it doesn't do anything to help if the client location is compromized.That's true. Filesystem encryption protects against the theft of your server, and the recovery of data from discarded hard disks. While the power is on, it doesn't do much more than slow everything down slightly.

> **Kissell said:**
> Now, say a client connects via SFTP and has a drive mounted, and then they leave their office and leave the computer on, my server can be compromized by their negligence.The cynic in me might ask what makes you think you can trust your users not to write their passwords on a post-it, or auto-save them into their SFTP clients.

My best suggestions are ...

**1: **Enforce a screensaver policy, by modifying everyone's power management settings, and emailing them to explain why it's important.

**2: **The only way I can think to do what the title of your thread asks would be to try something like this ...[LIST]
[*]Append a two-digit number to everyone's password on the SSH server.
[*]Every hour, change the number to correspond to the hour of the day. Existing connections would be unaffected by the change, but new sessions would have to use the new passwords.
[*]Every so often, kill any SFTP processes that have been active for more than, say, 90 minutes.
[/LIST]
Not very practical, but I thought I'd mention it anyway. The net effect would be to make saved passwords & auto-reinitiation of broken connections less likely to work (ie force re-authentication), but could kill I/O operations in progress. Exactly what you *don't* want to do, I imagine!

---

### Post by Kissell on 2008-12-31
Yeah, that all sounds right...  I was just hoping someone had something cool that I didn't know about...  I've come across a lot of neat programs from people in the forums here.

My problem with enforcing policies, like power management/screen saver timeouts, is that I don't always have access to the client PCs.  Say they're at home doing a VPN or something...  And yeah, killing after a timeout is pretty brutal...  I mean, what if they were actually doing something longer than 90 minutes...  it'd kill whatever they were working on...  

Seems like there's no way around it, except getting the users to buy into the severity of their negligence, and I'll have travelled in space before that happens.

---

