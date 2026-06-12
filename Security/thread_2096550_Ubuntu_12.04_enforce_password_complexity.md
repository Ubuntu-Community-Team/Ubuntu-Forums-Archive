---
title: "Ubuntu 12.04 enforce password complexity"
date: 2012-12-20
forum: Security
---

### Post by Drenriza on 2012-12-20
Hi guys.

I'am wondering the following.

When needing to create user accounts for new users how do you do the following.
[LIST=1]
[*]Create a temporialy password for a user that expires as soon as the user logs in for the first time.
[*]Set password complexity system wide. Example, a password must contain 1 upper and 1 lower case, 1 letter and be minimum 8 characters long.
[/LIST]

Kind regards.

---

### Post by sahabcse on 2012-12-20
[COLOR="Blue"]Create a temporialy password for a user that expires as soon as the user logs in for the first time.[/COLOR]

create a user and use chage command for expire the password.

For example

chage -d0 username --> this expires the password in first login

[COLOR="Blue"]Set password complexity system wide. Example, a password must contain 1 upper and 1 lower case, 1 letter and be minimum 8 characters long.[/COLOR]

/etc/pam.d/common-password

password requisite pam_cracklib.so retry=3 minlen=8 difok=3 ucredit=1 dcredit=1 ocredit=2 (lcredit=0 is for lowercase and usually isn't needed)

This should give you:
8 character length minimum
3 retries
1 uppercase
1 numeric digit
2 non-alphanumeric (other)
difok=3 sets the minimum number of characters that must be different from the previous password. Increase this number if you increase the minimum length of the password

---

### Post by Drenriza on 2012-12-20
Removed.

---

### Post by Pjotr123 on 2012-12-20
A good password can be surprisingly easy to create and remember:
[https://sites.google.com/site/easylinuxtipsproject/password](https://sites.google.com/site/easylinuxtipsproject/password)

...but I wouldn't know how to enforce it. :)

---

### Post by Drenriza on 2012-12-21
Thanks for the replies so far.

But anyone who knows how to enforce that users need to change password when max days expire? Without help of the administrator.
```
sudo chage -M <user>
```

---

### Post by gwm on 2012-12-22
Hi, I have tried sahabcse suggestions. I tried to set minlen=1 but it didn't seem to make any difference (12.04 unity).

I rebooted in case something perhaps needed to reinitialize but still no change.

The settings app for changing passwords doesn't seem to know about this config file.

---

### Post by Drenriza on 2012-12-22
> **gwm said:**
> Hi, I have tried sahabcse suggestions. I tried to set minlen=1 but it didn't seem to make any difference (12.04 unity).

I rebooted in case something perhaps needed to reinitialize but still no change.

The settings app for changing passwords doesn't seem to know about this config file.

I'am unsure if the file applies if you enter a password as root or with sudo. Since these (from what i know) by-pass normal password standards.

---

### Post by gwm on 2012-12-22
I log in as a user with administrator priviledges.
Then I click the icon for "System Settings".
Next, I click on "User Accounts".
I select the user, Unlock and supply an adminstrator password.
Finally, I click on the password and a dialog opens for me to change the password.
This dialog insists that I supply at least 6 characters.

You seem to suggest there another way of changing a user's password. Please tell me about it.

I started a terminal session and typed in

**sudo passwd user_name**

I was prompted for super user password, old password, new password etc.
This enabled me to change the password to to one that overrides the system settings.

---

