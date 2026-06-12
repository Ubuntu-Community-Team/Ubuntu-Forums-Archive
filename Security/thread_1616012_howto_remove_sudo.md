---
title: "howto remove sudo"
date: 2010-11-07
forum: Security
---

### Post by bunty on 2010-11-07
Hi,

I have installed ubuntu for a fairly novice user on a system that I have to support mainly via ssh and vnc. 

It has worked pretty well for a year and the user copes well with ubuntu. 

However, for reasons that I will elaborate I don't like the Ubuntu idea of having sudo configured carte blanche for all users. This essentially undoes the most fundamental unix security measures. 

Yes, I have read: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I find many of the advantages to be less than convincing and the list of disadvantages less than comprehensive. 

>> The Ubuntu installer has fewer questions to ask.
That's your number one, top of the list advantage?


>> Users don't have to remember an extra password (i.e. the root password), which they are likely to forget.
Why are they "likely" to forget? Do you assume anyone wanting to install Ubuntu is a retard? You are already starting to twist the facts to justify sudo. 



>> It avoids the "I can do anything" interactive login by default (e.g. the tendency by users to login as an "Administrator" user in Microsoft Windows systems), 

No. it creates the "I can do anything" user. You are trying simulate the MS situation, in line with the general aim of Ubuntu to be easy for windows users to adopt. 


>> you will be prompted for a password before major changes can happen, which should make you think about the consequences of what you are doing.

We already know the user is a windows trained no-brainer. We know the windows user just says "yes" to any question without reading it and supplies the admin password to a "install" Celine Dion audio CDs. Being asked for a password does not make the user think unless the user is inclined to think in the first place. You already assume that is not the case.

>> sudo adds a log entry of the command(s) run (in /var/log/auth.log). If you mess up, you can always go back and see what commands were run. It is also nice for auditing.

Yes, that valid. A useful feature for undoing a mess but not a security feature that outweighs the other issues.

>> Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first ...

Yes , but there are other simple ways to counter a brute-force attack. This is not a real advantage.


>> sudo can be setup with a much more fine-grained security policy.

EXCEPT that you dont ! You give the base user TOTAL sudo access. 


>> The root account password does not need to be shared with everybody who needs to perform some type of administrative task(s) on the system (see the previous bullet).

What a blast. You don't need to give everyone the root password .... because they don't need it, they already have full root access!


>> The authentication automatically expires after a short time ... 

Well this is hardly a security feature on a system where the non sudo terminal can just as easily be used to reset the user the password and then enter a sudo. Leaving a user terminal open is JUST AS DANGEROUS as leaving a root terminal active! And you call this a "benefit of user sudo"?



So, unless there's a real show-stopper argument that you forgot to list, I have to say I remain decidedly unconvinced of the benefits. 

Well what about a couple of disadvantages? Well I'd start by reiterating the last stated "benefit". Similarly , the idea of having limited users on *nix is , from a security point of view, to prevent privilege escalation. Insecure applications like web browsers , third party flash plugins and closed sourse applications like googleearth get access to the users part of the system. Also there is a continual stream of bugs and vulnerabilities being discovered across the board. 

If the user has limited rights, potential exploits gets ring-fenced to the area his has control and can't take over the system. On ubuntu any process that gets compromised has the potential to spawn a sudo process and gain entire control of the system. 

There seems little sense in listing any other disadvantages or inconveniences after that.


Now I'm well aware of how to set the root passwd and how to remove the user from having blanket sudo rights. The problem is how to do this without losing acces to all the GUI configuration tools and banishing all admin tasks to CLI (tho' that is where I would do most things).


I can see that the general unbuntu approach fits a certain class of user that I need to service but this issue needs resolving. 

I'm sure there must be a solution but I have not been able to find anything but the official line about what a great idea this is. 


Any help would be greatly appreciated.

---

### Post by ajgreeny on 2010-11-07
The best way would seem to be setting up a new user with admin rights (ie, you using ssh or whatever), and removing admin rights from your novice user.

Just make sure that user does not know your password, so therefore can not do anything to mess up your good configuration work on the OS.

> However, for reasons that I will elaborate I don't like the Ubuntu idea  of having sudo configured carte blanche for all users. This essentially  undoes the most fundamental unix security measures. By the way, that comment is not correct; only the first user on a system has admin rights by default.  Second and subsequent users need to be given admin rights when they are added if needed, but normally do not have it.

---

