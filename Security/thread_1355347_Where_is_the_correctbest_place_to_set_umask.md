---
title: "Where is the correct/best place to set umask?"
date: 2009-12-14
forum: Security
---

### Post by bananabob on 2009-12-14
I have been trying to set the umask for users to 002.

I have tried to alter this by setting it in the .bash_profile. But it does not take.

I then found that it was supposed to be set in /etc.login.defs but this doesn't seem to be the answer ([https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/71295](https://bugs.launchpad.net/ubuntu/+source/shadow/+bug/71295)). That link points to /etc/pam.d/login as being the correct place to set umask. See [http://manpages.ubuntu.com/manpages/hardy/man8/pam_umask.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pam_umask.8.html) for more information.

Now to a relative newbie this is proving to be very confusing. I would like to make the change in the correct/accepted/best place. Is there anyone who can answer this question definitively.  

I need to do this so that two users can share files when in the same group.

Thanks 
James

---

### Post by BkkBonanza on 2009-12-15
I would modify it where it is set now - that's in /etc/profile
Default is "umask 022" at end of that file.

If you want to modify it per user then it's ~/.profile but keep in mind that users can edit their own profile.

---

### Post by bananabob on 2009-12-18
Thank you - works fine.

---

