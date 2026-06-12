---
title: "passwd command broken"
date: 2009-07-13
forum: Security
---

### Post by Antonio Tavares on 2009-07-13
Hi!
Normally when I type passwd on any of the Ubuntu machines I'm using there is something like this happening:
```
#passwd
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
```

Now on an Intrepid server I've installed a few months ago, there is only the last part:
```
# passwd tota
passwd: password updated successfully
```

The computer doesn't ask me for a password!!!

If I try with a non-existent user the response is correct.
```
# passwd xpto
passwd: unknown user xpto
```

This happened (probably) after removing nxserver (comercial) and installing freenx. I tryed to unlock the special user "nx" with no success. 
Is this a bug on passwd program or on my brain? :p
Another hypotheses is the computer was compromised, but the only open port is ssh (22). The rest is firewalled.
And I recall this happening before, but I don't know how to solve it.
Can any kind soul help?

---

### Post by cariboo on 2009-07-14
You need to use sudo eg:

```
sudo passwd <user>
```

edit: Whoops didn't notice you were running as root

---

### Post by Antonio Tavares on 2009-07-14
> **cariboo907 said:**
> You need to use sudo eg:

```
sudo passwd <user>
```

edit: Whoops didn't notice you were running as root

Don't tell anyone please :p I know that the forum police may find me, but it's my computer, and my choice! There is absolutely nothing useful I could do on the command line except as root, so the first command I do every time I open a shell is "sudo su". For me, normal working user is for the graphic interface, and root is for the command line. I can think of nothing useful to do on a command line without root access. On the other hand, it's very rare the occasion I run a graphic application as root (except for "sudo nautilus" or "sudo gedit" but I have cp/mv/nano...).  I don't understand Ubuntu policy about this, but it seems to be different, and it implies typing sudo before every command. 

But I'm not fighting that policy, and I respect Ubuntu organization opinion, and just for being a good boy I've entered as a normal user and tried to change password, like this:
```
tota@theedge-gateway:~$ sudo passwd nx
passwd: a palavra-passe foi actualizada com sucesso

```  
The response is still the same: "password changed successfully"

So, the problem is still the same. I was wondering... Can I solve this by doing a distribution upgrade from Intrepid to Jaunty? I suspect it may continue, but...

---

### Post by bodhi.zazen on 2009-07-14
There is nothing wrong with running as root, one has to have root access to do many things such as update the system, etc, etc.

What we object to is when new users run as root rather then understanding the system.

Why learn linux permissions ? Just run nautilus as root. 
It is my computer , so sudo chmod -R 777 /
etc, etc.

We object to is :

1. running X (gnome / KDE) as root, which is almost never necessary.
2. Disabling security (sudo with no password) merely for convenience, without explaining and understanding the risks.
3. Running as root, merely for convenience, without explaining and understanding the risks.

If you wish to do those things, that is your choice and we respect that. If you start telling new users to do the same, without teaching them proper security / system administration we object.

See the difference ?

At any rate, I would file a bug report.

There is a thread where the problem was "likewise"

