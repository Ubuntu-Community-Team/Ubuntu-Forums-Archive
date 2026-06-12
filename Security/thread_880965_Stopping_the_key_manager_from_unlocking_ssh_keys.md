---
title: "Stopping the key manager from unlocking ssh keys"
date: 2008-08-05
forum: Security
---

### Post by Gorf on 2008-08-05
Is there a way to stop the key ring manager from prompting me to "unlock" my SSH RSA key and importing it every time I use it?  It's a real pain in the **** to have to click deny to the pop up every single time I try to ssh to a host.  I just want it to ignore my access attempts to my SSH key.

Thoughts?

---

### Post by Biochem on 2008-08-05
The good news :):

I did manage to get it done, and now my key manager is silent when i use ssh


The bad news:(:

I had to play so much that I'm not sure what step got it "not working"

My best guess is that I changed the key file.

This will rename the  key
```
mv ~/.ssh/id_rsa ~/.ssh/id_rsa_b
```

than with nano you create a config file to redirect ssh to the new key
```
nano ~/.ssh/config
```

enter the following lines. 
```
Host *
	IdentityFile ~/.ssh/id_rsa_b

```

Now all your ssh session will try the id_rsa_b key and I think user agent is only listening to id_rsa. 

For more information about the ssh config file:
```
man ssh_config
```

If it works please come back to tell us I would like to have a comfirmation that it's indeed a usable fix.

---

### Post by Mister.Vash on 2008-08-06
Run gconf-editor
navigate to /apps/gnome-keyring/daemon-components/
uncheck ssh
restart the gnome-keyring-daemon or reboot the system

---

