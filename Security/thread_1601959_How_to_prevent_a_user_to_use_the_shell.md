---
title: "How to prevent a user to use the shell ?"
date: 2010-10-20
forum: Security
---

### Post by msantamaria on 2010-10-20
I have created some a user account on my Ubuntu desktop computer and i wrote a a shell script with a menu for this user. I edit the bash file for this user, and now when the user logon  its automatically go to the menu that i made for him. The problem is if the users clicks CTRL + C . He can use the terminal . How i can solve this ? I dont want the user to have access to terminal.

---

### Post by Barriehie on 2010-10-20
So you're launching the menu via ~/.bashrc and it's a whatever.sh file?

---

### Post by WinstonChurchill on 2010-10-21
> **msantamaria said:**
> I have created some a user account on my Ubuntu desktop computer and i wrote a a shell script with a menu for this user. I edit the bash file for this user, and now when the user logon  its automatically go to the menu that i made for him. The problem is if the users clicks CTRL + C . He can use the terminal . How i can solve this ? I dont want the user to have access to terminal.
You really can't do what you're asking - if the user sits down in front of the computer with a graphical desktop, there's not much you can do to prevent them from executing whatever they want to. But remember that whatever they execute is only executed with their privileges, so there's very little they can actually do to mess with anybody but themselves... Why are you so concerned about this?

If what you're looking for is a kiosk-type computer that a lot of people use (for instance, for an internet cafe or something), the great and mighty Google will provide you with a wealth of resources.

---

### Post by wolfgangmcq on 2010-10-21
If the user has no privledges, they can't do anything. If you don't want them to use the command prompt anyway, you might try editing /etc/passwd. There should be an entry that says something like 
```
username:password:1000:1000:Full Name,,,:/home/username:/bin/bash
```
Change /bin/bash (or whatever's after the last colon) to the path of the menuing program.
[COLOR=red]***_IMPORTANT DISCLAIMER:_*** I do *not* take responsibility for what happens if you break something! [/COLOR][COLOR=black]I have never actually tried editing /etc/passwd, and would not advise doing so unless you really know what you're doing.[/COLOR]

---

### Post by FuturePilot on 2010-10-21
How are you launching this script? If you use

```
gnome-terminal --command
```
followed by the script. It will automatically close the terminal when the script exits or is terminated. However this really doesn't prevent the user from starting a terminal themselves. It just gets the terminal out of the way if your script is canceled.

> **wolfgangmcq said:**
> If the user has no privledges, they can't do anything. If you don't want them to use the command prompt anyway, you might try editing /etc/passwd. There should be an entry that says something like 
```
username:password:1000:1000:Full Name,,,:/home/username:/bin/bash
```
Change /bin/bash (or whatever's after the last colon) to the path of the menuing program.
[COLOR=red]***_IMPORTANT DISCLAIMER:_*** I do *not* take responsibility for what happens if you break something! [/COLOR][COLOR=black]I have never actually tried editing /etc/passwd, and would not advise doing so unless you really know what you're doing.[/COLOR]

This is a really, really bad idea. There are utilities for modifying user accounts. These prevent mistakes that can be made if you manually edit /etc/passwd. It's also considered to be more proper to use these utilities. Second, changing to shell to a non-valid shell will most likely make it impossible for the user to login.

---

### Post by WinstonChurchill on 2010-10-21
> **wolfgangmcq said:**
> If the user has no privledges, they can't do anything. If you don't want them to use the command prompt anyway, you might try editing /etc/passwd. There should be an entry that says something like 
```
username:password:1000:1000:Full Name,,,:/home/username:/bin/bash
```Change /bin/bash (or whatever's after the last colon) to the path of the menuing program[COLOR=black].[/COLOR]
While you're right in a sense, even if you change their shell, if the user has a graphical desktop all they have to do is open up Nautilus (the file manager), navigate to /bin and double click on "bash". Or they could download a shell from the internet and run it, or they could write their own shell and compile it and run it... in short, you really can't prevent somebody with a standard Ubuntu desktop from ending up with a shell. 

But I'll say again, a shell is not a problem so long as the user is unprivileged.

---

