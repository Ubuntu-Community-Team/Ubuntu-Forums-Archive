---
title: "&quot;New Day&quot; Login user...?"
date: 2008-11-10
forum: Security
---

### Post by XP.NO! on 2008-11-10
I remember reading on the internet years ago that on Linux (Not sure which distribution) that you could set up a login that acts like, for lack of a better term, a new day each time you log in. As in, it will delete everything every time you log in/off.

Just wondering if there is anything like this for Ubuntu? As I would like to do my web browsing etc in that sort of safe(r) situation.

Any help would be great!

Cheers, Joe

---

### Post by randy78 on 2008-11-11
You can use the Guest account feature in Ibex... 

Also remember that Clear Private Data in Firefox doesn't clear flash cookies, so you may want to chmod 000 /home/YourUserName/.macromedia/Flash_Player to prevent them from being written there.

Your best bet is to use Full Disk Encryption (Ubuntu alternate install disk), or at the very least, an Ubuntu LiveCD.

---

### Post by amac777 on 2008-11-11
What your describing sort of sounds like a guest account. If you're not using ibex or you don't want to have to login to your own account each time you could create a guest user using these steps:

1) Create a user called "guest". (I recommend you still use a decent password though to prevent remote users from being able break in)

System -> Administration -> Users and Group -> [create new user]

2) Login as the new user and setup everything that you want to setup. Make it how you want it to be each time you login. When you are done, logout.

3) Login as your regular (admin) user and run this command to make a frozen copy of the guest account as it is right now:

```
sudo cp -a /home/guest /home/guest_frozen
```

4) Run this command to create a script to delete the old home folder and copy over the frozen version for the guest account each time the guest logs in:

```
sudo nano /etc/gdm/PostLogin/Default
```

Put this in the script and then save the file:

```
#!/bin/bash
if [ "$LOGNAME" = "guest" ] ; then
        rm -R /home/guest
        cp -a /home/guest_frozen /home/guest
fi

```

Then make the script executable with this command:

```
 sudo chmod uga+x /etc/gdm/PostLogin/Default
```

5) Now whenever you login as "guest", the account will be reset to the frozen state.

---

### Post by Gamma746 on 2008-11-11
You could put /home on a ramdisk and use pam_mount to unmount it when you log out. Maybe something like ```
/dev/shm            /home        tmpfs           nosuid,noexec,nodev,uid=1000,gid=1000,umask=0077,user 0 0

``` in your fstab.

---

