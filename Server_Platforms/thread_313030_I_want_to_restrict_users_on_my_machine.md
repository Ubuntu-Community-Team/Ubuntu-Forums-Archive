---
title: "I want to restrict users on my machine"
date: 2006-12-05
forum: Server Platforms
---

### Post by jreid08 on 2006-12-05
How do I restrict a user to their own directory in Ubuntu.  I basically don’t want them to snoop in anyone else’s directories when they’re in Gnome, SSH, FTP, or anything else period.  Furthermore, I don’t even want them to see what other accounts are even on the machine.  Obviously I don't want to affect their PC'ing so I want programs to work for them and such.  Don't know if that matters so I mentioned it.

Long and short... I want them to use the machine.  I don’t want them to know what user accounts are on the machine, venture beyond where they need to be to do necessary work.

I want to be able to do this for only one user on the machine.  I don’t want other users that exist or would be created in the future to be affected by this.

Thanks for any help!
JR

---

### Post by loserboy on 2006-12-05
I have no need for this so i haven't done it yet but it looks simple enough, just go to System>administration>users & groups - add user

it should let u specify everything that you want, say like not allowing super user privilages and only giving them access to their own home folder and desktop. depending on how you have your login screen setup i dont think they will see other accounts.
lemme know how it goes and if it's as easy as all that

---

### Post by jreid08 on 2006-12-05
Basically I want to create an environment similar to most work environments where users are confined to their directory and wouldn't know any better.  The difference would be that I'd be using Ubuntu vs. Windows.

I'm running Gnome, unless I'm missing something or you can change the login screen, you only get an imput box for the username and password.  There isn't a situation similar to MS Home, where you can click on the user and then enter a password.

I'll give this a shot and see how it works,
JR

---

### Post by Iowan on 2006-12-05
> **jreid08 said:**
> 
I'm running Gnome, unless I'm missing something or you can change the login screen...
You can!
... but I'm not near my system to get details.

---

### Post by PvSinNL on 2006-12-05
> **jreid08 said:**
> Long and short... I want them to use the machine.  I don&#8217;t want them to know what user accounts are on the machine, venture beyond where they need to be to do necessary work.
This will be difficult, if it is possible at all. You can't restrict a single user's access (as in, e.g., reading its contents) to all directories other than his/her home directory without severely affecting his/her ability to run programs and such. The *nix access control model was never designed to do things like this. (Having said that, I don't see why it would be necessary to prevent users from looking around in /usr/bin or whatever.)

The other thing, preventing people from seeing other accounts on the machine: The only thing I can think of is to have separate groups, put home directories in subdirectories of /home, and make these subdirectories accessible to the respective users/user groups only. This wouldn't stop people from doing a "who" or "w" to see other logins, though.

---

### Post by loserboy on 2006-12-06
but even if they could see other accounts, ubuntu or linux in general is secure enough as far as i know that when setup properly you dont need to worry about them knowing that there are other accounts.

---

### Post by Halasear on 2006-12-14
open a shell prompt

change directory to root directory (/)

perform the following command.

sudo chmod o-rw *

That will cause all "Others" directories except for Owners and Groups from the root directory to not be read or written...  Yet allows them to be executed if they are already allowed.

There may be a better way, but it works...sorta :)

---

