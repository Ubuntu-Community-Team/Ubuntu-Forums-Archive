---
title: "encrypted home folder and swap"
date: 2010-08-09
forum: Security
---

### Post by kr651129 on 2010-08-09
Would the home folder/swap encryption option on the 10.04 installation cause libary read/write problems in programs like wine and cedega?

For more specifics [see my other thread]("http://ubuntuforums.org/showthread.php?t=1547209")

---

### Post by Bachstelze on 2010-08-09
> **kr651129 said:**
> could I be getting these errors because I selected an encrypted drive on the ubuntu install?

No.

---

### Post by FuturePilot on 2010-08-09
No.

---

### Post by gdonwallace on 2010-08-09
You should not be getting those errors on an encrypted folder.  When you login the encryption key is sent, and the folder is un-encrypted for your use.  The only time it would present a problem is if you logged in as a different user that does not have access to that encryped folder.  The system would not send that key to the folder.

As for swap, its not really a folder.  It can't be used for install (at least to my knowledge) as it is psudo-memory for Ubuntu to use.  Therefore, if something is loaded into swap for the entire session that you are logged in, once you log out, whatever that program was; it would be removed from swap and would not load on the next boot up / login.

---

### Post by kr651129 on 2010-08-09
Thanks for all the info, I never thought a decade old windows game would ever prove to be my biggest linux challenge to date

---

