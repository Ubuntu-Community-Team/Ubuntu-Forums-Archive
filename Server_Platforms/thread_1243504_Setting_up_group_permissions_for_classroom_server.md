---
title: "Setting up group permissions for classroom server"
date: 2009-08-18
forum: Server Platforms
---

### Post by jgb2185 on 2009-08-18
I understand the basics of Linux file permissioning, but some of the finer points escape me. I am setting up a classroom server running 9.04/Jaunty, and need to enable the teacher to access the student home directories. I am using a slightly modified version of [[COLOR="Blue"]this script[/COLOR]]("http://ubuntuforums.org/showthread.php?t=241805") to create new users on the server. The default permissions on a new user home directory are **755**, and the default permissions on file created in the home directory (such as **.profile**) appear to be **644**.

1) What combination of permissions and group memberships will allow the **teacher** ID to access the student home directory, and read/write/delete the files within?

2) How can this combination be made the default? (I am no scripting wizard, but I have sufficient chops to add commands to the user creation script referenced above, if need be.)

Thanks in advance...

JGB

---

### Post by Thirtysixway on 2009-08-18
Here's an example. Let's say we have a student named tod. Tod would be a member of the Student group.

His home folder could be owned by Tod and the group Teachers (tod:teachers).

Have the teacher accounts a part of the teachers group.  Then have his folder 775 or what have you.

---

### Post by Grim76 on 2009-08-18
You might look into setting up ACLs.  The man pages pretty well cover things.  You can setup defaults so that when a new student is added to /home then the Teachers can automatically get permissions.

---

