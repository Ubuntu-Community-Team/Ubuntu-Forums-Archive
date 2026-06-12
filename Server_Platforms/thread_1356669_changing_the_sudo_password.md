---
title: "changing the sudo password"
date: 2009-12-16
forum: Server Platforms
---

### Post by Vegan on 2009-12-16
I was wondering is it possible to change only the sudo password separately from the log-in one so that its more secure against unauthorized access?

for example user ubuntu logs in with his password, by default sudo uses the same password, I wanted to change only the sudo password not the log-in one.

Thanks in advance.

---

### Post by Grenage on 2009-12-16
Why would it be more secure that way?  A password is a password.

---

### Post by bruno9779 on 2009-12-16
> **Grenage said:**
> Why would it be more secure that way?  A password is a password.

It IS more secure, because you can give someone the password of your box, without giving away root access.

on the other hand, if this is the case, I would create a guest profile, with a login password different from root's password

---

### Post by snowpine on 2009-12-16
You can enable a separate "root password" to make Ubuntu more like other Linux distros in this regard.

I am not allowed to tell you how (according to forum rules), but I think it is okay to link to the instructions [on this page]("https://help.ubuntu.com/community/RootSudo#Enabling%20the%20root%20account").

Bruno is on the right track that the more elegant solution is to create a guest account with restricted privileges. :)

---

### Post by Grenage on 2009-12-16
Indeed, a separate account would be the proper way to go; that or assigning the root account a password.

---

### Post by cdenley on 2009-12-16
I think sudo can only use the password for the user running sudo, the password for the user sudo will run a command as, or the root password. I don't recommend setting a root password. The most secure setup would be to have an admin user who can use sudo with their password, and a regular user (which you would login as). You would then have to switch to your admin user to perform admin tasks which would have a different password than your regular user.
```

su adminuser
sudo rootcommand

```

---

### Post by craigp84 on 2009-12-16
Hi,

From the sudoers man page ("man 5 sudoers")

>       rootpw      If set, sudo will prompt for the root password instead of the password of the invoking user.  This flag is off by default.

       runaspw     If set, sudo will prompt for the password of the user defined by the runas_default option (defaults to root) instead of the password of
                   the invoking user.  This flag is off by default.

       targetpw    If set, sudo will prompt for the password of the user specified by the -u flag (defaults to root) instead of the password of the invok-
                   ing user.  This flag is off by default.



hope it helps,

-c

---

### Post by kewlrichie on 2009-12-16
The first username you setup during install is a "sudoer" all accounts after that using just the command adduser will not be added to the sudoers so they wouldnt be able to sudo and it will be a limited account if thats what you were looking for.

---

### Post by Vegan on 2009-12-18
I wanted to harden root access so a normal "adduser" cannot invoke sudo at all.

I see this as a security idea and I have seen this with other operating systems so why not Ubuntu.

by default the adduser creates a new user and group both with the same name. 

I would also like to change/organize groups so that web site users are in their own client group that is separate from the main system groups and where I can more easily limit access.

Then I can assign more secure access to various groups?

Hope my thinking is not to extreme.

So here is my thinking:

```

login: user
password: pass

sudo nano /etc/apache2/httpd.conf
password for sudo:

```
I wanted to have a different password for the sudo as for the admin's account as an extra layer of security, I do not want to have a su account, juts more secure.

---

### Post by cdenley on 2009-12-18
Users you add will be able to execute the sudo command, but with the default configuration, only members of the admin group (and root) can execute commands with sudo. New users created with "adduser" can try, but will fail.

By default, if sudo is configured to allow a group to execute a certain command, such as "/bin/nano /etc/apache2/httpd.conf", then users in that group will be able to execute that command when they give their own password. Be aware that when you allow the above command, you allow editing any file with commands such as "/bin/nano /etc/apache2/httpd.conf /etc/shadow". DO NOT ALLOW SUDO ACCESS TO A TEXT EDITOR.

If you want the "adduser" command to add users to a single group instead of creating a new group for each user, edit /etc/adduser.conf, and change "USERGROUPS" to "no". You can then set the default group id with "USERS_GID".

---

### Post by Vegan on 2009-12-18
ideally I would like to assign certain user accounts to various specific groups based on a typical corporate org chart layout.

---

### Post by cdenley on 2009-12-18
> **Vegan said:**
> ideally I would like to assign certain user accounts to various specific groups based on a typical corporate org chart layout.

No problem. Either assign them to a particular group when when adding the user
```

sudo adduser --ingroup myusergroup newuser

```
Or add the user to the group at any time
```

sudo adduser existinguser myusergroup

```

---

### Post by Vegan on 2009-12-18
Is it possible to have a user a member of 2 groups, such as admin and finance?

Or should I use a more sophisticated grouping layout?

---

