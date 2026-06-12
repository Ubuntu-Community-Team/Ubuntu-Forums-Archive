---
title: "Can't run shell scripts when I log in to my machine with ssh"
date: 2008-02-24
forum: Security Discussions
---

### Post by apecar54 on 2008-02-24
Hi,

I recently installed OpenSSH on a Linux workstation running Ubuntu 7.10.  I am now using this machine via SSH from another machine - this let me do away with the second monitor on my desk.  However, I am having a problem:  when I log in using SSH, I am not allowed to run shell scripts - even as root.  For example,

```

echo "df" > test
chmod +x test
./test

-bash: ./test: Permission denied

```

I have no problems running scripts locally, and I have no problems running executables remotely.  Any idea how I can work around this?

Thanks!

---

### Post by HermanAB on 2008-02-24
Well, that is not a proper script.  What you want is more like this:

```
#! /bin/bash
df
```

---

### Post by Mr. C. on 2008-02-25
The problem is that ./test tells the shell to launch and run the file named test, which asks the kernel to execute the file.  However, the kernel has special handling for "scripts", in that it reads the first line of the script to see if there is a magical interpreter line that starts with #!/path/to/interpreter.

The kernel will then launch that interpreter, and feed to it the contents of the file as STDIN.

Since your script does not contain the interpreter line, the kernel cannot successfully execute the script (it doesn't know which interpreter to exec).

So, either add the line that HermanAB indicates, or launch with one of:

```
sh test
bash test
```

which forces the launching of the interpreter which then itself reads the contents of the command script.

MrC

---

### Post by apecar54 on 2008-02-25
Mr. C & HermanAB,

Thanks for the suggestions.  It seems odd that it would be okay to omit the interpreter line on a local terminal, but not on a remote terminal.  In any case, I added
```

#!/bin/bash
```

To the beginning of my actual script.  Running it now gives:

```

-bash: ./runmodels: /bin/bash: bad interpreter: Permission denied

```

However, if I run the script as Mr. C suggested:

```

bash ./runmodels

```

It works without problems.  So, thanks for the help!  But it seems like there must be some OpenSSH setting that is limiting what I can do from the shell?  I should also mention that I have another machine running the 64-bit edition of 7.10; I do not have this issue on that machine.

---

### Post by Mr. C. on 2008-02-25
You're making an assumption about local vs. remote which is distracting you from the issue.

The shell and kernel execute shell scripts as I've described.  There is something else different between your two systems.

It is clear for the diagnostic output that bash lives in different directories on the two systems.  The resolution for this is to generally create a symbolic link to the bash executable to allow your scripts to run on any platform.

First, find the location of the bash's on your systems.  Choose one of those full paths to use as your default #!/interpreter line in your code.  it is typical to see #!/bin/bash, #!/usr/bin/bash, and even #!/usr/local/bin/bash.  It all depends on where that distro, package, or source installation located the binary.

Assume you want to use /bin/bash.  On all the other systems that do not have /bin/bash, create the symbolic link:

   ln -s /path/to/bash/on/this/system /bin/bash

This will allow your scripts to run using the #!/bin/bash interpreter.

Again, ignore the OpenSSH idea - its a red herring.  Once SSH has created the remote shell, it is entirely out of the way in terms of the sub-shell that is then running and executing commands on your behalf.

Instead, look *clearly* at, and understand the meaning of your error messages:

```
-bash: ./test: Permission denied
```

Anytime you see a permission problem, you should examine the permissions of the file.  Since they are not shared with us here, we're left to guessing.  But it is clear that the UID in which you are running on that system does not have permission *to do something* to that file.  Examine the permissions.

MrC

---

### Post by wirelessmonkey on 2008-02-25
[QUOTE=Instead, look *clearly* at, and understand the meaning of your error messages:

Anytime you see a permission problem, you should examine the permissions of the file.  Since they are not shared with us here, we're left to guessing.  But it is clear that the UID in which you are running on that system does not have permission *to do something* to that file.  Examine the permissions.

[/QUOTE]

Thank you MRC! ~99% of application problems can be dealt with by reading the output of the application itself. Logs are beautiful things!

Best of Luck

---

### Post by apecar54 on 2008-02-25
Mr. C:

You're right - OpenSSH is a red herring.  I hooked up a monitor to the computer again and tried to run the script.  It turns out that if I execute the script from my home directory, it runs without issue.  If I place the script in ~/work, it gives me the permission error.

The issue is not with the location of bash: it is in /bin on both systems.  But there does seem to be something about the directory ~/work that is causing permission errors when I run scripts (either as myself, or as root). 

This is what the permissions for the directory look like:
```

drwxr-xr-x 12 dan  dan    4096 2008-02-25 14:18 work
drwxr-xr-x 2  dan  dan    4096 2008-02-25 14:28 work2

```

So I can run the script from ~/work but not from ~/work2.

The only special thing about ~/work is that it is shared via samba.  Could this affect things somehow?

Thanks all for the help on this one.

---

### Post by Mr. C. on 2008-02-25
There appears to be a conflict in your statements:

"If I place the script in ~/work, it gives me the permission error."

vs.

"So I can run the script from ~/work ".

I'll presume the first statement is true.  Mounted file systems can be set to disable execution ability (so as to prevent trojans, etc).  See how the file system has been mounted.  You can check mounts with:
```

mount
```

Check the samba mounts and the options stated.  You'll probably find a noexecute option set.

MrC

---

### Post by apecar54 on 2008-02-26
Thanks, Mr. C. That was exactly the issue - ~/work was mounted as a separate filesytem, with a "noexec" option.  I changed the line in the fstab and it works without issue now.

I apologize for neglecting to mention that ~/work was a separate filesystem - I had forgotten that I set up the machine that way until you raised the possibility of the noexec option.

Thanks for your help.

---

