---
title: "sshd multiple users that share home"
date: 2011-06-01
forum: Server Platforms
---

### Post by SpinningAround on 2011-06-01
I'm setting up a svn server and would like users to share home dir. One problem is how to get sshd to identify the correct rsa key for the different users that shares the same .ssh folder. Will sshd even look for the key in a folder that isn't owned by the user trying to login?

setup
/home/svn (root:svn)

user1  | home folder 'svn' | .ssh/rsa_user1.pub
user2  | home folder 'svn' | .ssh/rsa_user2.pub
user3  | home folder 'svn' | .ssh/rsa_user3.pub

---

### Post by Lars Noodén on 2011-06-01
> **SpinningAround said:**
>  Will sshd even look for the key in a folder that isn't owned by the user trying to login?

No, it won't.  I set up an account that way to be sure and, if the authorized_keys file is not owned by the user logging in, it is not used.

---

### Post by Lars Noodén on 2011-06-01
What you could do is give the users each their home directory,  reset the **$HOME** variable to that of the group directory upon login and **cd** to the group home.  [PermitUserEnvironment](http://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files#environment.3D.22NAME.3Dvalue.22) needs to be set to yes.  By default it is disabled.

So the key could start like this, the environment variables get set before any programs are run :

```

command="cd;/bin/bash",environment="HOME=/home/grouphome" ssh-rsa AAAAB43Nz........

```

Then the **authorized_keys** file could be set to 400 and .ssh to 500 to reduce the chance of accidental changes.

---

### Post by SpinningAround on 2011-06-02
Thanks :)

---

