---
title: "Password change issue"
date: 2010-08-27
forum: Security
---

### Post by s0rc3r3r on 2010-08-27
I have a curious case.
I had this great idea *sigh to try and change the UBUNTU password.
So I took not so drastic effort..I went to System>Administration>Users and Groups.

There I clicked on my login name.Clicked on Properties and used the Change Password Button to Change my login password. I did that.
[I thought this is the way to change the login password]
After that

2)As usual I tried to launch the EMPATHY!! It started asking me about some KEYRING password!

I gave my new password and it worked.
Now...
the weirdness of the issue is that..
1)If I want to login to UBUNTU..I have to give the OLD Password [The password which I gave when installng Ubuntu;as if the password change has not come into affect]
TO mount..I have to give Old password
To update I have to give old password.

BUT!

2)To get my things done in EMPATHY..that is to get the KEYRING Challenge done! I have to give the new password and old password does not work here.

I am pretty confused.
1)I want to stop empathy from asking me about the KEYRING thing.Roll back the system to the previous state;before the password change thing

I would also like to know..what exactly went wrong or right? and What is really happening to my system.
I mean things are all normal, so far..but why the two passwords?

I dont use any heavy things on my machine..just a bit of browsing and Empathy..thats all.and only the default applications are installed on my machine.

I use Ubuntu Karmic 9.10
Thanks in advance

---

### Post by FuturePilot on 2010-08-27
Try this. [http://ubuntuforums.org/showpost.php?p=9765698&postcount=2]("http://ubuntuforums.org/showpost.php?p=9765698&postcount=2")

---

### Post by s0rc3r3r on 2010-08-28
that worked!!
thank you buddy for the information!

---

### Post by cariboo on 2010-08-28
If the keyring password is set to login, you shouldn't have to change the password there. 

The correct way to change your password is to go to Preferences->About Me and change your password there, then log out and back in again. You shouldn't be prompted for a paswword after that.

---

### Post by s0rc3r3r on 2010-08-29
yes. I managed to get it right.No Key ring challenge anymore.
Thanks for the help and support people.

:)
thanks again

---

