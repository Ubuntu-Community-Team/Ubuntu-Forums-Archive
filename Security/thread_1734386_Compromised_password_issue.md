---
title: "Compromised password issue"
date: 2011-04-20
forum: Security
---

### Post by teaker1s on 2011-04-20
Hi the problem occurs that the main user installed and the root password are the same by default on system.

To avoid malicious activity default user and root passwords changed-which then allowed root graphical login.

Help ubuntu creates a security hole:-

```
sudo passwd -dl root
``` to disable graphical login but has effect of removing recovery password

unfortunately recovery kernel with networking no longer asks root password or offers ctrl-d as option.

disabling root login in gnome login instead as we wish to put it back to default non graphical login for root only
Ubuntu geek suggests ```
sudo passwd -l root
``` but this will disable recovery root login as well


Thanks

---

### Post by mynameisnotbob on 2011-04-20
try usermod instead. That's how I re-lock it after I'm done and it doesn't disable Recovery Mode. use this code:
```
usermod -L root
```

---

### Post by mynameisnotbob on 2011-04-20
Recovery mode never asks for a password by default. Did you some how change that?

---

### Post by dfreer on 2011-04-20
Not really sure what your question is. By default root password and user password are **not** the same, the root account has no password at all, it's simply locked with the passwd -l command. 

Recovery mode is supposed to work without requiring a password for root at all, regardless of whether it is set, not set, locked, etc. At least my understanding it is, maybe that's changed (haven't used ubuntu in awhile).

Disabling root from logging in graphically is usually handled by the log in manager itself, at least on Debian. When you are sitting at the login screen, there is an option to configure the login manager generally (if not, you can access it from your System or Administration menu once you login). From that login manager menu, under the security tab I think, there should be an option to allow/disallow root login.

passwd -l root disables all root logins, except it shouldn't disable recovery mode.

---

### Post by mynameisnotbob on 2011-04-20
> **dfreer said:**
> Not really sure what your question is. By default root password and user password are **not** the same, the root account has no password at all, it's simply locked with the passwd -l command. 

Recovery mode is supposed to work without requiring a password for root at all, regardless of whether it is set, not set, locked, etc. At least my understanding it is, maybe that's changed (haven't used ubuntu in awhile).

Disabling root from logging in graphically is usually handled by the log in manager itself, at least on Debian. When you are sitting at the login screen, there is an option to configure the login manager generally (if not, you can access it from your System or Administration menu once you login). From that login manager menu, under the security tab I think, there should be an option to allow/disallow root login.

passwd -l root disables all root logins, except it shouldn't disable recovery mode.
no, you are correct.
except that there's no gui method to allow graphic root login.
in Ubuntu, I think it's X that makes graphic logins for root impossible
like trying to 'startx' in recovery mode

---

### Post by teaker1s on 2011-04-20
Okay against another system your-correct that the recovery kernel doesn't not ask for root password.

From what I can tell the root passwd has been enabled as the system asks for root password at recovery kernel or ctrl-D

usermod -L has the effect of:-

Control-D doesn't drops back to graphical options.

So as it stands to have root login password at recovery to stop it being altered without password =root passwd is enabled.

to stop playing via gui root login 
```
sudo gedit /etc/pam.d/gdm
```
add
```
 auth required pam_succeed_if.so user != root quiet
```

which has had the effect of authentication failure for root gui login but password still asked at recovery kernel.
sudo passwd -l root

If we disable root account can we force an admin login on recovery kernel easily and the sudo to gain root?-instead of completely unprotected access?

```
sudo passwd -l root
``` seems to restore default behaviour.

Or is grub the only easy way, though not secure.

---

### Post by mynameisnotbob on 2011-04-20
On 10.10 recovery terminal, sudo doesn't work, at least on my box. The only way to do administrative things is through the 'drop to root' option. I didn't even know there was a way to passwd-protect recovery console. Besides, that is, the BIOS System password. I know you could disable it, but passwd-protect?

---

### Post by teaker1s on 2011-04-20
> **mynameisnotbob said:**
> On 10.10 recovery terminal, sudo doesn't work, at least on my box. The only way to do administrative things is through the 'drop to root' option. I didn't even know there was a way to passwd-protect recovery console. Besides, that is, the BIOS System password. I know you could disable it, but passwd-protect?

From memory thinking about it recovery kernel works in single user mode.

Enabling root password then recovery kernel becomes password protected,but then means a root account could be remotely compromised.
(the reason ubuntu locks root account at a guess)

thinking about it you have a choice of stopping direct root logon and forcing logon and  sudo -as ubuntu does as standard.

Disable root password by locking and then physical access gives unprotected single user recovery kernel.

Grub boot loader password which isn't particularly robust

bios password and security screws.


:popcorn:

---

### Post by mynameisnotbob on 2011-04-20
Well, are you more threatened by hackers or break-ins/people in your own company?

---

### Post by bodhi.zazen on 2011-04-20
> **dfreer said:**
> passwd -l root disables all root logins, except it shouldn't disable recovery mode.

