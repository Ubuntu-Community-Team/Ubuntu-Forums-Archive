---
title: "HOWTO: Prevent ureadahead from Caching eCryptfs Filesystem Contents"
date: 2012-02-20
forum: Security
---

### Post by Githlar on 2012-02-20
[COLOR="Red"]I leave this here for archival purposes, please see my next post for a working solution.[/COLOR]

I've noticed this potential security hole for a while now. It may not be big or easy to break, but it could give a forensic analyst some tools to work with in order to break your filesystem encryption. If you've got samples of ciphertext and paintext, it makes it that much easier to find the key!

The problem: In a default install, on boot ureadahead watches file accesses from startup programs in order to pre-cache them for a speedier bootup. It has a run time of 45 seconds in the hopes that if you do not have autologin enabled it will stop running before you enter your password. Now, for quick typists or those with autologin enabled who have enabled the "Encrypted home folder" option during install (or moved over to an eCryptfs encrypted home folder) this poses a security risk. If your home directory is mounted prior to this 45 second run time, some portions of files and whole filenames are cached in a file for ureadahead. This undermines the expressed security of an eCryptfs filesystem.

The solution: The problem lies in the /etc/init/ureadahead-other.conf file.
Find the line that says:
```

start on mounted DEVICE=[/UL]* MOUNTPOINT=/?*

```
And replace it with:
```

start on mounted DEVICE=[/UL]* MOUNTPOINT=/?* TYPE=[!e][!c]*

```

---

### Post by cariboo on 2012-02-20
Have you contacted Dustin Kirkland about this? He is no longer employed by Canonical, but you can still contact him through his ubuntu.com email address.

---

### Post by Dave_L on 2012-02-21
> **Githlar said:**
> ...some portions of files and whole filenames are cached in a file...

Where is the information cached?

---

### Post by Githlar on 2012-03-07
DaveL, it is cached in /var/lib/ureadahead/home.[user].pack. You can view it by doing a: sudo ureadahead --dump /var/lib/ureadahead.[user].pack

It appears that I was wrong in my previous post. It turned out my ureadahead broke from some reason, so I assumed it was working when it was in fact no. The real problem lies in /etc/init/ureadahead.conf. The answer is a little less aesthetic and doesn't work as well as it should, but it does work.

Here's the solution I came up with:

[LIST=1]
[*] Undo the changes to /etc/init/ureadahead-other.conf if you made them
[*] Add the following to the end of /etc/init/ureadahead.conf:
```

post-stop script
  for file in /var/lib/ureadahead/home.*.pack; do
    case $file in
      /var/lib/ureadahead/home.charles.pack)
        wipe -f $file ;;
#INSERT_HERE
    esac
  done
end script

```
[*] If /usr/local/sbin/adduser.local exists, append to it. Otherwise, create the file and add the follow to it:
```

#!/bin/bash

if [ -e /home/.ecryptfs/$1/.ecryptfs/Private.mnt ]
then
  sed -ri "s|#INSERT_HERE|      /var/lib/ureadahead/home.$1.pack)\n        wipe -f \$file ;;\n#INSERT_HERE|" /etc/init/ureadahead.conf
fi

```
[*] Same goes for /usr/local/sbin/deluser.local:
```

#!/bin/bash

if [ $(cat /etc/init/ureadahead.conf | grep -c "home.$1.pack") -eq 1 ]
then
  sed -ir "\|      /var/lib/ureadahead/home.$1.pack.|,+1d" /etc/init/ureadahead.conf
fi

```
[*] Finally, make the files executable: sudo chroot +x /usr/local/sbin/{add,del}user.local
[/LIST]

Now, as I said, this isn't perfect. The reason is that Upstart launches ureadahead on the root device. The ureadahead launched on the root device caches all mounts that are not physically seperate devices, which includes eCryptfs filesystems mounted on /home. Unfortunately, ureadahead has no mechanism to exclude mountpoints and turning it off would be no good as your boot time would suffer.

So, with the above, the /var/lib/cache/home.[user].squashfs *does* get created, but very shortly after it gets securely wiped in-place. This is the purpose of the addition to /etc/init/ureadahead.

The adduser.local and deluser.local files are ran after their respective commands (adduser and deluser). If the adduser --encrypt-home is used to create a user, it adds that user's pack file to the list to be wiped after ureadahead does its caching (a list in /etc/init/ureadahead). The delusr.local file just removes that user's pack entry from the /etc/init/ureadahead.conf file.

---

### Post by Githlar on 2012-03-07
@cariboo907, I looked up Dustin Kirkland and he's an eCryptfs developer. The best fix for this situation would be a patch to ureadahead that adds either a parameter or config file for ureadahead that allows pruning of paths from the output. More information on [Bug #936822]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/936822").

P.S sorry about the long delay, I forgot to subscirbe to the thread.

---

