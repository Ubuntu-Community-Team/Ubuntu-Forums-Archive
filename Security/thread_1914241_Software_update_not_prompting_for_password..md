---
title: "Software update not prompting for password."
date: 2012-01-24
forum: Security
---

### Post by oneau on 2012-01-24
Hello,

Over the past few weeks I have noticed that the Update Manager is not asking for password, after I click "Install updates" button.

Initially, I thought that I must been mistaken, but just now (4:57 GMT 2012/01/24) I did an update and I was never asked for a password.

Has this been observed else where or is it just some issue on my system?

I am using Ubuntu 11.10. Let me know if any specific information is needed.

---

### Post by aeronutt on 2012-01-24
Good question. :)

But, it's a feature now.

[http://ubuntuforums.org/showthread.php?t=1811202](http://ubuntuforums.org/showthread.php?t=1811202)
[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)

---

### Post by cariboo on 2012-01-24
Software updates can only been done by the system administrator to installed packages, without a password, anything else needs a password, what's the problem?

---

### Post by oneau on 2012-01-24
Thanks for the reply. 

Good to know that it is an official feature and not some issue on my system. 

And, sorry that I didn't see the previous thread for the same topic.

---

### Post by oneau on 2012-01-24
> **cariboo907 said:**
> Software updates can only been done by the system administrator to installed packages, without a password, anything else needs a password, what's the problem?
Hello,

I am running Ubuntu on a laptop. Whenever I open "Synaptic Package Manager" or run "apt-get install" I need to enter my password. I thought this would be the case with "Update Manager" as well.

---

### Post by OpSecShellshock on 2012-01-24
> **oneau said:**
> Hello,

I am running Ubuntu on a laptop. Whenever I open "Synaptic Package Manager" or run "apt-get install" I need to enter my password. I thought this would be the case with "Update Manager" as well.

Here's how it works as I understand it:

You DO need a password when installing new software or applying package updates that make system configuration changes as part of the update (like kernel updates), and also when updating in a terminal.

You DON'T need a password when using Update Manager to update already-installed software.

---

### Post by oneau on 2012-01-24
> **OpSecShellshock said:**
> Here's how it works as I understand it:

You DO need a password when installing new software or applying package updates that make system configuration changes as part of the update (like kernel updates), and also when updating in a terminal.

You DON'T need a password when using Update Manager to update already-installed software.
Hello,

That is what I gather from the other replies, as well.

Thanks.

---

### Post by OpSecShellshock on 2012-01-24
> **oneau said:**
> Hello,

That is what I gather from the other replies, as well.

Thanks.

...and then of course I updated my kernel today without being prompted for my password, though I was prompted for it on my other system (also 11.10), so I dunno.

---

