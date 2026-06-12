---
title: "SSH Remote User, Denied"
date: 2006-08-27
forum: Server Platforms
---

### Post by redx on 2006-08-27
So I installed the Ubuntu 6.06 LAMP server onto my desktop and the first service I'm trying to set up is the SSH server. Everything went well with the install, I can log in with my username I created at install as well as the user I created using 'adduser USER' feature. The problem occurs when I try to create a user via SSH it seems to become erroneous. I created a user via SSH 'sudo adduser' with options to set HOME_DIR (/home/usr) and SHELL (/bin/bash)and then I try to login via SSH and I get a Permission Denied error. (I think it says something about wrong passwd but I know it's correct)

Anyone know what's wrong? Is there a security setting to prevent creating users remotely? Is there a 'debug' file I can look at to do some research on the EXACT error when it trys to authenticate?

Originally I had added 'AllowUsers user user user' to the sshd_config file but when taking it out, it seemed to continue to work so I just left it out.

---

### Post by foxylad on 2006-08-27
I think your "remotely created users" is a red herring - there should be no difference if you created them directly on the machine or via SSH. In fact all users on my machines (except the first one) were created via SSH.

The first place to look is at /etc/passwd, to make sure you created the user you expected - compare to other users in the file. You didn't mention setting the password for new users - I assume you did...

  ssh youradmin@yourmachine
  sudo adduser greg
  sudo passwd greg

Now go and see if greg has turned up in /etc/passwd. If so, try to log in with SSH as greg. You can check /var/log/auth.log for details of what happened.

The AllowUsers directive will restrict users to those named IF it exists - so removing it completely will allow all users, as you have discovered.

Cheers!
Greg.

---

### Post by redx on 2006-08-27
Thank you for your prompt response :D

I made sure after I created user 'abc' (user I created has a 3-char name) that I created the users' password (sudo passwd user) after that I went over to /etc/passwd and reviewed the line of text to make sure it resembled both my user and the 2nd user I created, both which can successfully SSH into the box. 

I just reviewed the '/var/log/auth.log' and there shown are all the failed attempts by user 'abc'. (Real user is obviously not abc) There looks to be two different types of errors listed.

The first:
User 'abc' from 192.168.1.1 not allowed because not listed in AllowUsers

(User 'abc' is in fact listed in my sshd_config - AllowUsers line)

Second:

Failed none for invalid user 'abc' from 192.168.1.1 port XXXX ssh2

(pam_unix) authtentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.1.1 user=abc

Failed password for invalid user abc from IP port XXXX ssh2

__________

So my user is definitely added in the "AllowUsers" parameter.
My password that I'm using is definitely correct, I changed it a billion times to the same thing.

Someone said that maybe my HOME DIR permissions are messed up?

](*,) 

Thanks again for your help ^_^ - Hope I can solve this, It's one of the oddest problems I've seen.

---

