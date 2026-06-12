---
title: "Guest Account is able to authenticate as root. Help!"
date: 2011-06-25
forum: Security
---

### Post by ahears on 2011-06-25
I am trying to use a guest account in Ubuntu 10.10 however I am unable to stop the guest account from authenticating as a superuser and gaining root permissions dispite removing all permissions from the user-group control panel. The new guest account I created is not part of the admin group. However, with my new guest account I am unable to start a guest session from the panel, AND if I use the guest session from the panel I dont have the problem with the guest session being able to authenticate. How do I prevent super user authentication from an account in this situation? It seems that any  account can authenticate and my /etc/sudoers file looks like this:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by Thewhistlingwind on 2011-06-25
Have you tried removing the guest account from the sudo group as well?

EDIT: Actually, I have no idea what I'm talking about, consider this a free bump.

---

### Post by bab1 on 2011-06-25
> **ahears said:**
> I am trying to use a guest account in Ubuntu 10.10 however I am unable to stop the guest account from authenticating as a superuser and gaining root permissions dispite removing all permissions from the user-group control panel. 
How did you create this *guest account*?  How do you know it is authenticated as root?  Root is the only super user.  No other account can *_authenticate as root_*.  Other accounts can temporarily run commands with root privileges ( a loose description of what really happens) using sudo.  

What is the user name for this account?  AFAIK the only accounts on a Linux host are root, system users (such as cdrom) or mortal users (humans).> 

The new guest account I created is not part of the admin group. However, with my new guest account I am unable to start a guest session from the panel, AND if I use the guest session from the panel I dont have the problem with the guest session being able to authenticate. 
I'm lost here, not sure what you are saying.  What do you mean by *guest session*?> 
How do I prevent super user authentication from an account in this situation? It seems that any  account can authenticate 

Once again; can you describe what you mean?  What unexpected results are happening? > 

and my

/etc/sudoers file looks like this:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

Have you modified this file in any way.  It looks like only the groups *sudo *and *admin* have sudo rights.

post the results of ```
getent group| grep admin
```
and the results of ```
getent group| grep sudo
```

---

### Post by ahears on 2011-06-27
The results are as follows: 

[B]lpadmin:x:111:user
admin:x:119:user
[/B]
and 

[B]sudo:x:27:
[/B]
respectively.

I have been using the guest session that appears in the panel to the top right menu drop down in Ubuntu 10.10. (the icon looks like a switch) to get the guest session option, however, I am able to authenticate with super-user privileges with***_ any_*** account even if I remove all privileges through the add remove users/groups GUI that comes with Ubuntu.

---

### Post by bab1 on 2011-06-27
> **ahears said:**
> The results are as follows: 

[B]lpadmin:x:111:nemisis
admin:x:119:nemisis
[/B]
and 

[B]sudo:x:27:
[/B]
respectively.

This shows that sudo is not the culprit in regards to the root privileges being granted to the user account named  *guest*. Did you create this account or was it there to begin with.  Is [**_[COLOR="DarkSlateGray"]this[/COLOR]_**]("http://www.linuxbsdos.com/2010/10/18/guest-session-and-guest-user-accounts-in-ubuntu/") what we are talking about?  Did you configure your guest account like [**_[COLOR="DarkSlateGray"]this[/COLOR]_**]("http://www.linuxbsdos.com/2010/05/24/how-to-create-a-guest-user-account-on-ubuntu-10-04/")?
> 

I have been using the guest session that appears in the panel to the top right menu drop down in Ubuntu 10.10. (the icon looks like a switch) to get the guest session option, however, I am able to authenticate with super-user privileges with***_ any_*** account even if I remove all privileges through the add remove users/groups GUI that comes with Ubuntu.
Explain what you mean by able to 'authenticate with super-user privileges".

On a Ubuntu system [COLOR="DarkGreen"]authenticate[/COLOR] means the user is verified as that user.  This is a combination of user/pass.  This is NOT [COLOR="Blue"]authorization[/COLOR].  [COLOR="Blue"]Authorization[/COLOR] is the rights you have to execute commands.  Only root can authenticate as root when either logging in or switching users (su).

