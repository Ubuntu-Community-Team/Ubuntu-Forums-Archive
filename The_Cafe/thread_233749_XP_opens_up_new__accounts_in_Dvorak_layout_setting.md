---
title: "XP opens up new  accounts in Dvorak layout setting."
date: 2006-08-10
forum: The Cafe
---

### Post by hanzj on 2006-08-10
Hello,

My goal: I would like new user accounts or new guest accounts to be using Qwerty keyboard layout. 
Whenever a new user account or a new guest account is created in Windows XP, the keyboard layout is in Dvorak, and not in Qwerty.

How did it ever become Dvorak, you may ask? Well, The first 2 user accounts on that XP computer use Qwerty. A 3rd account was created, and it uses Dvorak.

That 3rd account has already been removed. So the XP computer is back to 2 (qwerty) user accounts. What has happened? 
If I remember correctly, the default keyboard layout, at least for the 2nd user account, is in Qwerty.

---

### Post by hanzj on 2006-08-11
[http://support.microsoft.com/kb/318388/en-us](http://support.microsoft.com/kb/318388/en-us)
says,
> 
CAUSE
This problem may occur if the following conditions exist:
 &#8226;	A user without administrator permissions is logged on to Windows.
&#8226;	The default keyboard item in the registry does not match the default keyboard layout.

This problem occurs because the Msctf.dll file that is running under the permissions of the user account does not have sufficient permissions to evaluate the new default keyboard layout from the registry.

So can anyone tell me where exacly in the Registry (regedit) this "default keyboard item" is located?

---

### Post by hanzj on 2006-08-11
So how about this, WinXP  users? 
Please open up regedit (Start/Run/regedit) and then go to Find. Then type in qwerty. Then please find all occurences of "qwerty" and please post the location of each occurence. 

For example
 Hkey_Local_Machine\System\ControlSet001\Control\Keyboard_Layouts\0010409

Thanks.

P.S. This request is only to those who use the Qwerty layout. This is probably most of you.

---