### Post by tekkidd on 2009-12-18
> **Vegan said:**
> I was wondering is it possible to change only the sudo password separately from the log-in one so that its more secure against unauthorized access?

for example user ubuntu logs in with his password, by default sudo uses the same password, I wanted to change only the sudo password not the log-in one.

Thanks in advance.

Sudo is reffering to the user having sudo rights when you do sudo apt-get install xxx and it asks for a sudo password it is asking for your password not the sudo password to change it you have to change your password. All that sudo does is authenticate weather or not you have the right to execute sudo their is no " "sudo password"

---

### Post by Vegan on 2009-12-18
How can I assign sudo to only a specific set of users such as the CEO and the IT team. The Comptroller does not need sudo no does Sales etc.

The problem is that IT Team has a manager and subordinates. So limiting access to sensitive data needs to be secure to only select members.

---

### Post by cdenley on 2009-12-19
A user can be a member of as many groups as you like. In fact, the default user is a member of quite a few.
```

id

```

If you want the groups "ceo" and "it" to be able to execute any command with sudo, then edit the /etc/sudoers file using the "visudo" command
```

sudo EDITOR=nano visudo

```
add these lines
```

%ceo ALL=(ALL) ALL
%it ALL=(ALL) ALL

```
save, close

---

### Post by rd1381 on 2010-02-05
> **cdenley said:**
> I think sudo can only use the password for the user running sudo, the password for the user sudo will run a command as, or the root password. I don't recommend setting a root password. The most secure setup would be to have an admin user who can use sudo with their password, and a regular user (which you would login as). You would then have to switch to your admin user to perform admin tasks which would have a different password than your regular user.
```

su adminuser
sudo rootcommand

```

the problem with this solution is that many GUI menu items in ubuntu are configured to get root access by issuing a gtksu or sudo or kdesu command and having a separate account with sudo access doesn't help because ubutnu is somehow stupid in this matter because if you log in with a guest(limited:a account that doesn't have sudo access) and click on many of admin apps icon it still ask for your password and when you enter it it gives you an error(that you are not a sudoer) and the privileged account  password wont work either( it says incorrect pass)
what i find ideal is a situation like windows 7 which you can log in as a regular user and when performing admin acts it ask for the admin password in a GUI way.(and by the way windows has disabled administrator default account (they copied ubuntu way :) ) but still having a separate privileged account works ) ( please don't say windows got it wrong because imho loggin in with a user and doing admin stuff with the same login pass in NOT secure(you may want to log in a thousand time a day but not every time you want to do admin stuff) and the other way is logging with a privileged account to do admin stuff and this way negates the whole not having root login concept that linux users recommend everywhere on net)
the best compromise i found is to make sudo ask for root password but that requires to enable the root.so anybody knows how to make sudo ask for a specific account password but not the logged in one or the root one?.

---

### Post by cdenley on 2010-02-08
> **rd1381 said:**
> the problem with this solution is that many GUI menu items in ubuntu are configured to get root access by issuing a gtksu or sudo or kdesu command and having a separate account with sudo access doesn't help because ubutnu is somehow stupid in this matter because if you log in with a guest(limited:a account that doesn't have sudo access) and click on many of admin apps icon it still ask for your password and when you enter it it gives you an error(that you are not a sudoer) and the privileged account  password wont work either( it says incorrect pass)
what i find ideal is a situation like windows 7 which you can log in as a regular user and when performing admin acts it ask for the admin password in a GUI way.(and by the way windows has disabled administrator default account (they copied ubuntu way :) ) but still having a separate privileged account works ) ( please don't say windows got it wrong because imho loggin in with a user and doing admin stuff with the same login pass in NOT secure(you may want to log in a thousand time a day but not every time you want to do admin stuff) and the other way is logging with a privileged account to do admin stuff and this way negates the whole not having root login concept that linux users recommend everywhere on net)
the best compromise i found is to make sudo ask for root password but that requires to enable the root.so anybody knows how to make sudo ask for a specific account password but not the logged in one or the root one?.

That sounds like policykit, which is getting incorporated into the GUI admin tasks more and more. All GUI admin tasks may use it now, I'm not sure. You can authenticate as an admin user to perform admin tasks in the GUI, even if you are not logged into GNOME as an admin user.

---

### Post by rd1381 on 2010-02-08
> **cdenley said:**
> That sounds like policykit, which is getting incorporated into the GUI admin tasks more and more. All GUI admin tasks may use it now, I'm not sure. You can authenticate as an admin user to perform admin tasks in the GUI, even if you are not logged into GNOME as an admin user.

i guessed that much (frnder the menu that appears that show something like org.freedesktop.... something like that) 
by the way how it can get access to install or do root stuff in my limited account(by gettong another privilated user pass) when i cant even sudo?
i mean i can't sudo -u in my account.

---

### Post by cdenley on 2010-02-08
PolicyKit is not related to sudo. They are two different methods of privilege escalation. I believe it uses DBUS to communicate with a process via IPC to escalate privileges once authenticated.

By the way, you can "su myadminuser" to perform a task as another user, which would then allow you to use "sudo".

---

### Post by rd1381 on 2010-02-08
> **cdenley said:**
> PolicyKit is not related to sudo. They are two different methods of privilege escalation. I believe it uses DBUS to communicate with a process via IPC to escalate privileges once authenticated.

By the way, you can "su myadminuser" to perform a task as another user, which would then allow you to use "sudo".

for the first answer : i still dont get it. doesn't pocilykit sit on top on kernel and low level api ? i mean how does it get access to do the stuff it does when i cant get to do anything unless i login to super account or add myself to sudo ( which i dont like (it low security)).does it uses a special command(i mean if i wanted to emulate it in terminal) or it does somthing directly in kernel?( how can i get that?)? and can i add another command to it?(i doubt it) does it have a gui manager( i think i seen it before but don't remember where)


