---
title: "Network Design - Request For Ideas"
date: 2007-11-25
forum: Server Platforms
---

### Post by knorr.orange on 2007-11-25
I have been asked to help with designing a small network with WinXP clients (50 of them) and an Ubuntu server.  The basic requirements are as follows:
Client machines must be WindowsXP
Users must be authenticated by server
Users must always log into client machines
Users must be able to easily change their passwords
File shares available from server
web caching available
web content filtering available with "bad" requests logged with username

For the web cache and content filtering I am planning to use squid and dansguardian.  For the file sharing it will be samba.  The part I am not sure about is how to authenticate users.  I know samba can do it, but I have never done anything with it.  For the needs listed above is samba the best way to get this done, or is there a better or more simple way to accomplish the same thing.

---

### Post by foxylad on 2007-11-26
Samba is the best solution. I don't know much about Windows networking, but Samba is the solution - I suggest you get over to their site and start reading.

---

### Post by rickyjones on 2007-11-26
Here is what I would personally do.

I would install a Windows Server 2003 system for the central server using Active Directory. This accomplishes central logins, changing passwords from the client machine, and will simplify administration.

I would then use VMWare to run a virtual Linux system setup with Apache, Squid, etc... for intranet use and to cache web pages/log bad requests.

You can do all of this with one well configured piece of hardware.

-Richard

---

### Post by otake-tux on 2007-11-26
> **rickyjones said:**
> Here is what I would personally do.

I would install a Windows Server 2003 system for the central server using Active Directory. This accomplishes central logins, changing passwords from the client machine, and will simplify administration.

I would then use VMWare to run a virtual Linux system setup with Apache, Squid, etc... for intranet use and to cache web pages/log bad requests.

You can do all of this with one well configured piece of hardware.

-Richard

I don't think he asked what OS to use.  he already listed the tools at hand so I don't see how a winserver is relevant here.

---

### Post by koenn on 2007-11-26
> **rickyjones said:**
> Here is what I would personally do.

I would install a Windows Server 2003 system for the central server using Active Directory. This accomplishes central logins, changing passwords from the client machine, and will simplify administration.

I would then use VMWare to run a virtual Linux system setup with Apache, Squid, etc... for intranet use and to cache web pages/log bad requests.

You can do all of this with one well configured piece of hardware.

-Richard
Personnally, i don't think thats such a good idea.
- AD can be quite overwhelming for the unexperienced admin, so claiming it will simplify administration is a bit iffy
- Microsoft recommends deploying at least 2 domain controllers, to avoid single point of failure : you risk loosing a lot if your domain controller goes down
- running a Win2k3 server domain controller  as not much more than a host for a virtual machine with linux sounds like a lot of overhead for a very small benefit (the user management AD offers)


I'd say squid (& dansguardian) + samba matches the OP's specs perfectly. When set up as an NT4 domain controller it should take care of centralised user management. The only thing I'm not 100% about is the "Users must be able to easily change their passwords" - but the samba admin manual may have some info, and if not, I'm sure a suitable workaround can be found.

---