Can you provide an example how you do this: "I am able to authenticate with super-user privileges with***_ any_*** account..."

---

### Post by ahears on 2011-06-27
It seems that when running a program that would normal require a administrative privilege that the system Guest account (known as a 'guest session') and the account I created named 'guest' can authenticate with sufficient privileges to successfully give themselves more permissions. This can be done through the 'Users and Groups' menu in the system menu. How can I prevent this? I want to fail authentication from all accounts except those belonging to the admin group. I am unable to, as the user can still enter a superuser password and modify system settings. I checked both of your links but I have tried both of them - removing all priveliges and the new 'guest' account AND the 'guest session' can still enter the superuser password and gain administrative permissions to make system changes.

---

### Post by bab1 on 2011-06-27
> **ahears said:**
> It seems that when running a program that would normal require a administrative privilege that the system Guest account (known as a 'guest session') and the account I created named 'guest' can authenticate with sufficient privileges to successfully give themselves more permissions. This can be done through the 'Users and Groups' menu in the system menu. How can I prevent this? I want to fail authentication from all accounts except those belonging to the admin group. I am unable to, as the user can still enter a superuser password and modify system settings. I checked both of your links but I have tried both of them - removing all priveliges and the new 'guest' account AND the 'guest session' can still enter the superuser password and gain administrative permissions to make system changes.

If this is possible: "the user can still enter a superuser password...".  Then you have enabled the root password.  Ubuntu's default is to have not allow superuser access via a root password.

If you enable the root password you have implied that any user who knows the password can use it.  As a start, I would deny anyone from having the ability to log in to the system as root.  The only avenue to root status should be with su.  The whole idea of sudo is to control who can use su to gain root status.

I think this might be a bit circular,  but you might try using sudo to limit who has the right to use the command su (/bin/su) after removing root login capability. Sudo is more powerful that just letting some users run commands as root.

On the other hand if you allow guests on you system it is in peril at all times.  Physical access = 0 security.

---

### Post by ahears on 2011-06-28
I think you are right about the root password, however how do I remove it and only allow one user to use it for upgrades and system changes? I have already exhausted my expertise in this area. Oh, and I am using gksudo and sudo to gain superuser priveliges and there is no root account. It's only me and the guest, but the guest with no priveliges can gain priveliges by using my password from my account as I am the admin. Hang on I gotta read_ my own links_ MORE but I have done everything, I must be missing something...


Running synaptic as guest will fail even if I get the password correct but I am still able to get in the user and groups menu and grant myself admin priveliges (by entering the password for my account) from the menu and then get into the disk janitor, network tools, disk utility, mount and unmount and even delete partitions and rename drives!!! It is still a huge security problem. Maybe I'm looking at this all wrong, but shouldn't the privileges be limited to a designated account, and not available system wide?

---

### Post by bab1 on 2011-06-28
> **ahears said:**
> I think you are right about the root password, however how do I remove it and only allow one user to use it for upgrades and system changes? I have already exhausted my expertise in this area. Oh, and I am using gksudo and sudo to gain superuser priveliges and there is no root account. It's only me and the guest, but the guest with no priveliges can gain priveliges by using my password from my account as I am the admin. Hang on I gotta read_ my own links_ MORE but I have done everything, I must be missing something...