[http://ubuntuforums.org/showthread.php?t=1072851](http://ubuntuforums.org/showthread.php?t=1072851)

HTH.

Is the user "nx" an actual user who logs in, or a system user as in Freenx ?

---

### Post by scorp123 on 2009-07-14
> **Antonio Tavares said:**
>  Now on an Intrepid server I've installed a few months ago, there is only the last part:
```
# passwd tota
passwd: password updated successfully
```

The computer doesn't ask me for a password!!!
 My guess is that the account in question has some strange setting in **/etc/passwd** or **/etc/shadow** .... Would it be possible for you to post those files (e.g. remove the password hashes of "root" and other users)?

---

### Post by Antonio Tavares on 2009-07-14
Thank you for your help bodhi.zazen.

1. Concerning the discussion about sudo, your position seems more liberal than the official one in [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) that I don't agree with. I agree with you. As a matter of fact, on my everyday machine I'm running as a normal user, and I never use root or need it for more than installing software (and for that, synaptics asks me for the password). But there are some shortcomings that can be difficult to solve, and in irritation some people just throw away chmod 777 everywhere and the like. I'm not suggesting that is good. It just happens (not with me anymore!). What I don't agree with is putting sudo before all the commands I type. That's silly, because the only ONE reason to go to the command line is for administration purposes. Do you really do any kind of normal use of a computer on the command line? And even if you in particular do (maybe programming), remember that most people spend all their working days using Open Office, mail and Firefox. Command line is for administration ONLY. So I tend to look at the command line as a warning in itself. I don't just type anything without propper care. I start a terminal as root, do what admin work I need and then I close it. 

2. LIKEWISE:
I've checked [http://ubuntuforums.org/showthread.php?t=1072851](http://ubuntuforums.org/showthread.php?t=1072851) and it suggests that you can solve the passwd problem removing the package likewise ([http://en.wikipedia.org/wiki/Likewise_Open):](http://en.wikipedia.org/wiki/Likewise_Open):)
```
apt-get remove likewise
```
But I don't have likewise installed.

3. USER nx:
The user "nx" is a system user for freenx server ([http://en.wikipedia.org/wiki/Freenx](http://en.wikipedia.org/wiki/Freenx)). I'm following the install instructions on [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX), that worked perfectly on a newly installed jaunty server but fail on this intrepid one, as you can see:

```
sudo /usr/lib/nx/nxsetup --install --setup-nomachine-key --clean --purge
Removing special user "nx" ...done
Removing session database ...done
Removing logfile ...done
Removing home directory of special user "nx" ...done
Removing configuration files ...done
Setting up /etc/nxserver ...done
Generating public/private dsa key pair.
Your identification has been saved in /etc/nxserver/users.id_dsa.
Your public key has been saved in /etc/nxserver/users.id_dsa.pub.
The key fingerprint is:
(...)
Setting up /var/lib/nxserver/db ...done
Setting up /var/log/nxserver.log ...done
Setting up special user "nx" ...Adicionando o utilizador `nx' ao sistema (UID 113) ...
Adicionando um novo utilizador `nx' (UID 113) com o grupo `nx' ...
A criar a pasta pessoal `/var/lib/nxserver/home' ...
Palavra-passe alterada.
done
Adding user "nx" to group "utmp" ...done
Setting up known_hosts and authorized_keys2 ...done
Setting up permissions ...done
Setting up cups nxipp backend ...done

----> Testing your nxserver configuration ...
(...)

----> Testing your nxserver connection ...
Permission denied (publickey,password).
Fatal error: Could not connect to NX Server.

Please check your ssh setup:

The following are _examples_ of what you might need to check.

	- Make sure "nx" is one of the AllowUsers in sshd_config.
    (or that the line is outcommented/not there)
	- Make sure "nx" is one of the AllowGroups in sshd_config.
    (or that the line is outcommented/not there)
	- Make sure your sshd allows public key authentication.
	- Make sure your sshd is really running on port 22.
	- Make sure your sshd_config AuthorizedKeysFile in sshd_config is set to authorized_keys2.
    (this should be a filename not a pathname+filename)
  - Make sure you allow ssh on localhost, this could come from some
    restriction of:
      -the tcp wrapper. Then add in /etc/hosts.allow: ALL:localhost
      -the iptables. add to it:
         $ iptables -A INPUT  -i lo -j ACCEPT
         $ iptables -A OUTPUT -o lo -j ACCEPT

``` 

4. Bug Report
I think I'll file the bug report, but to be useful I would like to collect some more information.

5. Content of user security files
Thank you scorp123. I doubt that the problem is here, as I can't change the password of any of the users. Anyway, for the sake of ruling out every possibility, I'm puting here the contents of /etc/passwd and /etc/shadow. I've put (blablabla) instead of the password hashes:
```

cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
tota:x:1000:1000:Antonio Tavares,,,:/home/tota:/bin/bash
sshd:x:112:65534::/var/run/sshd:/usr/sbin/nologin
nx:x:113:131::/var/lib/nxserver/home:/usr/lib/nx/nxserver
(...)
cat /etc/shadow
root:(blablabla):14169:0:99999:7:::
tota:(blablabla):14160:0:99999:7:::
sshd:*:14160:0:99999:7:::
nx:*:14439:0:99999:7:::

```

---

### Post by bodhi.zazen on 2009-07-14
> **Antonio Tavares said:**
> Thank you for your help bodhi.zazen.

1. Concerning the discussion about sudo, your position seems more liberal than the official one in [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) that I don't agree with. 

That is why I posted, the thread you are referencing refers to logging in to X as root and in order to do so (via GDM) one needs to make all manor of changes to a number of system files. If you take a closer look I bet you probably do agree (just a guess) as there really is no reason to run gnome / KDE -> open office, firefox, etc, etc as root.

At any rate that is why I posted, for clarification of the policy.

I do not see any obvious problem with your passwd command or in the information you posted. Was it working before you installed FreeNX ? If so, perhaps that is where the problem originated.

I am not overly familiar with FreeNX, but nx appears to be a system user and I do not think you need to or should you set a password for "nx".

---

### Post by Antonio Tavares on 2009-07-14
> **bodhi.zazen said:**
> If you take a closer look I bet you probably do agree (just a guess) as there really is no reason to run gnome / KDE -> open office, firefox, etc, etc as root.

At any rate that is why I posted, for clarification of the policy

And it was really clarifying, because I know now that the forum is not so extreme after all. As I said, I know that I could run everything as root, but for anyone reading this thread, let it be clear that running your normal day to day life office applications, Internet, games or whatever as root is plainly useless and dumb and this is no security paranoia at all. One of the reasons Windows XP is such a security no-no is precisely of that wrong policy. As almost no one likes to change to Administrator every time a system change like updating a program is needed, they normally run all day long as root (administrator) and the malware enters easily. But Ubuntu (and Windows 7) have a different approach. You can run as a normal user and ascend on the same session to get some administration tasks done.

> **bodhi.zazen said:**
> 
I do not see any obvious problem with your passwd command or in the information you posted. Was it working before you installed FreeNX ? If so, perhaps that is where the problem originated.

I am not absolutly shore. Last time I changed a password was a month ago. But it seems it started after FreeNX install, so it could be that
> **bodhi.zazen said:**
> 
I am not overly familiar with FreeNX, but nx appears to be a system user and I do not think you need to or should you set a password for "nx".
No password needed. But from the error message on the install, it seems like the account is not working, on this part:
```
----> Testing your nxserver connection ...
Permission denied (publickey,password).
Fatal error: Could not connect to NX Server.

```

Note: For the ones that don't know, FreeNX allows graphical ssh login for 1 or several users to a Linux machine. A lot of users can share the same machine, and it is so quick that you can have remote access via Internet and feel no slowness at all. It's quicker than VNC and even better that Windows Terminal Server. As you know if you tried, normal Linux remote desktop (RDP) is too slow and unsafe to be of any use.
A detailed explanation is in [http://fedoranews.org/contributors/rick_stout/freenx/freenx.txt](http://fedoranews.org/contributors/rick_stout/freenx/freenx.txt)

I'm upgrading the server to jaunty. It's a production server so I have to be cautios, and as usual I'm having problems (normally every Ubuntu release there's at least an X server problem after first start). Tomorrow I'll tell how thing evolved.
Cheers!

---

### Post by bodhi.zazen on 2009-07-14
Yes, well Freenx connects with a key, so that error message is not as helpful as most.

I am not sure setting a nx password would help.

---

### Post by Antonio Tavares on 2009-07-14
Yes, I'm also in doubt. It could be other things. But I've read somewhere that this error can be due to a locked nx user, so I tryed, but I cannot unlock it also.
After another suggestion (don't recall where now), I've tryed to change nx password  and that was when I've discovered that passwd program was not working anymore.

---

### Post by cariboo on 2009-07-14
Just for clarification, I didn't answer your question, not because you were running as root, but because I don't know anything about freenx either. I feel the same way as bodni, what you do with your computer is your business, and if someone wants to run as root all the time, that's their problem.

I ran as root all the time myself back in the days when there weren't resources like the Ubuntu forums to explain why it wasn't a good idea. I learned the hard way why Redhat 5.2 asked you set up an unprivileged user as well as a root user, and was overjoyed when I first installed Ubuntu and needed to use sudo for administrative tasks.

---

### Post by scorp123 on 2009-07-15
> **Antonio Tavares said:**
>  ```

cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
tota:x:1000:1000:Antonio Tavares,,,:/home/tota:/bin/bash
sshd:x:112:65534::/var/run/sshd:/usr/sbin/nologin
nx:x:113:131::/var/lib/nxserver/home:/usr/lib/nx/nxserver
(...)
cat /etc/shadow
root:(blablabla):14169:0:99999:7:::
tota:(blablabla):14160:0:99999:7:::
sshd:*:14160:0:99999:7:::
nx:*:14439:0:99999:7:::

```

Hmmm ... OK. How about PAM? Can you please post the contents of these files:
[LIST]
[*]/etc/pam.conf
[*]/etc/pam.d/common-auth
[*]/etc/pam.d/common-password
[*]/etc/pam.d/common-account
[*]/etc/pam.d/passwd
[/LIST]

---

### Post by Antonio Tavares on 2009-07-15
> **cariboo907 said:**
> 
I ran as root all the time myself back in the days when there weren't resources like the Ubuntu forums to explain why it wasn't a good idea. I learned the hard way why Redhat 5.2 asked you set up an unprivileged user as well as a root user, and was overjoyed when I first installed Ubuntu and needed to use sudo for administrative tasks.
To be clear, **I run as root all the time on console only**. The graphical system is always logged as a normal user. The only reason to go to the console is for administration tasks. So the first command I type is "sudo su" (or ssh root@someserver). Otherwise I would loose time checking if that command or the other had failed me because of lack of rights. As you know, even simple commands like "top" don't give a reliable result on a normal user because some processes can be hidden.
I don't go browsing on "links" or happily type text on editors that I detest, like VI or whatever. Maybe if I was a programmer I would need the console in restricted user, but for office tasks, a graphical system is superior and more productive for everyday use. Even for moving files around is safer to use 2 nautilus windows, to see clearly what I am doing, not the text console. If I don't have access to those files, I just go the root text console and type "nautilus"

---

### Post by bodhi.zazen on 2009-07-15
> **Antonio Tavares said:**
> To be clear, **I run as root all the time on console only**. The graphical system is always logged as a normal user. The only reason to go to the console is for administration tasks. So the first command I type is "sudo su" (or ssh root@someserver). Otherwise I would loose time checking if that command or the other had failed me because of lack of rights. As you know, even simple commands like "top" don't give a reliable result on a normal user because some processes can be hidden.
I don't go browsing on "links" or happily type text on editors that I detest, like VI or whatever. Maybe if I was a programmer I would need the console in restricted user, but for office tasks, a graphical system is superior and more productive for everyday use. Even for moving files around is safer to use 2 nautilus windows, to see clearly what I am doing, not the text console. If I don't have access to those files, I just go the root text console and type "nautilus"

There is nothing wrong with what your are doing.

---

### Post by Antonio Tavares on 2009-07-17
I've been absent of this thread for a while, because I had a lot work recovering that server, and I had other work afterwards.

Concerning the upgrade, I will just say that in spite of Ubuntu being my favourite OS, there is a lot to be done in the upgrades! Every time I do a distro upgrade I end up without graphic interface, or worse. This time after offering me to compare the proposed alterations to a configuration file, I typed CTRL-Z to get out of the editor, and instead, it broke in the middle of the upgrade script going to the command line. I was left with a system that was neither 8.10 or 9.04!

I've formatted root as ext4 and reinstalled it from scratch using the instructions I left for myself: Apache, DNS, Proxy Squid, DHCP, Samba, SSH, freeNX and firewall. I lost some time finding that for some obscure reason eth0 was now being identified as eth1 and viceversa (that bug/feature is already reported by others). I've tried to apply same fwbuilder rules (swapping eth0 and eth1) but it seems there is a difference between 8.10 and 9.04, so I can't get to it by SSH. The firewall is not letting me in for some reason.

As expected on a new install, **the passwd problem didn't appear again**! Installing freeNX took about 2 minutes, but the all process of installation and configuration took 9 hours.

I Will probably go back to the server Monday, and if you (scorp123 and others) feel it's important to correct bugs for other people, I can post the PAM configuration (I have a backup of /etc there)

---

### Post by bodhi.zazen on 2009-07-17
Upgrades on any OS can be problematic. I have personally upgraded 8.04 -> 8.10 -> 9.04 with no difficulty (desktop) and others upgrade with problems.

On a production server I would go with LTS and upgrade with great caution (back up first).

Interrupting an upgrade, on any OS, is quite problematic and although it was accidental on your part could well have caused most of your problems, hard to say.

I would have restored from back up, faster then fixing a broken system.

When asked to review those kind of changes, if I manually edited the config file, I keep my changes. Otherwise accept the upgrade / changes.

Not sure if a bug report from the old system is going to be of any use as the root of the problem is an interrupted upgrade and that can leave the system in a variable and unstable condition, again on any OS.

Although upgrades often go smoothly, they are not guaranteed on any OS. Some OS (Fedora) it goes smooth, but it is still advised you do a fresh install (very conservative in the recommendations). I have upgraded Fedora 10 -> 11 with minor problema unrelated to Fedora (nvidia drivers).

---

### Post by Antonio Tavares on 2009-07-20
> **bodhi.zazen said:**
> Interrupting an upgrade, on any OS, is quite problematic and although it was accidental on your part could well have caused most of your problems
oh bodhi.zazen, you've understood the other way around. The timing of the events was:
1- On 8.10: Tryed to install freeNX.
2- Noticed the passwd problem.
3- Try solving, then googling with no result;
4- Asked ubuntuforums what to do
5- Couldn't solve even with your generous help;
6- Backup of /etc;
7- Tryed upgrade to 9.04 (in the hope that passwd would work again)
8- Problem happened, so the system was neither 8.10, neither 9.04
9- Formated root and reinstalled 9.04 from scratch (using my notes)
10- It is working very well, except the firewall (for now). 

> **bodhi.zazen said:**
>  I have upgraded Fedora 10 -> 11 with minor problema unrelated to Fedora (nvidia drivers).

I also had a problem in Ubuntu 9.04 on my ACER Aspire 1690, because ATI calls a RADEON X700 with 3 or 4 years "legacy" as if it were an old CGA card! As they don't put the source code to the public and don't give a damn to old cards, there are no drivers for the Xorg version that comes with Ubuntu 9.04. What Ubuntu could do, would be to check the sanity of the conversion. No drivers? No update of Xorg! (or use generic drivers). Most of all, no crashed screen! There's nothing more detracting for new users as a crashed X system. And even long time users like me don't want having to correct the X config all the time, or passing hours trying awful drivers that Nvidia and ATI put on their site...

Ubuntu (and Debian) already have the best installation system from all the OS I know. Installations are very simple and safe but the occasional crash is still happening. But the recognition and correct handling of the hardware is the most important thing an OS must do. We can not forget that it is the very reason for an OS to exist: Create an interface between user/application software and hardware.
So Ubuntu should focus on better installation routines and better handling of hardware. The other nice things can only be dealt after that most important part is taken care of.

---

### Post by movieman on 2009-07-20
> **Antonio Tavares said:**
> 
The computer doesn't ask me for a password!!!


Uh, you don't need to enter a password to change a password when you're running as root. There's no point, because if you're root you can just edit /etc/passwd and /etc/shadow anyway.

---

### Post by Antonio Tavares on 2009-07-20
> **movieman said:**
> Uh, you don't need to enter a password to change a password when you're running as root. There's no point, because if you're root you can just edit /etc/passwd and /etc/shadow anyway.

Thank you for your help, movieman but there are problems with your method:
1. The passwords must first be ciphered and only then copied by hand to the proper line on /etc/shadow with possible editing error;
2. I would have one server in which the standard method don't work;
3. The installer of NXfree would not work, maybe other installers would also not work;
4. Just to prove my point :), please tell me the password of this user:
movieman:$1$m0Iak$/Q3EX2Xy82z3NGq6RE3Zw0:14264:0:99999:7:::

---

### Post by movieman on 2009-07-20
I realise that English isn't your first language, but which part of 'you don't need to enter a password to change a password when you're running as root' is proving difficult to understand?

It's possible that some PAM configurations would require you to enter one if the password database is not normally accessible to root: but if you're using /etc/passwd and /etc/shadow, you do not need to enter a password in order to change a password if you're root.

---

### Post by Antonio Tavares on 2009-07-20
Oh my God. Either my English or my explanations seem to need improvement...
When I'm root, I do NOT need a password to use the password program "passwd", BUT, I need to type the NEW password of the user I'm editing. Problem WAS that I could NOT, because passwd did NOT ask, as it normally does 2 times, before going back to prompt. It just prompted "Password changed successfuly" (as if it was successful!)
I hope it was clear now. It seems to be a bug.

---

### Post by movieman on 2009-07-20
OK, I guess my english is the problem :). I agree, that certainly looks like a bug, I'm guessing it is some weird PAM configuration issue.

---

### Post by bodhi.zazen on 2009-07-20
> **Antonio Tavares said:**
> 4. Just to prove my point :), please tell me the password of this user:
movieman:$1$m0Iak$/Q3EX2Xy82z3NGq6RE3Zw0:14264:0:99999:7:::

The password is "Hi mom"

---

### Post by Antonio Tavares on 2009-07-22
> **scorp123 said:**
> Hmmm ... OK. How about PAM? Can you please post the contents of these files:
[LIST]
[*]/etc/pam.conf
[*]/etc/pam.d/common-auth
[*]/etc/pam.d/common-password
[*]/etc/pam.d/common-account
[*]/etc/pam.d/passwd
[/LIST]

Sorry for the long delay (and for destroying the server that had this error!) but for forensic studies that anyone interested can do, here it is the contents of the pam config:
```
____________________________
Contents of /etc/pam.conf:
# ---------------------------------------------------------------------------#
# /etc/pam.conf								     #
# ---------------------------------------------------------------------------#
#
# NOTE
# ----
#
# NOTE: Most program use a file under the /etc/pam.d/ directory to setup their
# PAM service modules. This file is used only if that directory does not exist.
# ---------------------------------------------------------------------------#

# Format:
# serv.	module	   ctrl	      module [path]	...[args..]		     #
# name	type	   flag							     #

____________________________
Contents of /etc/pam.d/common-auth:
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth	requisite	pam_unix.so nullok_secure
auth	optional	pam_smbpass.so migrate missingok
____________________________
Contents of /etc/pam.d/common-password
#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# The "md5" option enables MD5 passwords.  Without this option, the
# default is Unix crypt.
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# You can also use the "min" option to enforce the length of the new
# password.
#
# See the pam_unix manpage for other options.

password   requisite   pam_unix.so nullok obscure md5

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
# password required	  pam_cracklib.so retry=3 minlen=6 difok=3
# password required	  pam_unix.so use_authtok nullok md5

# minimally-intrusive inclusion of smbpass in the stack for
# synchronization.  If the module is absent or the passwords don't
# match, this module will be ignored without prompting; and if the 
# passwords do match, the NTLM hash for the user will be updated
# automatically.
password   optional   pam_smbpass.so nullok use_authtok use_first_pass missingok
____________________________
Contents of /etc/pam.d/common-account
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account	required	pam_unix.so
____________________________
Contents of /etc/pam.d/passwd
#
# The PAM configuration file for the Shadow `passwd' service
#

@include common-password
____________________________

```

---

### Post by Synchro on 2009-09-08
You might be running into an old PAM bug inherited from Debian: [http://www.debian.org/security/pam-auth](http://www.debian.org/security/pam-auth)

This bug produces exactly the symptoms you're seeing, and has an additional nasty feature you may not have noticed: it allows login as any user with a password without having to give the password...

---

### Post by ktritty on 2009-09-08
> **bodhi.zazen said:**
> The password is "Hi mom"
Sorry to break in, but I think bodhi can probably help me, if he can crack that.



I have a problem now when I login to one of my server builds.  At the prompt, which usually says "user@host:pwd$", it now says "I have no name!@host:pwd$"

I think this may be a result of a late night moment of clumsiness, during which the file /etc/passwd got chmodded 700

Can you tell me what the proper file mode should be for /etc/passwd?

Also, how can I in general view the current file mode of a file without making any changes?

Thanks

---

### Post by wirelessmonkey on 2009-09-08
ktritty;

ls -la will show file mode/permissions.

/etc/passwd should be
```

-rw-r--r-- 1 root root 

```

---

### Post by ktritty on 2009-09-09
> **wirelessmonkey said:**
> ktritty;

ls -la will show file mode/permissions.



Thank you!  Now my computer known my name again.

I find it odd though that the mode is 644 (isn't that world readable?) particularly if true guru's can convert this into "Hi mom"....

---

### Post by cariboo on 2009-09-09
No 777 is world readable, 644 is read by owner, write by owner, read by group and read by others

---

