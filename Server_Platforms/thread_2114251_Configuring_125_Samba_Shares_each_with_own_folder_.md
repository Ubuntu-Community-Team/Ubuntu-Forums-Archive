---
title: "Configuring 125 Samba Shares each with own folder and password"
date: 2013-02-09
forum: Server Platforms
---

### Post by dhabaarsotech on 2013-02-09
Hey,  I've been trying to accomplish this diy project for the past week and have run into a few setbacks so I figured I seek some assistance.   

Objective: To create 125 student folders shared on windows 7 computers all with their own unique password on each unique folder.    

Where I've gotten so far: I have set up a samba server and created a shared folder for students to save work into temporarily.  This has worked fine, however I occasionally run into the issue of the windows computers not finding the server.  I have my server set up on a unique ip address as well as the windows 7  computers configured as home networks with file sharing on. I still cannot to seem to figure why the server does not always appear.   I hope this is possible and students are able to save files simultaneously with their own password on their own folder that is visible on the network.   

I understand this may take me sometime but it would make my life and the life of some very bright young African students as well.   Any advice on how to begin this would be extremely helpful.   


Thanks!

---

### Post by tgalati4 on 2013-02-09
Do you have the Ubuntu file server configured as a WINS server?  What version of Ubuntu are you running?

Does each student have an account on the server?

```
man useradd
```

User home directories are automatically created as you add each user.  You can override that with the -d switch.

The real trick is to query each Windows machine to get the user's name and automatically add them to the user accounts.

---

### Post by dhabaarsotech on 2013-02-10
I'm running ubuntu 12.04 LTS and do not have samba configured as a WINS server.  I've manually added the students accounts under system settings: user accounts. Is there a difference between doing this and adding them via command line?

---

### Post by bab1 on 2013-02-10
> **dhabaarsotech said:**
> I'm running ubuntu 12.04 LTS and do not have samba configured as a WINS server.  
You don't need a WINS server on a single segment LAN (e.g. one subnet).> 
I've manually added the students accounts under system settings: user accounts. Is there a difference between doing this and adding them via command line?
No. They both achive the same goal.  Using the proper CLI command in a script would be helpful in the future.

If you have all the users added, and they have home directories, you can use the [homes] share to create each users private share.  You only need to create one (1) [homes] share.  Samba will create the shares for the individual users.  You need to add all the users to the samba user database with this command```
smbpasswd -a $NEW_USER
```...use the individual user login name where is says $NEW_USER.  

You can see the user in the database with this command```
sudo pdbedit -L
```

You can read some info on [homes] directories [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.samba.org/samba/docs/using_samba/ch09.html").  The information is under the heading "Handling Multiple Individual Users".

---

### Post by Morbius1 on 2013-02-10
> Where I've gotten so far: I have set up a samba server and created a  shared folder for students to save work into temporarily.  [COLOR=Blue]This has  worked fine, however I occasionally run into the issue of the windows  computers not finding the server.  I have my server set up on a unique  ip address as well as the windows 7  computers configured as home  networks with file sharing on.[/COLOR] I still cannot to seem to figure why the  server does not always appear.The real problem seems to be reliably "seeing" the server from the client. You can try rearranging the name resolve order on the server:
```
name resolve order = bcast host lmhosts wins
```Add that line under the wrokgroup line in smb.conf and then restart smbd and nmbd.

But since it appears that the server has a static ip address you would think it would be possible to just "map" the share in the Windows client using the servers ip address.

---

### Post by dhabaarsotech on 2013-02-18
Thanks I've now mapped the drive and added name resolve order = bcast host lmhosts wins to my samba configuration file.  It seems to have resolved the issue of the the windows clients not finding the server. 

I've only made accounts for 10 students so I can test them before adding the whole lot.   

I've made a main shared folder called Student Files (the one I've mapped) that has three folders inside 10th, 11th and 12th. 

 I've added the 10 different student folders in the 10th grade folder.  Using the Samba Server Configuration gui I've mapped the students shared folders with their accounts. However, it still does not ask me to enter a password when viewing the students mapped shared folders.  I'm guessing this has something to do with my directory order?

