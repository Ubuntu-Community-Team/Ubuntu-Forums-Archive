---
title: "Possible commandline root flaw in Dapper Drake"
date: 2006-06-15
forum: Server Platforms
---

### Post by ljoris on 2006-06-15
Hello People,

After re-installing my greyishly old compaq 500Mhz laptop with the Dapper Drake release i found typing #su did not grant me root access but #sudo su did without having to supply any kind of authorisation.

At the time i had fetched all kinds (security etc.) updates for this release allready.

Please submit your thoughts on what could've gone wrong and/or this is indeed an 'issue' on every nearly-fresh installation.


Regards,

Joris

---

### Post by Randomskk on 2006-06-15
The sudo command remembers a password for five minutes (unless you change this) in which time any new sudo command will not require a password.
If you opened a new terminal and typed "sudo su" - or "sudo -i" - you would be asked for your user password (the sudo password) before being given a root prompt.

If you use "sudo somecommand", enter your password and one minute later on the same terminal use "sudo su" you will be given a root account.

---

### Post by aysiu on 2006-06-15
I believe the timeout is actually 15 minutes.

---

### Post by Randomskk on 2006-06-15
Whoops, my bad.
The rest of the message still applies though :P

---

### Post by ljoris on 2006-06-16
Ehm, very sorry people.

Did not use su to my knowledge. Possible this was because, to my knowledge, a root pwd had not yet been set. Tried again today, not same result.

Today, will go down in infamy! Yeaks! Who would ever post such a pressumptious thread without verifying. 

Ok, I'll remain silent then ... !bang!

---