### Post by koenn on 2007-11-26
found this 2006 ubuntu-nl mailing list : [https://lists.ubuntu.com/archives/ubuntu-nl/2006-April/001196.html](https://lists.ubuntu.com/archives/ubuntu-nl/2006-April/001196.html) :

you can take some inspiration from the smb.conf [global] section.

From a follow up msg in that same thread :
users will be able to modify their password from XP  with ctrl+alt+del --> change password if smb.conf says  
```
unix password sync = No 
```

this may interfere with file system permissions on the shared folder, as those  rely on local unix accounts rather than samba accounts. 
You could do something creative with group permissions, or look through the samba documentation for more recent information or a better sollution.

---

### Post by mellowd on 2007-11-26
I wouldn't install the 2003 server either. Samba can do the authentication

---

### Post by netlogic on 2007-11-26
For one location of 50 users, stick with Samba 3 which gives you the NT4 style domain model. By the time your office grows more to different locations, Samba 4 should be ready for your deployment. Samba 3 is easier than the AD design, because it uses simplified NT4 style domain model. The rule I always followed so far for file sharing Windows client is avoid using AD if the locations are less than three and each locations have less than 200 users. Also, Samba requires no reinstallation if the server becomes a brick. That is why even you only have 50 users, you should ALWAYS have two Windows server.  In Linux, it is a process of simple copies of few files from etc  to get your backup server running. Also, Linux doesn't have roles like Windows that require reboots to change or reinstallation. For your network, I would setup two basic low end servers for authentications and applications and setup a cheap NAS server for data. There are few graphical NAS servers such as FreeNAS (FreeBSD) or Openfiler (Redhat based). Both of them support iSCSI and all other file sharing protocols. That will give you some redundancies that you might need.

Like I constantly have repeated on this forum. These days, you must know both OSes and learn to utilize both. Also, always maximize the need for Linux to save the cost of uprising price of IT software  during the time when the IT budget is really shrinking. I hope it helps.

---

### Post by knorr.orange on 2007-11-27
I should probably clarify a bit about why the Ubuntu server is desired.  They have a license agreement that allows for the WinXP clients, but would like to avoid extending that to cover "server" products.  I do not know about the contract specifics, but I think the goal is to slowly work their way off of MS products.  So even if the Win2003 server and AD solution would be available for the same cost (zero dollars,) it gets the in a bad situation long term, making it harder to get off of the MS products all together.  I appreciate all of the proposals, including the completely rational idea to use the MS solution, but I should have mentioned the above reasons for choosing the Linux-based server.

---

### Post by knorr.orange on 2007-11-27
From what I can see here, it looks like for my basic needs, Samba can do it.  I have read through a lot of samba documentation and various HOWTO's and am confused at exactly what I need to do to get the authentication set up.  Would someone please point me to something describing what I actually need to do here?

From what I can tell, I need to change samba's configuration to be a (the?) primary domain controller.  Then I need to tell it which machines are permitted to join the domain.  From the Windows side, it looks like I need to go to each PC and tell it to use the NT4 authentication.  Assuming that all is correct, I am still missing the part about managing users and passwords.  Can someone explain how new users can be added and how the passwords are managed?

---

### Post by rickyjones on 2007-11-27
> **knorr.orange said:**
> From what I can see here, it looks like for my basic needs, Samba can do it.  I have read through a lot of samba documentation and various HOWTO's and am confused at exactly what I need to do to get the authentication set up.  Would someone please point me to something describing what I actually need to do here?

From what I can tell, I need to change samba's configuration to be a (the?) primary domain controller.  Then I need to tell it which machines are permitted to join the domain.  From the Windows side, it looks like I need to go to each PC and tell it to use the NT4 authentication.  Assuming that all is correct, I am still missing the part about managing users and passwords.  Can someone explain how new users can be added and how the passwords are managed?

From my experience, and this is why I suggested Active Directory, is that the all Samba solution will involve you logging on to the server and issuing the command "add user" or "user add" command for each user you wish to create. Then you need to go through and, for each user, do "smbpasswd -a [username]". This was my experience about a year ago.

-Richard

---

### Post by koenn on 2007-11-27
> **knorr.orange said:**
> From what I can see here, it looks like for my basic needs, Samba can do it.  I have read through a lot of samba documentation and various HOWTO's and am confused at exactly what I need to do to get the authentication set up.  Would someone please point me to something describing what I actually need to do here?

You need to set configure Samba as "PDC" a.k.a. (NT4-style) Primary Domain Controller. Here's the relevant chapter of the Samba HOWTO : - you'd be interested in the sample smb.conf + some background -  :  [http://samba.org/samba/docs/man/Samba3-HOWTO/samba-pdc.html](http://samba.org/samba/docs/man/Samba3-HOWTO/samba-pdc.html)
google with 'samba' and 'domain controller' or 'PDC' should give a few more. This one looks good, but maybe a bit old :
[http://linux-israel.net/pdf/samba-pdc.pdf](http://linux-israel.net/pdf/samba-pdc.pdf) (pdf !)

Then, you need to create computer and user accounts. 
Computer accounts can be created automatically, from the "join this computer to a domain" dialog on the windows client, or by creating accounts on the samba server. creating computer accounts is identical to creating user accounts, but the account name is, IIRC, computer netbios name + $, eg computer name 'bilbao' -> account : bilbao$
described here ::[http://madpenguin.org/cms/index.php/?m=show&id=72](http://madpenguin.org/cms/index.php/?m=show&id=72)

User accounts are created on the server. I do believe that you (still) need both a unix account and a samba account for each user, but i think the "password chat" in [global] section of smb.conf saves you some trouble in that a unix account is created automatically when you create a samba account. (with smbpasswd ). If not, it shouldn't be too hard to create a script that handles that.

If you only have a few users, you can create the accounts by hand, 1 by 1, but if it's a lot, it pays to make a script that reads a list of usernames and creates accounts for each user, eg with a default password that users need to change themselves afterwards. 

Official Samba docs (interesting stuff there !)
[http://samba.org/samba/docs/man/Samba3-HOWTO/](http://samba.org/samba/docs/man/Samba3-HOWTO/)
[http://samba.org/samba/docs/man/Samba3-ByExample/](http://samba.org/samba/docs/man/Samba3-ByExample/) (case studies and examples)
[http://samba.org/samba/docs/man/](http://samba.org/samba/docs/man/)

In case you don't like your google results, I'll let you borrow some of mine that looked promising : 
[http://club.mandriva.com/xwiki/bin/view/KB/ConnectCsamba6](http://club.mandriva.com/xwiki/bin/view/KB/ConnectCsamba6)
[http://daniel.fiser.cz/?go=samba](http://daniel.fiser.cz/?go=samba)
[http://www.enterprisenetworkingplanet.com/netos/article.php/1151091](http://www.enterprisenetworkingplanet.com/netos/article.php/1151091)


Have fun !

---

### Post by koenn on 2007-11-27
> **rickyjones said:**
> From my experience, and this is why I suggested Active Directory, is that the all Samba solution will involve you logging on to the server and issuing the command "add user" or "user add" command for each user you wish to create. Then you need to go through and, for each user, do "smbpasswd -a [username]". This was my experience about a year ago.

-Richard
Whereas with an Active Directory domain, 

0. you'd log on to the server, or install admin tools on your PC
1. Click Start, click Administrative Tools, and then click Active Directory Users and Computers. The Active Directory Users and Computers MMC opens. 
If it is not already selected, click the node for your domain. For example, if your domain is example.com, click example.com.
2. In the details pane, right-click the folder in which you want to add a user account.
Where?
&#8226; Active Directory Users and Computers/domain node/folder
3. Point to New, and then click User.
4. In First name, type the user's first name.
5. In Initials, type the user's initials.
6. In Last name, type the user's last name.
7. Modify Full name to add initials or reverse the order of first and last names.
8. In User logon name, type the user logon name. Click Next.
9. In New Object - User, in Password and Confirm password, type the user's password, and then select the appropriate password options.
10. Click Next, review the new user account settings, and then 
11.click Finish.
( [http://technet2.microsoft.com/windowsserver2008/en/library/9df0428f-8ea6-4e91-8531-6ce837fd5a351033.mspx?mfr=true](http://technet2.microsoft.com/windowsserver2008/en/library/9df0428f-8ea6-4e91-8531-6ce837fd5a351033.mspx?mfr=true) ) 

I'm not really convinced that this is easier, faster, more efficient, ....

---

### Post by netlogic on 2007-11-27
Well... I use both platforms. I am a consultant that means I have to cater to other IT departments wishes. MS AD does have tons of great features, but here are some issues.

1. The cost of users per seats in AD has gone up on every releases. Even you are a small shop, per seat license is very expensive. Also, the enterprise license has become extremely expensive.
2. 2008 is garbage. I have been beta testing it on my spare time. I already found few security flaws. MS must learn they shouldn't add more features until they fix the old bugs.
3. MS servers command line tools are completely broken. It doesn't even have a command line completion. That means an admin  has to understand a bit complex programming language like visual basic to write scripts. Even how simple that sounds, UNIX shell scripts are a lot easier than learning VB. Admins are admins. They aren't programmers.
4. It still bundles with a telnet server instead of sshd. You can download a free sshd server like copsshd, but it would be nice if it was integrated, so admins can fully utilize what sshd can do. However, what would be the point if the commandline tools are still completely backwards?
4. It requires reboots or reinstallation to change roles or migrate AD database. 
5. Something very little can become overly complex very quickly.
6. They really haven't re-invented their kernel in many years. Still it is very efficient compact microkernel, but it is compiled in a way, you have to reboot the server for many small task change related things. They constantly adding new apps instead of working on their cores that are still not very functional.

Linux environment isn't perfect. Reverse engineering an application that wasn't designed to work certain ways, requires tons of tweaking. It isn't the fault of Samba. MS purposely make things complex so it is harder to work with their clients. They have played these tricks in the past with Netware 4. MS  doesn't make a bad product, but  they try so hard to bundle products, so you get stuck with them for upgrades. Their focus always have been increase the profit margins instead of providing the best products that customers really want. Their intentional design of the products are excellent, but they always seem to fall through when you utilize them in the real environment. They have the technology resources to make this happen, but their MS managements probably won't let it happen.

Here is a link to how to setup Samba as PDC.

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

---

### Post by snake1130 on 2007-11-28
I have had the same problems you have had.... never the perfect HOW TO untill I found this [HowToForge]("http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller") page on setting up Samba to be a domain controller.

To add user and such you can do that via [Webalizer]("http://www.howtoforge.com/perfect_server_ubuntu7.10_p7").  Webalizer also gives you much more control over your server.

---

### Post by knorr.orange on 2007-11-28
Thanks for all the replies!  The howtoforge article looks great and I'll be working my way through that.

On the point of creating users, I agree that it doesn't look to friendly, but at least that is a one-time task (and then on-off users later.)  I don't see anything mentioned about changing passwords though.  It would be a problem if that required any sort of administrator action.  Assuming everything is set up and running, how would users change their passwords as they use their accounts?  Does it "just work" with Windows and samba taking care of it, or will some additional method be required?

---

### Post by sciurus on 2007-11-29
> **knorr.orange said:**
> Can someone explain how new users can be added and how the passwords are managed?

You can do this with [SWAT.]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html") 
Your users can even log in and change their own passwords.

You should look into [Ebox;]("http://ebox-platform.com/") it makes it very simple to do everything you want. Sadly, it isn't integrated well with ubuntu yet (should be in Hardy) but you can use their [debian installer]("http://ebox-platform.com/get/ebox_installer.iso").

---

### Post by knorr.orange on 2007-11-29
> **sciurus said:**
> You can do this with [SWAT.]("http://samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html") 
Your users can even log in and change their own passwords.

You should look into [Ebox;]("http://ebox-platform.com/") it makes it very simple to do everything you want. Sadly, it isn't integrated well with ubuntu yet (should be in Hardy) but you can use their [debian installer]("http://ebox-platform.com/get/ebox_installer.iso").

For ebox, my concern would be that if it's a turn-key solution and we need to ever do things outside of that, there is risk of breaking things.  I have not tried EBOX, but that has been my experience with similar products/configurations.

I haven't touched swat in a long time, but that's a good point.  One concern would be if it looked too complex to users.  I'll have to try it out and see I suppose.  Off hand, do you know if it can be dumbed down to have just one page asking for current user/pass and then for the new password?

---

### Post by koenn on 2007-11-29
> **knorr.orange said:**
> Assuming everything is set up and running, how would users change their passwords as they use their accounts?  Does it "just work" with Windows and samba taking care of it, or will some additional method be required?

[http://ubuntuforums.org/showpost.php?p=3842697&postcount=6](http://ubuntuforums.org/showpost.php?p=3842697&postcount=6)

---

### Post by knorr.orange on 2007-11-30
> **koenn said:**
> [http://ubuntuforums.org/showpost.php?p=3842697&postcount=6](http://ubuntuforums.org/showpost.php?p=3842697&postcount=6)

Oh boy do I feel foolish, sorry for asking the same question again!

---

