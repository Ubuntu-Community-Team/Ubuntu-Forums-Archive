---
title: "Question of share folder"
date: 2011-06-13
forum: Security
---

### Post by steventantan on 2011-06-13
Hi all

I am a new learner of linux. I face a problem when I build up a samba server.

The question is how can I hide the folder which is not relating to user.

For example, assume there have 2 folders &#8220;A&#8221; & &#8220;B&#8221;, and one user &#8220;C&#8221;. I have set the permission &#8220;C&#8221; to folder &#8220;A&#8221;, but not to folder &#8220;B&#8221;. When the user &#8220;C&#8221; access to share drive, it will only show folder &#8220;A&#8221;, and &#8220;B&#8221; is invisible.

---

### Post by capscrew on 2011-06-13
> **steventantan said:**
> [FONT=Times New Roman][SIZE=3]Hi all[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I am a new learner of linux. I face a problem when I build up a samba server.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The question is how can I hide the folder which is not relating to user.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman]For example, assume there have 2 folders “A” & “B”, and one user “C”. I have set the permission “C” to folder “A”, but not to folder “B”. When the user “C” access to share drive, it will only show folder “A”, and “B” is invisible.[/FONT]

The parameter used in the /etc/samba/smb.conf is ***veto files***.  This is used in the share definition.  You can read about it [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html#VETOFILES").

A word of advice:  This is not a substitute for correct file structure or file permissions.  This is really a work around for a specific situation that can't be resolved any other way.  I never share anything from a users home directory.  Try and rethink how you can NOT use this parameter and still achieve what you need.  Maybe you can do some file restructuring.

What exactly are you trying to do?

---