Not exactly, that disables password authentication.

root can still log in with a ssh key or kerberos.

---

### Post by bodhi.zazen on 2011-04-20
> **teaker1s said:**
> From memory thinking about it recovery kernel works in single user mode.

Enabling root password then recovery kernel becomes password protected,but then means a root account could be remotely compromised.
(the reason ubuntu locks root account at a guess)

thinking about it you have a choice of stopping direct root logon and forcing logon and  sudo -as ubuntu does as standard.

Disable root password by locking and then physical access gives unprotected single user recovery kernel.

Grub boot loader password which isn't particularly robust

bios password and security screws.


:popcorn:

Not really sure what you are wanting to accomplish.

First you need to limit physical access. If one has physical access they have root access, the only possible defense would be encryption, but there are some limits to encryption.

Second, if someone has access to an admin account (an admin account is an account with root access, either with su or sudo), then they have root access.

su is no more or less secure then sudo.

Probably the easiest solution for what you want, on Ubuntu, is to simply make a second account, without sudo access, for daily use.

---

### Post by teaker1s on 2011-04-20
> **bodhi.zazen said:**
> Not really sure what you are wanting to accomplish.

First you need to limit physical access. If one has physical access they have root access, the only possible defense would be encryption, but there are some limits to encryption.

Second, if someone has access to an admin account (an admin account is an account with root access, either with su or sudo), then they have root access.

su is no more or less secure then sudo.

Probably the easiest solution for what you want, on Ubuntu, is to simply make a second account, without sudo access, for daily use.

Person who is an issue has been physically removed from access. The two main concerns now are 

1) a little information is a dangerous thing and it appears more than one person has been involved in unauthorised access.
 It appears they gained access to privileges previously by rebooting to recovery console root in past-that's why root password was enabled previously
(poor security not of my doing, suggested better physical security)

2) From the opinions on here and the fact I have now disabled root login, provided physical access is restricted the recovery kernel is  safe from unauthorised root access.

Now digging through to find that various folders and directories have wrong permissions, looks like guy administering may have gone bad before leaving and at least one other person has screwed with it.

I stand by the ubuntu root locked account policy, it was more a case of what they had done to it-thanks for help and suggestions.

---

### Post by mynameisnotbob on 2011-04-20
Well, good luck to you in fixing it.

---

### Post by teaker1s on 2011-04-20
> **mynameisnotbob said:**
> Well, good luck to you in fixing it.

thanks it looks like a mass chmod 777 so hopefully chown to respective owners and some suitable chmod permissions should sort a lot of it.:popcorn:

Also have removed several from ftp group and changed passwords.

---

### Post by mynameisnotbob on 2011-04-20
wow...that is havoc.
least it wasnt chmod 000.

---

### Post by teaker1s on 2011-04-20
> **mynameisnotbob said:**
> wow...that is havoc.
least it wasnt chmod 000.

or chown'd to a no existent user yes it could be done. 

Use existing an system as template, think the plan was future ftp of directories

---

### Post by mynameisnotbob on 2011-04-20
out of interest, does that include the /etc and /usr directories on the server? 777ing those disables sudo. I would know:-({|=.

---

### Post by bodhi.zazen on 2011-04-20
> **teaker1s said:**
> thanks it looks like a mass chmod 777 

OUCH

It takes a bit of time to recover from that, and I have only seen one person do so successfully.

It may be easier to back up the data, reinstall, and restore data. You also would know there are no hidden threats that way.

I would watch the box for suspicious activity ;)

---

### Post by mynameisnotbob on 2011-04-20
Is it just one box, or a server?

---

### Post by SeijiSensei on 2011-04-20
One protection against people logging into the recovery console is to establish a BIOS password, if your system has that option.  The downside is that the system will go offline if someone reboots it without knowing the password.  However you may be willing to pay that price to protect the entire system against intruders.

---

### Post by teaker1s on 2011-04-21
> **mynameisnotbob said:**
> out of interest, does that include the /etc and /usr directories on the server? 777ing those disables sudo. I would know:-({|=.

Seems mainly limited to var which screamed about ownership when sudo used- now owned by root and permissions set for www folder.

Users home folders were set wide open as well

Looks like the plan was ftp access and either quietly downloading data or possibly website take down.


While I understand it is an issue as it stands, cloning system as backup or transferring to install seems an idea-just watching for suspicious activity.

---

### Post by mynameisnotbob on 2011-04-21
Lot&#347; of backdoors a good admin can put in...

---

### Post by teaker1s on 2011-04-21
Working along the lines that the alterations so far are basic, without out remote access it will be difficult to attack- I hear your concerns, bit response needs to be relative to threat.

So far the obvious points of attack are childish by comparison to what I had expected.

There appears to be no booby trapped stuff or crontab  stuff.

I'm of course grateful for any suggestions or help.

---

### Post by mynameisnotbob on 2011-04-21
I mean if you have any problems, I&#7743; sure that there is someone on the forums who can help you.

---

