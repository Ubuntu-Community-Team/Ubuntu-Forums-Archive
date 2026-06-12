---
title: "Change root password?"
date: 2009-06-03
forum: Security
---

### Post by uupreti on 2009-06-03
Can I change my root password ( I don't know old root password ) using Live CD? If yes then How can I do that? If not then what can we do if we forget root password?

Thanks.

---

### Post by lisati on 2009-06-03
Have a look here; [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Feel free to continue with the questions.

---

### Post by uupreti on 2009-06-03
That's a good article but I think I did put my question in wrong way. Let's put it in this way. I forgot all the password in my ubuntu system ( not even my password and root password ). Can I recover or reset my password booting from one of the Live CD?

---

### Post by sisco311 on 2009-06-03
If the root password is locked, then you can boot in recovery mode and reset the password(s):
[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

If you have a root password then you have to boot the kernel with the *init=/bin/bash* option:



And yes you can use a LiveCD as well.

---

### Post by uupreti on 2009-06-03
> **sisco311 said:**
> If the root password is locked, then you can boot in recovery mode and reset the password(s):
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

If you have a root password then you have to boot the kernel with the *init=/bin/bash* option.

And yes you can use a LiveCD as well.

Exactly. That's what I thought before doing but my case is different..

I am in recovery mode and it is asking me for root password before doing anything. Now let's say I have an account **test** and password is **test123** but it is explicitly saying me to enter my root password and prompt is waiting for me to enter root password. If I don't enter root password ( which I don't know) , it will bring me back to same menu. 

FYI: I am using Ubuntu 9.04 Desktop version and I don't know what would happen to previous version.

---

### Post by sisco311 on 2009-06-03
May I ask you why don't you know the root password?

It's your computer, isn't it? :)

---

### Post by uupreti on 2009-06-03
> **sisco311 said:**
> May I ask you why don't you know the root password?

It's your computer, isn't it? :)

Simple answer is I forgot :)

I was under impression that Unix/Linux system is not like Windows where if you forget administrator password then there is nothing you can do about besides re-installing ( unless you use some fairy trick to get back). 

As far as I remember I used to do that a lot in redhat/centos Linux..and why not in Ubuntu?? :(

---

### Post by sisco311 on 2009-06-03
> **uupreti said:**
> Simple answer is I forgot :)


OKAY

in the grub menu highlight the Ubuntu menu entry (NOT the recovery mode)

hit e for edit, then highlight the kernel line and hit e again

remove *ro quiet splash* from the end of the line and

append it with *rw init=/bin/bash* and hit Enter then b to boot.

type: 

```
passwd *username*
```

to change the password and press Ctrl+Alt+Del to reboot.

OPTION2:

Boot the LiveCD, mount the root partition, chroot to the partition and change the password.

Assuming that /dev/sda1 is your root ("/") partition:
```

sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo mount -t sysfs none /mnt/ubuntu/sys
sudo mount -t proc none /mnt/ubuntu/proc
sudo mount --bind /dev/ /mnt/ubuntu/dev
sudo mount --bind /dev/pts /mnt/ubuntu/dev/pts
sudo chroot /mnt/ubuntu
passwd username
exit
sudo reboot

```

---

### Post by cdenley on 2009-06-03
> **uupreti said:**
> 
I was under impression that Unix/Linux system is not like Windows where if you forget administrator password then there is nothing you can do about besides re-installing ( unless you use some fairy trick to get back). 


There is a reason why ubuntu has no root password by default, and there is a reason why posting instructions for setting a root password is not allowed on this forum. Why did you set a root password to begin with? If you hadn't set a root password, you wouldn't be prompted for one in recovery mode.

---

### Post by aysiu on 2009-06-03
By default, Ubuntu does not have a root password. It has a user password, and users in the *admin* group (which includes the first user created during installation) can temporarily escalate to root privileges using their own passwords.

To reset the first user's password if the first user is the only *admin* user, you can use recovery mode, which will give you a root password.

If you set a root password, though, you cannot boot into recovery mode, so, yes, you would use a live CD to reset the password. Probably the easiest thing would be to edit the /etc/group file and confirm the *admin* user is in the *admin* group and that sudo is working properly:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by uupreti on 2009-06-03
> **cdenley said:**
> There is a reason why ubuntu has no root password by default, and there is a reason why posting instructions for setting a root password is not allowed on this forum. Why did you set a root password to begin with? If you hadn't set a root password, you wouldn't be prompted for one in recovery mode.

Wow. Isn't it weird? That means I mustn't have to set root password ever? It's kind of confusing idea to me. I was kind of doing experiment with Ubuntu and I set it. Now I am curious about my question. But if it is not allowed to discuss it in here then I won't force you guys. 

Thanks anyway..

---

### Post by uupreti on 2009-06-03
> **sisco311 said:**
> OKAY

in the grub menu highlight the Ubuntu menu entry (NOT the recovery mode)

hit e for edit, then highlight the kernel line and hit e again

remove *ro quiet splash* from the end of the line and

append it with *rw init=/bin/bash* and hit Enter then b to boot.

type: 

```
passwd *username*
```to change the password and press Ctrl+Alt+Del to reboot.



I was looking for something like this but when I follow these steps, I got the root prompt but when I enter passwd <username> command, it says me **bash passwd: command not found**. It's weird ....:(

---

### Post by sisco311 on 2009-06-03
> **uupreti said:**
> I was looking for something like this but when I follow these steps, I got the root prompt but when I enter passwd <username> command, it says me **bash passwd: command not found**. It's weird ....:(

hmmmm

maybe the PATH variable is not set
try:
```
/usr/bin/passwd <uname>
```

and of course if you have a different /usr partition, then you have to mount it:
```
mount /dev/sd<XY> /usr
```

> **aysiu said:**
> If you set a root password, though, you cannot boot into recovery mode, so, yes, you would use a live CD to reset the password. Probably the easiest thing would be to edit the /etc/shadow file and confirm the admin user is in the admin group and that sudo is working properly

Excellent idea.

OP: boot the LiveCD, mount the root partition and lock the root password by editing the /etc/shadow file. 

from something like this 
> [noparse]root:[/noparse]**[noparse]$1$xT12LOOLWUT$L<thisisthepassword>qs2/wM4nNIWjNPidn1R/[/noparse]**[noparse]:14396::::::
bin:x:0::::::
daemon:x:0::::::[/noparse]

to
> [noparse]root:!:14396::::::
bin:x:0::::::
daemon:x:0::::::[/noparse]


**$1$xT12LOOLWUT$L<thisisthepassword>qs2/w....1R/** is the encrypted password, you have to replace it with "!" to lock the root account. 

then you can reboot in recovery mode.

---

### Post by uupreti on 2009-06-03
> **aysiu said:**
> 
If you set a root password, though, you cannot boot into recovery mode, so, yes, you would use a live CD to reset the password. Probably the easiest thing would be to edit the /etc/shadow file and confirm the *admin* user is in the *admin* group and that sudo is working properly:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)


Ok it solved my problem. 

One friend suggested me to boot kernel with **rw init=/bin/bash** to reset password. It took me too singler user mode but it says wrong command. 

But anyway Thanks for your help and this is exactly what I was looking for (At least I could change password editing files) .

---

### Post by uupreti on 2009-06-03
> **sisco311 said:**
> 


**$1$xT12LOOLWUT$L<thisisthepassword>qs2/w....1R/** is the encrypted password, you have to replace it with "!" to lock the root account. 

then you can reboot in recovery mode.

I didn't know about **"!" **. So for now I created MD5 encrypted password and replace that part. But good to know that **"!"** will lock user account.

You guys rocks...

Thanks..

---

