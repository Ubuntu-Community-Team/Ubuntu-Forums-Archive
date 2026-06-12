---
title: "proftpd  cannot start inetd/xinetd"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by SlugSlug on 2012-03-28
I have a fresh install of xubuntu 12.04 and copoed over my /etc/proftpd/  dir form backup on ubutnu 10.04


upon trying to start I get 
```

ProFTPD warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
```

The config looks ok 


```

# This is a basic ProFTPD configuration file (rename it to
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName                      "ProFTPD Default Installation"
ServerType                      inetd
DefaultServer                   on

# Port 21 is the standard FTP port.
Port                            21

# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask                           022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd).
MaxInstances                    30

# Set the user and group under which the server will run.
User                            nobody
Group                           nogroup

# To cause every FTP user to be "jailed" (chrooted) into their home
# directory, uncomment this line.
DefaultRoot ~

# Normally, we want files to be overwriteable.
<Directory />
  AllowOverwrite                off
</Directory>

# A basic anonymous configuration, no upload directories.  If you do not
# want anonymous users, simply delete this entire <Anonymous> section.
<Anonymous ~ftp>
  User                          ftp
  Group                         ftp

  # We want clients to be able to login with "anonymous" as well as "ftp"
  UserAlias                     anonymous ftp

  # Limit the maximum number of anonymous logins
  MaxClients                    10

  # We want 'welcome.msg' displayed at login, and '.message' displayed
  # in each newly chdired directory.
 # DisplayLogin                  welcome.msg
 # DisplayFirstChdir             .message

  # Limit WRITE everywhere in the anonymous chroot
 # <Limit WRITE>
#    DenyAll
 # </Limit>
    <Limit DELE>
      DenyAll
    </Limit>

</Anonymous>
SystemLog /var/log/proftpd/proftpd.log
TransferLog /var/log/proftpd/xferlog

```

---

### Post by cariboo on 2012-03-28
This may be a dumb question, but do you have xinetd installed?

---

### Post by SlugSlug on 2012-03-28
Yep,

---

