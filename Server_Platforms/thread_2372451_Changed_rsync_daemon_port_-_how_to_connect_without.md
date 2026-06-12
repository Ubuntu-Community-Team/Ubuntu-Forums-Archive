---
title: "Changed rsync daemon port - how to connect without SSH"
date: 2017-09-25
forum: Server Platforms
---

### Post by warwound on 2017-09-25
I'm working on a project where we have an SSH server and an rsync server running on a number of android devices.
The android devices are each connected to a ubuntu server via USB.
The server must keep the contents of the android devices' sdcard sync'd with a master copy on the server.

This sync must be done over USB, using wifi is not an option.

My solution so far involves using the android '[adb]("https://developer.android.com/studio/command-line/adb.html#forwardports")' tool to forward local ports on the server to remote ports on the android device.

```

adb forward tcp:22 tcp:22
adb forward tcp:873 tcp:873

```

TCP traffic to port 22 on the ubuntu server is forwarded to port 22 on the android device so i can start an SSH session from the server to the android device:

```

ssh root@127.0.0.1

```

And start the rsync daemon on the android device:

```

rsync --address=127.0.0.1 --config=/sdcard/rsyncdroid/conf/rsyncd.conf --daemon --ipv4

```

Then i can run an rsync client command on the server:

```

rsync --delete -rt --stats '/cygdrive/c/Users/martin/master_copy/' '127.0.0.1::sdcard/'

```

TCP traffic to port 873 on the ubuntu server is forwarded to port 873 on the android device, and the rsync command works perfectly.
No authentication is involved or desired.

*So from the ubuntu server i can connect to an android device using default SSH and rsync ports.*
BUT I need to be able to connect 6 or more android devices and sync to each of them at the same time.

So for each android device that is connected to the ubuntu server via USB i shall forward 2 unique ports:

**Device #1**
```

adb forward tcp:4096 tcp:22
adb forward tcp:4097 tcp:873

```

**Device #2**
```

adb forward tcp:4098 tcp:22
adb forward tcp:4099 tcp:873

```

I can create an SSH session with either of these 2 android devices by specifying the **-p** parameter:

**Device #1**
```

ssh root@127.0.0.1 -p 4096

```

**Device #2**
```

ssh root@127.0.0.1 -p 4098

```

But how do i specify a port in the rsync client command?
I tried the obvious:

**Device #1**
```

rsync --delete -rt --stats '/cygdrive/c/Users/martin/master_copy/' '127.0.0.1:4097::sdcard/'

```

This causes the command to try and execute over SSH, i get prompted 'do i want to continue (y/n)?' and answer 'y' and the command fails with a segmentation fault.
I've experimented with variations of the above, nothing worked.
Also found on the [rsync documentation]("https://download.samba.org/pub/rsync/rsync.html") this syntax (in bold):

```

Access via rsync daemon:
  Pull: rsync [OPTION...] [USER@]HOST::SRC... [DEST]
        **rsync [OPTION...] rsync://[USER@]HOST[:PORT]/SRC... [DEST]**
  Push: rsync [OPTION...] SRC... [USER@]HOST::DEST
        **rsync [OPTION...] SRC... rsync://[USER@]HOST[:PORT]/DEST**

```

This looks like the synxtax i used above and that failed.

Can anyone help?

Thanks.

---

### Post by Tadaen_Sylvermane on 2017-09-25
rsync is built to use ssh, its not really an option as far as I know. i don't think you can make it use something else. maybe rewrite the code i guess, but what else would you use?

---

### Post by SeijiSensei on 2017-09-25
You can force rsync to use the insecure rsh protocol.  See "man rsync" for details.

---

### Post by warwound on 2017-09-26
> **SeijiSensei said:**
> You can force rsync to use the insecure rsh protocol.  See "man rsync" for details.

That got me thinking...

A search took me to [https://www.samba.org/ftp/rsync/rsync.html](https://www.samba.org/ftp/rsync/rsync.html) where i found:

> 
There are two different ways for rsync to contact a remote system: using a remote-shell program as the transport (such as ssh or rsh) or contacting an rsync daemon directly via TCP.
The remote-shell transport is used whenever the source or destination path contains a single colon (:) separator after a host specification.
Contacting an rsync daemon directly happens when the source or destination path contains a double colon (::) separator after a host specification, OR **when an rsync:// URL is specified** (see also the "USING RSYNC-DAEMON FEATURES VIA A REMOTE-SHELL CONNECTION" section for an exception to this latter rule).


So i changed the URL for the rsync server from:

```

127.0.0.1::sdcard/

```

to

```

rsync://127.0.0.1:<my port here>/sdcard/

```

And it works perfectly.

Thanks for both replies.

---