When making the folders shared in ubuntu I've right clicked on the folder click properties and then share this folder then modify this share.  In samba configuration gui I've added the users.  Then set up a share by adding a new share and only giving access to the student whose folder the share is set up with.  

The issue is that I can still view all of the student's folders and not get asked for a password and user name when trying to access each individual folder.

---

### Post by PowerBarry43 on 2013-02-18
Hi

Sounds to me like you need to set the student's user as the owners of their folder and make the folder permissions 770 so owners and group members can read and write but nobody else eg:

```
chown student1 /path/to/folder
chmod 770 /path/to/folder
```

you may need to set the create mask option to 0770 in your smb.conf file too, the default is 0755 which is world and group read and execute and only owner write.

hope this helps!

Barry

---

### Post by Morbius1 on 2013-02-18
> I've added the 10 different student folders in the 10th grade folder.   Using the Samba Server Configuration gui I've mapped the students shared  folders with their accounts. However, it still does not ask me to enter  a password when viewing the students mapped shared folders.  I'm  guessing this has something to do with my directory order?There is someting a Windows samba client does that Linux client does not. When a Windows client browses the network it automatically and without the Windows user's knowledge passes that users Windows login user name and password to the server. If you created users on your Samba server that match the Windows users name and then created samba passwords that match the Windows login password authentication has already taken place and accepted without a prompt. 
> When making the folders shared in ubuntu I've right clicked on the  folder click properties and then share this folder then modify this  share.  In samba configuration gui I've added the users.  Then set up a  share by adding a new share and only giving access to the student whose  folder the share is set up with.  Now that could be another problem. You created 2 shares of the same folder using 2 different methods at the same time. It's possible one conflicts with the other.

Samba Classic shares are in /etc/samba/smb.conf.
Samba Usershares are in /var/lib/samba/usershares.

Take a look at the output of the following command to see how these Nautilus created shares are configured:
```
net usershare info --long
```

---

### Post by chrisguk on 2013-02-18
Wouldn't it be easier to setup an FTP server and give each user their own space.  As you said the server has a static IP so I guess you could create DNS and then students could use the hostname.  You don't have to worry about persistent connections etc then unless you want them to use this space as an extended hard drive thats always there.

So if I have read right you just want them to store files in much the same way as a cloud service.  FTP would be my choice for many reasons I think not to mention the security aspect is easier to control.  Samba works for many but in my lab it just serves files I use on a media player.

---

### Post by dhabaarsotech on 2013-02-18
Barry,

Thanks for the reply. I've done exactly what you said and now have run into the error in windows saying windows cannot access then the path of the folders location. 

Thanks

Dan

---

### Post by dhabaarsotech on 2013-02-18
> Wouldn't it be easier to setup an FTP server and give each user their  own space.  As you said the server has a static IP so I guess you could  create DNS and then students could use the hostname.  You don't have to  worry about persistent connections etc then unless you want them to use  this space as an extended hard drive thats always there.

So if I have read right you just want them to store files in much the  same way as a cloud service.  FTP would be my choice for many reasons I  think not to mention the security aspect is easier to control.  Samba  works for many but in my lab it just serves files I use on a media  player. 

Originally, the the lab was set up with an FTP server until recently somehow the configuration file was erased. I did not do the original configuring and it was all done using filezilla on a windows machine.  Most of the students became fairly familiar with using the server however many are new computer users and find the process a bit difficult. I figured having their own folder/password would be a bit easier for having them save files to the server.  

If I were to start again with creating an FTP server in ubuntu what might be the easiest client to use and the least time consuming for creating 120 accounts/passwords?  

I figured the samba method may be a bit more time consuming on my part but would be overall be easier for the students in the long run.   Yes I kind of am going for a cloud-like solution.  It would also make it easier for students with their own laptops requiring less configuring on their part. 

