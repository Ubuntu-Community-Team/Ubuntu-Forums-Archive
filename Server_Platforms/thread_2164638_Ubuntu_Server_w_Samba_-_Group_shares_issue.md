---
title: "Ubuntu Server w/ Samba - Group shares issue"
date: 2013-08-01
forum: Server Platforms
---

### Post by rune_pedersen2 on 2013-08-01
Hi!

New to forums, and relatively new to Linux and Samba.
I'll try to explain my issue as detailed and thoroughly as possible, so please, bear with me.

I've been setting up an Ubuntu Server, and Samba Server for our company, to work as a fileserver, which has 7 computers connected.
I use Webmin to administrate users and groups, as well as Samba-administrative stuff, such as users, groups, shares, and settings.
I've got groupshares, restrictions and privileges to work as I entended, but I ran into a problem.

Using shares up against a group, let's say 'Accounting', I'll have to change the owner to the respective group, whilst that share only works to that specific group.

So the owner is root:Accounting, with chmod 775. Viola, the share works for every user which is connected to the 'Accounting' group.

The problem is that I want several groups to have access to that one share, or I'll have to give all users on the network the same rights to all shares, and I can't share that folder to any other group\users.

e.g:
I have 3 groups:
- Administration
- Accounting
- Office

I have 7 folder I want to share:
- Accounts
- Customers
- Products
- Photos
- Archive
- Machines
- Employees

Now, I want the **Administration-group** to have access to **all folders.**
I want the **Accounting-group** to have access only to **Accounts,** and **Customers.**
**Office** should have access to **Archive, Employees,** and **Machines.**

I have no idea how to do so, because if I make a share to a folder, that folder needs to have owner set to the group that has the share.

The samba-server is configured to synchronize with added\changed UNIX-users\groups.
It's set to security: *share *- I still encounter the same problem with *user*.
The server is not connected to a domain, as is none of the other users on the network.
Shares work, if the right ownership is configured, but that restricts me to sharing only to one specific user\group.

Thanks for any help!

regards,
Rune

---

### Post by Morbius1 on 2013-08-01
So you have a folder say at ... /mnt/Accounts.
You have changed ownership/permissions to: root:accounting / 775
And you want to allow access to anyone in the administration and accounting group.

So you would use "valid users" to restrict access only to those two groups and "force group" to change their individual group once samba has allowed access. Something like this:

[Accounts]
path = /mnt/Accounts
valid users = @administration, @accounting
read only = no
force group = accounting

---

### Post by rune_pedersen2 on 2013-08-02
Thx alot for the suggestion!
Makes a bit more sense now.

Unfortunately the computer I ran the server on (Hewlet Packard) shut down, and would'nt start up again. Ordered a new computer in parts, so I'll try that when I have it up and running!

---

