---
title: "SSO again"
date: 2014-01-01
forum: Resolution Centre
---

### Post by shahan3.14 on 2014-01-01
Also I don't know why it just created a new account for me when I just wanted to reset my password...  How do I consolidate my accounts the other is "shahan11"

---

### Post by coffeecat on 2014-01-01
All explained here:

[http://ubuntuforums.org/showthread.php?t=2164051](http://ubuntuforums.org/showthread.php?t=2164051)

> **Gmail/googlemail**. If you have a google email account, please note that gmail/googlemail has a few quirks that cause problems with email matching between Ubuntu One and the forum account. The email match is a simple string match. Google treats accountname@googlemail and accountname@gmail as the same, but the SSO log in setup sees them as different addresses. Also, Google allows you to add periods in the account name, thus accountname@gmail, account.name@gmail, acc.ount.name@gmail, and so on, all go to the same gmail inbox, but are seen as different addresses by SSO login. Please be sure you are using the same domain name and use of periods in the account name in Ubuntu One that are in your forum account email address when logging in for the first time.

You used the same gmail in Ubuntu One as in your original shahan11 account, but you included a period in the local part of the address in Ubuntu One that is not present in the shahan11 version. I have arranged things so that you will log into the shahan11 account next time you log in from Ubuntu One.

---

### Post by Iowan on 2014-01-01
Moved to Resolution Centre.
Your accounts differ by a "." The old account, created in June, has no SSO association. (It also has no posts logged.) To regain the old account, you would need to set the SSO **preferred** email to the one used to register the old account. Once that is done, an admin can disassociate this account from SSO, and your next login will re-link with the old account. 

A few things to consider:
Passwords were all randomized when the forum was re-loaded. They aren't really used, as SSO has taken over their function.  
We can't "merge" accounts. You can use whichever account you prefer, and we will disable the other one.  
Once an SSO account is linked to a forum account, you can change the email address on either/both and the accounts will stay linked. 
(There is still a 10-post requirement to edit your forum profile.)

---

