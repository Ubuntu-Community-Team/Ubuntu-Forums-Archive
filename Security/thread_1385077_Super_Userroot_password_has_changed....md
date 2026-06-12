---
title: "Super User/root password has changed??..."
date: 2010-01-19
forum: Security
---

### Post by WillardTheGrey on 2010-01-19
I used to be able to install from the "Ubuntu Software Center" but now when it asks for a password to install, I type in the same one that I have been using since the start and get "Authentication Failure".

What did I do and how do I fix it?

I have Ubuntu 9.10
I am the only user of this computer(I better be anyway).
I have not messed with the root account.
Password is eight characters consisting of upper and lower case, symbols, and numbers.

Thank you.

---

### Post by adam814 on 2010-01-19
Did you change your user password?  I believe the Software Center uses gksudo for authentication, so it should be your user password.  Ubuntu disables the root account by default and favors sudo for obtaining superuser privileges.

---

### Post by sisco311 on 2010-01-19
Is your user in the admin group?

Can you use sudo and/or pkexec in a terminal?
```
sudo echo "sudo works"
```
```
pkexec echo "pkexec works"
```

What's the output of:
```
id
cat /etc/group | grep $USER | grep admin
```

> **adam814 said:**
> Did you change your user password?  I believe the Software Center uses gksudo for authentication, so it should be your user password.  Ubuntu disables the root account by default and favors sudo for obtaining superuser privileges.

Actually Software Center uses policykit for authentication, but, by default, policykit should also prompt for the user password.

---

### Post by WillardTheGrey on 2010-01-19
```
sky@Computer:~$ id
uid=1000(sky) gid=1000(sky) groups=4(adm),20(dialout),24(cdrom),46(plugdev),
104(lpadmin),120(sambashare),1000(sky)
sky@Computer:~$ cat /etc/group | grep $USER | grep admin
lpadmin:x:104:sky
sky@Computer:~$ 


```And I didn't change my password.

Thanks for the quick replies.

---

### Post by sisco311 on 2010-01-19
> **WillardTheGrey said:**
> ```
sky@Computer:~$ id
uid=1000(sky) gid=1000(sky) groups=4(adm),20(dialout),24(cdrom),46(plugdev),
104(lpadmin),120(sambashare),1000(sky)
sky@Computer:~$ cat /etc/group | grep $USER | grep admin
lpadmin:x:104:sky
sky@Computer:~$ 


```And I didn't change my password.

Thanks for the quick replies.

Boot in the Recovery Mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by WillardTheGrey on 2010-01-19
> **sisco311 said:**
> Boot in the Recovery Mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

Worked perfect.

Thank you.

Now I feel like a retard.:oops:

---

### Post by afrodeity on 2010-06-02
I need to reinstall the Lexmark 2650 driver after upgrading to Lucid. Now when I run the installer script and enter my root password, it says wrong password. 

I just used this password in the Software Centre, I am the admin, what is going on?

sudo works

pkexec works

```
id
uid=1000(afrodeity) gid=1000(afrodeity) groups=4(adm),20(dialout),21(fax),24(cdrom),29(audio),30(dip),44(video),46(plugdev),100(users),103(fuse),104(lpadmin),112(netdev),113(couchdb),115(admin),119(gdm),120(sambashare),124(vboxusers),133(mythtv),1000(afrodeity),1003(hamachi)

```

```

cat /etc/group | grep $USER | grep admin
lpadmin:x:104:afrodeity
admin:x:115:afrodeity

```

---

### Post by sisco311 on 2010-06-02
@afrodeity: Did you try to run the script as root?
```
sudo -i path/to/script
```

---

### Post by afrodeity on 2010-06-02
Thanks Sisco311. Must have been the rush to scan a legal document after lawyer woke me up this morning, completely missing half my brain and not ready for this. Thanks for the corrective. No, I forgot to "sudo" it, and the script didn't remind me either. Life just got complicated, but at least I am in "peaceful and undisturbed possession" of my elecricity.

---