### Post by uRock on 2010-11-07
> **ajgreeny said:**
> By the way, that comment is not correct; only the first user on a system has admin rights by default.

+1 When new user accounts are made, they don't have the ability to sudo as they have a Desktop user account and not and Admin account.

All of my systems have multiple accounts and I have to go through and give them Admin permissions or else my wife will have me running to her system every ten minutes to make adjustments to her system. My daughter is the only one that doesn't get an Admin account, because she loves to do everything she sees me doing. I had to downgrade her to desktop user when she found a way around OpenDNS by deleting the Eth0 profile in Network Manager and creating a new one. She's only six and she no longer has root privies.

---

### Post by FuturePilot on 2010-11-07
> **ajgreeny said:**
> The best way would seem to be setting up a new user with admin rights (ie, you using ssh or whatever), and removing admin rights from your novice user.

Just make sure that user does not know your password, so therefore can not do anything to mess up your good configuration work on the OS.

By the way, that comment is not correct; only the first user on a system has admin rights by default.  Second and subsequent users need to be given admin rights when they are added if needed, but normally do not have it.

This is probably the best way.

---

### Post by SuilAmhain on 2010-11-07
If you need a user to be able to run things without keying in passwords you could edit the sudoers file. They'd still need to type sudo but it's something. Add something similiar to the sudo file

```
Username     ALL = NOPASSWD: ALL
```

Very detailed info from here:
[http://www.sudo.ws/sudo/sudoers.man.html](http://www.sudo.ws/sudo/sudoers.man.html)

I'm not completely sure on this but if for example you added a user to say the firestarter group they would be able to run that program without requiring sudo at all.

I work in an AIX environment with a small team and have recently rolled out sudo to prevent nasty things happening. We have had a server root password changed without anyone remembering what it was and someone did a mv * on rootvg which caused all sorts of problems...

sudo is very beneficial and I can not see your issue with it. Win Vista and 7 have UAC which is very similiar.

---

### Post by snowpine on 2010-11-07
Hi Bunty, "sudo" is just a tool. There are many valid arguments for *and* against using sudo. Ultimately it is *your* decision; don't let anyone else tell you what to do!

There is, however, one **huge** argument *for* using "sudo" that I'm surprised nobody has mentioned yet: All of the Ubuntu help documentation, the Ubuntu wiki, and all the how-to's and tutorials on these Forums assume you are using sudo. If you do not use sudo, you are missing out on all this great documentation. :)

---

### Post by psusi on 2010-11-07
Yea, it's real simple; the installer makes you an admin so tell it who YOU are, then create the user a ( non admin ) account later.

---

### Post by The Cog on 2010-11-08
> **uRock said:**
> My daughter is the only one that doesn't get an Admin account, because she loves to do everything she sees me doing. I had to downgrade her to desktop user when she found a way around OpenDNS by deleting the Eth0 profile in Network Manager and creating a new one. She's only six and she no longer has root privies.
That's one dangerous little lady!

@bunty:
Only members of the **admin** group can use sudo to elevate any command they choose. By default, only the first user created during install is a member of the admin group.

For other users that need extra privileges, you can make them members of the admin group if you trust them enough. Alternatively, you can edit the sudoers configuration to permit only the commands you choose, and allocate them to users or groups as required. Other posts here link to instructions on how to edit sudoers.

---

### Post by arapaho on 2010-11-08
I've read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
but I still need some clarification, please.

"Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are. Since the root account password is locked, this attack becomes essentially meaningless, since there is no password to crack or guess in the first place."

1. User's names are usually simple and user's logins not very long and complicated. And potentially cracking sudo password attacker can do bad things too. Is it correct?
2. What does it mean that root logins are disabled by default? The Root account exist, so how can it be more secure without password? I don't get it. Please, explain.
3. Is it better to leave it as it is or set a super-strong root password and always use only sudo anyway.

---

### Post by bunty on 2010-11-08
Thanks for all the replies. It looks like I can get a saner setup by creating a second user and reserving default user for admin tasks. But I don't even like having sudo on the system. 

> Only members of the admin group can use sudo to elevate any command they choose. By default, only the first user created during install is a member of the admin group.

So 98% of ubuntu installations will be barely any better than windows users permanently running as admin! This is madness. It seem that main "advantage" of this is supposed to be one less question during installation (setting the root password).

This misses the opportunity to point out to the user the meaning and importance of having a separation of permissions and leaves default Ubuntu as one of the least secure distros. Sadly it's also the most widely used. 


