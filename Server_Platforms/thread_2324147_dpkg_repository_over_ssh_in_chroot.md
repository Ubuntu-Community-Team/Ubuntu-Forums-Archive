---
title: "dpkg repository over ssh in chroot"
date: 2016-05-11
forum: Server Platforms
---

### Post by Ralf_Nickel on 2016-05-11
Hi,


I have a dpkg repository on a 14.04 server that's available over ssh only. Apt-get works pretty well with the line
```
deb ssh://192.168.1.2/opt/landingserver/jail/repository/ ./

```

Now I have set up the ssh-server to chroot to /opt/landingserver/jail/, which also works if i connect by ssh-client or sftp. The problem is, that if i now change my apt config to 
```
deb ssh://192.168.1.2/repository/ ./

```apt-get is not able to find the repository and exit with the message
```
Failed to fetch ssh://192.168.1.2/home/sztechnik/repository/./Packages  File not found

```

i created the chroot jail with makejail and the following configuration
```
chroot="/opt/landingserver/jail/"
forceCopy=["/etc/ssh/ssh_host*","/etc/ssh/sshd*","/etc/ssh/moduli","/etc/pam.conf","/etc/security/*","/etc/pam.d/ssh","/etc/pam.d/other","/etc/hosts","/etc/nsswitch.conf","/var/run/sshd","/lib/security/*","/etc/shells","/etc/nologin","/etc/environment","/etc/motd","/etc/shadow","/etc/hosts*","/bin/*sh", "/lib/libnss*","/dev/pt*","/dev/ttyp[0-9]*", "/usr/lib/sftp-server", "/usr/bin/scp"]
preserve=["/dev/","/home"]
userFiles=["/etc/passwd","/etc/shadow"]
groupFiles=["/etc/group","/etc/gshadow"]
users=["sztechnik"]
groups=["sshd"]
testCommandsInsideJail=["start-stop-daemon -start -quiet -pidfile /var/run/sshd.pid -exec /usr/sbin/sshd"]
testCommandsOutsideJail=["ssh localhost"]
processNames=["sshd"]

```

The logfile did not give any hints about errors and i think that it has something to do with the dependencies in the chroot. Maybe one has a tip?


thanks
Ralf

---

### Post by Ralf_Nickel on 2016-05-18
> **Ralf_Nickel said:**
> Hi,
... and i think that it has something to do with the dependencies in the chroot. Maybe one has a tip?


Found out that, as it connects via ssh, it requires the find command. Added it to the makejail-dependencies and it works.


thanks for watching ;)

---

