---
title: "rkhunter /etc/passwd alerts"
date: 2011-12-23
forum: Security
---

### Post by mikegior on 2011-12-23
Hello all,

This morning I ran rkhunter to do a routine check of my system and it yeilded some warnings when it came to the passwd and group checks. 

```


[08:51:51] Info: Starting test name 'group_changes'
[08:51:51]   Checking for group file changes                 [ Warning ]
[08:51:51] Warning: Changes found in the group file for group 'vboxusers':
[08:51:52]          User 'michael' has been added to the group
[08:51:52] Warning: Group 'vde2-net' has been added to the group file.
[08:51:52] Warning: Group 'uml-net' has been added to the group file.

```

The line stating 'michael' has been added to the group 'vboxusers' is fine, I know I've done that, so it isn't news to me. However, the lines stating 'vde2-net' has been added to the group file as well as 'uml-net' is news to me and I'm uncertain as to what they are. It appears that these two were also added to the passwd file.

```

[08:51:51] Info: Starting test name 'passwd_changes'
[08:51:51]   Checking for passwd file changes                [ Warning ]
[08:51:51] Warning: User 'vde2-net' has been added to the passwd file.
[08:51:51] Warning: User 'uml-net' has been added to the passwd file.

```

So I went and took a look at the end of /etc/passwd to see what these two things are and this is what it entails:

```

vde2-net:x:117:130::/var/run/vde2:/bin/false
uml-net:x:118:131::/home/uml-net:/bin/false

```

/home/uml-net does not exist and /var/run/vde2 does not appear to exist either. I'm not sure what 'uml-net' and 'vde2' are, but I'm sure they aren't malicious. My main concern is a bad configuration of some sort which could lead to other issues/vulnerabilities.

Any ideas?

---

### Post by localhost8080 on 2011-12-23
> 
```

vde2-net:x:117:130::/var/run/vde2:/bin/false
uml-net:x:118:131::/home/uml-net:/bin/false

```

/home/uml-net does not exist and /var/run/vde2 does not appear to exist either. I'm not sure what 'uml-net' and 'vde2' are, but I'm sure they aren't malicious. My main concern is a bad configuration of some sort which could lead to other issues/vulnerabilities.

Any ideas?


the /bin/flase bit at the end is the shell that they use, so it basically means that these 'users' cannot log in to a shell

check
```
man 5 passwd
```
for an explination

---

### Post by mikegior on 2011-12-23
Right, having these entries still worries me. Is it okay to delete them? What could the be related to?

---

### Post by Dangertux on 2011-12-23
uml-net is a user/group utilized by user mode linux kernels. It's normal to see there.

vde2-net is a user/group utilized when virtualization is being used. So I'm assuming you're using VirtualBox, KVM or something similar

One would assume michael is a user you created? Or someone else with access to the machine created. The additional info given to you about shells is correct, and supports that these are system user accounts. Please keep in mind rkhunter sets a benchmark the first time it is run, and results from subsequent scans are analysed comparitively against that original scan. So if changes were made in the interim (even if they are legit) they may show up.

This is a false positive, unless you can not explain the username michael.

Hope this helps.

---

### Post by mikegior on 2011-12-23
The user michael is legitimate, it's mine. If that's the case, then I suppose everything is secure still. Thanks everything, this is deemed solved! :)

---