Yes you are missing the whole idea.  When you use sudo or su (or for the GUI gksudo or gksu) you are not gaining privileges.  With sudo you are executing a command as root (root is doing the execution).  When you use su you are **s**witching **u**sers (su does NOT mean super user).  You can switch to another mortal user if you know that users password.  If I am logged in as jon (jon@here:~$) and I use the command su like this ```
jon@here:~$su bill
```
and use Bill's password, I am now using the user bill's account.  I am not assuming his privileges in my account.  The prompt should look like this ```
bill@here:/home/jon$
```
This is because I am still at the same location I was before I issued the su command.  If I issue this command ```
bill@here:/home/jon$[COLOR="Red"]cd[/COLOR]
```
I will move to the user bill's home directory (because I am in essence bill) and the prompt will be ```
bill@here:~$
```If you issue this command ```
]bill@here:~$[COLOR="Red"]pwd[/COLOR]
``` You will see that you are at ```
/home/bill
```

To exit form bill (bill's shell) you can do this at the prompt```
exit
```Now you will be back to jon's shell and prompt.    

All this leads to how you are using sudo and who you think you are.  You the person is not whom we are talking about.  The you is the user account and how that works with sudo or su.

With sudo in the Ubuntu default state the mortal user (jon or bill) if they are in the admin group can run ANY command as root.  This can be configured to a SPECIFIC command and a different group.  You could for instance allow the user bill to run only the command "sudo reboot" as root (the only way it will work is as root).  Sudo stand for switch user (and) do...

I suggest you read read up on sudo and su.  You can start [**_here_**]("http://www.google.com/search?q=sudo+tutorial&btnG=Go!").  

> 
Running synaptic as guest will fail even if I get the password correct but I am still able to get in the user and groups menu and grant myself admin priveliges (by entering the password for my account) from the menu and then get into the disk janitor, network tools, disk utility, mount and unmount and even delete partitions and rename drives!!! It is still a huge security problem. Maybe I'm looking at this all wrong, but shouldn't the privileges be limited to a designated account, and not available system wide?

Read the above.  The right to use sudo is by default based on an account and it is system wide.  Like I said it can be changed.  Read the tutorial.

On last thing.  Always use the command [COLOR="Blue"]visudo[/COLOR] to edit the sudoers file.  It handles the formating and the syntax.  You will just mess up the sudoers file if you use any text editor without visudo.  By default visudo invokes nano as the editor.  Do not ever invoke nano directly on the sudoers file.  See [**_here_**]("https://help.ubuntu.com/community/Sudoers") for info on changing the editor.

---

### Post by ahears on 2011-06-29
> **bab1 said:**
> Yes you are missing the whole idea.  When you use sudo or su (or for the GUI gksudo or gksu) you are not gaining privileges.  With sudo you are executing a command as root (root is doing the execution).  When you use su you are **s**witching **u**sers (su does NOT mean super user).  You can switch to another mortal user if you know that users password.  If I am logged in as jon (jon@here:~$) and I use the command su like this ```
jon@here:~$su bill
```and use Bill's password, I am now using the user bill's account.  I am not assuming his privileges in my account.  The prompt should look like this ```
bill@here:/home/jon$
```This is because I am still at the same location I was before I issued the su command.  If I issue this command ```
bill@here:/home/jon$[COLOR=Red]cd[/COLOR]
```I will move to the user bill's home directory (because I am in essence bill) and the prompt will be ```
bill@here:~$
```If you issue this command ```
]bill@here:~$[COLOR=Red]pwd[/COLOR]
``` You will see that you are at ```
/home/bill
```To exit form bill (bill's shell) you can do this at the prompt```
exit
```Now you will be back to jon's shell and prompt.    

All this leads to how you are using sudo and who you think you are.  You the person is not whom we are talking about.  The you is the user account and how that works with sudo or su.

With sudo in the Ubuntu default state the mortal user (jon or bill) if they are in the admin group can run ANY command as root.  This can be configured to a SPECIFIC command and a different group.  You could for instance allow the user bill to run only the command "sudo reboot" as root (the only way it will work is as root).  Sudo stand for switch user (and) do...

I suggest you read read up on sudo and su.  You can start [**_here_**]("http://www.google.com/search?q=sudo+tutorial&btnG=Go%21").  



Read the above.  The right to use sudo is by default based on an account and it is system wide.  Like I said it can be changed.  Read the tutorial.

On last thing.  Always use the command [COLOR=Blue]visudo[/COLOR] to edit the sudoers file.  It handles the formating and the syntax.  You will just mess up the sudoers file if you use any text editor without visudo.  By default visudo invokes nano as the editor.  Do not ever invoke nano directly on the sudoers file.  See [**_here_**]("https://help.ubuntu.com/community/Sudoers") for info on changing the editor.

Ok, so just to be safe I read all of the documentation and I understand all of it. I have even changed my 'sudo visudo' command to execute my favorite editor for the '/etc/sudoers' file, and I have listed my '/etc/sudoers' file at the top of the listing. My problem is still that I can use the _System >> Administration >> Users and Groups >> Advanced Settings >> User Privileges >>  Administer the System_ check-box to gain administrator privileges from* any account* using an admin password, thus permanently gaining the ability to elevate to an Administrator, *and then gain access to the list of user names and other critical information* (without permission to use this password). Someone could easily get my password and still not know the name of my account (which is the only account in the admin group) and use it to gain Administrator status. Even a guest that is not allowed to Switch Users could after using that password. The Ubuntu Gui doesn't seem secure to me. Maybe it's 'gksu' and not sudo that is the problem. This only occurs in the Ubuntu GUI...

---

### Post by guzjd on 2011-06-29
I don't think it is a GKSU problem.  As stated in the man pages GKSU is a frontend for SU. SU doesn't use the SUDOERS file. SUDO & GKSUDO does.
 
What exactly is the purpose of this account that you've made?

---

### Post by ahears on 2011-06-29
> **guzjd said:**
> I don't think it is a GKSU problem.  As stated in the man pages GKSU is a frontend for SU. SU doesn't use the SUDOERS file. SUDO & GKSUDO does.
 
What exactly is the purpose of this account that you've made?

Other people use my computer. I am around people who want to try hacking but don't have the brains to do it in a controlled environment such as Virtual Box. I am also going to college to get a degree in computer science but in the mean time I am learning at my own expense. I am dual booting Ubuntu with Windows 7 (Just to try it out Window 7) and have some security concerns with Ubuntu. Such as being able to "Authenticate" (I use 'authenticate' loosely) to change system settings through the Ubuntu GUI. > Ok, so just to be safe I read all of the documentation and I understand  all of it. I have even changed my 'sudo visudo' command to execute my  favorite editor for the '/etc/sudoers' file, and I have listed my  '/etc/sudoers' file at the top of the listing. My problem is still that I  can use the _System >> Administration >> Users and Groups  >> Advanced Settings >> User Privileges >>   Administer the System_ check-box to gain administrator privileges from* any account* using an admin password, thus permanently gaining the ability to elevate to an Administrator, *and then gain access to the list of user names and other critical information*  (without permission to use this password). Someone could easily get my  password and still not know the name of my account (which is the only  account in the admin group) and use it to gain Administrator status.  Even a guest that is not allowed to Switch Users could after using that  password. The Ubuntu Gui doesn't seem secure to me. Maybe it's 'gksu'  and not sudo that is the problem. This only occurs in the Ubuntu GUI... I have found that in Ubuntu on any account; if I use the right password I can gain Administrator priveliges. I can't figure out why a 'guest session' or an account created to have only desktop user privileges (or in my case 0 privileges for a guest; except wireless access) would be able to run *any* program, and when prompted for a password be able to type one in and gain Administrator privileges! Ie. If I am Guest, I CAN enter a password and *GIVE* privileges to myself *(as a user with no privileges marked in the _System >> Administration >> Users and Groups  >>  Advanced Settings >> User Privileges >>   Administer the  System_ check-box)* equal to a Administrator. This should not be possible from any account that is not in the Admin group as is show in my '/etc/sudoers' file.

---

### Post by guzjd on 2011-06-29
In your case I would set up your users with separate accounts and configure Auditing. A tool like tripwire or aide is also good to generate a report to ensure they aren't modifying files they shouldn't be.
 
Sounds to me like they are general users and don't need admin rights.
 
You can go into the network properties (GUI) and give them access to modify networking properties if you so desire, but shouldn't be necessary for them to connect to the network, if I remember correctly.
 
Most of your important files that have password information or are for system use are pretty well protected with filesystem permissions. 
 
Auditing would just be good to check who is logging in and what kind of stuff they are doing on your system.
 
I can't track down where the guest account became a problem but it could have a uid assigned to it that is within the system range (0-99) if I remember correctly.

---

### Post by ahears on 2011-06-30
Well it seems my problem is that the command line and GUI do not behave the same. Ie. sudo v.s. gksudo (or **G**t**k** **S**witch **U**ser **DO)**. There are different behaviours, still, as a Desktop user with no privileges, I can enter a password and gain Administrator access from any account in the GUI, despite my inability to do so from the command line. I still need help.

---

### Post by bab1 on 2011-06-30
> **ahears said:**
> Well it seems my problem is that the command line and GUI do not behave the same. Ie. sudo v.s. gksudo (or **G**raphi**k** **S**witch **U**ser **DO)**. There are different behaviours, still, as a Desktop user with no privileges, I can enter a password and gain Administrator access from any account in the GUI, despite my inability to do so from the command line. I still need help.

The Gk stands for Gtk not Graphik.  :D  Just Thought I would toss that in.  Gtk is what most of the GUI for Gnome is built with.

So now we are saying the ANY desktop user can use gksudo and run root owned routines?  What circumstances are you referring to when you say this: "I can enter a password and gain Administrator access from any account in the GUI"

Originally you said this was the guest-session that was available through your account (with a /tmp based shell).  Then you said you created it with Users and Groups.  Can you explain how you created this user that can use  anther users password.  

The use of the term "I" doesn't seem to work  here.  We are not talking about you (the "I") we are talking about Ubuntu users and the rights (permissions) granted them or the user that they are sudo'd to.  To say "I" really means the user that you are logged into the system.  Lets use the users login when referring to the situation.  It will be clearer. 

Is this just a regular user with a home directory under /home?  When a basic user is logged in and invokes gksudo (or sudo for that matter) the only password that is valid to elevate privileges  is their own password.

---

### Post by ahears on 2011-06-30
> **bab1 said:**
> The Gk stands for Gtk not Graphik.  :D  Just Thought I would toss that in.  Gtk is what most of the GUI for Gnome is built with. 

Oops, my mistake... a little error on my part.. Thank you, that makes more sense.. in all of my reading I must have missed this one. :)

> 
So now we are saying the ANY desktop user can use gksudo and run root owned routines?  What circumstances are you referring to when you say this: "I can enter a password and gain Administrator access from any account in the GUI"

Originally you said this was the guest-session that was available through your account (with a /tmp based shell).  Then you said you created it with Users and Groups.  Can you explain how you created this user that can use  anther users password.  

The use of the term "I" doesn't seem to work  here.  We are not talking about you (the "I") we are talking about Ubuntu users and the rights (permissions) granted them or the user that they are sudo'd to.  To say "I" really means the user that you are logged into the system.  Lets use the users login when referring to the situation.  It will be clearer. 

Is this just a regular user with a home directory under /home?  When a basic user is logged in and invokes gksudo (or sudo for that matter) the only password that is valid to elevate privileges  is their own password.That is exactly it, any user can use my password and gain privileges. When I am the "Guest" I mean that I have tested both the 'Guest Session' available in the System Logout Menu (I think thats the name) which provides me with the ability to switch users, log out, shut-down, etc.. _*and*_ I have used the method of creating an account with the name 'Guest' (which will invalidate the 'Guest Session') and then removed all privileges through the 'Users and Groups' menu , selected a password of 'password', and disabled the password prompt at login for this account. After all of this, I am still able to use ***my*** password from ***my*** personal account (which is the *only* account in the Admin group) in the GUI 'Users and Groups' menu to gain Administrator privileges while logged into the _*guest*_ account.

---

### Post by redmk2 on 2011-06-30
> **ahears said:**
> Oops, my mistake... a little error on my part.. Thank you, that makes more sense.. in all of my reading I must have missed this one. :)

That is exactly it, any user can use my password and gain privileges. When I am the "Guest" I mean that I have tested both the 'Guest Session' available in the System Logout Menu (I think thats the name) which provides me with the ability to switch users, log out, shut-down, etc.. _*and*_ I have used the method of creating an account with the name 'Guest' (which will invalidate the 'Guest Session') and then removed all privileges through the 'Users and Groups' menu , selected a password of 'password', and disabled the password prompt at login for this account. After all of this, I am still able to use ***my*** password from ***my*** personal account (which is the *only* account in the Admin group) in the GUI 'Users and Groups' menu to gain Administrator privileges while logged into the _*guest*_ account.

The "Guest" user you created is the same as any other user.  In this case it is just a name, no different than bill, bob, father, son, sister of wife.  In fact, to the system they are just characters in a string.

A normal user account is very different from a *guest-session* user.

I'll bet if you made the password operational that the problems would go away.  The system is misconfigured in my opinion.

---

### Post by bab1 on 2011-07-01
> **redmk2 said:**
> The "Guest" user you created is the same as any other user.  In this case it is just a name, no different than bill, bob, father, son, sister of wife.  In fact, to the system they are just characters in a string.

A normal user account is very different from a *guest-session* user.

I'll bet if you made the password operational that the problems would go away.  The system is misconfigured in my opinion.


+1 I think you have misconfigured the account is some way too.

You describe situations I can't duplicate.  I have accounts that can't use sudo or gksudo and my guest-sessions won't allow the use of any password.  My guest-sessions user can only be created inside my login.

---

### Post by FuturePilot on 2011-07-01
> **ahears said:**
> I think you are right about the root password, however how do I remove it and only allow one user to use it for upgrades and system changes? I have already exhausted my expertise in this area. Oh, and I am using gksudo and sudo to gain superuser priveliges and there is no root account. It's only me and the guest, but the guest with no priveliges can gain priveliges by using my password from my account as I am the admin. Hang on I gotta read_ my own links_ MORE but I have done everything, I must be missing something...


Running synaptic as guest will fail even if I get the password correct but I am still able to get in the user and groups menu and grant myself admin priveliges (by entering the password for my account) from the menu and then get into the disk janitor, network tools, disk utility, mount and unmount and even delete partitions and rename drives!!! It is still a huge security problem. Maybe I'm looking at this all wrong, but shouldn't the privileges be limited to a designated account, and not available system wide?

These are all Policy Kit rules. Policy Kit is supposed to act this way. You would have to fool around with the Policy Kit rules to change the way this works.

---

### Post by ahears on 2011-07-01
> **redmk2 said:**
> The "Guest" user you created is the same as any other user.  In this case it is just a name, no different than bill, bob, father, son, sister of wife.  In fact, to the system they are just characters in a string.

A normal user account is very different from a *guest-session* user.

I'll bet if you made the password operational that the problems would go away.  The system is misconfigured in my opinion.

 *How is it misconfigured?* I know there is something  wrong with the system. This is not a situation that is easy for me to  simply reinstall, especially if there is no guarantee that it will be  corrected by doing so.
 
> **bab1 said:**
> +1 I think you have misconfigured the account is some way too.

You describe situations I can't duplicate.  I have accounts that can't  use sudo or gksudo and my guest-sessions won't allow the use of any  password.  My guest-sessions user can only be created inside my  login.

No offense, but I  am now on Page 2 of this thread and I am getting nowhere. My '/etc/sudoers' file is listed on page one. The restrictions in that file do not stop any user from using the password in the GUI to gain Administrator account status. Now, on the other hand, when running synaptic from any other account than ones listed in the Admin group. Synaptic will not run and the process is cancelled. Using the 'Users and Groups' Should not run as well, but in my case this is not true. Hold on. 

Ok, I have accidentally started the XServer as root and lost control of my .ICEAuthority file and had to change permissions, although I did not fix permission throughout the entire '/home/myaccount' directory because I wasn't sure what to change.. I only made enough changes to get me back into the XServer as the user. I think I'll start a new thread as this may be outside the purview of this thread.

---

### Post by ahears on 2011-07-01
> **FuturePilot said:**
> These are all Policy Kit rules. Policy Kit is supposed to act this way. You would have to fool around with the Policy Kit rules to change the way this works.


Do tell...  How do I do that?

---

### Post by ahears on 2011-07-01
> **redmk2 said:**
> The "Guest" user you created is the same as any  other user.  In this case it is just a name, no different than bill,  bob, father, son, sister of wife.  In fact, to the system they are just  characters in a string.

A normal user account is very different from a *guest-session* user.

I'll bet if you made the password operational that the problems would go  away.  The system is misconfigured in my opinion.

 *How is it misconfigured?* I know there is something  wrong with  the system. This is not a situation that is easy for me to  simply  reinstall, especially if there is no guarantee that it will be   corrected by doing so.
 
> **bab1 said:**
> +1 I think you have misconfigured the account is some way too.

You describe situations I can't duplicate.  I have accounts that can't   use sudo or gksudo and my guest-sessions won't allow the use of any   password.  My guest-sessions user can only be created inside my   login.

No offense, but I  am now on Page 2 of this thread and I am getting  nowhere. My '/etc/sudoers' file is listed on page one. The restrictions  in that file do not stop any user from using the password in the GUI to  gain Administrator account status. Now, on the other hand, when running  synaptic from any other account than ones listed in the Admin group.  Synaptic will not run (even when I enter the Admin password) and the process is cancelled. Using the 'Users and  Groups' Should not run as well, but in my case this is not true.[COLOR=Lime][/COLOR] It's in the GUI that another user can use ***my*** password when prompted by the system, and gain access because [COLOR=Lime][COLOR=SeaGreen]everything on the command line is ok[/COLOR][/COLOR]. Maybe, my account which is set as Administrator is the same as having the 'root' account activated, but root has no password and does not exist as an account. I have created the 'Guest' account several times from scratch and still have the same problem. *_My password should not be able to be used system wide!_*

> **FuturePilot said:**
> These are all Policy Kit rules. Policy Kit is supposed to act this way. You would have to fool around with the Policy Kit rules to change the way this works.

How do I access the policy kit?

---

### Post by ahears on 2011-07-01
Ok, so here is the difference between the two programs I mentioned earlier:


> 

synaptic uses sudo (more precisely gksu which is a GUI frontend for sudo).

users-admin (aka **System >> Administration >> Users and Groups**), like most modern GUI applications, uses polkit (PolicyKit).

I am marking this thread as solved because this is caused by polkit (PolicyKit) and should be more clearly addressed in the Security Forum. See Thread: 'http://ubuntuforums.org/showthread.php?p=11003553#post11003553'

Thank you everyone.

---

### Post by Extrm3 on 2011-07-02
I think what ahears is trying to do is to remove the right for the guest user to use the su command.

Now, I don't know how to do this, but maybe some ubuntu guru might come along and help with that.

Note: Even though the guest user can use your **other **accounts (the admin account) password the guest user would still have to know that password, and since the whole point of having this guest account is to not give him your password I can't see the problem with this authorization since he shouldn't know the password.

---

### Post by ahears on 2011-07-02
> **Extrm3 said:**
> I think what ahears is trying to do is to remove the right for the guest user to use the su command.

Now, I don't know how to do this, but maybe some ubuntu guru might come along and help with that.

Note: Even though the guest user can use your **other **accounts (the admin account) password the guest user would still have to know that password, and since the whole point of having this guest account is to not give him your password I can't see the problem with this authorization since he shouldn't know the password.


Again what this comes down to is the Policy kit. I don't want users to be able to execute anything they shouldn't even if they somehow guessed the password for the system. As you will notice how Synaptic will fail even when the password is correct, however the **Users and Groups** will run when a password is entered correctly. The reason for this is mentioned above. It comes down to application, I can have a 20 character password and protect the system from anyone making attempts at hacking it, (and sacrifice the realistic possibility of using my account due to massive password length) or I can find a way to deny users from these programs even if they get the password correct. I either need to learn how to make a policy that can control program use, or use a huge password that cripples my account use. Ie. Windows Policy will can halt a user from performing certain actions, and the user will never be prompted for a password that would allow them to elevate when a System Policy prevents it. If I wanted all administrative tasks to be performed locally, I would be hard pressed to control that if I had any other user on the system except me. _My entire system security would hinge on that *ONE* password, which is not secure if you ask me._

---

### Post by cariboo on 2011-07-02
The reason most password are guessed, is because most people use a word that means something to them. Users & Groups can generate passwords for you that will be almost impossible to guess. It may take a few days for your fingers to memorize the new password, but in a short amount of time you will be using it just like your old password.

---

