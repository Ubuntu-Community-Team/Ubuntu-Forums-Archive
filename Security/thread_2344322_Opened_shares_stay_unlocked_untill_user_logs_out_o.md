---
title: "Opened shares stay unlocked untill user logs out of the machine entirely!"
date: 2016-11-24
forum: Security
---

### Post by rick3332 on 2016-11-24
Hello. 

Is there a way to warn the community of users that using the file  manager as a client for shares is a dangerous practice unless you log off immediately  after, every time. It has just been exploited here, to my horror!!

The current password scheme for Nemo file manager forces security openings everytime the user views a share. The policy of leaving all shares open till logout with no way to close them is flawed! I am looking for a fix/workaround to the following issue:

Cannot "logout" of a share without  closing down and logging out the entire linux user account:
  ---- insecure because shares quietly remain open and available forever or until the user logs off, reboots, or the share admin changes the password. User cannot open a share, use it, then close that share.
  ---- forces a  logout of the entire user if the share password changes, its the only way I have found to enter a new share password.
  ---- forces the user to logout of thier linux acount just to access a share using different remote credentials. When I am testing to see if share permission changes worked it is a big job with all the logging in and out.


If the user selects "save password" then it is saved in the keyring, and if user selects "remember till logout" it is not saved. The problem is that both of these options remember it until the user logs out. If I save and then later delete from keyring it still remembers until logout. Killing nemo does not clobber the password temporary cache either.

I have searched and found the question asked repeatedly (for nemo and nautilus) of how to forget passwords and about where they are cached in the first place.  No answer.

To be in any way secure for use  with remote shares, shouldn't both file managers simply have a "forget cached passwords" button?
 Is there a CLI way to make it forget?
 Is there a  way to cripple nemo clients  so they are never allowed to access anything that requires a password?
 Is there a way to prevent nemo from even being allowed to handle passwords in the first place (as it is not secure if they remain quietly/actively open in the background)?

---

### Post by mikewhatever on 2016-11-25
Not sure what Nemo is, Nautilus in Ubuntu has three options:
1. Don't remember.
2. Remember for session.
3. Remember forever.

Each of them is useful in certain environments, and I don't see how number 2 is a problem. Forever is a long time, and users are never logged in forever.

---

