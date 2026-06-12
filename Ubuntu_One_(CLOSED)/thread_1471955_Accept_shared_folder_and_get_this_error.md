---
title: "Accept shared folder and get this error"
date: 2010-05-03
forum: Ubuntu One (CLOSED)
---

### Post by vzhen on 2010-05-03
I am trying to share shared folder via email

[email]myemail@yahoo.com[/email]   to  [email]myemail@hotmail.com[/email]

When i click the link and accept button.

I get this error

> Something has gone wrong (500)

We've recorded this problem and it will get investigated with the logs. If this problem is urgent, please file a bug report and include this number: OOPS-ID-1585appserver20308

For more general information on Ubuntu One subscribe to our mailing list, check our blog or follow Ubuntu One on twitter and identi.ca to get updates.


**Question:**
If i share a folder via email to [email]abc@yahoo.com[/email] is it mean ONLY share to [email]abc@yahoo.com[/email] OR every ubuntu one user can access it if they have the link?

**Suggestion**:
Let user type in sharing title and message that appear in the email. This is because standard message and title always make people think that is spam virus ...... and they ignore.

**Website login problem:**
Everytime i login at login.ubuntu.com. it doesn't automatic link me back to my storage and i have to type change login.ubuntu.com to one.ubuntu.com and click sign-in to login.

---

### Post by duanedesign on 2010-05-04
Some maintenance was being done on the servers recently. I have no idea if that is the cause of your issue. However if this continues to be a problem I would [file a bug]("https://bugs.launchpad.net/ubuntuone-servers/+filebug") against the package ubuntuone-servers with the OOPS-ID number.

If you share a folder, that folder is only shared by the one user you chose to share it with.

If you go to [https://one.ubuntu.com/](https://one.ubuntu.com/) and then click 'Sign In' this will take you to login.ubuntu.com  and redirect you appropriately to the dashboard. The SSO is used by  multiple Ubuntu sites so there is no particular redirect going directly to login.ubuntu.com directly.

---

### Post by rtg on 2010-05-04
> **vzhen said:**
> I am trying to share shared folder via email

[email]myemail@yahoo.com[/email]   to  [email]myemail@hotmail.com[/email]

When i click the link and accept button.

I get this error

It looks like completely server-side error, but it also falls within the timeframe when the rollout was happening.

Could you please check whether you are able to accept the share offer now?

*I just shared a folder and got it accepted*

> **vzhen said:**
> **Question:**
If i share a folder via email to [email]abc@yahoo.com[/email] is it mean ONLY share to [email]abc@yahoo.com[/email] OR every ubuntu one user can access it if they have the link?

The share offer can be claimed by a different user in case they have a link. Not sure whether this is a feature or a bug though.

> **vzhen said:**
> **Suggestion**:
Let user type in sharing title and message that appear in the email. This is because standard message and title always make people think that is spam virus ...... and they ignore.

This is interesting. Something like "Personal message" when the folder is shared. Filed [LP:575085]("https://launchpad.net/bugs/575085")

> **vzhen said:**
> **Website login problem:**
Everytime i login at login.ubuntu.com. it doesn't automatic link me back to my storage and i have to type change login.ubuntu.com to one.ubuntu.com and click sign-in to login.

login.ubuntu.com is not actually a gateway for one.ubuntu.com, you might want to use [https://one.ubuntu.com/auth/login/](https://one.ubuntu.com/auth/login/) instead. By logging in to login.ubuntu.com you are accessing Ubuntu Single Sign On service which is in turn used by one.ubuntu.com for user authentication.

---

