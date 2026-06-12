---
title: "yet another (repeatable) goof by Firefox"
date: 2020-05-24
forum: The Cafe
---

### Post by Skaperen on 2020-05-24
when i use Firefox to log in with new users to some site, it normally prompts me to save the login user an password i just used.  but i found a failure situation.  the happens even with all saved passwords entirely cleared out to force a real user and password input.  the bad situation is logging in to AWS with a multi factor authentication (MFA) device.  it does not try to save the user and password.  but if one is already saved, it will use it.  if you disable the MFA on that user (from the AWS root user in the IAM service, and login to that user, again, then it will save the password.  then go back and enable the MFA, again, and now it has the IAM user saved along with its password.  of course you still need to enter the 6 digit MFA code following the password.  i think that AWS prompting for the MFA after the password is somehow the triggering culptit to Firefox's goof.

---

### Post by Hwæt on 2020-05-25
I hate 2FA with every fiber of my being. It should *always* be opt-in, not opt-out imo.

---

### Post by Skaperen on 2020-05-26
if you own the AWS account, it is opt-in.  you can just leave it unchanged and there is no MFA involved.  you can set up IAM users without MFA, too.  just don't add an MFA to them.

the only case of no choice is when all you get is a IAM user on some else's account where the other user, maybe your employer, chose to use MFA.

i chose to use MFA.

---

