---
title: "Run vbox as guest user with ubuntu host?"
date: 2012-11-25
forum: Virtualisation
---

### Post by nwalkey on 2012-11-25
Is there anyway to run Virtualbox as a guest user with an immutable virtual disk and not have it be a royal pain? I've got it set up and I'll have it working but as soon as I reboot the permissions aren't set right for the next guest account. I've tried a few different things but they all seem to fail when I reboot the computer. 
I've tried:
create the machine from guest(fails for obvious reasons)
create machine from user account(doesn't work due to permissions)
create the machine in a folder that guest has privileges outside of the tmp folder(doesn't work)
chmod 777 for all files involved with the machine (this works but when I restart it stops working. If I look in nautilus at the permissions on two of the files after a reboot it will say guest-xxxxxx(where xxxxx is the random string created from the last guest))

I cannot understand why the permissions keep changing. I've also changed the ownership to be the user account that isn't guest and that will change to the guest account when it runs. This happens on the .vbox file. The snapshots are another problem as well as they are created by the guest account...

---

