---
title: "Problems with user/groups and apache www directories"
date: 2007-06-05
forum: Server Platforms
---

### Post by MystaMax on 2007-06-05
I've got a ubuntu 6.06 server running apache, and have some questions about users and groups.

I've got various sub directories in /var/www and they are currently all owned and grouped w/ root.

Currently, I cannot edit these files b/c of their user and group association. Its starting to become tedious to sudo every file.

So for testing, I changed one of the directory's groups to www-data (*sudo chgrp -R www-data /foldername*), added myself to that group (*I edited /etc/group, located www-data:x:33: and changed it to www-data:x:33:mhyatt*), and changed the permissions for the group to rwx (*sudo chmod g+rwx /foldername*). After doing all this, I still couldn't edit files w/o using sudo.

I'm not sure why its not working, and can't really find an explanation via google. After giving up I changed the owner of the folder to www-data as well and that worked.

I guess another question I have is, **whats the best way to have your directories configured so that you can edit them without sudo and still have a somewhat secure web server**. 

Any tips, clues, or help is appreciated.

---

### Post by turinglabs on 2007-06-05
The best way to do this is by adding your user to a group other than www-data, since apache itself runs under that user. Use the 'sudo vigr' command to edit group memberships, I like to use the pre-defined group 'staff' for stuff like this. 

Then you have to change both the files and directories containing those files to the new group, and make them r/w (files) r/w/x (directories).  Here is an easy way to properly change all directories and files under /var/www, assuming the group 'staff' will have write privs:

```

cd /var/www
find . -type d | xargs chmod 775
find . -type f | xargs chmod 664
chown -R root.staff *

```

---

### Post by MystaMax on 2007-06-07
Doug-

Sorry it took me a while to say thank you, as your solution worked. So, Thanks :)

The reason I posted in the first place is because I was reading over [Ubuntu Unleashed]("http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/") (BTW, the book is online for free) by Paul Hudson, and it speaks of adding/adjusting groups a bit differently. I used the technique in the book (before posting my question) and it messed up my /etc/group file completely. After, I was not apart of any group, but the one I ran the command with:

```


sudo usermod -G www-data mhyatt


```I thought running the above code would add me to the www-data group, which it did. But, it also removed me from all other groups I was a member of. That didn't seem right. **Was it because I was logged in?**

I had to boot into recovery mode, and add myself to the admin group so I could sudo again. Then I realized it created a backup, so I restored it and it fixed the problem.

In Chapter 14, Managing Users, and the section managing groups, it talks about group managing tools. I'm not sure if these are Ubuntu specific, but I had never heard of them or used them. They are:

> 
groupadd This command creates and adds a new group.

groupdel This command removes an existing group.

groupmod This command creates a group name or GIDs but doesn't add or delete members from a group.

gpasswd This command creates a group password. Every group can have a group password and an administrator. Use the -A argument to assign a user as group administrator.

useradd -G The -G argument adds a user to a group during the initial user creation. (More arguments are used to create a user.)

usermod -G This command allows you to add a user to a group so long as the user is not logged in at the time.

grpck A command for checking the /etc/group file for typos.

Explanation basically stops there. It tells you how to add groups, add a user to a group, and check the group file for errors. The book goes on to explain how to do it via GUI, and I'm not interested in learning the GUI way. I can figure that out. The book is thin on the subject.

**If you're up for a discussion on this, or don't mind enlightening me on the subject, it'd be appreciated. **Otherwise I'm just babbling on ;)

---

### Post by turinglabs on 2007-06-07
> **MystaMax said:**
> 
Sorry it took me a while to say thank you, as your solution worked. So, Thanks


No problem, glad to help.

> **MystaMax said:**
> 
sudo usermod -G www-data mhyatt

I thought running the above code would add me to the www-data group, which it did. But, it also removed me from all other groups I was a member of. That didn't seem right. **Was it because I was logged in?**


The usermod ( 8 ) man page explains:

"If the user is currently a member of a group which is not listed, the user will be removed from the group. This behaviour can be changed via -a option, which appends user to the current supplementary group list."

I didn't realize this, I'm not sure it's 'good' behavior for a command of this sort to remove group memberships by default. It should probably be reversed - the default should be to append the group to the user's supplementary groups list.

The caveat about the user not being logged in just means that the user has to log out and in again for the group membership to take effect, not that the command won't make the changes to the group file.

> **MystaMax said:**
> 
In Chapter 14, Managing Users, and the section managing groups, it talks about group managing tools. I'm not sure if these are Ubuntu specific, but I had never heard of them or used them.


Most Linux distros have some variation on some or all of these commands. Using them is personal preference, mine is to us 'vigr' and 'vipw' to do simple user and group management, The commands you listed can be very useful for making changes from a script, however.

One useful trick for creating users from a script or just without the password prompt is this:

```

useradd -c "Full Name" -m -g <primary group> -G <group1>,<group2>,...,<groupN> -p `openssl passwd <password>` <username>

```

Here ,<primary group> is the user's login group, <group1>,...,<groupN> are supplementrary groups, <password> is the plaintext password, and <username> is the login name. The '-m' switch creates their home directory for you. Just be aware that this command will be in your shell history file if you execute it from a prompt, with the password fro all to see. In Feisty, at least, you can precede this command with a space and it won't be appended to your history file. See Bash (1) and search for 'HISTCONTROL' for details.

---