I've just updated this system from 9.04 to 9.10 via vnc and all went remarkably smoothly and the results look good. I'm impressed with a lot about Kubuntu but this issue would prevent me from recommending it to anyone likely to just opt for default installation. 

When widespread malware and visus problems start to hit linux, it will be via Ubuntu. This needs to change.

---

### Post by sisco311 on 2010-11-08
> **bunty said:**
> Now I'm well aware of how to set the root passwd and how to remove the user from having blanket sudo rights. The problem is how to do this without losing acces to all the GUI configuration tools and banishing all admin tasks to CLI (tho' that is where I would do most things).


Set gksu's authentication mode to su:
```
gksu-properties
```

And configure policykit to prompt the users for the root password, as root:
```
cd /etc/polkit-1/localauthority.conf.d/
mv 50-localauthority.conf 90-localauthority.conf
```

---

### Post by bunty on 2010-11-08
[http://forums.gentoo.org/viewtopic-t-847413.html?sid=1acd3de2f55d9eb4ddebc835968f8fe8](http://forums.gentoo.org/viewtopic-t-847413.html?sid=1acd3de2f55d9eb4ddebc835968f8fe8)

> Impact 


An attacker could exploit these vulnerabilities to cause programs 
linked against the library to crash or execute arbitrary code with the 
permissions of the user running the vulnerable program, which could be 
the root user.

[http://www.libpng.org/pub/png/libpng.html](http://www.libpng.org/pub/png/libpng.html)

> Several versions of libpng through 1.4.2 (and through 1.2.43 in the older series) contain a bug whereby progressive applications such as web browsers (or the rpng2 demo app included in libpng) could receive an extra row of image data beyond the height reported in the header, potentially leading to an out-of-bounds write to memory (depending on how the application is written) and the possibility of execution of an attacker's code with the privileges of the libpng user (including remote compromise in the case of a libpng-based browser visiting a hostile web site). This vulnerability has been assigned ID CVE-2010-1205 (via Mozilla).


THAT is why a web browser and day to day tasks should not be run by a user with more than local privileges.

I'm not going to post an exploit here but it would not take much imagination when the the user can run sudo su !

---

### Post by psusi on 2010-11-08
> **arapaho said:**
> 
2. What does it mean that root logins are disabled by default? The Root account exist, so how can it be more secure without password? I don't get it. Please, explain.

It means the account is locked so you can not log in as root.  It is more secure since you can't guess the password of an account that doesn't have one.

> **arapaho said:**
> 3. Is it better to leave it as it is or set a super-strong root password and always use only sudo anyway.

It is better to leave it the way it is.

> **bunty said:**
> 
So 98% of ubuntu installations will be barely any better than windows users permanently running as admin! This is madness. It seem that main "advantage" of this is supposed to be one less question during installation (setting the root password).

No, you've got it all wrong.  In windows you log in as root all the time, so any program you run can trash your system without your consent.  With sudo you only run a program with root privileges when you choose, and there is no way to do it by accident or have a program do it without your consent since you have to enter your password.

> **bunty said:**
> This misses the opportunity to point out to the user the meaning and importance of having a separation of permissions and leaves default Ubuntu as one of the least secure distros. Sadly it's also the most widely used. 

Again, wrong.

> **bunty said:**
> 
When widespread malware and visus problems start to hit linux, it will be via Ubuntu. This needs to change.

And wrong again.

---

### Post by ajgreeny on 2010-11-08
Sorry bunty, you still are not getting it, and I completely agree with psusi's answer.  I am as sure as it is possible to be that you have got the wrong end of the stick completely regarding this business of the root account being disabled.

You seem to think that this leads to all users automatically having the ability to carry out administrative activities that in other distros, where root is enabled, would require the root password.  That is where you are totally wrong.  To do that users still need to have the elevated privileges that can only be achieved by members of the admin group.

As many people including myself, have pointed out, only the first user made on the system has admin privileges, and is a member of the admin group.  Those who are not members of admin they can not carry out any admin programs or edit any system filesin any way; only files in their own home folder can be written to by those users.

You have said> I'm not going to post an exploit here but it would not take much imagination when the the user can run sudo su !  You still seem to believe with this comment that any user can type **sudo su** in terminal and magically have admin privileges.  Please understand that only the first user will have the ability to do this, all other users would be unable to raise their status and therefore unable to use **sudo su**.

Think again!  In my opinion the use of sudo is at least as secure as any other distro that uses the root account system with a root password, if not more so.

---

### Post by Rubi1200 on 2010-11-08
I don't normally like quoting large chunks of text, but in this instance it is quite necessary:

> In fact, don't log in as root at all. Period. Log in on your user account    and **su** to root when needed. Whether the login is remote    or local. Or use **sudo**, which can run individual commands    with root privileges.     (There should be a **sudo** package    available from your vendor.)           This takes some getting used to, but it is    the "right" way to do things. And the safest. And will become     more a more natural way of doing this as time goes on.    
   
I know someone is saying right now "but that is so much trouble, I am    root, and it is my system". True, but root is a specialized account that    was not ever meant to be used as a regular user account. Root has access to    everything, even hardware devices. The system "trusts" root.    It believes that you know what you are doing. If you make a mistook, it    assumes that you meant that, and will do it's best to do what you told it    to do...even if that destroys the system!    
[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Security-Quickstart-HOWTO.html#GENERAL](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Security-Quickstart-HOWTO.html#GENERAL)

Everything said by ajgreeny and psusi is 100% correct.

---

### Post by bodhi.zazen on 2010-11-08
> **arapaho said:**
> I've read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
but I still need some clarification, please.

"Every cracker trying to brute-force their way into your box will know it has an account named root and will try that first. What they don't know is what the usernames of your other users are. Since the root account password is locked, this attack becomes essentially meaningless, since there is no password to crack or guess in the first place."

sudo and su are equally secure / insecure. For the most part they have very similar vulnerabilities.

> 1. User's names are usually simple and user's logins not very long and complicated. And potentially cracking sudo password attacker can do bad things too. Is it correct?
2. What does it mean that root logins are disabled by default? The Root account exist, so how can it be more secure without password? I don't get it. Please, explain.
3. Is it better to leave it as it is or set a super-strong root password and always use only sudo anyway.

#1 and #3 are related and you are mixing apples and oranges. Strong user/password on su vs weak user/password on sudo condenses to strong vs weak passwords. Simply enforce a strong password policy and su vs sudo is irrelevant.

#2 - The root account is locked by default meaning you can not log into an Ubuntu system as a root user using a password.

Honestly, this entire conversation is rather pointless. My advice is:

1. Understand how sudo works. Use it if you like.

2. Understand how su works. Use it if you like.

3. If you disable sudo on Ubuntu and enable the root account, understand the security implications and what to "fix" including ssh (by default the openssh-server allows root logins with a password. This is not a problem so long as you use sudo , but if you convert to su ...).

So long as you know what you are doing, you will be fine.

---

### Post by bunty on 2010-11-08
[QUOTE="ajgreeny"]You still seem to believe with this comment that any user can type sudo su in terminal and magically have admin privileges. Please understand that only the first user will have the ability to do this, all other users would be unable to raise their status and therefore unable to use sudo su.[/QUOTE]

thanks, I do "get it". The fact that it's "only the first user" hardly means it's OK, since 98% of home systems will be installed like that and that is what the installer intends. 

There is no suggestion that this is "just the first" and you should make another for everyday use. The ubuntu way is you work as admin user all the time. That's what I'm criticising. 

Thanks to your comments and those of others I think I can configure unbuntu to a more acceptable security policy. 

That does not undermine the point that the default user having full admin privileges and sudo su access is madness. 

Since that is the account most people use on ubuntu any discussion needs to rest there , not get diverted into what else you can do if you're well informed enough to know how stupid it is as it stands.

---

### Post by bodhi.zazen on 2010-11-08
> **bunty said:**
> There is no suggestion that this is "just the first" and you should make another for everyday use. The ubuntu way is you work as admin user all the time. That's what I'm criticising.

The "admin" user has the same privileges as any other user with the exception that s/he can escalate to root.

su is no more secure as the administrative user can still escalate to root. The vulnerabilities are equal.

If these kind of issues concern you, I highly suggest you learn to use tools such as selinux and apparmor.

---

### Post by bunty on 2010-11-08
> 3. If you disable sudo on Ubuntu and enable the root account, understand the security implications and what to "fix" including ssh (by default the openssh-server allows root logins with a password. This is not a problem so long as you use sudo , but if you convert to su ...).

Maybe I'm missing your point but if I get a ssh login as user then do sudo su with the same user password , how is this fundamentally more secure than a root login?

---

### Post by tgm4883 on 2010-11-08
> **bunty said:**
> Maybe I'm missing your point but if I get a ssh login as user then do sudo su with the same user password , how is this fundamentally more secure than a root login?

I think the point would be that in order to gain access to a machine you have to crack 2 combinations. Username AND password. Since root is the main user on every Linux distro, the only way to fix that is to randomize the root username (in this case, using the first username)

If you enable the root user, then half of the work is done for the attacker. 

IMHO, The idea behind sudo is that if an attacker gains access to the machine (without knowing the password), then to gain root access the user would still need to know the password for the user in the sudoers file.

---

### Post by CandidMan on 2010-11-08
I think what they're trying to get across is that to crack an ssh server you need

a) An identity i.e. user name

b)The corresponding password

Every Ubuntu distro has the 'root' user, but only mine has random-name@random-desktop

If you had another account as admin, that would probably be brute-forced or whatever, and youi'd only be inconveniencing yourself
You could go on forever with redundant accounts and layers of security...

---

### Post by bodhi.zazen on 2010-11-08
> **bunty said:**
> Maybe I'm missing your point but if I get a ssh login as user then do sudo su with the same user password , how is this fundamentally more secure than a root login?

If you are asking me, I never claimed su was more or less secure then sudo. I think they are equally secure / insecure depending on your perspective.

By default, on Ubuntu, the root account is locked, so you can not log in as root via ssh (or the console) using a password. It is this feature, locking the root account, and not sudo or su, that increases security.

If you set a root password, you decrease security as there is now one more account with root access (root + any user(s) you allow to access root via su).

Ubuntu uses sudo to gain root access, and thus you need 2 pieces of information to log in to a root shell - a user name and a password.

With the root account enabled you need one piece of information - a (root) password.

At the end of the analysis, either way (sudo or su) it comes down to the strength of the login password and not sudo vs su.

Logging in as root is a separate, but related, issue from privilege escalation.

If you log in to an account that can access root via either su or sudo, root access is close behind via a seeming unlimited number of techniques. You need to prevent shell access in the first place.

This is where both apparmor and selinux will help. With both selinux and apparmor I can lock down non-administrative accounts such that you can not gain root access (via privilege escalation) even if you have the su (root) password or sudo (admin) password (you may of course login as root if you have the su password or the admin user if you have the sudo password, either way you have root).

Now, the third issue you are asking about is a ssh server.

If you are asking how to secure ssh, use keys and disable passwords altogether (for ssh logins). Again this has nothing to do with su or sudo.

I think you are missing the point, the advantage of sudo is NOT security, it is in configuration and customization.

su give root access in an all or none fashion. sudo can be configured to allow root access to a more restricted set of commands.

If you prefer su, go for it, but do not fool yourself that it is more (or less) secure then sudo. From a security perspective, IMO, su and sudo are equally secure/insecure and the arguments favoring one or another are made by people who do not understand the security issues.

As I indicated earlier, if you wish to increase security, learn to use ssh keys and learn to use apparmor or selinux, and understand the security of any services you install.

---

### Post by WeAreLinux on 2010-11-08
Sorry to interrupt the heated discussion, but I have a quick question please.

> This is where both apparmor and selinux will help. With both selinux and apparmor I can lock down non-administrative accounts such that you can not gain root access (via privilege escalation) even if you have the su (root) password or sudo (admin) password (you may of course login as root if you have the su password or the admin user if you have the sudo password, either way you have root).

I thought after creating a non-admin account, that account don't have any access to sudo or su once the "Administer the system" box is not checked. Is this incorrect? :)

---

### Post by cariboo on 2010-11-09
A user has to be in the adm group in order to be part of sudoers, so if you're running 10.10, set the user as a desktop user, and they won't be able to use sudo.

---

### Post by WeAreLinux on 2010-11-09
> **cariboo907 said:**
> A user has to be in the adm group in order to be part of sudoers, so if you're running 10.10, set the user as a desktop user, and they won't be able to use sudo.

That applies to 10.04 too, right? I'm asking because you specifically mention running 10.10.

---

### Post by psusi on 2010-11-09
> **WeAreLinux said:**
> That applies to 10.04 too, right? I'm asking because you specifically mention running 10.10.

Yes, it has always worked that way.

Admin = can use sudo.

This is by default of course, you can change it by editing the sudoers file.

---

### Post by Dave_L on 2010-11-09
> **cariboo907 said:**
> A user has to be in the adm group in order to be part of sudoers, so if you're running 10.10, set the user as a desktop user, and they won't be able to use sudo.

"adm" or "admin"? Both of these are groups (in /etc/group). Only "admin" is referenced in /etc/sudoers.  Is the "adm" group used for anything?

---

### Post by sisco311 on 2010-11-09
> **Dave_L said:**
> "adm" or "admin"? Both of these are groups (in /etc/group). Only "admin" is referenced in /etc/sudoers.  


admin

> **Dave_L said:**
> 
Is the "adm" group used for anything?

Yep, the adm group has read permission on some of the non-world-readable log files (i.e. /var/log/auth.log).

---

### Post by Dave_L on 2010-11-09
Thanks :)

