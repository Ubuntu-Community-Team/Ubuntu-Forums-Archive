---
title: "Normal user can read e.g. /etc/group ?"
date: 2009-01-05
forum: Security
---

### Post by Devport on 2009-01-05
I switched from gentoo to ubuntu ( again ) and when I read some docs about sudo on ubuntu it came to my mind to just check if /etc/group is readable by normal users and it is. I am no security expert but I think system files shouldnt be readable by any user - especially something like /etc/group or /home. Its a good way to find out which users are there and trying to hack their accounts.

This leads me to the point that it seems to me that ubuntu / any linux distro needs an overhaul with regards to system file attribs ( especially /etc, /boot - even /lib and so on to prevent someone from finding out if there are libs / versions of libs which can be attacked ) so that they are more secure.

---

### Post by cdenley on 2009-01-05
Doesn't /etc/group and /etc/passwd have to be world readable in order for the user to determine it's own shell, home directory, and group memberships? Is there a unix-based OS which does not have these files world-readable by default? If an attacker gains shell access, I think you have bigger problems than the attacker being able to read /etc/group or /etc/passwd.

---

### Post by Devport on 2009-01-05
> **cdenley said:**
> Doesn't /etc/group and /etc/passwd have to be world readable in order for the user to determine it's own shell, home directory, and group memberships?
I am not sure about this one but if its the case this can be fixed - shells maybe are suid ( I am no security expert ). Home directory and group membership management are admin tasks anyway.

> **cdenley said:**
> Is there a unix-based OS which does not have these files world-readable by default?
Indeed thats very much the point - file attribs arent taken into account as of yet which is IMHO not correct - an unpriviliged user has nothing to see in system files. And it definatly reduces security.

> **cdenley said:**
> If an attacker gains shell access, I think you have bigger problems than the attacker being able to read /etc/group or /etc/passwd.
On multiuser systems everyone with an account has access which doesnt mean every one should be able to read any system  details. Besides that in e.g. a university people are often bored and wont bother to read any system file and maybe try to hack things.

Anyone with an unpriviliged user account can login ( no matter if its via a keyboard or ssh ) and simply find out who has admin rights to know which account(s) should be attacked. Especially if there are more than one admins the likeness of one of them having a weak password increases.

There are so many ways for someone with unpriviliged access to find out the security holes of a system only because of those file attribs :

- check which versions of libs / apps ( e.g. ssh ) with possible security risks are installed
- check which hosts / ips / users have ssh access
- check the firewall rules
- check which users are there

I - having been a system admin at university - dont want all users with an account to have access to so much system related information.

---

### Post by dperfors on 2009-01-05
System files are world readable so that the system can use it without having root permissions. This is normal for most of the file in /etc. Personally I don't care because as long as someone doesn't have access to the machine it is not a problem.
As long as it is not possible to read password information, everything should be fine :)

You are talking about universities, I think they don't want to store all users on the linux/unix machine itself, but they will use a server which stores that information (for example using LDAP)

---

### Post by cdenley on 2009-01-05
> **Devport said:**
> I am not sure about this one but if its the case this can be fixed - shells maybe are suid ( I am no security expert ). home directory management is an admin task anyway.

I'm not a security expert either, but wouldn't that cause their shell to run as root?

> **Devport said:**
> 
Indeed thats very much the point - file attribs arent taken into account as of yet which is IMHO not correct - an unpriviliged user has nothing to see in system files. And it definatly reduces security.

What do you mean system files? They obviously need read access to many things outside their home directory if they are going to be able to run anything like a text editor, window manager, or a web browser. These applications will also require the user to be able to read libraries.

Anything you can do to restrict local users would be a security benefit, but protecting yourself from local users is an uphill battle. I know firsthand a list of users can be useful to attackers. However, there is only so much you can do to restrict local users while still allowing them to perform ordinary tasks like web browsing.

---

### Post by scorp123 on 2009-01-06
> **Devport said:**
> shells maybe are suid  Eeeeeek!! [-X  Nope, they're not. "suid" programs run as "root" and that's really the last thing you want: a shell with the "suid" bit set !!! [-X 

> **Devport said:**
>  Home directory and group membership management are admin tasks anyway.  And so? You still need to see certain things or else already your login would fail. :D

> **Devport said:**
>  an unpriviliged user has nothing to see in system files. And it definatly reduces security.  2 x wrong. If you completely shut out an ordinary user from /etc they would not be able to login, e.g. have their password checked, have their user and group ID's assigned, and so on. Because those processes are running under the user's priviledges he absolutely must have read access to certain files. The really important files (e.g. **/etc/shadow** ) are still inaccessible. That's what matters. 

> **Devport said:**
>  Besides that in e.g. a university people are often bored and wont bother to read any system file and maybe try to hack things.  Same as in any corporate environment ;)

> **Devport said:**
>  Anyone with an unpriviliged user account can login ( no matter if its via a keyboard or ssh ) and simply find out who has admin rights to know which account(s) should be attacked. Especially if there are more than one admins the likeness of one of them having a weak password increases.  You could work with ACL's and further restrict access to certain things for certain users. I do that sometimes, especially with external guys and temporary folks whom I don't trust. 

> **Devport said:**
>  I - having been a system admin at university ...  Then you should know all of the above and not ask such strange things :D

---

### Post by pdtpatrick on 2009-01-06
well said .. good job :)

---

### Post by kevdog on 2009-01-07
You could just stick your users in a jail and then you wouldn't have to worry about it.

---

### Post by scorp123 on 2009-01-07
> **kevdog said:**
> You could just stick your users in a jail ... As a matter of fact, this is **exactly** what happens in certain companies if users snoop around too much ... :twisted:

:lolflag:

---

