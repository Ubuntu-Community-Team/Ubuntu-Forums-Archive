---
title: "sudo default config weak"
date: 2007-08-04
forum: Server Platforms
---

### Post by low_rent on 2007-08-04
hi all


on ubuntu when you do a sudo it ask the current user passwd ( not the root one )  your user needs to be the one at the installation by ubuntu ( you have some "admin" rights )
 
low_rent@unsafebox:~$ id 
uid=1000(low_rent) gid=1000(low_rent) groupes=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(low_rent)
low_rent@unsafebox:~$ sudo su root
Password:your_user_password ( not the root one...)
root@unsafebox:/home/low_rent# id
uid=0(root) gid=0(root) groupes=0(root)
root@unsafebox:/home/low_rent# 

if we open  /etc/sudoers we can see :

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL  --> 0.o

i understand that ubuntu is a user friendly distribution and make things easier for the local user . but, anyone can get root using the local user password .


so can we call this a default config weak leading to privilege escalation ?


regards laurent

---

### Post by apetresc on 2007-08-04
Isn't this intentional? I'm no security expert, but this is the same behaviour I've seen on every Linux box I've used (not just Ubuntu).

I thought the reasoning was that only the users who were "trusted" would even be in the admin group. Therefore it makes sense that they use their own password to use sudo -- the password is not meant to keep THEM out, but rather to prevent someone who gained user privileges from going to sudo. If the user themselves should not know the root password, they shouldn't be in the admin group to begin with. I don't see how this is a security concern...

**edit:** Err, "admin" group, not "wheel" group. Too much FreeBSD for me =x

---

### Post by aysiu on 2007-08-04
No, not anyone. Only users in *admin* group.

Create a new user who is **not** in the *admin* group and then try ```
sudo su root
```  It won't work.

---

### Post by low_rent on 2007-08-04
> No, not anyone. Only users in admin group.

well i know :)
so for you guys an admin should have the same privileges as root ?
i'm sorry , but i see a security issue here ...
at least if you wanna su root it should ask for the root passwd 0.o

---

### Post by apetresc on 2007-08-04
> **low_rent said:**
> well i know :)
so for you guys an admin should have the same privileges as root ?
i'm sorry , but i see a security issue here ...
at least if you wanna su root it should ask for the root passwd 0.o

"admin" is simply the name of a group. In some distributions (and UNIXes), it was called "wheel". In others it's actually called "sudo." It's basically just a group that a user is made a member of to denote the fact that they are allowed to 'sudo.' If they have been given that trust by the sysadmin, why would they have to know a second password? Under what set of conditions would that improve security?

If you want the user to sudo, add them to the 'admin' group.
If you don't want the user to sudo, remove them from the 'admin' group.

There's no need for "teach them a new password" in there. The request for a password is only there to:

1) Prevent people other than the actual user from sudoing (whether someone has gained user privileges somehow, or just sat down at somebody else's desk)
2) To prevent the user from accidentally making a certain class of mistake. "sudo rm * .txt" instead of "sudo rm *.txt" for example.

---

### Post by aysiu on 2007-08-04
> **low_rent said:**
> well i know :)
so for you guys an admin should have the same privileges as root ?
i'm sorry , but i see a security issue here ...
at least if you wanna su root it should ask for the root passwd 0.o
No, that would be the real security issue--setting up a root password.

1. Enabling a proper root account prevents more of a security risk because "everyone" knows there is an account called *root* that has privileges over the entire system. Username down. Privilege down. All that's needed is to guess the password.

2. Even though the default Ubuntu doesn't dole out privileges this way, *sudo* can easily be implemented so as to allow certain users root access to only certain tasks, not total root access. Enabling a root account doesn't give you that customization in security classes.

3. If you put someone in the *admin* group, you trust that user. If you don't trust a user, don't put her in the *admin* group.

4. If you have reason to believe a user cannot be trusted with root privileges any more, you can just remove her from the *admin* group, instead of changing the root password and then having to inform all the other users who have the root password of what the new password is.

---

### Post by eentonig on 2007-08-04
Users in the admin group ARE admins. So yes, I'm fine with them providing their password.

It's actually a lot safer this way, because it allows you to account for whom did some changes. And not 'root' (who is used by x admins) did a change, but we can't find out who actually was root at that time.

Also, when Susan leaves the office, I find it easier to block her account. Then block her account and make sure everybody knows that I changed the root password.

---

### Post by low_rent on 2007-08-04
well then why dont you let the local user choose wether or not he wanna use sudo and set it like this ?

i still see a security hole here , by default config .
i've tested a bunch of distrib and for the moment ubuntu is the only one with this line in /etc/sudoers

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by eentonig on 2007-08-04
Yes, 

All admins get admin rights. What's the security issue in this? Why would I put someone in the admin group, if I don't want him to be admin?

---

### Post by aysiu on 2007-08-04
> **low_rent said:**
> well then why dont you let the local user choose wether or not he wanna use sudo and set it like this ?

