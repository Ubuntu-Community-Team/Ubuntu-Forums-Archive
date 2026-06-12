---
title: "locked myself out while trying to secure system"
date: 2012-04-18
forum: Security
---

### Post by justo222 on 2012-04-18
the other day, i was trying to mess around with the security and it backfired.  now, i've locked myself out of the system.  i have ubuntu 11.10 64-bit installed.  all users are locked out.  i know... it was stupid of me to try this on my main system, but it was late and i was really wanting to try it out....  :(

i tried the "live install" and could not gain access to the etc folder on the hard drive.  i only had access to the logical /etc folder that the live session created.

i tried booting up in recovery mode, but that didn't let me in either.

last night, i tried a re-install choosing just the install of the program files.  everything seemed to go ok until i re-booted and tried to log in.  still locked out.

i even got desperate enough to try a complete fresh install by re-formatting the linux partitions and  was going to copy back my files from backups, but the system still won't let me on and now i can't even boot into my windows partition (located on a 2nd hard drive) on that computer.  i think i can still get on the windows hard drive by making the computer think that there is only one hard drive on the computer, but i didn't have time to try that.  besides i'm not really interested in getting windows running as much as i am the linux side.

any help on this would be appreciated.

jj

---

### Post by winh8r on 2012-04-18
This should help you get back in:

[http://www.psychocats.net/ubuntu/resetpassword]("http://www.psychocats.net/ubuntu/resetpassword")

While you are there , look at the other topics on that site for restoring sudo permissions too, in case you need them as well.

Hope this helps.

---

### Post by Skaperen on 2012-04-18
Did you mount the hard drive filesystem at some mount point like /mnt and then do chroot to run on that system from the current kernel?  Once chroot is done, /etc should be a different one.

---

### Post by justo222 on 2012-04-19
thanks guys for the quick responses!

when i got home last night, i tried the info from the psychocats site.  actually, i thought that i had tried this step before posting, but it didn't seem to work due to receiving an error about the password not being changed and this seemed to be verified by the system not allowing me to edit the files that i had corrupted.  i even double checked the command's spelling ("passwd" not "password").  anyway, i tried it again and got a different error message.  i wrote it down but forgot to bring it in to work today.  anyway, when i returned to the recovery screen and tried the "resume normal boot", i was able to get in.

i didn't think to try the chroot command, but i'll keep it in mind if i run into some added problems while trying to get this system back to normal.  one thought i had on this, though, is, wouldn't chroot ask for a password?  if so, i doubt that it would have worked initially as all accounts were locked out.  i had tried to carefully enter in the passwords to no avail.

thanks again for the quick support and great help!!
jj

---

### Post by darkod on 2012-04-19
As far as I know, chroot from live mode doesn't ask you for a password. If that's how you were planning to chroot.

Try it, before you need it next time. :)

---

### Post by Skaperen on 2012-04-19
The live mode system is operating from its own set of credentials, which are basically unprotected at the console.  So you are automatically logged in on the "ubuntu" user, and can sudo to do anything, including chroot.  The process that chroot launches will start with root permissions which should get you anything.  But if that fails somewhere, you can still manipulate the mounted filesystem or the disk partition directly in other ways, such as replacing the /mnt/etc/passwd file with another, or formatting the partition and reloading files from a backup (be sure the UUID is the same as seen in /mnt/etc/fstab).

---

