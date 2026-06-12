---
title: "Root"
date: 2005-10-09
forum: The Cafe
---

### Post by champ_rock on 2005-10-09
when i try to login as root using the login screen then it says sys administrators cant login from here.......
from where do u login as root

---

### Post by Pablo_Escobar on 2005-10-09
Ubuntu speciality is that root is turned off as default - security reason.

You can always use sudo for root work, and the best practice is never to login as root, but if You must use Enabling Root Account from [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by darkmatter on 2005-10-09
[QUOTE=champ_rock]when i try to login as root using the login screen then it says sys administrators cant login from here.......
from where do u login as root[/QUOTE]

If you must have root access through GDM. There is a simple two-step process to follow.

1> Set root password

In a terminal, ener the following

```
sudo passwd root
```


you will be prompted for your USER password, enter it.

Next, you will be prompted to create a root password and then once again to confirm the password. Do so.

2>Enable root login.

Go to System -> Administration -> Login Screen Setup

You will be prompted for your password (user password for sudo)

Under the Security tab in the Setup GUI, check 'Allow root to login with GDM'

After you have done this, log out of your account and log in as root with tthe username 'root' (obviously) and the password you had created for the root account.

Only do this if you absolutely MUST have full root access. Sudo is the better choice for most situations, as it allows root access, but with a 15 minute time limit per session.

---

### Post by IBLPNZIT on 2005-10-11
Hello all,

I have need some help. I have made a big boo-boo. 

I needed to access files in the root directory, and I thought the way to change this might be to chnage my home directory (non-admin user) to the same as /root. Only problem is, I can't login becuase it says my login/profile settings/files are in use. Can anyone help me?

Thanks so much,

Josh

---

### Post by Stormy Eyes on 2005-10-11
Reboot, and press ESC to get to the boot menu. Use recovery mode, and edit [/etc/passwd](http://publibn.boulder.ibm.com/doc_link/en_US/a_doc_lib/files/aixfiles/passwd.htm) to fix your normal user's home directory. Don't forget to click the link first; it contains valuable info on /etc/passwd. To edit from a shell prompt, do **nano /etc/passwd**.

---