This can't  be the first time this has been done for a student server. I've researched quite a bit but finding information that you don't have to seed through pages of manuals is quite difficult.  I would like to stay away from the FTP method if at all possible but if this is going to turn into a huge headache then it may be better to revert back to the original method.

---

### Post by Morbius1 on 2013-02-18
[COLOR=Blue]*If you are still considering a Samba solution:*[/COLOR]

The more I think about this I think you are going to have to remove the shares you created through Nautilus and I'll give you an example why:

Let's say you created a classic samba share that looks like this:
> [morbius]
path = /StudentFiles/10thGrade/Morbius
read only = No
valid users = morbius[COLOR=Blue]*Only one person will gain access to that share and that's morbius. If  you set the samba password for morbius to match his login password on his Win7 box then he will gain access without being asked for credentials.*[/COLOR]

Then you create a share of the same folder in Nautilus - the share as described in the output of the "net usershare" command would look something like this:
> [morbius]
path=/StudenFiles/10thGrade/Morbius
comment=
usershare_acl=Everyone:F,
guest_ok=n[COLOR=Blue]*There is no such thing as a "valid users" in the kind of shares created by Nautilus. That share becomes available to anyone that has a valid user name and password.*[/COLOR]

Now the question is which share definition is Samba taking orders from and it's the reason why you shouldn't create shares on the same target using both methods at the same time.

---

### Post by SeijiSensei on 2013-02-18
I think it would much easier to simply give each student a normal account with a home directory and share [homes] with Samba.  Is there a reason they need to grouped into a separate directory?  If you want to let students within the same grade share files, create three groups "g10", "g11" and "g12" assign the students to the appropriate group with adduser:

```
adduser --gid g10 username-of-tenth-grader
```

If you would prefer to have each student have a personal group, as is the default, then you can edit the two EXTRA GROUPS directives in /etc/adduser.conf to put them in an additional grade-level group with --add_extra_groups: 

```
adduser username-of-eleventh-grader --add_extra_groups
```

Then repeat the process with smbpasswd.

There are ways to set up a user with a password from the command prompt, but they are a bit tricky.  A Google search will bring up some examples.  That technique allows you to write a script that reads a file of usernames and passwords to create all the users at once.

---

### Post by Morbius1 on 2013-02-18
+1

With 125 users a [homes] share will be the only way to maintain your sanity. The general form looks something like this:
> [homes]
comment = Home Directories
valid users = %S
read only = No
create mask = 0700
directory mask = 0700
browseable = NoYou will notice that it has no path because by definition it points to a particular user's ( valid users = %S ) home directory. Also note that it is tagged as not browsable. A given Windows user will only see his own share and not the other 124.

So for each new student you create a local user on the server ( with his own home directory ), create a samba password for that user, and you're done.

---

### Post by dhabaarsotech on 2013-02-18
Ok, so I've changed my home share settings and will look for a script to add a bunch of users at once.  

The main reason why I wanted to create a directory called 10th grade was to make it easier for the students when they want to find their folder.   My overall goal is to have a shortcut on the desktop that links to the server where when opened will have a folder for each grade and in each folder the students name with their shared folder that is password protected.  

I'm still a little confused though.  After I changed the share home directory settings. I still do not see each user appear on my server on the windows computers.  Should they just appear on the windows machines or do I have connect to them a certain way?

---

### Post by Morbius1 on 2013-02-18
> I'm still a little confused though.  After I changed the share home  directory settings. I still do not see each user appear on my server on  the windows computers.  Should they just appear on the windows machines  or do I have connect to them a certain way?     If the user name and passwords match then the share MORBIUS will appear in the list. If the name is the same but the password is different then morbius will be prompted for a password before the share is visible.

---

### Post by Morbius1 on 2013-02-18
If you are still having issues please post the output of the following command:
```
smbtree -U morbius
```** Change morbius to one of your user's names.
** When it asks for a password give it the samba password for that user.

