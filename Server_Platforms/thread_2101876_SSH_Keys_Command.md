---
title: "SSH Keys Command"
date: 2013-01-05
forum: Server Platforms
---

### Post by Shogun147 on 2013-01-05
Hi there,

So in .ssh/authorized_keys we could set a command path for each key on authorization.

I know that RedHat server have a global AuthorizedKeysCommand in ssh_config and allow to write an alternative authorization script for ssh.

Is this possible in Ubuntu server or is planned to be implemented in the near future?
There are some patches for OpenSSH but is not best solution and it may have security bugs.

Any idea about this?

Thanks & Happy New Year!

---

### Post by hawkmage on 2013-01-06
Both RedHat and Ubuntu use OpenSSH and have the configuration directive AuthorizedKeysCommand.

---

### Post by Shogun147 on 2013-01-11
Yeah thanks. There just are no any info about this in man and this command is not in config file by default.
But what i've found in openssh docs is that actually this command allow just to scale authorized_keys file and no more.

So there is no possibility for this command script to get ssh pub key and do it's own authentication for users.

For example if a user try to ssh git@host:username/repository ... the command will get only 'git' username and path i think, but no pub key... like github does.

Is this possible somehow or not?

---

### Post by hawkmage on 2013-01-12
I am not sure what you are asking.  Are you wanting to have access to directories based on the ssh key that you provide?  If this is what you want then ssh is not the tool.  ssh is for securely logging in to get a command prompt.

---

### Post by Shogun147 on 2013-01-12
> **hawkmage said:**
> I am not sure what you are asking.  Are you wanting to have access to directories based on the ssh key that you provide?  If this is what you want then ssh is not the tool.  ssh is for securely logging in to get a command prompt.

I just want to do my own ssh pub key lookup from a database and identify the user in the command script, then allow or deny access.

This could be achieved by using the forced command for each key in authorized_keys.

For ex: 
command="auth git" id-rsa ...
command="auth shogun" id-rsa ...

and in auth script
#!/usr/bin/env node

var user = process.argv[2];

if (user == 'git') {
  // allow only git user
  process.exit(0);
} else {
  // deny access
  process.exit(1);
}

also there is a SSH_ORIGINAL _COMMAND in the env.

I thought that a global AuthorizedKeysCommand will run a script for all the users that try to login or run a command throught ssh and set the username and ssh pub key as arguments so the script may identify and allow or deny...

But now it looks like this could be used only to output the authorized_keys file content.
command="auth git" id-rsa ...
command="auth shogun" id-rsa ...

Looks a little nonsense to me.

---

### Post by hawkmage on 2013-01-12
From your last description it does sound like AuthorizedKeysCommand will do most of what you want by having a centralized store of allowed keys.  The one thing that you want that it will not do is set the UID.  The user name is passed by the ssh client.

The AuthorizedKeysCommand script takes a single argument which is the user name and output to stdout the keys you want to consider to be valid for that user.  The format of the output should lust like what would go into the authorized_keys file.  (Here is a page with a good reference for the file [http://linux.die.net/man/8/sshd](http://linux.die.net/man/8/sshd))

---

### Post by Shogun147 on 2013-01-12
> **hawkmage said:**
> From your last description it does sound like AuthorizedKeysCommand will do most of what you want by having a centralized store of allowed keys.  The one thing that you want that it will not do is set the UID.  The user name is passed by the ssh client.

The AuthorizedKeysCommand script takes a single argument which is the user name and output to stdout the keys you want to consider to be valid for that user.  The format of the output should lust like what would go into the authorized_keys file.  (Here is a page with a good reference for the file [http://linux.die.net/man/8/sshd](http://linux.die.net/man/8/sshd))

Yes i know this. I just hoped that this command script will allow more low level control over authorization. This will not allow to use one global username for git access over ssh for ex, like github does. ex: [email]git@github.com:Username/repository.git[/email] ...

Ok, thanks for replies.

---

