---
title: "Disable SSH Key Access Question"
date: 2010-06-15
forum: Security
---

### Post by tigerblue123 on 2010-06-15
Dear Peoples, 

I currently have a user on my Ubuntu server that I want to block completely from login. I know right now they login with SSH keys so they don't need to enter their SSH password. 

Can anyone tell me how to remove the SSH key login for their username and root user which I believe they use too and block SSH access alltogether. I will then just change the root SSH password. 

I'm terrified they will do some harm so I need them blocked out ASAP.  

Is there a way I can get a list of SSH users? Sorry for being a newb.

Thanks so much for your help.

---

### Post by Bachstelze on 2010-06-15
You could just delete the account. ;) If you want to prevent login without deleting the account, set the user's login shell to /bin/false:

```
sudo chsh -s /bin/false <username>
```

To see a lost of users currently logged in:

```
users
```

---

### Post by tigerblue123 on 2010-06-15
Thank you!!

I could also try this in the file "/etc/ssh/sshd_config"?

AllowUsers user1
AllowGroups users

Would that JUST allow user1 to access?

---

### Post by Bachstelze on 2010-06-15
> **tigerblue123 said:**
> Thank you!!

I could also try this in the file "/etc/ssh/sshd_config"?

AllowUsers user1
AllowGroups users

Would that JUST allow user1 to access?

That would allow user1 and everyone in the users group, and refuse everyone else. By the way, another way to do what you want is to use DenyUsers:

```
DenyUsers user1
```

Would deny user1 and allow everyone else.

---

### Post by prshah on 2010-06-15
> **tigerblue123 said:**
> Is there a way I can get a list of SSH users? 

While the other options are good, you can also simply delete the ~/.ssh/authorized_keys file of the user in question (~ refers to the user's home directory, DONT try it when logged into your own account) to prevent passwordless ssh logins.

---

### Post by tigerblue123 on 2010-06-15
Thanks for all your help. Fantastic!

If I delete the /root/.ssh folder will I still be able to login with a password as root?

---

### Post by Bachstelze on 2010-06-15
> **tigerblue123 said:**
> Thanks for all your help. Fantastic!

If I delete the /root/.ssh folder will I still be able to login with a password as root?

Yes (the directory does not exist by default). However, this seems a bit overkill. As prshah said, if you delete the authorized_keys file, the user will not be allowed to login using his key (he will however still be able to login with the password if password authentication is allowed and he has the correct password).

---

### Post by prshah on 2010-06-15
> **tigerblue123 said:**
> If I delete the /root/.ssh folder will I still be able to login with a password as root?

Root logins are HIGHLY DISCOURAGED. Login as a regular user, then take root privileges with sudo when required.  

There is a setting in /etc/ssh/sshd_config to prevent root logins: set "PermitRootLogin" to "no".

However, this is just an advisory; it's your server, do as you will ;)

---

