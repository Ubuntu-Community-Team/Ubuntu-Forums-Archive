---
title: "How to change root password in Ubuntu (terminal)"
date: 2014-12-11
forum: Security
---

### Post by niki85 on 2014-12-11
Hello,

What is easy way for change root password of my ubuntu 14.10 server, via terminal (putty) ?

Thanks.

---

### Post by schragge on 2014-12-11
In Ubuntu, the root account [is locked by default](https://help.ubuntu.com/community/RootSudo) and doesn't have any password -- you simply cannot log in as root and should use [sudo](http://manpages.ubuntu.com/manpages/utopic/en/man8/sudo.8.html) command instead.

---

### Post by niki85 on 2014-12-11
> **schragge said:**
> In Ubuntu, the root account is locked by default and doesn't have any password -- you simply cannot log in as root and should use *sudo* command instead.

I install ubuntu 14.10 and i get info:

root
password

with this info i login there, how i can change password ?

Thanks.

---

### Post by schragge on 2014-12-11
You should be more precise then. Where did you get that info from? From Ubuntu Installer? How did you install your system? From an official CD image? Did you run the installation in expert mode?

Usually, you don't set up the root password during Ubuntu installation procedure. Instead, installer only asks you to set up a normal user who will get root privileges through sudo (see step 9 [here]("https://help.ubuntu.com/14.04/serverguide/installing-from-cd.html")). You probably *can* set up root password if running installation in expert mode, but then you supposedly know what you are doing.

From [post=13182548]your post here[/post] I see that you have a user named *admin*. Is it this user whom you mean when you say *root password*?

---

### Post by niki85 on 2014-12-11
> **schragge said:**
> You should be more precise then. Where did you get that info from? From Ubuntu Installer? How did you install your system? From an official CD image? Did you run the installation in expert mode?

Usually, you don't set up the root password during Ubuntu installation procedure. Instead, installer only asks you to set up a normal user who will get root privileges through sudo (see step 9 [here]("https://help.ubuntu.com/14.04/serverguide/installing-from-cd.html")). You probably *can* set up root password if running installation in expert mode, but then you supposedly know what you are doing.

From [post=13182548]your post here[/post] I see that you have a user named *admin*. Is it this user whom you mean when you say *root password*?

I buy ovh dedicated server, install ubuntu 14.10 they send me on mail ''root'' and ''password'' who i can use for login inside, now i want to change this password, how i can make this ?

Thanks.

---

### Post by Penguin360 on 2014-12-11
> **niki85 said:**
> I buy ovh dedicated server, install ubuntu 14.10 they send me on mail ''root'' and ''password'' who i can use for login inside, now i want to change this password, how i can make this ?

Thanks.

Then you should contact OVH. They may have restrictions on changing password. But anyway, they are the ones who can help you faster and better.

---

### Post by niki85 on 2014-12-11
> **Penguin360 said:**
> Then you should contact OVH. They may have restrictions on changing password. But anyway, they are the ones who can help you faster and better.

I send request to ovh but they support is terrible slow :)

---

### Post by oldos2er on 2014-12-11
> **niki85 said:**
> I buy ovh dedicated server, install ubuntu 14.10 they send me on mail ''root'' and ''password'' who i can use for login inside, now i want to change this password, how i can make this ?

```
man passwd
```

---

### Post by niki85 on 2014-12-11
> **oldos2er said:**
> ```
man passwd
```

can you please explain ?

Thanks.

---

### Post by schragge on 2014-12-11
See [passwd](http://manpages.ubuntu.com/manpages/utopic/en/man1/passwd.1.html)

---

### Post by thnewguy on 2014-12-11
Wow, people are really not being helpful in this thread. It's a fairly straight forward question.

To change the password for the root user, first login to the root account with the password you were given by your provider. Then run the command
```
passwd
```
You may then be asked to enter your "old" password, the one your provider gave you. The system will then ask you to give it a new password. you will be asked to enter the new password twice. Assuming your new password passes a series of minimal checks to make sure it's long enough and not a dictonary word, your password will be changed.

---

### Post by lisati on 2014-12-11
> **thnewguy said:**
> Wow, people are really not being helpful in this thread. It's a fairly straight forward question.

Perhaps the reason that people have been hesitant to be more direct is that having the root account enabled in Ubuntu is unusual.

From the [RootSudo]("https://help.ubuntu.com/community/RootSudo#root_account") documentation:
> Enabling the Root account is rarely necessary. Almost everything you need to do as administrator of an Ubuntu system can be done via sudo or gksudo. If you really need a persistent Root login, the best alternative is to simulate a Root login shell using the following command...

It is very easy for someone who is inexperienced with *nix systems to accidentally break their system when logged in as root. All it takes is a simple typo for things to go horribly wrong. Using "sudo" helps add a layer of protection that limits the damage.

---

### Post by niki85 on 2014-12-11
> **thnewguy said:**
> Wow, people are really not being helpful in this thread. It's a fairly straight forward question.

To change the password for the root user, first login to the root account with the password you were given by your provider. Then run the command
```
passwd
```
You may then be asked to enter your "old" password, the one your provider gave you. The system will then ask you to give it a new password. you will be asked to enter the new password twice. Assuming your new password passes a series of minimal checks to make sure it's long enough and not a dictonary word, your password will be changed.


Thanks Sir, this is it!

---

### Post by lisati on 2014-12-11
> **niki85 said:**
> Thanks Sir, this is it!

The command you found to work was mentioned earlier in this discussion, in [post 8]("http://ubuntuforums.org/showthread.php?t=2256300&p=13185199&viewfull=1#post13185199"). What the "man" command does is provide information on a command.

If your question has been answered, please mark this thread as "solved" using the "Thread Tools" menu.

---

### Post by niki85 on 2014-12-11
> **lisati said:**
> The command you found to work was mentioned earlier in this discussion, in [post 8]("http://ubuntuforums.org/showthread.php?t=2256300&p=13185199&viewfull=1#post13185199"). What the "man" command does is provide information on a command.

If your question has been answered, please mark this thread as "solved" using the "Thread Tools" menu.

done, thanks guys.

---

### Post by CharlesA on 2014-12-11
> **lisati said:**
> Perhaps the reason that people have been hesitant to be more direct is that having the root account enabled in Ubuntu is unusual.

True. However, unless the VPS or Dedicated server was installed by the user it will probably only have the root account with no sudo account, depending on how the template was set up.

---

### Post by Penguin360 on 2014-12-11
Off topic: if their support for dedicated server customers is slow, then you should stay away from them.

---

### Post by sudharshankr on 2014-12-15
If you have logged into the root account, then in the terminal type the command:

```
passwd
```

then you will be prompted for a new unix password which on entering will reset it.

---

