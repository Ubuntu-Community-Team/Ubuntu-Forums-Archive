---
title: "SAMABA and windows AD authentication"
date: 2010-03-16
forum: Server Platforms
---

### Post by rockercya on 2010-03-16
hi
 
i am currently working in a windows server 2003 domain environment and i want to install and configure a ubuntu server 9.10 as a samba file server and i want to allow windows domain users to access the samba shares with windows authentication from the AD , so they can use their windows user names and passwords to access samba shares.
 
i followed the wiki docs and configured kerb5.conf , smb.conf and winbind but i am unable to add the samba pc to the windows domain
 
can anyone help me on this??
 
 
thanks

---

### Post by miguel_lobos on 2010-03-16
> **rockercya said:**
> i am unable to add the samba pc to the windows domain
 
can anyone help me on this??


Is it safe to assume that you have the Windows domain administrative privileges to add a machine to the domain? Can you elaborate a little bit more on what you have tried to do to add this machine to the domain? The details are very important here, please fill us in on specifics of what you have done to add the machine to the domain.

Regards,

Lobos

---

### Post by R.Bucky on 2010-03-16
It is my understanding that the current version of Samba will not interact with Server 2003. However, Samba 5 is reported to have the capability that you are asking. I operate a similar environment with SBS 08 and a central Ubuntu 8.04 with Samba acting as a central file share. If you have few clients, you could restrict clients to folders based on IP, create another login and PW for a folder, or wait until Samba5.

---

### Post by capscrew on 2010-03-16
> **R.Bucky said:**
> It is my understanding that the current version of Samba will not interact with Server 2003. However, Samba 5 is reported to have the capability that you are asking. I operate a similar environment with SBS 08 and a central Ubuntu 8.04 with Samba acting as a central file share. If you have few clients, you could restrict clients to folders based on IP, create another login and PW for a folder, or wait until Samba5.

I believe you mean Samba 4 which is still in development.

---

### Post by rockercya on 2010-03-17
hi guys
 
thanks for all the replies,
 
i reconfigured all the files and this time i managed to add the SAMBA pc to the domain, now the SAMBA machine is listed in the active directory and 
also im able to list all the domain users and groups through the samba machin by using **wbinfo -u** and **wbinfo -g,**
 
now i want to create samba share folders in the linux machin and allow domain users to access those shares by providing their domain usernames and paswords,
 
how this could be achieved? any idea...
 
 
regards
 
chamara

---

