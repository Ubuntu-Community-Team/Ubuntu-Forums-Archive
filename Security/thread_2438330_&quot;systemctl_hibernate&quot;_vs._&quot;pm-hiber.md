---
title: "&quot;systemctl hibernate&quot; vs. &quot;pm-hibernate&quot; and passwords"
date: 2020-03-10
forum: Security
---

### Post by frankvw on 2020-03-10
On my Lubuntu 18.04 install, hibernation worked right out of the box from the command line. (I am about to add the relevant options to the power menu.) However, during tests I noticed one odd thing.

```
sudo systemctl hibernate
``` hibernates the system and, upon waking up, displays the message ```
resuming from /path/to/swapfile
``` followed by the login (username/password) interface. So the system is basically secure on waking. (Yes, I *am* aware of the security risks involved with having a memdump stored in an unencrypted swapfile!)

```
sudo pm-hibernate
``` also hibernates the system but, upon waking up, does not display the ```
resuming from /path/to/swapfile
``` message and does not ask for a password; the system is fully accessible right away.

Why is this? Is this normal behavior and, if so, what is the rationale behind it?

// FvW

---

### Post by TheFu on 2020-03-10
No 18.04 system here with any PM tools, but on 16.04 ... 

```
$ which pm-hibernate
/usr/sbin/pm-hibernate
tf@istar:~$ file /usr/sbin/pm-hibernate
/usr/sbin/pm-hibernate: symbolic link to ../lib/pm-utils/bin/pm-action
tf@istar:~$ file /usr/lib/pm-utils/bin/pm-action   
/usr/lib/pm-utils/bin/pm-action: POSIX shell script, ASCII text executable
```

So, if your system is setup similarly, take a look inside /usr/lib/pm-utils/bin/pm-action to see what is really happening?

Just a thought.

I don't hibernate due to security considerations. I either use standby, if the machine isn't moving, or completely shutdown, if it will be moving.  Also, I don't use a swap file. Always use a swap partition or swap LV. Just because something is a default, that doesn't mean it is a good idea.

---

### Post by EuclideanCoffee on 2020-03-10
This article provides a tutorial on creating passwords for encrypted swap.

[https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)

I've also found this forum thread: [https://ubuntuforums.org/showthread.php?t=2398264](https://ubuntuforums.org/showthread.php?t=2398264)

I believe this function is not native because it would be a burden to have to enter a password upon wake up. If you encrypt the LVM partition, the swap should already be encrypted. Therefore the encryption is encapsulated, which is quite typical in design. I don't think that means it encrypts upon hibernate. It will just appears like it's not encrypted while booted because while on, the system is unencrypted. I'd be curious if you or someone could provide information on the state of encryption in hibernation after following the steps above. I actually don't think it improves your security beyond having a second password on a non-encrypted system.

As far as I understand, this is "unsafe," but I haven't provided the work to show you why that is the case.

---

### Post by TheFu on 2020-03-10
Hibernation stores the frozen contents of RAM into the swap file.  It leaves that storage unlocked, so any encrypted container using DM-crypt/LUKS will be unencrypted while the system is hibernated into the swap file/partition/logical volume. 

I use an encrypted LVM setup.  The layout is: [https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987)
Everything except /boot/ and /boot/efi/ are contained within a LUKS container. If the machine is booted, that LUKS container is open/unlocked.

Whether there is a password needed or not when coming out of standby is controlled by the screen saver "timeout" setting.  The screensaver used it user-controlled.  DEs often provide their own, which might be buggy.  It is possible to disable that and use **xscreensaver**, which has always worked as expected for me. Pick your own poison.

---

### Post by EuclideanCoffee on 2020-03-10
Right, I assumed that's the case.

I believe LUKS2 has encrypted hibernation as a builtin feature. At least that's what I heard from Fedora last time I attended a webinar about such things.

---

### Post by frankvw on 2020-03-11
> **TheFu said:**
> So, if your system is setup similarly, take a look inside /usr/lib/pm-utils/bin/pm-action to see what is really happening?

Thanks for pointing me into the right direction! Yes, pm-action is a script in which **run_hooks sleep hibernate** appears to be the active ingredient. In other words, a totally different thing from the approach followd by **systemctl**. 

> **TheFu said:**
> I don't hibernate due to security considerations. I either use standby, if the machine isn't moving, or completely shutdown, if it will be moving.  Also, I don't use a swap file. Always use a swap partition or swap LV. Just because something is a default, that doesn't mean it is a good idea.
Agreed. The particular machine I'm hibernating has no secure data on it whatsoever, so security is no big concern here, but I still prefer a login password. :) And yes, I've got a swap LV; I don't do swap files myself, either. I prefer properly organized partitions to keep system, swap and data separate.

// FvW

---

### Post by frankvw on 2020-03-11
> **EuclideanCoffee said:**
> As far as I understand, this is "unsafe," but I haven't provided the work to show you why that is the case.
In my OP I did note that I am aware of the security risks of storing a memdump into an unencrypted swap file. I wouldn't do that on a system with any security consideration but this particular laptop holds no security-sensitive stuff whatsoever. I still prefer a login password, though. :)

// FvW

---

### Post by EuclideanCoffee on 2020-03-11
> **frankvw said:**
> I still prefer a login password, though. :)

Did you find the links from the community wiki helpful? Your feedback would help others attempting the same process which is already documented. This may also be a chance to update or remove the tutorial if it's unhelpful. There's another method I posted from the forums too, from a community expert on disk encryption.

---

