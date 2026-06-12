---
title: "[IDEA] Simple Password protection/locking of individual folders"
date: 2009-02-22
forum: Ubuntu Brainstorm
---

### Post by macvr on 2009-02-22
hi all,

i know that the usual rationale is to advice, setup different user account and this prevents the other users from accessing your folders.

but this does not prevent users with knowledge of the root password from accessing your folders/files, so how does this keep your files safe!*[atleast in windowsXP there is no root user which can allow access to other administrator's files]* 

so wouldnt it be nice that there are individual folders that are password locked by the one user to not be accessed by the other user?

i dont understand of the whole rationale of the different users accounts in the home computers!different user accounts just allow different setup of the desktop... what if the family doesnt need different setups? just one person want to lock a certain private folder!

why not have all the users use the same account but like how firefox has the profiles option,let the applications have profiles? wouldnt that be less space consuming? rather than having different multiple users having the same software installed in each account!

[COLOR="Blue"]EDIT: i'v worked out this little hack ,its by using the permissions settings, which works for me like a charm > [/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showpost.php?p=6777859&postcount=1]("http://ubuntuforums.org/showpost.php?p=6777859&postcount=1")[/COLOR]

---

### Post by mc4100 on 2009-02-23
There's too many variables for this to work. There would need to be some cross platform implementation, and even then there will be ways around. Just use encryption.

---

### Post by iponeverything on 2009-02-23
If your using Ibex, creating an encrypted folder is as simple as right clicking and going to "encrypt".

---

### Post by macvr on 2009-02-23
guys,
with my limited knowledge, i'v come up with this hack...>

[http://ubuntuforums.org/showpost.php?p=6777859&postcount=1]("http://ubuntuforums.org/showpost.php?p=6777859&postcount=1")

but this uses the root password , using the user account password would be the most ideal...

any thoughts on improving this?

---

### Post by Flimm on 2009-02-23
> **macvr said:**
> but this does not prevent users with knowledge of the root password from accessing your folders/files, so how does this keep your files safe!*[atleast in windowsXP there is no root user which can allow access to other administrator's files]* Actually, Windows XP does have [a hidden adminstrator account](http://www.infopackets.com/news/security/2004/20041021_security_risk_hidden_admin_account_in_winxp_part_2.htm), which can read other users' documents.

---

### Post by macvr on 2009-02-23
> **Flimm said:**
> Actually, Windows XP does have [a hidden adminstrator account](http://www.infopackets.com/news/security/2004/20041021_security_risk_hidden_admin_account_in_winxp_part_2.htm), which can read other users' documents.

hei, i'v seen that.....!
 but i was always wondering why that "Administrator" account was being created during safe mode, even though my user account was having administrator privileges! guess i didnt realize its full use!

---

