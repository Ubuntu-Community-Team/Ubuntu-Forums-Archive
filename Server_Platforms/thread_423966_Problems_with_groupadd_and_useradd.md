---
title: "Problems with groupadd and useradd"
date: 2007-04-26
forum: Server Platforms
---

### Post by paulrs on 2007-04-26
Folks,

    I'm very much a newbie to Ubuntu, and I'm trying to set up some users and groups on a fresh install of Ubuntu Desktop version 7.04.  I executed the following commands:

[FONT="Courier New"]sudo groupadd cvs
sudo groupadd svn
sudo useradd -c "CVS User" -d /opt/cvsroot -s /sbin/nologin -g cvs cvs
sudo useradd -c "SVN User" -d /opt/cvsroot -s /sbin/nologin -g svn svn
sudo useradd -c "Paul" -d /home/paulrs -m -k /etc/skel -s /bin/zsh -G cvs,svn paulrs
sudo passwd paulrs
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully[/FONT]

All of these commands (except for the password change) executed without error or any message at all (which seemed a bit odd at first, but I didn't take much note of it).  I then tried logging in as my new paulrs user, but could not.  I decided to have a look at the /etc/passwd file, and found that none of the three new users appeared in the file (I did a cat /etc/passwd | grep <userName>).  I then checked the /etc/group file for my two new groups and also did not find them.  I then took a look to see if the /home/paulrs directory was created, and indeed it was.  I did an ls -l on /home and found that the paulrs directory was not owned by paulrs but by user id 1005.  Interestingly, 1005 is 3 more than the last user ID in the /etc/passwd file, which makes sense, because I created three new users.

    So, what did I do wrong, and what am I misisng here?  I realize that there is a GUI that can be used to create users and groups, but I would prefer to use the command line, because I can keep a full transcript of everything I have done. Also, at this point, I would really like to know how to clean this up properly.

Thanks,
Paul

---

### Post by huygens on 2007-04-27
It should not be that difficult to repair things as it seems that only the /etc/groups and /etc/passwd where not updated.
However, you could try to use the addgroup and adduser command lines instead of manually editing the above mentioned files.
I tend to prefer addgroup/adduser instead of groupadd/useradd... I understand better there options.
So I would do this:
```
[FONT=Courier New]sudo adduser --system --group --home /opt/cvsroot --disabled-login cvs
sudo adduser --system --group [/FONT][FONT=Courier New]--home /opt/cvsroot [/FONT][FONT=Courier New]--disabled-login [/FONT][FONT=Courier New]svn
sudo adduser --shell /bin/zsh paulrs
sudo adduser paulrs cvs
sudo adduser paulrs svn[/FONT]
```A bit of explanation, line by line:[LIST=1]
[*]Create a system user and group called both cvs. And specify the home /opt/cvsroot. The skeleton files are not copied there if this directory already exist. No login is possible (equivalent to set the shell to /bin/nologin or other variant)
[*]Same as point 1 but for svn now.
[*]Create a normal user with zsh shell. The home will be /home/paulrs and the /etc/skel files will be copied to it if the directory does not exist yet. This command will ask you for the user password and for user name, room, phone. Just fill in what is necessary! The group of this user will be the same as its name. So a group paulrs has been created.
[*]Add user to the group cvs
[*]Add user to the group svn[/LIST]That's it :-)

Some more tweak you could do, depending on your needs... You could add the paulrs user to the admin group as well so it can perform sudo commands: sudo adduser paulrs admin. Also, you could use the --disabled-password for the creation of the user paulrs. Login using "su - paulrs" or the graphical login prompt will fail. But connection via SSH using public/private key would still be authorised.
Check 'man adduser'

---

