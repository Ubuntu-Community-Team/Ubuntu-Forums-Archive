---
title: "Remote Desktop (Password problem)"
date: 2010-12-07
forum: Security
---

### Post by redemption38 on 2010-12-07
Hello all,


I'm under ubuntu 10.10 and i would activate the remote desktop.
He works correctly when i don't seized any passeword, but, when i give a password, it is impossible to me to connect with VNC.
VNC say "authentification error".
When i open the options of remote desktop, The password field is empty, it's like he can't save my seized.


Anyone can help me for this mysterious problem? ;)


thank you a lot

---

### Post by lukeiamyourfather on 2010-12-07
Are you saying the client forgets the password when you open it again, or are you saying the server won't allow anyone to connect when there is a password? The question is not very clear.

---

### Post by wojox on 2010-12-07
Did you set up Public or Private Keys?

---

### Post by redemption38 on 2010-12-07
euh... idon't know, where can i check that?

---

### Post by redemption38 on 2010-12-07
> **lukeiamyourfather said:**
> Are you saying the client forgets the password when you open it again, or are you saying the server won't allow anyone to connect when there is a password? The question is not very clear.

when i open preferences > remote desktop the second time, my password are not saved and the field is empty.

I think, when i seized a password and i close de remote desktop configuration window, he d'ont save my password.

---

### Post by lukeiamyourfather on 2010-12-08
> **redemption38 said:**
> when i open preferences > remote desktop the second time, my password are not saved and the field is empty.

I think, when i seized a password and i close de remote desktop configuration window, he d'ont save my password.

Did it ever? It seems like this would be a security issue if it was saving passwords for logins on remote machines. If it used to then I'd check with the developers of that application, they probably have a mailing list.

---

### Post by TheFr00n on 2010-12-08
> **redemption38 said:**
> I think, when i seized a password and i close de remote desktop configuration window, he d'ont save my password.

I have experienced a similar problem recently. In my experience, it is not enough just to type a password on the Remote Desktop config screen. There is also a checkbox next to it.

Now, you must tick that box before you may enter a password. But after you have entered the password, untick the box. And then tick it *again*. Your password will now be saved.

I do not know why this problem exists. I think it has something to do with how the GUI for config tool works (it also sometimes hangs while checking your network status).

In any case, this is what worked for me. Good luck!

---

### Post by redemption38 on 2010-12-08
> **TheFr00n said:**
> I have experienced a similar problem recently. In my experience, it is not enough just to type a password on the Remote Desktop config screen. There is also a checkbox next to it.

Now, you must tick that box before you may enter a password. But after you have entered the password, untick the box. And then tick it *again*. Your password will now be saved.

I do not know why this problem exists. I think it has something to do with how the GUI for config tool works (it also sometimes hangs while checking your network status).

In any case, this is what worked for me. Good luck!

unfortunetly, this tips don't work with me :(

---

### Post by redemption38 on 2010-12-11
I found a track, i think the problem come from de keyrings.
i have a default keyrings at startup of the computer but, if try to delete my keyrings with application > accessories > passwords and encryption keys, i have an error message

"no such keyrings exists"
i can't change the passwords too
and the folder ~/.gnome2/keyrings doesn't exist.

i think i must fix this problem and so remote desktop will fix too.

how can i fix this, i haven't any idea.

---

### Post by redemption38 on 2010-12-13
It's OK, I fixed the problem
it's not in the ~/.gnome2/ folder where the keyrings are.
It is in /home/user/.gnome2/
so i have deleted all *.keyring files and i did reboot.
At the opening of the session, a new keyring is asked. i seized a new password, and after that, i seized a password in the remote desktop configuration window.
The password are correctly saved.

thank you all

---

