---
title: "/etc/shadow changes?"
date: 2011-09-16
forum: Server Platforms
---

### Post by RichardM_TS on 2011-09-16
Hi there,

I've written a script to assist with intrusion detection which consists of an MD5 hashlist of sensitive/important files on the system which is then compared to a current md5sum of the same files.
I'm currently testing this and have come across the MD5 hash of /etc/shadow being different on every server that I am testing this on (it's run by cron every 1am).

In which situations would /etc/shadow change?
I was under the assumption that it just stored password hashes, is there any other reason why the md5sum of this file would alter other than a password being changed?

Thanks for any insight you can provide.

---

### Post by haqking on 2011-09-16
> **RichardM_TS said:**
> Hi there,

I've written a script to assist with intrusion detection which consists of an MD5 hashlist of sensitive/important files on the system which is then compared to a current md5sum of the same files.
I'm currently testing this and have come across the MD5 hash of /etc/shadow being different on every server that I am testing this on (it's run by cron every 1am).

In which situations would /etc/shadow change?
I was under the assumption that it just stored password hashes, is there any other reason why the md5sum of this file would alter other than a password being changed?

Thanks for any insight you can provide.


The contents of each will be different based on the users and passwords in the file ?

or am i not understanding you ?

/etc/shadow contents

[LIST=1]
[*]User name : It is your login name
[*]Password: It your encrypted password. The password should be minimum 6-8 characters long including special characters/digits
[*]Last password change (lastchanged): Days since Jan 1, 1970 that password was last changed
[*]Minimum: The minimum number of days required between password  changes i.e. the number of days left before the user is allowed to  change his/her password
[*]Maximum:  The maximum number of days the password is valid (after that user is forced to change his/her password)
[*]Warn : The number of  days before password is to expire that user is warned that his/her password must be changed
[*]Inactive : The number of days after password expires that account is disabled
[*]Expire : days since Jan 1, 1970 that account is disabled i.e. an absolute date specifying when the login may no longer be used
[/LIST]

---

### Post by RichardM_TS on 2011-09-16
> **haqking said:**
> The contents of each will be different based on the users and passwords in the file ?

or am i not understanding you ?

/etc/shadow contents

[LIST=1]
[*]User name : It is your login name
[*]Password: It your encrypted password. The password should be minimum 6-8 characters long including special characters/digits
[*]Last password change (lastchanged): Days since Jan 1, 1970 that password was last changed
[*]Minimum: The minimum number of days required between password  changes i.e. the number of days left before the user is allowed to  change his/her password
[*]Maximum:  The maximum number of days the password is valid (after that user is forced to change his/her password)
[*]Warn : The number of  days before password is to expire that user is warned that his/her password must be changed
[*]Inactive : The number of days after password expires that account is disabled
[*]Expire : days since Jan 1, 1970 that account is disabled i.e. an absolute date specifying when the login may no longer be used
[/LIST]


Thanks for the informative post!
So, if I'm understanding this correctly:

> Last password change (lastchanged): Days since Jan 1, 1970 that password was last changed

This will update every day, right?
I was hoping for a method to detect password changes, I monitor /etc/passwd as well but I thought /etc/shadow would give me warning of a root password change.
Maybe I should wrap the passwd binary in a script to email the changes... hmm

---

### Post by haqking on 2011-09-16
> **RichardM_TS said:**
> Thanks for the informative post!
So, if I'm understanding this correctly:



This will update every day, right?
I was hoping for a method to detect password changes, I monitor /etc/passwd as well but I thought /etc/shadow would give me warning of a root password change.
Maybe I should wrap the passwd binary in a script to email the changes... hmm


  In Ubuntu a password change will be logged to /var/log/auth.log

 /var/log/secure in other distros i think

---

### Post by RichardM_TS on 2011-09-16
> **haqking said:**
> In Ubuntu a password change will be logged to /var/log/auth.log

 /var/log/secure in other distros i think

Fantastic, thankyou..

---

### Post by haqking on 2011-09-16
> **RichardM_TS said:**
> Fantastic, thankyou..


try it to make sure yours is though, dont take my word for it ;-)

change a password then use log file viewer to view auth.log and the last few entries should pertain to the password change.

If this solves your issue, please mark thread as solved using thread tools.

cheers

---

### Post by SeijiSensei on 2011-09-17
If you just want to check the hashes, you could strip them out and store them separately.  Then run a daily script that uses awk to pull the hashes from /etc/shadow and compares them with those in the benchmark file.

---