---

### Post by alphaamanitin on 2010-11-09
> **bodhi.zazen said:**
> If you are asking me, I never claimed su was more or less secure then sudo. I think they are equally secure / insecure depending on your perspective.

By default, on Ubuntu, the root account is locked, so you can not log in as root via ssh (or the console) using a password. It is this feature, locking the root account, and not sudo or su, that increases security.

If you set a root password, you decrease security as there is now one more account with root access (root + any user(s) you allow to access root via su).

Ubuntu uses sudo to gain root access, and thus you need 2 pieces of information to log in to a root shell - a user name and a password.

With the root account enabled you need one piece of information - a (root) password.

At the end of the analysis, either way (sudo or su) it comes down to the strength of the login password and not sudo vs su.

Logging in as root is a separate, but related, issue from privilege escalation.

If you log in to an account that can access root via either su or sudo, root access is close behind via a seeming unlimited number of techniques. You need to prevent shell access in the first place.

This is where both apparmor and selinux will help. With both selinux and apparmor I can lock down non-administrative accounts such that you can not gain root access (via privilege escalation) even if you have the su (root) password or sudo (admin) password (you may of course login as root if you have the su password or the admin user if you have the sudo password, either way you have root).

Now, the third issue you are asking about is a ssh server.

If you are asking how to secure ssh, use keys and disable passwords altogether (for ssh logins). Again this has nothing to do with su or sudo.

