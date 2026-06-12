---
title: "Keys in notification area prompting change to privileges"
date: 2010-03-28
forum: Security
---

### Post by markling on 2010-03-28
Since reinstalling Ubuntu 9.10 and learning how to get the Notification Area working properly:

I've noticed an bunch-of-keys icon appearing intermittently in my notification area.

It appeared about 20 mins ago. I hovered the mouse over it and it generated the following text:

"Click on the icon to drop all elevated privileges"

I right-clicked on the icon, thinking I might learn something more about it. But it disappeared. No other messages were given.

It appeared again about five or ten minutes ago. I did not click on it. But it disappeared of its own accord after a minute or two.

What is this? Should I have clicked on it? What have I done? How can I get this bunch of keys under my control?

---

### Post by mpt on 2010-03-28
I don’t know what it’s for, but a similar thing appears in Ubuntu Lucid (except this time it’s a menu rather than a disappearing icon). [I’ve reported it as a bug]("http://launchpad.net/bugs/550502").

---

### Post by sisco311 on 2010-03-28
If, in PolicyKit, the authentication mode for an action (i.e. install software or mount a partition) is set to *auth_admin_keep* or *auth_self_keep* the authorization is kept for a brief period when PolocyKit doesn't prompt you for a password. You can drop the elevated privilege by clicking the key icon. It's PolicyKit's equivalent of *sudo -k*.

---

### Post by markling on 2011-04-24
Cool. Don't know what you're talking about. But, cool.

---