sorry if its to much to ask

and for your second answer: its no use for me at least. because when i su to anther account its not same as sudo (i cant so some stuff( and gui wont work cause it needs some access to screen (x) that it cant get)

---

### Post by cdenley on 2010-02-08
As I already said, it communicates with the policykit process with IPC, which runs as root, to escalate privileges.
```

sudo ps -ef|grep "[p]olkitd"

```

I never tried it, but to use policykit from the terminal, look into the pkexec command.
```

man pkexec

```

To configure it:
System>Administration>Authorizations

---

### Post by sisco311 on 2010-02-08
> **rd1381 said:**
> 

and for your second answer: its no use for me at least. because when i su to anther account its not same as sudo (i cant so some stuff( and gui wont work cause it needs some access to screen (x) that it cant get)

First you have to allow the admin user to connect to the X server:
```
xhost SI:localuser:**username**
su - username
gui-application 

```
By I still don't get what's the point of having another 


BTW, as cdenley pointed out, if you are logged in as a non-admin user policykit will prompt you for an admin password. A lot of GUI applications already use policykit: gnome-system-tools (Users & groups, Date & time, Shares... ), NetworkManager, palimpsest,  software-center...

> **rd1381 said:**
> 
...
(please don't say windows got it wrong because imho loggin in with a user and doing admin stuff with the same login pass in NOT secure(you may want to log in a thousand time a day but not every time you want to do admin stuff) and the other way is logging with a privileged account to do admin stuff and this way negates the whole not having root login concept that linux users recommend everywhere on net)


In Linux (and Unix in general), the superuser is root. The Windows equivalent of root is Administrator.

sudo allows authorized users (by default users in the admin group) to run certain programs as root.

So, basically you are logged in as a normal user & use a suid root application to run commands as root, just like you use runas in Windows.

---

### Post by rd1381 on 2010-02-09
> **cdenley said:**
> As I already said, it communicates with the policykit process with IPC, which runs as root, to escalate privileges.
```

sudo ps -ef|grep "[p]olkitd"

```

I never tried it, but to use policykit from the terminal, look into the pkexec command.
```

man pkexec

```

To configure it:
System>Administration>Authorizations

that is very interesting 
thanks for your answer
though using pkexec doesnt help me cause it uses predefined policy that are not changeable (i mean like adding a command to its list to ask for another user pass and grant access)

your other post is a godsend
thanks for "xhost SI:localuser:*username*" its great 

as for your question that why i want to do these stuff is that i want to be able to configure ubuntu like windows .so that i can log in with a limited user but still be able to do admin stuff with another user pass. right now ubuntu doesn't do that in default and playing with sudoers file to do that messed up my system 2 time already ( imho ubuntu has a bad way of handling root account and enabling and disabling it )
so if i add myself to sudo(admin)group then my limited password can do anything and if i dont i cant do anything in my limited account(*** you said policykit has many apps configured ,but funnily enough not synaptic:) ) so i have to loging to anther super account.

but this command that you mentioned is very helpful .thanks a lot man

---

### Post by cdenley on 2010-02-10
> **rd1381 said:**
> 
you said policykit has many apps configured ,but funnily enough not synaptic:) ) so i have to loging to anther super account.


Ubuntu Software Center does use policykit. You should be able to accomplish anything you need to with a policykit enabled interface. I can't really say for sure since I usually use the terminal myself.

---

### Post by rd1381 on 2010-02-10
> **cdenley said:**
> Ubuntu Software Center does use policykit. You should be able to accomplish anything you need to with a policykit enabled interface. I can't really say for sure since I usually use the terminal myself.

thanks man. i did not know that
but still i am like you , i am (forced) learning terminal and i like it.:)
and it would be great if policykit was configurable for users to add new command to it.

---

