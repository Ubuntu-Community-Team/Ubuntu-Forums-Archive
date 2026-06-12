---
title: "Configure SSH authentication per-user"
date: 2009-01-29
forum: Security
---

### Post by kdorf on 2009-01-29
I've got somewhat of an interesting problem on my hands. Haven't yet found a solution in the man pages or on Google, so I thought I'd ask here.

I want to configure SSH to allow only a specific type of authentication for my username. Specifically, I want to use public key authentication. That's easy enough if you can modify sshd_config. The kicker is, though, that I don't have root access as it's a public box (owned by my university).

For some reason, they only allow Unix passwords to be between 6 and 8 characters. Not very secure if you ask me. I was wondering if there was some way I could set it up for my account so that it will deny attempts to log in with the password, and only use pubkey authentication.

Again, I don't have root access to this machine.

I tried editing ~/.ssh/config and setting PasswordAuthentication no but what I found is that this only prevents the program SSH from using password authentication on outgoing connections. That is, if I'm on that machine and I type "ssh somewhere" it will not bother trying to use PasswordAuthentication. Has no effect on connections coming into that machine.

Any ideas?

---

### Post by Dr Small on 2009-01-29
If you don't own the box and don't have root access, then it's impossible (at least, I believe so). It's the SSH server which controls the settings for authentication and the user can't change that.

---

### Post by kdorf on 2009-01-29
Hmm, I was afraid of that. As mature as SSH is, I'm surprised that hasn't been implemented.

While I could understand why users couldn't allow additional methods of authentication, I don't understand why users can't prevent certain types of authentications that the server would allow.

In any case, thanks for the speedy response.

---

### Post by bodhi.zazen on 2009-01-29
There are several options available to you, but you need to discuss the issue with your University IT department, they set the rules on their network not you.

This is as it should be, I doubt you would like what you are proposing if the roles were reversed (you were the sys admin and ssh allowed users to decided to change the settings so they can ssh in without a password because they found that more convenient).

---

