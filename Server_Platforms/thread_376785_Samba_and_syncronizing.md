---
title: "Samba and syncronizing"
date: 2007-03-05
forum: Server Platforms
---

### Post by ovelaur on 2007-03-05
Hi

I am using Samba without LDAP as a domain controller with roaming profile. I have followed different How-To's, but still have a few questions:

How do I syncronize outlook.pst file? I use POP3 email, and already has different .pst files that I syncronize, but the inbox (outlook.pst) is not syncronized. How can I best do this?

How can I make a user a local administrator on specific client computers? So that the users are able to install programs etc...

When logging off one of my client computers the, computer first asks for a server user and password, and then syncronizes ALL the registered users folders. What is wrong?

I am using Win-XP (for now) on all clients. But will start using Ubuntu for desktop on two of my clients in the near future.

My smb.conf looks like this:

[global]
workgroup = WORKGROUP
netbios name = SERVER1
server string = %h server (Samba, Ubuntu)

passdb backend = tdbsam
security = user
username map = /etc/samba/smbusers
name resolve order = wins lmhosts bcast
domain logons = yes
preferred master = yes
wins support = yes

# Set CUPS for printing
printcap name = CUPS
printing = CUPS

# Default logon
logon drive = H:
logon script = scripts/logon.bat
#logon home = \\server1\%u\.profile
logon path = \\server1\profile\%U

# Useradd scripts
add user script = /usr/sbin/useradd -m %u
delete user script = /usr/sbin/userdel -r %u
add group script = /usr/sbin/groupadd %g
delete group script = /usr/sbin/groupdel %g
add user to group script = /usr/sbin/usermod -G %g %u
add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
idmap uid = 15000-20000
idmap gid = 15000-20000

# sync smb passwords woth linux passwords
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n Retype\snew\sUNIX\spassword:* %n\n .
passwd chat debug = yes
unix password sync = yes

# set the loglevel
log level = 3

[homes]
comment = Home
valid users = %S
read only = no
browsable = no

[printers]
comment = All Printers
path = /var/spool/samba
printable = yes
guest ok = yes
browsable = no

[netlogon]
comment = Network Logon Service
path = /home/samba/netlogon
admin users = Administrator
valid users = %U
read only = no

[profile]
comment = User profiles
path = /home/samba/profiles
valid users = %U
store dos attributes = Yes
create mode = 0600
directory mode = 0700
writable = yes
browsable = no

[allusers]
comment = All Users
path = /home/shares/allusers
valid users = @users
force group = users
create mask = 0660
directory mask = 0771
writable = yes

[accounting_group]
revalidate = yes
valid users = user1,user2
writeable = yes
path = /home/accounting

---

### Post by elst on 2007-03-05
> **ovelaur said:**
> Hi

I am using Samba without LDAP as a domain controller with roaming profile. I have followed different How-To's, but still have a few questions:

How do I syncronize outlook.pst file? I use POP3 email, and already has different .pst files that I syncronize, but the inbox (outlook.pst) is not syncronized. How can I best do this?

How can I make a user a local administrator on specific client computers? So that the users are able to install programs etc...

When logging off one of my client computers the, computer first asks for a server user and password, and then syncronizes ALL the registered users folders. What is wrong?


It's been a while since I did Windows desktop stuff, but IIRC:

a) Use IMAP (or Exchange) to host mail on a server. It may be better to think of Outlook of an Exchange client rather than a general-purpose mail client, and .pst files as local caches rather than safe primary storage. I recall that we had some kind of issue with syncing .pst files, as MS apparently expected folks to use Exchange for caching and syncing Outlook data.

b) Add the domain user account to the local Administrators group for that system.

c) I think that's how it works - we saw this issue with Offline Folders and disabled it for multi-user workstations. On the whole it didn't seem particularly well-designed. Most of the logic is at the client, so it will probably be the same whether you use Samba or a Microsoft file server.

---

