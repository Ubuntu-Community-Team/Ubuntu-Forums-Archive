---
title: "Another Apache2 security thread"
date: 2005-06-29
forum: Server Platforms
---

### Post by Mr. Electric Wizard on 2005-06-29
All these security breach threads has got me wondering about how secure my system is?
I have my Ubuntu PC behind a Router with the firewall turned on.
I installed Ubuntu on this PC, then applied all my patches and updates, etc.
I do have samba running to play music files on my Ubundu box that reside on my XP box in the other room.
I installed Apache2 the other day and put up a personal web site.
I forwarded port 80 on my router to pass port 80 traffic to my Ubuntu box.
How safe is this?

I do not plan on running PHP, SSH, and no sort of ASP, etc. on this box, just serving static web pages...

I understand that by opening up my network to the outside world I am probably asking for trouble, but I sure would like to serve up some pages...

How safe am I?

---

### Post by LordHunter317 on 2005-06-29
If all the pages are static, and you don't have any dynamic content modules, you're pretty safe.  Just make sure to keep apache2 up to date if there are any security issues.   That's the core concern.

Also, make sure any modules you don't need to run aren't loaded.  The modules to be loaded are contained in files in /etc/apache2/modules-enabled.  You can use a2enmod and a2dismod to enable/disable them.   Static content will probably allow you to remove most of them.

Also, make sure your web content isn't owned by the apache user.  That way, in the event of a break-in, it can't be modified as easily.

---

### Post by Mr. Electric Wizard on 2005-06-29
The www directory has been moved to the /home/user directory, so the only one that has permissions to change is me...

Thanks for the reply.  I figured I was fairly safe, I know a lot safer than running an IIS webserver.
Never hurts to be too careful...

---

### Post by LordHunter317 on 2005-06-29
[QUOTE=Mr. Electric Wizard]The www directory has been moved to the /home/user directory, so the only one that has permissions to change is me...[/quote]Now that was sorta silly.  You don't need to move it, just change the permissions via chown/chmod.

>  I figured I was fairly safe, I know a lot safer than running an IIS webserver.IIS 5 & 6 are just fine, once properly patched, IME.

---

### Post by Mr. Electric Wizard on 2005-06-29
[QUOTE=LordHunter317]Now that was sorta silly.  You don't need to move it, just change the permissions via chown/chmod.

IIS 5 & 6 are just fine, once properly patched, IME.[/QUOTE]

True, true...  Newbie here.  Still learning.

---

