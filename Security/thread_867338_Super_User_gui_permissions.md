---
title: "Super User gui permissions"
date: 2008-07-22
forum: Security
---

### Post by CapnRazor on 2008-07-22
I cant seem to use any of the admin tools available from the menu on the top left of the screen. most options are greyed out.

I have tried to make copies of the launchers to my destop and prefacing the launcher command with gksudo but the apps either die quietly without opening the UI or open but remain greyed out.

My work around at present is I added a root password and su in a shell then launch the app and detach it. 

I have not lived with a unix like system for years now and I am not used to working with sudo. 

my sytem is ubuntu-8.04.1-server-i386 with the gnome desktop installed via apt-get.

any help appreciated.

---

### Post by The Cog on 2008-07-23
Make sure your normal user is a member of group **admin** - only admin members are allowed to use sudo.

---

### Post by CapnRazor on 2008-07-23
> **The Cog said:**
> Make sure your normal user is a member of group **admin** - only admin members are allowed to use sudo.

Thank you for the reply.

I checked the group settings and my account was in group admin, I made admin my primary group just to test and still can not administer via the GUI.

I am guessing that by choosing the server install then adding the GUI after the fact, that there is a setting that I am missing related to sudo.

---

### Post by Oldsoldier2003 on 2008-07-24
/etc/sudoers needs to have this line in order for users in the admin group to sudo:

```

%admin ALL=(ALL) ALL
```

If you have physical access to the machine you can reboot using recovery mode and edit the file as root.

---

### Post by evets25 on 2008-07-24
Also, you should only edit this file with the command "visudo" and NOT a regular text editor. If you use a regular editor but make a typo, you can render your system unusable, but by using visudo, it will catch this type of thing for you.

---

### Post by ivo_ac on 2008-07-24
Now I happen to have the same problem yesterday which led me to re-install my system although now I know it was unnecessary.

For some reason (I think a bug) the system admin tool on my system does not store the user file correctly when you change users.

I changed rights of some users on "users and groups" and the tool deleted admin rights on all my users.

To check if you have the same problem, go to "users and groups" (I think thats the name, I have dutch language) and check the properties of your user. If the option "system management" is not checked, you have the same problem.

Reboot your system in recovery mode and choose option "drop to root".
Now type on the command line: "adduser .... admin" in which .... is your username.

If that does not do the trick, admin may not be in the sudoers file.
Again boot with recovery mode, drop to root en type on the command line "visudo" now add the line "%admin ALL=(ALL) ALL".

To add a line in VI editor, scoll to the line and type A.

Hope that helps.

Ivo.

---

### Post by CapnRazor on 2008-07-29
Thank you all for the suggestions! I tried visudo as root and found that the line %admin ALL=(ALL) ALL was in place allready.

given that I could use the practise installing anyway I will try a reinstall and see if I get the same result, (I still think it is related to installing server then adding gnome afterwards).

---

