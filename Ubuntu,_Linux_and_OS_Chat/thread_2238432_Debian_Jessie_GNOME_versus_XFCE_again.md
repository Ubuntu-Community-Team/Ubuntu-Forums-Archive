---
title: "Debian Jessie: GNOME versus XFCE again"
date: 2014-08-07
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-08-07
This is from a GNOME dev's angle: [http://oskuro.net/blog/freesoftware/gnome-as-default-jessie-desktop-2014-08-07-23-58](http://oskuro.net/blog/freesoftware/gnome-as-default-jessie-desktop-2014-08-07-23-58)

Can someone please explain this bit:> Security: GNOME is more secure. There are no processes launched with root permissions on the user&#8217;s session. All everyday operations (package management, disk partitioning and formatting, date/time configuration&#8230;) are accomplished through PolicyKit wrappers.?

---

### Post by slooksterpsv on 2014-08-08
Sometimes when logging in as a user, some applications or processes (additional services, if you'd like to think of it) will run as root user. Think bluetooth - if it's not initialized until the user logs in, root would have to start that service for bluetooth. GNOME doesn't do this, it'll start everything root needs before the user logs in so no root attachments are on the users processes when they login (session).

PolicyKit wrappers... hmm... IIRC this is referring to a permissions based system like a grouping. If you're part of the admins group you can initialize these areas - package management, partitioning, etc. - because your user has permissions wrapped in a specific policy. For example:

Jane is not in admin group
Sven IS in the admin group

Jane attempts to run disk partitioning, the application checks for appropriate permissions via the policies stated on the system and lets the user know they don't have access to run it.
SVen attempts to run disk partitioning, he has permissions to run the app where the policies state admin group users can run this app. He's able to do what he needs.

Again, I believe that how it works, but I could be wrong.

---

### Post by grahammechanical on 2014-08-08
Well, now we know why the Ubuntu ISO image became too large to fit on a CD disc.

It looks to me that someone's personal taste is being pushed into what should be a co-operative project.

> [COLOR=#000000][FONT=Verdana]We would also like that in the future, changes of this nature will not be announced in a git commit log, but widely discussed in debian-project and the other usual development/decision channels, like the change of init system happened recently. We will, whichever the final decision is, continue to package GNOME with great care to ensure our users get the best possible desktop experience Debian can offer.[/FONT][/COLOR]

Someone thinks he is Linus Torvalds.

From the little bit of reading that I have done on PolicyKit it does not so much as grant permissions to users as limit permission of utilities forcing an administrator authentication. We can see the default set of PolicyKit policies in /usr/share/polkit-1/actions

---

### Post by vasa1 on 2014-08-08
Thanks, slooksterpsv and grahammechanical! This seems to be quite a complicated subject.

---

