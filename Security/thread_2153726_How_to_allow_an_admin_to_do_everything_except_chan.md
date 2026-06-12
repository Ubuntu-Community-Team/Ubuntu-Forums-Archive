---
title: "How to allow an admin to do everything except changing password of another admin : Ub"
date: 2013-06-12
forum: Security
---

### Post by solarinside on 2013-06-12
Hi everyone,

I need some help about Ubuntu 12.04.

I would like to make some "levels" for a multi-session Ubuntu PC. For example, having 3 groups :
[LIST]
[*]  Admin 0  // Contents the first one who has been created and has the right to be root
[*]  Admin 1  // The second one, has the right to do everything (root) but not changing password of the one who is in the Admin 0 group      
[*] Admin 2  // Those in this group are only allow to install.  Their passwords should be changed by those who are in Admin 1 
[*]
[/LIST]

  After some searches, i've found that it's possible to allow or to  forbid a group to do something with visudo, editing the sudoers file.  And my Admin 0 refers to the %admin of this sudoers file.

Nevertheless, i don't know which command adding.

 I would like to add something like that : 
[LIST]
[*]
[*] %Admin 1 ALL = (root) PASSWD: /here the path to the file wich allows or not the modify password/
[*]
[/LIST]


  What do you think about it? I don't know what is the file which is concerned in this case. Also, what should i had to allow the Admin 1 group to modify password of the Admin 2 group?


  Thanks for your answers.


  Nicolas

---

### Post by Lars Noodén on 2013-06-12
The level Admin1 can't really be achieved because it's not possible to select by negation in Sudo, only by inclusion.  However, the level Admin 2 can be done easily by adding the right programs, at least for the text interface.

```

%admin2 ALL=(ALL) PASSWD: /usr/bin/apt-get

```

Though there might be a way for them to get around that with 'apt-get -c' but that would require deliberate planning on their part and means you have a social problem not a technical problem. 

About which programs you need to add for the graphical Software Center, that's a bit harder to figure out.

---

### Post by solarinside on 2013-06-12
Hi Lars Noodén,

Thanks a lot for your quick answer.
So, if i understand well, it's not possible to forbid an admin to change the password of another admin? 

I thought that PASSWD was link to the ask of the password, so i write this command  


%admin2 ALL=(ALL) PASSWD: /usr/bin/apt-get

That will ask a password for installing or that will just not ask one? And which password, the one of those who are trying to install, or an admin password?

---

### Post by Lars Noodén on 2013-06-12
It's not possible to forbid an admin from changing the password of another admin if that first admin has full access to the system.  You can try blocking access to /usr/bin/passwd with sudoers, but then the malicious admin could always copy the file to a new name and then run that.

```

%admin2 ALL=(ALL) PASSWD: /usr/bin/apt-get

```
That will allow any user in the group *admin2* to install or remove software using [apt-get](http://manpages.ubuntu.com/manpages/raring/en/man8/apt-get.8.html).  They will have to type their own password first.  Then there is a period that they can continue to use sudo without a password until the timestamp_timeout interval is hit.  See the manual page for sudoers(5) for the details, but the default is 15 minutes.  If you change PASSWD: to NOPASSWD: then they can run the subsequent programs without needing to enter their own password.  

In addition to specifying a program, you can limit the account to using specific options:

```

%helper ALL=(ALL) NOPASSWD: /sbin/ifconfig eth0 *

```

That would allow users in the group *helper* to run ifconfig but only when working with eth0.

---

### Post by solarinside on 2013-06-12
I've thought about this solution to forbid the access to /usr/bin/passwd (but is it directly link to /etc/shadow ?). Nevertheless, i'll probably risk to not be able to connect with a member of the admin 1 group if he doesn't have the right to access to the password folder?

Also, if they are in "sudo mode" (for the admin2 group), they are only able to install with an apt-get, but they're not able to do other things, no?

Last, what is eth0??

Perhaps, should i be able to forbid the admin1 group to launch the exec or file which allows to change a password?

---

### Post by Lars Noodén on 2013-06-12
> **solarinside said:**
> I've thought about this solution to forbid the access to /usr/bin/passwd (but is it directly link to /etc/shadow ?). 


Then all they'd need to get around that is to copy /usr/bin/passwd to /usr/local/bin/chpassword and run that.  Negation cannot work with sudo.  You  have to find rules that do what you want working inclusively.

> **solarinside said:**
> Nevertheless, i'll probably risk to not be able to connect with a member of the admin 1 group if he doesn't have the right to access to the password folder?

Also, if they are in "sudo mode" (for the admin2 group), they are only able to install with an apt-get, but they're not able to do other things, no?


If the only program listed for their account is apt-get, then that's all they can run.  If you want you can get very specific about which programs they actually can run and even which parameters and options they are allowed to use.  Read the manual page for [sudoers](http://manpages.ubuntu.com/manpages/raring/en/man5/sudoers.5.html) especially the section about "Wildcards"

> **solarinside said:**
> 
Last, what is eth0??

Perhaps, should i be able to forbid the admin1 group to launch the exec or file which allows to change a password?

eth0 is the first ethernet interface, it's a common network interface found on connected systems and thus a good example.

---

### Post by solarinside on 2013-06-12
Well perhaps it's possible to forbid a member of the admin 1 to not copy /bin/password, isn't it?

---

### Post by Lars Noodén on 2013-06-12
In addition to cp, there's tar, cpio, rsync, dump/restore, zip, gzip, bzip2, grsync, and many, many more.  You'd then have to figure out all the combinations that would prevent running a copy of /usr/bin/passwd or /bin/su or overwriting /etc/shadow.  It might be doable but the sudoers file would be thousands of lines long at least and one mistake would let loose the whole zoo.  In practice it's not possible to use negation to control access with sudo.  Better to use the honor system.  Either they are reliable and worthy of full root, or else just give them access to specific individual programs one at a time.

---

### Post by solarinside on 2013-06-12
Ok, I see, very difficult!

Someone has suggested me this command : 


%admin1   ALL = !/usr/bin/passwd

But he is agree with the fact that if can't change the root password, it should be impossible for an admin1 to change the password of an admin2...

---

### Post by Lars Noodén on 2013-06-12
> **solarinside said:**
> Someone has suggested me this command : 
%admin1   ALL = !/usr/bin/passwd


That case is covered in the description above.  Several ways around it:

sudo /bin/bash
passwd admin2

Or

sudo cp /usr/bin/passwd /usr/local/bin/passwd
sudo /usr/local/bin/passwd admin2

Or 

sudo su -c "passwd admin2"

And so on and so forth.

---

### Post by solarinside on 2013-06-12
Well, and just forbid the cp command on only one directory?

---

### Post by Lars Noodén on 2013-06-12
If cp is blocked then there would be tar and the others mentioned above.  

tar cf - /bin/cp | (cd /tmp/; tar xf -);
sudo /tmp/bin/cp a b

I'm not sure if there are infinite combinations but it approaches infinity.

The one way that does work is to make a list of the allowed applications.

---

