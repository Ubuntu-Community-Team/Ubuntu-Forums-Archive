---
title: "Change login email from one SSO to another"
date: 2020-02-07
forum: Resolution Centre
---

### Post by patrick75 on 2020-02-07
Hi there,

I'm in the process of merging to SSO account into one.

However, the old one is used to access this forum.

How could I migrate the login email of this forum to another?

BR,
Patrick

---

### Post by coffeecat on 2020-02-07
The way SSO works with the forum is that an Ubuntu One SSO account and forum account are linked in such a way that it can only be unlinked by a forum admin (or someone with admin permissions). Changing the email in either of the SSO or ubuntuforums accounts will not make any difference. The only time that the emails are important is with the initial linking, usually when a user logs in the first time from Ubuntu One, and the system looks for an email match and sets up a link if there is one, or creates a new forum account with the same email if not.

That preamble is important for you to know what is going on.

In your case, as I understand your post, is that you are about to delete the old Ubuntu One SSO account which is linked to this forum account. What would need to happen is for us to remove the linking information for this forum account, and for you to change your preferred email in your newer Ubuntu One SSO account to match the one associated with your forum account. Please be aware that we do not administer Ubuntu One, so you would have to make the Ubuntu One changes yourself. If you need to set the email associated with the old SSO account as preferred in the new SSO account, I think you will need to ensure that the old account is either deleted, or that you have changed the email in that to something else. Just as with the forum, you can't have two SSO accounts with the same email - as I understand it.

Before we go any further, please post back to confirm that you understand, and that you are sure you know the email address associated with this forum account. Please don't post it in this thread - we consider it privileged and confidential information.

---

### Post by patrick75 on 2020-02-07
Currently, I had:
1. SSO_old (using email_old) which is used to log in the forum
2. SSO_new (using email_new)

If I read correctly, the process would be:
1. Forum admin unlink the connection between SSO_old and forum account
2. I send a request to Ubuntu for merging SSO_old and SSO_new
3. I change the preferred email of SSO_new back to email_old
4. Log in the forum with SSO_new.

As Ubuntu SSO account allows multiple email address (and only one "preferred"), is Step3 required?
If I set "preferred email" to email_new AFTER Step4, or remove email_old from SSO_new, am I still capable to log in the forum?

---

### Post by coffeecat on 2020-02-07
I have no idea whether you can "merge" Ubuntu One accounts. You may have to simply delete the old one.

Once we've unlinked this forum account from Ubuntu One, you need to log into the forum from an Ubuntu One account which has the same email as the forum account **set as preferred** in your Ubuntu One account. It must be set as preferred, not simply just one the emails you are allowed in Ubuntu One.

If you log in with an Ubuntu One account with the email associated with your forum account set as preferred in the Ubuntu One account, the system will link the two accounts automatically. Thereafter, you can change the email in either or both of the Ubuntu One and forum accounts as much as you want without breaking the link. As I said before, only a forum admin can unlink the two accounts. 

If you log into the forum from your new Ubuntu One account with a preferred email that is not in the forum database, the system will create a new forum account with a username derived either from your Ubuntu One username, or from the local part of your email if you untick your name in your Ubuntu One Personal Data Request page.

More here: [https://ubuntuforums.org/showthread.php?t=2230004](https://ubuntuforums.org/showthread.php?t=2230004)

It all seems a bit complicated, but it is logical. And before you ask: this was imposed on us. We hate it.

---

### Post by patrick75 on 2020-02-07
OK. I totally understand the situation.
Please unlink this account.
Thank you for your support.

---

### Post by coffeecat on 2020-02-07
I have disassociated the patrick75 forum account from the linked Ubuntu One SSO account.

Good luck!

---

### Post by patrick75 on 2020-02-13
I successfully finished the process.

Thank you fir your help.

---

