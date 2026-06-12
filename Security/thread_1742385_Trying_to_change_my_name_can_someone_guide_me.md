---
title: "Trying to change my name can someone guide me?"
date: 2011-04-28
forum: Security
---

### Post by ClientAlive on 2011-04-28
I hope this is a good place to post for this. I wanted to come somewhere where I thought I'd run into someone familiar with this type of thing.

I'm using Ubuntu 11.04 by the way.

I used this  [http://www.cyberciti.biz/faq/ubuntu-linux-howto-rename-user-account/](http://www.cyberciti.biz/faq/ubuntu-linux-howto-rename-user-account/)  link to try and change my old uname to something I prefer better. When I did the install I didn't really think about what I wanted it to be I just wanted to get the install over with. Now I want to change it to what I want.

Below you can see what I've tried and the complaint I'm getting from the system. I'm not sure how to solve this. Can anyone tell me the right way to do this?

Thanks a bunch guys.


```

oldname@computer:~$ sudo usermod -l oldname newname
[sudo] password for oldname: 
usermod: user 'newname' does not exist
somename@computer:~$ man usermod
oldname@computer:~$ sudo usermod -l {oldname} {newname}
usermod: user '{newname}' does not exist
oldname@computer:~$ id newname
id: newname: No such user
oldname@computer:~$ id {newname}
id: {newname}: No such user
oldname@computer:~$ sudo usermod -l newname oldname
usermod: user oldname is currently logged in
oldname@computer:~$ id newname
id: newname: No such user
oldname@computer:~$ sudo -s
root@computer:~# usermod -l newname oldname
usermod: user oldname is currently logged in
computerexit

```

---

### Post by fdrake on 2011-04-28
> **ClientAlive said:**
> I hope this is a good place to post for this. I wanted to come somewhere where I thought I'd run into someone familiar with this type of thing.

I'm using Ubuntu 11.04 by the way.

I used this  [http://www.cyberciti.biz/faq/ubuntu-linux-howto-rename-user-account/](http://www.cyberciti.biz/faq/ubuntu-linux-howto-rename-user-account/)  link to try and change my old uname to something I prefer better. When I did the install I didn't really think about what I wanted it to be I just wanted to get the install over with. Now I want to change it to what I want.

Below you can see what I've tried and the complaint I'm getting from the system. I'm not sure how to solve this. Can anyone tell me the right way to do this?

Thanks a bunch guys.


```

oldname@computer:~$ sudo usermod -l oldname newname
[sudo] password for oldname: 
usermod: user 'newname' does not exist
somename@computer:~$ man usermod
oldname@computer:~$ sudo usermod -l {oldname} {newname}
usermod: user '{newname}' does not exist
oldname@computer:~$ id newname
id: newname: No such user
oldname@computer:~$ id {newname}
id: {newname}: No such user
oldname@computer:~$ sudo usermod -l newname oldname
usermod: user oldname is currently logged in
oldname@computer:~$ id newname
id: newname: No such user
oldname@computer:~$ sudo -s
root@computer:~# usermod -l newname oldname
usermod: user oldname is currently logged in
computerexit

```

read again your link it says:
```
usermod -l {new-login-name} {current-old-login-name}
```
you are doing the opposite : 
you: old  new
the link says: new old!

EDIT : so do this; logout in the login screen! press CTRL+alt+F1  (i am assuming yopu don't have a root user) . login in with you username and password.

type those:
```

sudo adduser temporary
<set the password and just press enter>
exit
<this should bring you to the original login prompt, if not type 'exit' again>
<now login with the 'temporary' user account and password>
<now try to change your username>
usermod -l {new-login-name} {current-old-login-name}
exit
<until u get the login prompt>
<press CTRL+alt+F7 to login on the gui screen and see if this works>

```

---

### Post by ClientAlive on 2011-04-28
Is that the same as if I use the gui to create a new user under "users and groups" in "system settings"? When I looked into that it says it's going to create home directory along with it. I'm a little concerned about the final result and not having another user account that I forget about on the machine.

I did realize that I was entering in the information in the wrong order. About half way down you can see where I changed to the right order. What is this temporary user? How long will it be on my system or will I need to do something to remove it after?

Thanks
-----------------------

Edit: Oh, by the way, if what you mean by having a root user is something I have to do extra to make it so, I don't think I do.

---

### Post by fdrake on 2011-04-28
you can delete the user after you have done those changes. you cannot change a user's name while is logged in and since (from what i understand there isn't any other user on the machine) i am creating a temporary user to run the process while your user is logged out. Root user can me configured but ubuntu doesn't have by default for your own security.

to delete the temporary user, type:
```

<to delete user>
sudo deluser temporary
<to delete the folder in the /home/ of temporary user>
sudo rm -r /home/temporary

```

---

### Post by ClientAlive on 2011-04-28
> **fdrake said:**
> you can delete the user after you have done those changes. you cannot change a user's name while is logged in and since (from what i understand there isn't any other user on the machine) i am creating a temporary user to run the process while your user is logged out. Root user can me configured but ubuntu doesn't have by default for your own security.

to delete the temporary user, type:
```

<to delete user>
sudo deluser temporary
<to delete the folder in the /home/ of temporary user>
sudo rm -r /home/temporary

```


Awesome! I'll give it a try. Thanks!

---

### Post by ClientAlive on 2011-04-28
Yup! That worked. Didn't realize I would have to jump through so many hoops to do it - but it worked.

Found out that "temporary" wasn't in the sudoers file (no admin priveledges) and had to log back in as me (switch to). changed his privileges through the gui: system settings > users and groups > advanced settings. After that I was golden. Logged back in as temporary and did what I needed to do. Back to me and deleted temporary and his home directory. Perfect!

Thanks a bunch man.

Have a great night.

---

### Post by fdrake on 2011-04-28
:p  i am glad it worked. good night! ):P

---

