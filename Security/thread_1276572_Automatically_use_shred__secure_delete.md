---
title: "Automatically use shred / secure delete?"
date: 2009-09-27
forum: Security
---

### Post by paradigm2 on 2009-09-27
Hello, I would like to set up Ubuntu to automatically use shred / secure delete instead of the regular 'rm'.  Mainly from within Gnome/Nautilus.  This way files will be securely deleted and not as easily recoverable.

Any easy way to do this?

---

### Post by paradigm2 on 2009-09-27
I guess another related question.

In terminal I often use 'rm -rf <directory>' to delete a directory and all subdirectories.  But I notice that the shred command does not have a comparable option for '-r'.

Is there truly no easy way to do this?

---

### Post by paradigm2 on 2009-09-27
I believe I've PARTIALLY answered my own initial question:

[http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

Midway down it is the one which utilizes Nautilus actions.

However it would be nice to have this done automatically just by hitting delete as opposed to having to choose wipe in the context box......anyone?

As to the second one, I found 'wipe' has comparable syntax to 'rm'.

---

### Post by HermanAB on 2009-09-27
Howdy, you have a noble idea, but setting up a system such that it is really secure is very hard.  You have to start by thinking carefully about what threat you are trying to protect against.

If you want to protect data at rest (when the machine was turned off by you and freshly turned on by an adversary), then full disk encryption is the way to go.  This can be done with LUKS or TrueCrypt.

If you wish to protect data while the machine is running and you are logged in, then it is much more difficult.  You can encrypt individual files with GPG or TrueCrypt with some success, but it hard not to leave bits and pieces of plain text temporary files behind.  Connections to other machines should be encrypted using SSH or IPSEC.

Doing a file based secure erase is hard.  Shred and the like don't really work - for various reasons.

Hope that helps to get you thinking - keep reading - there are lots of things to learn.

---

### Post by Agent ME on 2009-09-27
> **HermanAB said:**
> Doing a file based secure erase is hard.  Shred and the like don't really work - for various reasons.
Shred works. It stops files from being recovered from the harddrive later.
The only way it could fail is if for some reason part of the file got copied to the swap section of the harddrive. It would be overwritten eventually, and most people wouldn't search the swap for usable data, but you could encrypt the swap partition. (I believe the command ecryptfs-setup-swap can set this up, but haven't tried it.)

> **paradigm2 said:**
> I guess another related question.

In terminal I often use 'rm -rf <directory>' to delete a directory and all subdirectories.  But I notice that the shred command does not have a comparable option for '-r'.

Is there truly no easy way to do this?
The find command is useful here.

This command shreds and deletes all files in the current directory (and its subdirectories):
```
find . -type f -execdir shred -fvzun1 '{}' \;
```

This command finishes the job by deleting all folders and non-file items (symlinks, fifo pipes) in the current directory and its subdirectories:
```
find . \! -type f -delete
```

---

### Post by cdenley on 2009-09-28
Shred should work fine until you start journaling data. By default, ext3 doesn't, but I'm not sure about ext4. The "srm" command has a recursive option.
```

sudo apt-get install secure-delete
man srm

```

I don't think you can configure nautilus to shred instead of deleting (it would take too long, anyway). You can add the option to the right-click menu, though.
```

sudo apt-get install nautilus-actions
nautilus-actions-config

```
path: /usr/bin/srm
parameters: -f -r %M
conditions>appears if selection contains "Both"
conditions>appears if selection has multiple...

after saving/closing, restart nautilus
```

killall nautilus
nautilus&

```

---

