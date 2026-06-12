---
title: "Samba user authentication without a Windows server"
date: 2006-12-20
forum: Server Platforms
---

### Post by Steve Smith on 2006-12-20
I have a simple home network with an Ubuntu server and two Windows clients.  I can't find anything online that seems to describe exactly how I want authentication to work.  Rather requiring a common username on both the Ubuntu and Win machines, when you try to access a server share I'd like it to ask for a username and password.  In addition, I don't want to have to add users with smbpasswd, but instead have all users on the server automatically accessible via Samba.  When a user logs on they should then have acccess to their home directory, along with /home/shared, as long as they belong to the group 'shared', which owns that directory.

I've read bits of what I need, but I don't understand it well enough to be able to piece them together!

Thanks in advance,
Steve

---

### Post by peanut butter on 2006-12-20
what you have to do is set up a ldap server on the ubuntu box with samba. I couldent find instructions anywhere so i used debian (ubuntu's parent) with [ebox]("http://www.ebox-platform.org") using their customized installer. Im not trying to discourage you from using ubuntu, but this is automated, and is easy to install, otherwise i have no idea. I also has a Windows domain controlling capabilitys.:)

---

### Post by Steve Smith on 2006-12-21
Thanks.  I've just had a look at LDAP on the wiki and on Wikipedia, and it all looks quite elaborate for what I'm trying ot achieve!

If anyone has a simpler solution I'd be keen to hear it!

---

### Post by punx45 on 2006-12-21
if ebox comes in a .deb package you will be able to install it on ubuntu.   
even if it doesnt, most software comes in a variety of packages, and all would be available as source.

unfortunately, thats as far as i can help, as I am SAMBAless (a result of being Windowsless :D)

---

### Post by Steve Smith on 2006-12-21
Thanks!  I've botched it for now and will give it a go when I have more time.

> **punx45 said:**
> I am SAMBAless (a result of being Windowsless :D)

Lucky you...

---

### Post by punx45 on 2006-12-21
yep.. though i did consider it for a time when deciding how best to share drives with a MacBook Pro and Ubuntu desktop.   Considering the absurdity of using MS protocols on a network where no such machine existed, I decided to go with NFS over SAMBA.

---

### Post by xianthax on 2006-12-22
you need samba acting as a domain controller and you need to setup winbind to convert the windows user names to unix user ID's.

[http://www.ubuntuforums.org/showthread.php?t=280305](http://www.ubuntuforums.org/showthread.php?t=280305)

this how to is for setting up a ubuntu server to authenticate against a windows domain controller, but it includes the setup instructions for getting winbind working, from there you just need to setup the samba install to act as the domain controller.

-xian

---

### Post by dannyboy79 on 2006-12-22
> **xianthax said:**
> you need samba acting as a domain controller and you need to setup winbind to convert the windows user names to unix user ID's.

[http://www.ubuntuforums.org/showthread.php?t=280305](http://www.ubuntuforums.org/showthread.php?t=280305)

this how to is for setting up a ubuntu server to authenticate against a windows domain controller, but it includes the setup instructions for getting winbind working, from there you just need to setup the samba install to act as the domain controller.

-xian

i thought I read that a computer has a tough time beating out windows xp as the master? I know that I have tried making my ubuntu server the master browser, domain master, local master,  setting the os level really high  etc etc and no matter what, winxp pro always wins!  the other thing I then have a problem with is that when win xp isn't on, my samba network bascially fails cause there is no domain master anymore? how is this solved??? I am not trying to jack your thread because this will help you also.

---

### Post by Steve Smith on 2006-12-23
> **xianthax said:**
> you need samba acting as a domain controller and you need to setup winbind to convert the windows user names to unix user ID's.

Thanks, but will that not make an association between the current-logged-on user in XP and a user account in Ubuntu?  If so that's not what I want, I'd rather it be independent of the logged on XP user.  Could you let me know if that's what you mean.

To update to where I'm at now, when the Win XP machine tries to access a share it gives a username/password box.  Entering any user's Samba details in there logs that person on and displays their home directory.  The only thing I cannot do now is eliminate the need to do smbpasswd for each user.  I'd rather every user to have their Samba password automatically synchronised with their main account.  If they change their main password, the Samba password should change.  If I add a user to Ubuntu, they should automatically be added to Samba.

> **dannyboy79 said:**
> I am not trying to jack your thread because this will help you also.

The more the merrier, I say!

---

### Post by xianthax on 2006-12-23
if i understand what you really want to do is have single sign on to access network resources, which implys you need to setup a domain.  

my recommendation is to use samba as a domain controller...you can read more about how to set this up here:

[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/samba-pdc.html)

and the answer about the password is basicly "yes" when you log into the domain your user credentials will be used to let you access shares, etc.  basicly with domain level security there is no password to access the shares, samba checks your user credentials with the domain controller to see if you are allowed to access a resource.

depending on your conifguration and needs you may need to add additional services to your server also, (WINS, DNS, etc.)

-xian

---