There should be a listing named: morbius ( or that user's name ) in the list of shares.

If not post the output of this command:
```
ls -al /home
```And this one:
```
testparm -s
```

---

### Post by dhabaarsotech on 2013-02-18
this is for the user Jamaal Maxamed:

>  
smbtree -U morbiusWORKGROUP
    \\TEACHER                Teacher server (Samba, Ubuntu)
        \\TEACHER\Grade 12           
        \\TEACHER\Abdi Aziz Se'eed    
        \\TEACHER\Grade 10           
        \\TEACHER\Student Files      
        \\TEACHER\Grade 11           
        \\TEACHER\Abdirahman Muuse    
        \\TEACHER\print$             Printer Drivers
        \\TEACHER\IPC$               IPC Service (Teacher server (Samba, Ubuntu))
    \\LAB-19                 Lab-19
    \\FWINDOWS-PC

> 
ls -al /home
teacher@Teacher:~$ ls -al /home
total 64
drwxr-xr-x 16 root                      root                      4096 Feb 18 22:39 .
drwxr-xr-x 23 root                      root                      4096 Feb  2 02:00 ..
drwxr-xr-x  2 abdiazizseeed             abdiazizseeed             4096 Feb  1 23:55 abdiazizseeed
drwxr-xr-x  2 abdirahmanmuuse           abdirahmanmuuse           4096 Feb  1 23:56 abdirahmanmuuse
drwxr-xr-x  2 hamdaahmedmohamed         hamdaahmedmohamed         4096 Feb  1 23:56 hamdaahmedmohamed
drwxr-xr-x  2 hamsefaisalabdi           hamsefaisalabdi           4096 Feb  1 23:56 hamsefaisalabdi
drwxr-xr-x  2 ibrahimmusemohamed        ibrahimmusemohamed        4096 Feb  1 23:56 ibrahimmusemohamed
drwxr-xr-x  2 jamaalmaxamed             jamaalmaxamed             4096 Feb  1 23:56 jamaalmaxamed
drwxr-xr-x  2 liibaanabdirahmanabdilahi liibaanabdirahmanabdilahi 4096 Feb  1 23:57 liibaanabdirahmanabdilahi
drwxr-xr-x  2 mohammedclaahi            mohammedclaahi            4096 Feb  1 23:57 mohammedclaahi
drwxr-xr-x  2 nadiamahamoudabdilahi     nadiamahamoudabdilahi     4096 Feb  1 23:57 nadiamahamoudabdilahi
drwxr-xr-x  2 rodaahmedmohamed          rodaahmedmohamed          4096 Feb  1 23:57 rodaahmedmohamed
drwxr-xr-x  2 saleebaanali              saleebaanali              4096 Feb  1 23:57 saleebaanali
drwxr-xr-x  2 shabcaanmahamedcali       shabcaanmahamedcali       4096 Feb  1 23:57 shabcaanmahamedcali
drwxr-xr-x  2 shukriahmedali            shukriahmedali            4096 Feb  1 23:58 shukriahmedali
drwxr-xr-x 31 teacher                   teacher                   4096 Feb 18 22:20 teacher

> 
testparm -s
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = bcast host lmhosts wins
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by Morbius1 on 2013-02-18
You have no [homes] share defined. If your intent is to use the [homes] share then you need to add it to /etc/samba/smb.conf:
```
[homes]
comment = Home Directories
valid users = %S
read only = No
create mask = 0700
directory mask = 0700
browseable = No                      
```Then restart samba:
```
sudo service smbd restart
```Your other shares must have been created through Nautilus. The output of the following command will verify that:
```
 net usershare info --long
```

---

### Post by dhabaarsotech on 2013-02-18
I was almost 100 percent positive I had the home shares defined.  This will be the third time I've edited my smb config file today and added that same information. I just did exactly what you said restarted and then checked again to make sure it was there and it was so hopefully it will stay there.  Here is the output from 

net usershare info --long



[Grade 12]
path=/home/teacher/Desktop/Student Files/Grade 12
comment=
usershare_acl=Everyone:R,TEACHER\(null):F,
guest_ok=y

[Abdi Aziz Se'eed]
path=/home/teacher/Desktop/Student Files/Grade 10/Abdi Aziz Se'eed
comment=
usershare_acl=Everyone:R,TEACHER\(null):F,
guest_ok=n

[Grade 10]
path=/home/teacher/Desktop/Student Files/Grade 10
comment=
usershare_acl=Everyone:R,TEACHER\(null):F,
guest_ok=y

[Student Files]
path=/home/teacher/Desktop/Student Files
comment=
usershare_acl=Everyone:R,TEACHER\(null):F,
guest_ok=y

[Grade 11]
path=/home/teacher/Desktop/Student Files/Grade 11
comment=
usershare_acl=Everyone:R,TEACHER\(null):F,
guest_ok=y

[Abdirahman Muuse]
path=/home/teacher/Desktop/Student Files/Grade 10/Abdirahman Muuse
comment=
usershare_acl=Everyone:R,TEACHER\(null):F,
guest_ok=n

---

### Post by Morbius1 on 2013-02-18
> I was almost 100 percent positive I had the home shares defined.  This  will be the third time I've edited my smb config file today and added  that same information.That's why < fill in the name of your personal diety > ceated the "testparm -s" command. To see if what you changed is what Samba thinks you changed.

In my option all of those shares created through Nautilus should go. Usershares are great in a peer-to-peer type of environment in a home lan but when you have 100+ clients things get messy.

For example, this share allows everyone and your Aunt Tilly to have full access:
> [Student Files]
path=/home/teacher/Desktop/Student Files
comment=
usershare_acl=Everyone:R,TEACHER\(null):F,
guest_ok=yThis share allows authenticated users only ( and not just Abdi Aziz Se'eed ) :
> [Abdi Aziz Se'eed]
path=/home/teacher/Desktop/Student Files/Grade 10/Abdi Aziz Se'eed
comment=
usershare_acl=Everyone:R,TEACHER\(null):F,
guest_ok=n
But all the user has to do is go through the [Student Files] share and he has access to everytning under /home/teacher/Desktop/Student Files.

Unless the [homes] share doesn't do what you want I'd go back into Nautilus and just unshare them.

---

### Post by dhabaarsotech on 2013-02-18
That makes a lot of sense.  Hence why when I somehow had it working earlier for a bit I could log onto Abdi Aziz Se'eed's account and then still access other students folders even though I did not even log into their folder.  I'll stop sharing everything in Nautilus then.  I just like the directories because they kept the student's accounts organized and made it easier for them to find.   So what's next then? I've added home shares to my smb config file.  Should the students shares start appearing? How can they log into their home directories in windows? And does this mean that since they can log into their home directory it will have other directories in their share such as documents and music etc?

---

### Post by Morbius1 on 2013-02-18
> I've added home shares to my smb config file.  Should the students shares start appearing?** Run the following command and pass the correct samba password:
```
smbtree -U abdiazizseeed
```You should get a listing named: abdiazizseeed

** From Windows it will be the same thing. 
> How can they log into their home directories in windows?If you created an exact match in name and samba password to the Windows login they don't have to login in. Let me be more explicit:

I am a Windows user. I log into my WIndows box with the user morbius and a password morbiuspw. If you create a server user named morbius and gave him a samba password = morbiuspw:
```
sudo smbpasswd -a morbius
```Then when I browse the network I will have automatic access to my home directory. If the name matches but the samba password does not them I will have to pass the correct password.
> And does this mean that since they can log into their home directory it  will have other directories in their share such as documents and music  etc?     Yes.

---

### Post by SeijiSensei on 2013-02-18
Depending on the number of machines involved, you might want to consider setting Samba up as a "[domain controller]("http://www.techrepublic.com/blog/itdojo/set-up-samba-to-serve-as-a-domain-controller/3135")."  Then you can control what happens when users log in.  For instance, you could force the running of a script on the Windows boxes that maps H: to \\server\username and creates a mapping to their home directories automatically.  If you only have a few machines, you can install a script on each of them to run "net use H: \\servername\%USERNAME%" after login to mount the share.

---

### Post by koenn on 2013-02-18
I'm all for using home shares in this case, same reasons as others have mentioned.


>  just like the directories because they kept the student's accounts organized and made it easier for them to find.

this shouldn't be a problem - home shares done right will be accessible as \\TEACHER\username so the users don't need to 'know how to find' their home.



Small addition : you *can* set a path for home directories/shares. iirc it's mentioned somewhere in the smb.conf file; you can comment that out and redefine it in your [homes] definition. In your case, maybe something like 
```
path = /home/teacher/Desktop/StudentFiles/%S  
```
where samba will replace **%S** with the username of the relevant user.
(personally, I'd prefer something like /srv/students/... i.s.o /home/teacher/... )

The folders must exist, but I don't think the actually have to be the linux user account's home dir. Although that's probably a good idea anyway, if only to get the permissions on the folders correct. setting the home dir can be done with an option to the useradd comment. 

And if you have to do this 125 times, it's probably a good idea to create a small script for it.

---

### Post by dhabaarsotech on 2013-02-19
> 
If you created an exact match in name and samba password to the Windows login they don't have to login in.


I really would like them to have to log in. I'm guessing if I don't make their samba password match the same as their windows login then this can happen.

> 
Then when I browse the network I will have automatic access to my home  directory. If the name matches but the samba password does not them I  will have to pass the correct password.
 	Quote:
 	 	 		 			 				And does this mean that since they can log into their home directory  it  will have other directories in their share such as documents and  music  etc? 			 		 	 	 
Yes.


This is one of the reasons why I did not want to share homes.  Having less directories in their share the better.  I only want to have one folder with their name on it and nothing else inside except their student files.

I'm confused on why this is such a difficult process. I wouldn't think that creating a folder that is password protected on a server would be incredibly hard. I guess for 125 people it might be but it still does not seem like it would be an incredibly strenuous process. 

What I don't understand is that in nautilus/samba it seemed to work fine. The only problem I ran into was one creating samba accounts in the configuration gui the accounts needed to be linked to an account on the local linux server.  If I could just create as many samba accounts as I wanted then link to their own share then I would be ok.

All of the windows machines are running deep freeze so saving files for the students locally won't work.  I just want a shortcut on the desktop linking to the server where each folder has their name and an individual password.  The easier for the students the better. The less they have to remember other than clicking on a folder and entering a password the easier my job is. 

Samba seemed like a great solution but I'm really considering going back to FTP.  It was actually quite easy until the password part came into play.  I would hesitate but some of these kids are so bad they tend to delete other peoples work by an accident or even on purpose.  

Any other suggestions on this process would be greatly appreciated. Thanks for all the help already.

---

### Post by bab1 on 2013-02-19
> **dhabaarsotech said:**
> I really would like them to have to log in. I'm guessing if I don't make their samba password match the same as their windows login then this can happen.



This is one of the reasons why I did not want to share homes.  Having less directories in their share the better.  I only want to have one folder with their name on it and nothing else inside except their student files.

I'm confused on why this is such a difficult process. I wouldn't think that creating a folder that is password protected on a server would be incredibly hard. I guess for 125 people it might be but it still does not seem like it would be an incredibly strenuous process. 

What I don't understand is that in nautilus/samba it seemed to work fine. The only problem I ran into was one creating samba accounts in the configuration gui the accounts needed to be linked to an account on the local linux server.  If I could just create as many samba accounts as I wanted then link to their own share then I would be ok.

All of the windows machines are running deep freeze so saving files for the students locally won't work.  I just want a shortcut on the desktop linking to the server where each folder has their name and an individual password.  The easier for the students the better. The less they have to remember other than clicking on a folder and entering a password the easier my job is. 

Samba seemed like a great solution but I'm really considering going back to FTP.  It was actually quite easy until the password part came into play.  I would hesitate but some of these kids are so bad they tend to delete other peoples work by an accident or even on purpose.  

Any other suggestions on this process would be greatly appreciated. Thanks for all the help already.
The Samba [homes] directory is not the same as the Linux /home directory.  They can be used together but the two items are not the same thing.

You DO NOT need to use /home/<user_name> as the home directory for any Linux user you create.  If you wanted a home directory structure like this```
/srv/10th/<student_name> 
```...you could do that.  The homes share would show up as //SERVERNAME/<student_name>.  

When you create the user you have the ability to define the home directory.  The share always is //SERVERNAME/folder, not "path to the folder".  Samba shares do not display the file system hierarchy at all.

Using the command line (no matter how painful it seems) is worth while.  You get to control with precision the user structure.  Later (as previously posted) you can script this and the project won't be so painful going forward.

IMO Samba usershares won't work at all for what you want.  Neither will using a GUI interface work.  I would learn to use the "[COLOR="Blue"]adduser[/COLOR]" CLI tool rather than "[COLOR="Red"]useradd[/COLOR]" tool.  It is more Debian/Ubuntu centric in it's defaults, but either one will work if you insist and want to set the proper parameters yourself.

[COLOR="Blue"]Edit:[/COLOR]> What I don't understand is that in nautilus/samba it seemed to work fine. The only problem I ran into was one creating samba accounts in the configuration gui the accounts needed to be linked to an account on the local linux server. If I could just create as many samba accounts as I wanted then link to their own share then I would be ok.[COLOR="Blue"]
Samba usershares are specifically for the creation of shares by ***non-root users***.  The only permissions are the user or everyone.  This of course is not appropriate for a system that is administered centrally.  The GUI doesn't have enough options to do what you want.  You need to edit the smb.conf file by hand (if you add custom home dir) as well as  adding the users.
[/COLOR]

---

### Post by Morbius1 on 2013-02-19
> I'm confused on why this is such a difficult process. I wouldn't think  that creating a folder that is password protected on a server would be  incredibly hard. I guess for 125 people it might be but it still does  not seem like it would be an incredibly strenuous process. It's not. Here you go:
> [morbius]
path=/home/teacher/Desktop/Student Files/morbius
read only = no
guest ok = no
valid users = morbiusIn order to pull that off though you need to do certain things:
** You need to create the morbius user.
** You need to add him to the samba password database.
** You need to create the /home/teacher/Desktop/Student Files/morbius folder.
** You need to chown the directory so that it's accessible to morbius
[COLOR=Blue]** And you need to do that 125 times[/COLOR]
> What I don't understand is that in nautilus/samba it seemed to work  fine. The only problem I ran into was one creating samba accounts in the  configuration gui the accounts needed to be linked to an account on the  local linux server.No it did not work fine. The Nautilus-share method has no way to recreate the "valid users" limiter in it. The shares will be available to everyone with a valid samba password not just morbius.
 > [QUOTE]If you created an exact match in name and samba password to the Windows login they don't have to login in.I really would like them to have to log in. I'm guessing if I  don't make their samba password match the same as their windows login  then this can happen.[/QUOTE]With a username / password match a passing of credentials and a login is taking place but it's taking place automatically without the users intervention. That's a peculiarity of a Windows client.

The use of the special [homes] share was an attempt to relieve you of creating a unique share for every one of your 125 clients. You could use it with a path as described above:
> [homes]
comment = Home Directories
path = /home/teacher/Desktop/Student Files/%S
valid users = %S
read only = No
create mask = 0700
directory mask = 0700
browseable = NoBut then:
** You need to create the /home/teacher/Desktop/Student Files/morbius folder.
** You need to chown the directory so that it's accessible to morbius
[COLOR=Blue]** And you need to do that 125 times[/COLOR]
> This is one of the reasons why I did not want to share homes.  Having  less directories in their share the better.  I only want to have one  folder with their name on it and nothing else inside except their  student files.Then do as bab1 suggested and create each user a special way ( [COLOR=Blue]bab1, sorry, I'm going with what I'm familiar with[/COLOR]. [COLOR=Blue]Feel free to convert to a better way if appropriate[/COLOR] ). Create each new user as follows:
```
sudo useradd -m -k /dev/null morbius
```The user will be created without a local login to the server itself and have a home directory that is blank. Now you can go back to using the standard [homes] share without a path and the client will see an empty folder when he accesses it.

---

### Post by bab1 on 2013-02-19
> **Morbius1 said:**
> It's not. Here you go:
In order to pull that off though you need to do certain things:
** You need to create the morbius user.
** You need to add him to the samba password database.
** You need to create the /home/teacher/Desktop/Student Files/morbius folder.
** You need to chown the directory so that it's accessible to morbius
[COLOR=Blue]** And you need to do that 125 times[/COLOR]
No it did not work fine. The Nautilus-share method has no way to recreate the "valid users" limiter in it. The shares will be available to everyone with a valid samba password not just morbius.
 With a username / password match a passing of credentials and a login is taking place but it's taking place automatically without the users intervention. That's a peculiarity of a Windows client.

The use of the special [homes] share was an attempt to relieve you of creating a unique share for every one of your 125 clients. You could use it with a path as described above:
But then:
** You need to create the /home/teacher/Desktop/Student Files/morbius folder.
** You need to chown the directory so that it's accessible to morbius
[COLOR=Blue]** And you need to do that 125 times[/COLOR]
Then do as bab1 suggested and create each user a special way ( [COLOR=Blue]bab1, sorry, I'm going with what I'm familiar with[/COLOR]. [COLOR=Blue]Feel free to convert to a better way if appropriate[/COLOR] ). Create each new user as follows:
```
sudo useradd -m -k /dev/null morbius
```The user will be created without a local login to the server itself and have a home directory that is blank. Now you can go back to using the standard [homes] share without a path and the client will see an empty folder when he accesses it.
I would just point out that when you declare the home directory (/srv/something) and stop login with /bin/false as the shell, you automatically create the home directory (saves work) and can leave the [homes] share pretty much as the default.  I believe Samba scans the /etc/passwd to determine the home directory like this ```

homer:x:2086:2086:Homer Simpson,,,:**[COLOR="Red"]/srv/10/homer[/COLOR]**:[COLOR="Blue"]/bin/false[/COLOR]

```

---

### Post by Morbius1 on 2013-02-19
> **bab1 said:**
> I would just point out that when you declare the home directory (/srv/something) and stop login with /bin/false as the shell, you automatically create the home directory (saves work) and can leave the [homes] share pretty much as the default.  I believe Samba scans the /etc/passwd to determine the home directory like this ```

homer:x:2086:2086:Homer Simpson,,,:**[COLOR=Red]/srv/10/homer[/COLOR]**:[COLOR=Blue]/bin/false[/COLOR]

```
I believe mine does the same thing except it creates the home directory in the default location:
```
sudo useradd -m -k /dev/null morbius
```It will create the home directory at the default location: /home/morbius and the "-k /dev/null" option will make sure the contents of the /home/morbius directory is empty initially.

---

### Post by bab1 on 2013-02-19
> **Morbius1 said:**
> I believe mine does the same thing except it creates the home directory in the default location:
```
sudo useradd -m -k /dev/null morbius
```It will create the home directory at the default location: /home/morbius and the "-k /dev/null" option will make sure the contents of the /home/morbius directory is empty initially.

Actually I think this is 'much ado about nothing".  

After thinking about it a while I believe the way I would handle this is to just create a path in the [homes] share to a folder in the users /home directory such as /home/<user>/homework (or some such)  The share would then be //SERVER/<user>.  The caveat is no duplicate user names.  With /bin/false as the login shell the user would only be able to get to /home/<user>/homework directory or lower.  In other words the ***share root*** is /home/<user>/homework.  

As usual; a million ways of getting to the same outcome.  They all should work.  Of course it's all up to the OP now.  I think this horse is about dead.

---