I think you are missing the point, the advantage of sudo is NOT security, it is in configuration and customization.

su give root access in an all or none fashion. sudo can be configured to allow root access to a more restricted set of commands.

If you prefer su, go for it, but do not fool yourself that it is more (or less) secure then sudo. From a security perspective, IMO, su and sudo are equally secure/insecure and the arguments favoring one or another are made by people who do not understand the security issues.

As I indicated earlier, if you wish to increase security, learn to use ssh keys and learn to use apparmor or selinux, and understand the security of any services you install.

+1

Once again, bodhi.zazen,  I think you have given the most comprehensive security response.  I had not thought of the issue as less of a security issue and more of a configuration issue.  I would say though that if I was wanting a server with security I might look into a FreeBSD or FreeNAS server with some jails set up.  Not that I fully understand jails, but from what I have read they seem to greatly increase security.  I expect Ubuntu also has this service, yes?

AlphaA

---

### Post by bodhi.zazen on 2010-11-09
> **WeAreLinux said:**
> Sorry to interrupt the heated discussion, but I have a quick question please.



I thought after creating a non-admin account, that account don't have any access to sudo or su once the "Administer the system" box is not checked. Is this incorrect? :)

Assuming the non-admin user knows the password ..

Open a terminal, 

```
su <admin_user>
#Enter admin user password

sudo -i 
# root shell
```

The only thing that stops you with a default install, sudo or su, is a password.

This is why you need a strong password for your admin user.

With selinux or apparmor "properly configured" you can not su or sudo to a root shell from a non-admin account, you need to log in either as with an admin account.

---

### Post by bodhi.zazen on 2010-11-09
> **alphaamanitin said:**
> +1

Not that I fully understand jails, but from what I have read they seem to greatly increase security.  I expect Ubuntu also has this service, yes?

AlphaA

I would start by looking at a chroot and running servers in a chroot. OpenVZ , LXC , and FreeBSD jails are very similar technology (conceptually) to a chroot jail.

Personally, not to beat a dead horse, but if you are using :

Ubuntu -> Apparmor
Fedora / Centos / RHEL -> SELinux

Again, choose your OS and learn the security features or tools within the OS.

---

### Post by WeAreLinux on 2010-11-09
Thanks cariboo907, psusi, & bodhi.zazen for the information.

---

