---
title: "Load balanced ssh"
date: 2014-05-28
forum: Server Platforms
---

### Post by TheFuzz4 on 2014-05-28
So I'm not sure if this is the right place for this, or if this is even a remotely good idea.

What I would like to do is setup in my firewall a load balanced rule for ssh sessions and have my firewall proxy out the ssh session.  I can do sticky sessions with this so I'm not worried about the user migrating to another host.  I mainly just want this for when I'm doing maintenance on one server then my users can still ssh in. 

Do I just need to build out a new server and give it the same hostname as the existing one?  Then just copy over the /etc/passwd, groups, shadow and the ssh keys? to the new box and rsync the /home from old to new?  Thank you in advance for your help with this, I know this is an odd request and I'm not even sure if its possible or if there is a sort of cluster setting for ssh.  I looked at sshcluster but that is not what I'm looking to do.  Thanks.

---

### Post by TheFu on 2014-05-28
ssh connections need to know the hostname/ip address. If they are different (and they will be almost always), then train the users to try serverA - if that doesn't respond, use serverB instead.  You can simplify the setup of serverB by copying the ~/.ssh/ directories for every user over, assuming they only use ssh-keys.  If you want single userid/password management - do NOT use /etc/passwd files. Use LDAP from a central server and replicate as needed to ensure it is always available to client machines trying to validate userid logins.

The same applies to home directories. Use some sort of clustering file system (GlusterFS...) or NFS.

As to having a single input address for ssh ... i suppose that could be done using a reverse proxy.

BTW, I connect to multiple different servers all the time. Some appear to be on the same IP (really just the same public IP), so using different ports is how to manage that. Whether this works for you depends on your network setup.

---

