---
title: "usg disa_stig Help needed to fix Landscape Client after upgrading to disa_stig"
date: 2024-06-27
forum: Security
---

### Post by gregd-anico on 2024-06-27
Hi, 

We are trying to get our servers STIG compliant.  We are running the Landscape client on the servers as well.  When it tries to run the /usr/lib/landscape/apt-update script it is getting the following error:

error: Unable to set supplementary groups IDs: Operation not permitted

It is running the command this way:

 ```
sudo -u landscape /usr/lib/landscape/apt-update
```

The file is owned by root and the group is landscape:

```
ll  /usr/lib/landscape/apt-update

```-rwxr-xr-- 1 root landscape 14488 Feb 14 23:34 /usr/lib/landscape/apt-update

Has anybody ran into this yet?  The error I see on the Landscape server side is the following:

```
Upon execvpe /usr/lib/landscape/apt-update ['/usr/lib/landscape/apt-update'] in environment id 140206224633216
:Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/twisted/internet/process.py", line 397, in _fork
    self._execChild(path, uid, gid, executable, args, environment)
  File "/usr/lib/python3/dist-packages/twisted/internet/process.py", line 468, in _execChild
    os.execvpe(executable, args, environment)
  File "/usr/lib/python3.10/os.py", line 584, in execvpe
    _execvpe(file, args, env)
  File "/usr/lib/python3.10/os.py", line 598, in _execvpe
    exec_func(file, *argrest)
PermissionError: [Errno 13] Permission denied: '/usr/lib/landscape/apt-update'

```
Any help would be appreciated.

Greg

---

### Post by 0f4d0335 on 2024-06-27
Have you tried updating the server manually with apt update? It could be an issue with a package causing the error.

---

### Post by gregd-anico on 2024-06-27
> **0f4d0335 said:**
> Have you tried updating the server manually with apt update? It could be an issue with a package causing the error.

This is a Landscape script that gets the list of packages that is on the client and passes them to the Landscape server.  But yes, I have ran it as root and it works.  It just cannot run it as the service account "landscape".  The user landscape is not an account that can login
```
grep landscape /etc/passwd
landscape:x:111:117:Landscape Owner:/var/lib/landscape:/usr/sbin/nologin

```

---

### Post by 0f4d0335 on 2024-06-27
> **gregd-anico said:**
> This is a Landscape script that gets the list of packages that is on the client and passes them to the Landscape server.  But yes, I have ran it as root and it works.  It just cannot run it as the service account "landscape".  The user landscape is not an account that can login
```
grep landscape /etc/passwd
landscape:x:111:117:Landscape Owner:/var/lib/landscape:/usr/sbin/nologin

```

Hi gregd-anico,

So I see you can run the script with root. This leads me to a few questions about landscape.

Are you running a default configuration or have you modified how the root user operates? I worked with landscape in 2019, and then I believe it ran as root. Perhaps you're trying to keep compliance with running everything as a service application account, which is a good policy, but it may lead to shell escapes, especially if you're using a sudoer file. Also then I believe you added landscape to the sudoers file? If it's a default configuration, then Landscape should've configured this for you. And there should be a basic apt update script available.

So if you're using the default configuration and are still having issues, I would contact your customer service rep from Canonical as they own the application. I can look into it later this weekend if no one else has any ideas since I'd need to install landscape into a VM if they still have trial versions just to get a clearer idea what the latest version has.

---

### Post by gregd-anico on 2024-06-27
I am asking if people that are running Landscape server and clients and are running `usg disa_stig` for the STIG compliance  have ran into this issue.  And how they were able to fix it.  Its more of a usg issue than a lanscape issue.   'usg - Audit and remediation tool for security benchmarks compliance automatization.'

---

### Post by 0f4d0335 on 2024-06-27
> **gregd-anico said:**
> I am asking if people that are running Landscape server and clients and are running `usg disa_stig` for the STIG compliance  have ran into this issue.  And how they were able to fix it.  Its more of a usg issue than a lanscape issue.   'usg - Audit and remediation tool for security benchmarks compliance automatization.'

Ah okay. The problem originally seemed to be related to how Landscape was configured as you were talking about OS security, but I'm glad the people running the program could help. We're a bit limited in the forums.

---

