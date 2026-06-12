---
title: "cryptsetup and reiser4: unknown fstype, bad password or options?"
date: 2007-05-06
forum: Server Platforms
---

### Post by havenonick on 2007-05-06
hello,

i compiled a new kernel, including reiser4.
/ is formatted as reiser4 and encrypted using cryptsetup.

after entering my luks password on request while booting i get the following error:
> cryptsetup: unknown fstype, bad password or options?
(gets looped, but booting works, just annoying!)

i traced down this message to
/usr/share/initramfs-tools/scripts/local-top
```
	if [ -z "$FSTYPE" ] || [ "$FSTYPE" = "unknown" ]; then
			echo "FSTYPE IS $FSTYPE" #added by me for debugging
			echo "cryptsetup: unknown fstype, bad password or options?"
			$cryptremove
			sleep 3
			continue
		fi
```

as you can see i added a new line:
echo "FSTYPE IS $FSTYPE" #added by me for debugging
which gives me "FSTYPE IS unknown" while booting.

so the problem is simple: cryptsetup doesn't know reiser4, therefore $FSTYPE is defined as unknown.
my problem is:
1) where is $FSTYPE defined? i simply can't find where it is defined.
2) how to make reiser4 known to the check which checks if the filesystem is known or not?

thanks in advance!

---

