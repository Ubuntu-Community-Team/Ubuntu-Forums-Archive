---
title: "normal user can execute scripts that normally need root"
date: 2009-08-17
forum: Security
---

### Post by malachi1990 on 2009-08-17
So I'm teaching myself bash scripting, and as my first attempt, I created this basic script to update my system and clean out unneeded packages:

sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get autoremove && sudo apt-get autoclean

So i set this up and just to see what happens, executed it with normal user privileges.  And it (the script) happily does everything, not once asking me for a password.  Had I entered the commands manually, I would have needed to enter my sudo password.  

Definitely points out the greatness of package managers, but also a serious security risk for anyone who decides to download third party scripts for any reason (unless the downloaded script would require sudo to run?).

**NOTE** this is on karmic koala, and may not apply to other releases.

---

### Post by bodhi.zazen on 2009-08-17
run the command

```
sudo -k
```

Then try again.

---

### Post by moron on 2009-08-18
> **bodhi.zazen said:**
> run the command
```
sudo -k
```
Then try again.

To add to the above, the issue is that sudo caches your user's raised permissions.  The reason you were not prompted was because relatively recently you had already successfully ran sudo.  If you had logged out and then back in as another user, you would have been prompted for the password sine that user would not be in the same state.

The "-k" flag clears the cache and always forces a request for the password next time sudo is ran.

"man sudo" is your friend.

=)

Cheers

---

### Post by bodhi.zazen on 2009-08-18
Thank you for the beautiful explanation =)

---

### Post by malachi1990 on 2009-08-23
It worked, though the interesting thing is that I had let sudo time out before trying this.  But maybe I wasn't paying attention.

---

