---
title: "Setting up a new account on my system"
date: 2010-09-06
forum: Security
---

### Post by dogdo on 2010-09-06
Basically in addition to the first installation account on my system (my account) ive also set up another user alongside my own. Its not a admin account but 'desktop user' account but in the group id section this account comes as '1001'-what does this 1001 mean?

Furthermore are there any risks i should know about arising from setting up another account on my pc?

---

### Post by OpSecShellshock on 2010-09-06
1001 is just the ID of the account. If you look, you'll notice that the first account you made has a user ID of 1000. So it's just incrementing. There aren't really any risks with regular user accounts that don't also exist with any user account (including the first one). The only real difference is that the second account can't elevate privileges.

It's also good to note that there aren't really any specific security advantages to setting up a second, "regular user" account since even an account that can elevate privileges has to do so manually prior to administrator-level actions. The rest of the time it's just a regular account like everyone else's.

---

### Post by Rubi1200 on 2010-09-06
If the purpose of the second account is to allow another user other than you to use the computer you might want to consider changing the file permissions on your home folder so that the other person cannot access your files.

---

### Post by dogdo on 2010-09-06
> **Rubi1200 said:**
> If the purpose of the second account is to allow another user other than you to use the computer you might want to consider changing the file permissions on your home folder so that the other person cannot access your files.

yes that is what i want to do for the second account-How do i go about changing the file permissions then to only allow my home folder to be accessed by me?

---

### Post by Rubi1200 on 2010-09-06
See here for an explanation:
[http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php](http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php)

Scroll down to the section on directory permissions.

---

### Post by dogdo on 2010-09-06
> **Rubi1200 said:**
> See here for an explanation:
[http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php](http://gd.tuwien.ac.at/linuxcommand.org/lts0070.php)

Scroll down to the section on directory permissions.

seems a bit complicated...

i found this (see attachment)-can i not configure my home folder to be only used by me from here?

---

### Post by cariboo on 2010-09-06
No you can't do it from inside your home directory, you have to navigate to /home.

---

### Post by dogdo on 2010-09-06
So i take it you mean from here? 

Ive set the permissions to not allow other users except my own account to access my home folder. And i encrypted my home folder during the installation process. Am i good then?

---

### Post by bodhi.zazen on 2010-09-06
Open a terminal and enter the following command:

```
chmod 770 ~
```

---

### Post by dogdo on 2010-09-07
This is what i got back-confused i am 


daddy@daddy-laptop:~$ chmod 770
chmod: missing operand after `770'
Try `chmod --help' for more information.
daddy@daddy-laptop:~$

---

### Post by bodhi.zazen on 2010-09-07
> **dogdo said:**
> This is what i got back-confused i am 


daddy@daddy-laptop:~$ chmod 770
chmod: missing operand after `770'
Try `chmod --help' for more information.
daddy@daddy-laptop:~$

You need to specify a directory (or file)

chmod 770

is NOT the same as 

chmod 770 ~

~ is short hand for $HOME or /home/your_user_name

---

### Post by Rubi1200 on 2010-09-07
> **bodhi.zazen said:**
> You need to specify a directory (or file)

chmod 770

is NOT the same as 

chmod 770 ~

~ is short hand for $HOME or /home/your_user_name
Please correct me if I am wrong, but I was under the impression that to make the home directory private the command would be ```
sudo chmod 700 /home/your_user_name
```

---

### Post by bodhi.zazen on 2010-09-07
> **Rubi1200 said:**
> Please correct me if I am wrong, but I was under the impression that to make the home directory private the command would be ```
sudo chmod 700 /home/your_user_name
```

Well, 770 works, unless you have specifically added another user to your users group.

By default your home directory is owned by your login username and login user group.

ls -l /home =)

New users added to the system will not be a part of your user group unless you specifically add them .

---

### Post by Rubi1200 on 2010-09-07
Thanks for clarifying this; a quick follow-up question. If I have already set permissions to 700, do you recommend changing it to 770?

---

### Post by dogdo on 2010-09-07
So how will i know whether or not my home directory is private now? 

If the home folder is encrypted anyway does it really matter that its private or not?

---

### Post by bodhi.zazen on 2010-09-07
> **Rubi1200 said:**
> Thanks for clarifying this; a quick follow-up question. If I have already set permissions to 700, do you recommend changing it to 770?

700 770 , either are fine.

> **dogdo said:**
> So how will i know whether or not my home directory is private now? 

If the home folder is encrypted anyway does it really matter that its private or not?

If it is encrypted, changing the permissions would only matter if you make use of the "switch user" feature or others log into your system remotely, such as ssh or VNC (while you are logged in).

---

### Post by Rubi1200 on 2010-09-07
Thanks bodhi for taking the time to answer my questions.
:)

---

### Post by amac777 on 2010-09-07
> **dogdo said:**
> So how will i know whether or not my home directory is private now?

Login as another user (create a test user for this purpose if necessary) and see if you can access files in your home directory.

---

### Post by dogdo on 2010-09-07
> **amac777 said:**
> Login as another user (create a test user for this purpose if necessary) and see if you can access files in your home directory.

Ok i have another user account set up-so how do i go about attempting to access my files on the primary installation account ?

---

### Post by uRock on 2010-09-07
Sign in as other user, then in the places menu click Home Folder, then the up arrow where you should see Lost and Found along with all of the user account's Home Folders. The one for the primary account should have an x on it and when clicking to open it a popup should occur with an error message saying you do not have permission.

---

### Post by bodhi.zazen on 2010-09-07
> **Rubi1200 said:**
> Thanks bodhi for taking the time to answer my questions.
:)

You are most welcome.

---

### Post by amac777 on 2010-09-07
> **dogdo said:**
> Ok i have another user account set up-so how do i go about attempting to access my files on the primary installation account ?

In addition to uRock's method, you can also try going to the terminal and then use these commands to list all the user's home folders on your system and see their permissions:
```

cd /home
ls -l
```

You can then try to "cd" into each user's home directory to see if it's possible.

---

### Post by dogdo on 2010-09-10
Ok i checked and my primary home user folder is indeed private.

I used the encrypt home folder option at installation-so does that mean as long as my primary account isn't logged into that my primary home folder data is encrypted from the views of another logged in secondary account?

---

### Post by amac777 on 2010-09-10
The permissions you set to make the folder private keep other regular users from entering your home folder. 

The encryption should prevent root or somebody who takes your hard drive out of your computer etc from being able to access your files. 

Again, I'd recommend you check it for yourself by doing experiements. Some examples:

1. Reboot and enter the recovery mode and check out your home folder to see what is available.

2. Login with your real user and also login as another user with admin privlidges at the same time and see what the other user can see in your real home account.

---

### Post by bodhi.zazen on 2010-09-10
> **dogdo said:**
> Ok i checked and my primary home user folder is indeed private.

I used the encrypt home folder option at installation-so does that mean as long as my primary account isn't logged into that my primary home folder data is encrypted from the views of another logged in secondary account?

It should work that way, you can test it if you like.

---

### Post by davidjmayo on 2010-11-18
Excellent. Just what I was looking for to protect folders from my daughter.
Thank you everyone.

---

