---
title: "Will adding noexec to /home partition protect against malicious email attachments?"
date: 2015-04-12
forum: Security
---

### Post by greg2lapa on 2015-04-12
People in the family  are not very discriminating when it comes to opening email attachments. I am searching for a way to minimize the risk as much as possible.

Will installing Ubuntu with a root (/) partition & a home (/home) partition while adding
```
nodev,nosuid,noexec
```
to fstab provide any protection? My understanding is that the email attachment danger originates from someone opening a document (e.g., a LibreOffice Writer document) and a script runs that installs malicious software. Obviously a password should be requested by Ubuntu for something to install but a lot of these attacks use zero days that bypass the password requirement. Would adding noexec help defend against this? will it break anything? Seems all executions happen on the / partition so the /home partition not having execute capabilities seems doable.

---

### Post by TheFu on 2015-04-13
I've never heard this technique, but you could just try it and see.
Another options is to remove execute permissions for problem users in their HOME using extended attributes. 

A blackhat hacker can easily get around the lack of execute permissions by having some other program call the script - perhaps bash.
**/bin/bash bad-script.sh** for example. Then the first line would be read, interpreted and run.

The best answer I know for security is to have **backup religion**.  Unprivileged users shouldn't be able to do any harm on a fully patched system unless a zero-day is dropped. Then there really isn't any protection beside having versioned backups anyway.

Plus there is the whole Unix philosophy that the system is there to be used by users. That's why users can install any software they like to their home directories - even using the package mananger by changing the install-to path.  Software developer do this all-the-time to have many different versions of perl, python, ruby, etc. on the system for the applications and libraries they are working on.

Plus, the most dangerous file I know on a Linux desktop machine are the .desktop files and those do not require execute privileges to work.

---

### Post by greg2lapa on 2015-04-15
Do you have any insight into whether a solution might be setting up an AppArmor profile for the apps that would open attachments? I notice evince has a profile but LibreOffice Writer and Calc do not. Do you know where I might find a secure profile for Writer and Calc? I don't understand AA enough to be able to write my own.

---

### Post by TheFu on 2015-04-15
Apparmor has a tool you run that creates new profiles for programs. There is a how-to somewhere - google found it last time I needed it - plus there are youtube videos, if you learn better that way.  Then you run the tool with the program and do everything you want to be possible - avoiding the things you don't want possible. That should create the profile you want.  I suspect the tool will never stop a program from writing to $HOME, however.  I do NOT know this for sure.

You could make the HOME read-only for the users. That would be mean.  I've only done this for highly specialized servers with 1 purpose. Their login forced the program and when they ended the program, they were logged out.  Never did this for a user's main desktop computer.

---