### Post by kewlrichie on 2010-03-17
What about this [http://articles.techrepublic.com.com/5100-10878_11-5072177.html]("http://articles.techrepublic.com.com/5100-10878_11-5072177.html")

---

### Post by rockercya on 2010-03-17
i tried the link but it doesnt say much about the samba share settings,
if i want to allow windows domain users to access the samba share with their domain usernames and passwords, what should i put in the " valid users = " field ??
 
and also do i need to have local samba user accounts and passwords in the smbpasswd file?
 
 
 
 
regards
 
chamara

---

### Post by shizakapayou on 2010-03-17
Here are the two steps I followed to join my 8.04.4 to my Server 2008 active directory domain:

[https://help.ubuntu.com/community/Samba/Kerberos](https://help.ubuntu.com/community/Samba/Kerberos)
[https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

The specific settings for smb.conf are covered in there.  The valid users options is commented out in mine.

Here's one of my working share definitions:

```
[OldProjects]
        path = /home/OldProjects
        writeable = yes
        browseable = yes
        force create mode = 0770
        force directory mode = 0770
        security mask = 0777
        force security mode = 0
        directory security mask = 0777
        force directory security mode = 0
```

File system permissions on the shared folder handle group permissions.  My requirements are pretty simple, you're either a member of the group and allowed full access, or not a member and no access.  I do have acl enabled as well if needed.

---

### Post by rockercya on 2010-03-18
Hi
 
this is the settings i gave to the samba share call myshare, here to the valid users setting i have given a domain username call **cweerasinghe ,** but when i try to connect to the share by using this doman user account it gives an access denied error, 
 
[myshare]
           create mask = 0765
           comment = IT Dept share
           browseable = yes 
           printable = no
           writable = yes
           valid users = TESTDOMAIN\cweerasinghe
           public = no
           path = /MYSHARE
 
 
i have given the winbind separator as \ , so when i connect to the share i give domain credentials as **testdomain\cweerasinghe** and the domain password
 
is this the correct way of giving a domain users account to the valid users setting?
**valid users = TESTDOMAIN\cweerasinghe**
 
help please 
 
Regards
 
chamara

---

### Post by jrssystemsnet on 2010-03-18
> **R.Bucky said:**
> It is my understanding that the current version of Samba will not interact with Server 2003.Incorrect - I've got a Samba 3.40 server living happily on a Server 2003 AD right now.  It's Server 2008 that you're thinking of.


> if i want to allow windows domain users to access the samba share with their domain usernames and passwords, what should i put in the " valid users = " field ??

You don't need to set a "valid users" line at all, unless there are users or groups you specifically want to exclude from a share.

> and also do i need to have local samba user accounts and passwords in the smbpasswd file?No.

If you're going the Winbind route instead of the LDAP route, you may find my how-to article helpful: [http://ubuntuwiki.net/index.php/Samba,_Active_Directory_with_Winbind](http://ubuntuwiki.net/index.php/Samba,_Active_Directory_with_Winbind)

---

### Post by jrssystemsnet on 2010-03-18
> **rockercya said:**
> i have given the winbind separator as \ , so when i connect to the share i give domain credentials as **testdomain\cweerasinghe** and the domain password
 
is this the correct way of giving a domain users account to the valid users setting?
**valid users = TESTDOMAIN\cweerasinghe**

Yes, that's the correct syntax.  If that's not working, then you've got an error in your winbind configuration within Samba somewhere.

---

### Post by jrssystemsnet on 2010-03-18
> Originally posted by **rockercya**
*i checked the lin you ent and i have done exactly as you mentioned there, i added my samba machine to the domain and its listed in the AD,  and also *wbinfo -u* and *wbinfo -g* is also working fine , and also im able to acquire kerbaros ticket,  my problem is when i connect to the share it gives me an acess denied error*

Try commenting out the line restricting valid users.  If you don't include a "valid users" line **at all**, can you connect using a domain user's credentials?

You can check right from the console on the server by using **smbclient -U username -I 127.0.0.1 //127.0.0.1/MYSHARE** to see if it will let you access the share.

---

### Post by rockercya on 2010-03-18
hi
 
i removed the **valid users** line and then tried to connect to the samba share, this time it didnt ask for ausername or password,  I am able to access the share without providng a username or password, i want to creat separate folders in samba for  each domain user 
 
here is my nsswitch.conf file, please chk that and let me know if anything is wrong there
 
 
 
 
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.
 
passwd:         compat winbind
group:          compat winbind
shadow:         compat
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

 
 
 
regards
 
chamara

---

### Post by jrssystemsnet on 2010-03-18
I think you need "winbind" under shadow, as well.  Here is my (working, connected to Server 2003 AD) nsswitch.conf:

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```To be honest I don't really *understand* nsswitch.conf; I just cribbed from FAQs until I got it working.

---

### Post by rockercya on 2010-03-18
hi
 
i changed the shadow setting as in your nsswitch file but still its not working, 
otherthan smb.conf ,winbind and kerbaros are there any other files that needs to be configured?
 
regards
 
chamara

---

### Post by jrssystemsnet on 2010-03-18
> **rockercya said:**
> hi
 
i changed the shadow setting as in your nsswitch file but still its not working, 
otherthan smb.conf ,winbind and kerbaros are there any other files that needs to be configured?
 
regards
 
chamaraYes, at a bare minimum you also have to make CERTAIN that your machine is using the same DNS as your DCs do, and you must make CERTAIN that your system time very closely matches the system time on the DCs for the domain.

I suggest you undo everything you did and follow the guide I linked you to from top to bottom, it covers everything you need to do in order to get a working share on the domain.

The only thing it doesn't cover is the syntax for declaring a share, which looks like this (adding in your valid user restriction):

```
[sharename]
    comment = describe the share here
    read only = no
    writeable = yes
    path = /data/smbshare
    guest ok = no
    valid users = DOMAIN\username

```

Again, I would suggest that - AFTER starting over completely, and following the guide I linked from top to bottom -you start out NOT restricting valid users, and just checking to make sure that Samba successfully authenticates against the domain at all.  Once you've done that, you can add the valid users line to restrict access as you like.

---

### Post by jrssystemsnet on 2010-03-18
Hey, I just noticed this in the smb.conf file you PM'ed:

```
winbind separator = /
```

Get rid of that line.  That's a FORWARD slash you used, not a backslash... which is probably keeping DOMAIN\username from working right.  Just get rid of that line entirely, you don't need it.

---

### Post by rockercya on 2010-03-18
hi guys :D
 
thanks for all your help , finally i have managed to make samba work and authenticate from windows AD, what i had done wrong was i had given the valid user values in under the share settings in the smb.conf file as **TESTDOMAIN\domainuser** and i guess thats why the domain users couldent get authenticated from the windows AD, 
 
i installed webmin , and then created samba shares and gave valid user values from webmin, then i tried to connect to the samba shares and it workd fine, when connecting i didnt give the domain name with a winbins separator
 
eg : TESTDOMAIN\username,
 
i Just typed the domain user name and the password and it worked,
after doing that  the share setting in my smb.conf file looked like this
 
[B][IT]
        comment = IT Share
        valid users = cweerasinghe,trandombage,njayarathna
        path = /ITSHARE[/B]
 
here the valid user names are separated by commas, so i guess the way i gave valid user values in the SMB.CONF file could be the reason why it didnt work
 
 
regards
 
chamara

---

### Post by jrssystemsnet on 2010-03-18
It wasn't working because you had set the winbind separator to forward slash, but you were writing fully qualified domain usernames with a backslash.  Had you not changed the winbind separator, **DOMAIN\user** would have worked fine as well.

You should really get set up so that fully qualified names work, otherwise you may have problems if you have overlap in namespace between the local system and the domain.

Also, please mark the thread **[SOLVED]** if your problem is fixed, to help others find answers. :)

---

### Post by rockercya on 2010-03-22
hi
 
i changed the winbind separator to \, but when it is changes i cant access the shares,

now i have a nother problem with users permissions, i cant allow yours to write to samba shares unless the directory is defined as bublic shares eoth the **public = yes** setting, 
 
any idea about how to let only certain usrs to give permissin to write to share folders??

---

