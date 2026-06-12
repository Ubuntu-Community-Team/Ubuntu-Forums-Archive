---
title: "Can't Get libpam-ssh-agent-auth Working In 13.10 Saucy"
date: 2013-11-04
forum: Server Platforms
---

### Post by SleepingProphet on 2013-11-04
Greetings everybody! I've been wrestling with this particular issue most of the day, and have been making SOME progress, but I'm still a bit stuck.
I would like to be able to authenticate an SSH session using a private key file and then use that same authentication to also authenticate sudo requests.
The system I am connecting FROM is a Windows box using Putty and Pageant.
The system I am connected TO is a Ubuntu server box running 13.10 Saucy (32-bit), and specifically OpenSSH server.
I have successfully generated a 4096-bit RSA key and am able to use that to connect to SSH sessions without issue.

To facilitate the sudo authentication, I am trying to install and use libpam-ssh-agent-auth.
It's on SourceForge and is documented over here: [http://pamsshagentauth.sourceforge.net/](http://pamsshagentauth.sourceforge.net/)
There's a LOT of info and how-tos online regarding this library.
Some of my progress:
I found that you must enable user agent forwarding AND have Pageant up and running in Putty to successfully get the the user agent to actually show up over on the Ubuntu server. I also had to add the "AllowAgentForwarding yes" to /etc/ssh/sshd_config, and the line "Defaults env_keep += SSH_AUTH_SOCK" to /etc/sudoers (after the other 3 Defaults lines).
These changes appear to have allowed the SSH authentication socket to propagate up to the sudo commands, as tested in the following way:

```
echo "$SSH_AUTH_SOCK"
/tmp/ssh-4LcT4GZtZ8/agent.6725
sudo echo "$SSH_AUTH_SOCK"
/tmp/ssh-4LcT4GZtZ8/agent.6725
```

Prior to making these changes, I was getting no SSH_AUTH_SOCK at all, and then was getting it only in the normal command prompt, not in sudo.

The final step appears to be making the appropriate configuration changes to /etc/pam.d/sudo and then getting libpam-ssh-agent-auth installed.
I have tried compiling it myself, and also installing precompiled .debs from two different PPAs as part of my quest to get this working (like I said, been trying all day :()
This final step is what has me stuck.

It is my understanding that my test case should be to run a "sudo -K" and then sudo any command. The -K resets the sudo timer, forcing re-authentication on the next sudo attempt.

I figured the Server forum would be the best place for this topic since its a pretty specific and special case that's really only of interest to guys making special use of SSH. Sorry if its in the wrong spot.
Thanks

---

