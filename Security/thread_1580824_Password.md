---
title: "Password"
date: 2010-09-23
forum: Security
---

### Post by Astroguy on 2010-09-23
When installing a fresh copy of Ubuntu, I went to change my user name and make myself administrator.
I had not yet entered any passwords.
I made a password and put it in twice, and the program comes back with "failed" please enter current password.
Is there a default password when first setting this up??
Thanks

---

### Post by CharlesA on 2010-09-23
Are you booting off a livecd or is this after you installed?

If it's after you installed, you should have set the user/password during install.

If you are booting off the livecd, there is no password prompt to use sudo (to get admin/root privlages)

---

### Post by Astroguy on 2010-09-23
I am using a live USB. I just installed the ISO (again) (with format) and started Ubuntu.
I went to system.administration.users and changed the default to my name, and clicked "administrator" for type.
Then wanted to add a PW. I had not entered any passwords so I just filled in the new PW boxes.
It came back and wanted my current PW which I have not set.
So it won't allow me to make a password until I tell it one that doesn't exist.

---

### Post by CharlesA on 2010-09-23
Are you doing the live usb with persistence?

The default password should be ubuntu///ubuntu

---

### Post by Astroguy on 2010-09-24
I just loaded the ISO without persistence. Tried ubuntu///ubuntu and get the same result.

---

### Post by CharlesA on 2010-09-24
I think the live cd is special in that the password is set and you cannot change is since they've set it up so that it's logged in automatically and sudo doesn't prompt for a password.

If this were a normal install, you could just set the password.

---

### Post by Astroguy on 2010-09-24
Thanks Charles. I haven't decided if I want to permanently install it yet. It seems to want to keep "crashing" on me and I may wait until Iknow it better.

---

