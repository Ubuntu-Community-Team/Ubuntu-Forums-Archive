---
title: "Gitosis installation of public key not working"
date: 2010-12-05
forum: Server Platforms
---

### Post by Atolla on 2010-12-05
**I resolved the issue, see post #4.**

I've installed gitosis on a home server running Kubuntu Maverick, but am unable to get the ssh public key to work. When I try to clone, I get a password prompt.

What I did is:
On my own computer running Ubuntu Maverick
```
ssh-keygen -t rsa
```
I entered a password for the key file. Then I copied the resulting public key to the server's tmp directory:

```
scp .ssh/id_rsa.pub user@SERVER:/tmp
```

On the server I installed gitosis and initialized gitosis using my copied public ssh key file:
```

sudo apt-get install gitosis
sudo -H -u gitosis gitosis-init < /tmp/id_rsa.pub

```

The last of which results in the following output:
```

Reinitialized existing Git repository in /srv/gitosis/repositories/gitosis-admin.git/
Reinitialized existing Git repository in /srv/gitosis/repositories/gitosis-admin.git/

```

So far so good, so I go back to my own computer and do:
```
git clone gitosis@SERVER:gitosis-admin.git
```
Which results in:
```

Initialized empty Git repository in /home/me/gitosis-admin/.git/
gitosis@SERVER's password:

```

When I do a simple ssh command to the gitosis user on the server I also get the password prompt.

What am I doing wrong?

---

### Post by Atolla on 2010-12-05
Still the same problem.
I compared the contents of /srv/gitosis/.ssh/authorized_keys on the server and /home/me/.ssh/id_rsa.pub on my computer. The server does have the entry for my computer.
The keys are not identical, are they supposed to be?

---

### Post by Atolla on 2010-12-05
It turns out that the key that is in the /srv/gitosis/.ssh/authorized_keys file is the public key I had generated on the server before. However, when I delete it and run gitosis-init again, it comes back again, I even removed the generated key .ssh/id_rsa.pub in the home folder on the server. It still comes back.

Anybody have any ideas?

---

### Post by Atolla on 2010-12-05
Solved!:popcorn:

It turns out when uninstalling Gitosis, some files are left behind. Even when doing an apt-get purge the configuration files really weren't removed. Also, this means that gitosis-init can only be run once, when you want to change the key file, you have to manually remove the /srv/gitosis directory as well.

I found this out by doing a grep of the key that was erroneously in the /srv/gitosis/.ssh/authorized_keys file. I found that this key is stored somewhere in /srv/gitosis and used instead of the supplied keyfile.

---

### Post by Wi1d on 2011-11-03
> **Atolla said:**
> Solved!:popcorn:

It turns out when uninstalling Gitosis, some files are left behind. Even when doing an apt-get purge the configuration files really weren't removed. Also, this means that gitosis-init can only be run once, when you want to change the key file, you have to manually remove the /srv/gitosis directory as well.

I found this out by doing a grep of the key that was erroneously in the /srv/gitosis/.ssh/authorized_keys file. I found that this key is stored somewhere in /srv/gitosis and used instead of the supplied keyfile.

Thank you for posting this fix! I was beginning to pull out my hair.

---

