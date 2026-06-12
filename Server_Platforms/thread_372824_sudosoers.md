---
title: "sudosoers"
date: 2007-02-28
forum: Server Platforms
---

### Post by geakMonkey on 2007-02-28
Hello,

I have a new install of Dapper Server. I need to grant root privledges to another admin plus a few webmasters and helpers. So, far, I have

root=    ALL(ALL)
myself=ALL(ALL)
assistant=ALL(ALL)
webmaster=ALL(ALL)
webslave=ALL(ALL)

Of course those are aliases. 

Anyway, I keep reading threads and posts about differences in loging as admin using sudo su and su. What is the difference? What is safest for the Ubuntu Server system?

I want to be able to not give root permission to assistant, webmaster, and webslave. They all need lesser and lesser levels of permission: assistant should have some root privledges; webmaster should have read-write-execute permissions on the var/www and usr/local (and one for the cgi-bin) directories; and webslave should only have read-write for the var/www for copying and moving files within folders. How do I configure that?

---

### Post by Mr. C. on 2007-03-01
You're going to need to come up to speed on the concepts of Unix/Linux users, groups, and permissions.
 
The "su" program was written long ago to allow a user to Switch Users (hence "su").  This command allowed a user to create a new shell, or run a command, with the privileges of some other user, often the "root" user.  But this was inconvenient for running routine jobs that required switching back and forth between users (due to constantly having to enter the user's/root's password), and good admin's don't leave privileged shells unattended.

So, "sudo" was create to perform the same job as "su"; but it keeps a small database of when you last sudo'd to a user.  If you sudo again within a configured time period, no password was required.

Both can be used to do the same thing - run a new shell, or a command, with the privileges of another user or group.  The "su" command requires a valid user shell (in /etc/passwd), whereas sudo does not.  Neither is more or less secure than the other.

The sudo command allows the ability to give various users various sets of permission to run various programs.  But don't be fooled by this - if you give anyone root privileges, you had better either a) not care if they have them, or b) be very comfortable with Unix user, groups, and permissions.  It is very difficult to know how to configure /etc/sudoers

You're not going to find any easier answers than this.  Again, I'd strongly encourage you to learn and understand Unix users, groups and permissions first.  They are key to understanding the security of your system.

---

### Post by gaten on 2007-03-01
If practiced correctly, sudo is a more secure way to go. The way you have it set up right now isn't a great idea, but I don't know your situation. sudo allows you to delegate administrative access to someone WITHOUT giving out the root password (always a bad idea). 

However, your sudo file is unrestrictive and open, and essentially gives root access to all the users in the file. What you need to do is read the sudoers man page, and like the poster above suggested, learn about groups and permissions. Alot of your issues could be resolved by groups. For instance, putting your "webmaster" and "webslave" users into the www-data group and make sure that all your webpages have read, write and executable permission by the www-data group. Hope that helps and drives home the point about learning groups and permissions.

---

### Post by geakMonkey on 2007-03-06
Ok, I needed to know how to set the Groups and Aliases for each Group: that was the confusion for me.  So far, I added myself, webmaster and webslave to the www-data group. I am still trying to figure out how to give www-data sudoer permission. Do I treat the group like a user in the sudoers file?

root= ALL(ALL)
myself=ALL(ALL)
assistant=?(?)
webmaster=?(?)
webslave=?(?)
www=data=?(?)

some examples[http://www.sudo.ws/sudo/man/sudoers.html#examples]("http://www.sudo.ws/sudo/man/sudoers.html#examples")

---

### Post by Mr. C. on 2007-03-06
You are still misunderstanding.  You need to understand Unix/Linux users, groups, and permissions FIRST.  Otherwise, just give everyone the root password and be done with it, because you are highly likely to create unintended holes in your security.

Show a list of your users, groups, and permissions.

Explain exactly *what function* you want each user or group to be able to perform.

As in :
 - user "sally" can reboot the system.
 - group "webadmins" can restart apache
 - user "joe" can have full root prvis.

Without these defined up front, nobody can assist you... securely.

MrC

---