i still see a security hole here , by default config .
i've tested a bunch of distrib and for the moment ubuntu is the only one with this line in /etc/sudoers

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
You can "see a security hole" all you want, but you haven't yet described one.

The *admin* users can gain root privilege. So what? They're *admin* users.

In other Linux distributions, you let regular users know the root password, and they log in as root.

Both are equal security risks on one level, because you have to trust the users you're giving that privilege.

Apart from that, *sudo* is actually more secure. Read more here about the pros and cons of each security implementation:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by low_rent on 2007-08-04
> **eentonig said:**
> Yes, 

All admins get admin rights. What's the security issue in this? Why would I put someone in the admin group, if I don't want him to be admin?

well because when you do install ubuntu it ask for username 
and nowhere it's written "create an admin"
so when you start using your userfriendly distrib you dont know 
that you have some admin privilege .you normally think you have a 
normal user account . and i'm sure here on this forum a lots of people think they have a normal user account .
also when  you are accustomed to use some linux distrib first time you install ubuntu the first question is " what's the password root and how do i activate it ?"


under certains circonstances i see a security risk .

---

### Post by aysiu on 2007-08-04
> **low_rent said:**
> well because when you do install ubuntu it ask for username 
and nowhere it's written "create an admin"
so when you start using your userfriendly distrib you dont know 
that you have some admin privilege .you normally think you have a 
normal user account . and i'm sure here on this forum a lots of people think they have a normal user account .
also when  you are accustomed to use some linux distrib first time you install ubuntu the first question is " what's the password root and how do i activate it ?"


under certains circonstances i see a security risk .
And you haven't yet explained what the security risk is.

If someone is installing an operating system, she is the administrator. If she's installing a regular Linux distribution, she has the root password and the user password. If she's installing Ubuntu or Mac OS X, she has a user who is able to temporarily escalate to root privileges through the use of *sudo*.

That user is not root all the time. *sudo* has to be invoked in order for root privilege to be attained, and most of the uses of *sudo* escalate privilege for only one command. For example, when I do *sudo apt-get update*, I'm invoking *dpkg* with root privileges, but everything else that's running (Firefox, Nautilus, Thunderbird, etc.) are all still running with regular user privileges.

Even in your scenario, where a user knows to type ```
sudo su root
``` or ```
sudo -i
``` or ```
sudo -s
``` she'll still have escalated privileges only for the terminal commands. Everything else running is still running as user.

Why don't you ask questions to better understand *sudo*? Or actually read [the documentation on it](https://help.ubuntu.com/community/RootSudo)? Instead of criticizing something you don't really understand?

---

### Post by low_rent on 2007-08-04
....
just saying it's completly stupid to add the admin group with ALL(ALL)ALL on the /etc/sudoers default config .

---

### Post by aysiu on 2007-08-04
> **low_rent said:**
> ....
just saying it's completly stupid to add the admin group with ALL(ALL)ALL on the /etc/sudoers default config .
Why is it stupid? You still haven't explained why.

---

### Post by bodhi.zazen on 2007-08-04
> **low_rent said:**
> ....
just saying it's completly stupid to add the admin group with ALL(ALL)ALL on the /etc/sudoers default config .

Well low_rent there is always a way to access root, all access to all systems you administrate.

sudo -i or su -

pick you poison ...

BUT I would like to see a second password for sudo, different from the admin user(s) log in password, that would be cool....

The Ubuntu approach is to lock the root account. If you do not like it you can either edit sudoers or enable the root account

That is the beauty of choice ...

---

### Post by apetresc on 2007-08-05
I think I understand what low_rent is saying now. (I don't agree, I just "got" it now). In some other distributions like, say, Debian, you set a separate password for root, so you know in your day-to-day operation that when you have to type that special root password, you're doing something qualitatively different, something that requires escalated privileges, and you will be more weary. 

On the other hand, a beginner user who is switching from another distro to Ubuntu, may not realize that, when they are typing their own password, *they* in a sense are "becoming" root, and if they are used to the Debian-style way of doing it, they may not even realize that an escalation of privileges has occurred since there is no longer a clear dichotomy between "superuser" and "regular user."

Of course, it is wrong to call this a "security hole." It's simply a design decision that Ubuntu made differently from other distros. Both ways are more or less secure when used properly, and both are more or less weak when used improperly.

---

### Post by codmate on 2007-08-06
This confusion is almost always caused when people come to a distro using a sudo style system from a root-account based system (like Red Hat).

I, for the reasons said above, actually believe the sudo way of doing things is better (you have to guess admin account name as well as the password).

What would clarify things for newer users is some simple wording on the installer.
Windows asks you to create and admin account and offers to let you make user accounts. 

It would be good if Ubuntu acted in a similar fasion.
I forget the wording on the installer, but it would be nice if it made it clear that you are  initially creating an admin user whose account should be treated with the same respect you would treat 'root'.

Personally I run several accounts on my server, only one is a member of the admin group.

This can in no way be described as a security hole. It's merely a design decision that is clear to those of us who understand sudo and could do with some explaination on install to those coming from other distros or operating systems.

---

