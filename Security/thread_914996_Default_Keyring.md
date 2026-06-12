---
title: "Default Keyring"
date: 2008-09-09
forum: Security
---

### Post by rycharde on 2008-09-09
I am re-posting a question which was answered, but did not work.
I am having trouble responding to e-mail contacts in ads.
When I go to respond a window comes up stating:
Enter password for default keyring to unlock the application 'evolution'
(/usr/bin/evolution) wants access to the default keyring but it is locked.
I received a response stating I should use the password for ubuntu, as all the passwords are stored in evolution.  
That did not work.
Does anyone have any other suggestions??

Thanks

---

### Post by cdenley on 2008-09-09
> **rycharde said:**
> I am re-posting a question which was answered, but did not work.
I am having trouble responding to e-mail contacts in ads.
When I go to respond a window comes up stating:
Enter password for default keyring to unlock the application 'evolution'
(/usr/bin/evolution) wants access to the default keyring but it is locked.
I received a response stating I should use the password for ubuntu, as all the passwords are stored in evolution.  
That did not work.
Does anyone have any other suggestions??

Thanks

The password for your keyring isn't necessarily the same as your user account. The first time you use the keyring, you are prompted to create the password for the default keyring. If you don't know the password you entered, you can delete the keyring. This will remove any passwords you have stored.
```

rm ~/.gnome2/keyrings/login.keyring

```

You will be prompted for your e-mail password now, as if you never entered it. If you select to have the password remembered, you will be prompted to create a password again when the new default keyring is created.

---

### Post by joshuachad on 2008-09-10
Also check out this link. That way you get a tad of education also ;)

[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/]("http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/")

---

