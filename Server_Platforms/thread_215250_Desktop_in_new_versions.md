---
title: "Desktop in new versions?"
date: 2006-07-13
forum: Server Platforms
---

### Post by bohsocks on 2006-07-13
Does anything think that in newer versions of Ubuntu, there will be included a desktop?  I know people have been asking about it so I don't know.

---

### Post by Suzan on 2006-07-13
Sorry, I don't understand you. What do you mean with "desktop"??

---

### Post by Sajji on 2006-07-13
I think the question is:  When will Ubuntu Server ship with a GUI.  X Server - currently you have to manually install it.  It's easy, but takes a while.

I think that's it.  Could be wrong.

---

### Post by az on 2006-07-13
The point of the server install is to install *less*, not more.

To achieve what you want, it probably would be faster to just install the desktop version from the live cd and then install apache2 php5-mysql libapache2-mod-php5 mysql-server linux-server

and you end up with exactly the same system as if you havd install the server LAMP selection and then installed ubuntu-desktop on top of that.

Nothing prevents you from running a server from a desktop or vice versa.  It just goes against best security practices, that's all.

You would not do this for a production server.  The server install cd is geared to people who use it for mission-critial production use.

---

### Post by FredSambo on 2006-07-13
> The server install cd is geared to people who use it for mission-critial production use.

thank the god(s)-of-your-choice for that!

---

### Post by Sajji on 2006-07-13
While I agree that the point of a server is to be less not more, it is easier to navigate through a "windows" environment.  For us Linux beginners, it's a lot easier than trying to remember commands.  Plus, I think most people are downloading server because of the pre-configured LAMP.  If you install Ubuntu Desktop and try to install and configure Apache, MySQL and PHP yourself...for a beginner like me, it's too timeconsuming and a pain in the a$$.

I took the approach to install the LAMP server and then install the GUI on top.  It was so much easier than the other way around.

Sajji

---

### Post by az on 2006-07-13
> **Sajji said:**
> While I agree that the point of a server is to be less not more, it is easier to navigate through a "windows" environment.  For us Linux beginners, it's a lot easier than trying to remember commands.  Plus, I think most people are downloading server because of the pre-configured LAMP.  If you install Ubuntu Desktop and try to install and configure Apache, MySQL and PHP yourself...for a beginner like me, it's too timeconsuming and a pain in the a$$.

I took the approach to install the LAMP server and then install the GUI on top.  It was so much easier than the other way around.

Sajji

The other way is faster.

But the problem is that there is no GUI to apache or any other basic server software on linux, and not the installer.

Even if you install the desktop (or just X and a filemanager) you still manage your server through commands.

---

### Post by DrSturgeon on 2006-07-15
> **Sajji said:**
> For us Linux beginners, it's a lot easier than trying to remember commands.

I generally try not to sound like a snob, but a server installation is not for beginners.

Presumably they don't include the gui on the CD because they need space for apache and stuff.  I have nothing against asking the user if they want to download a gui during the install process.  In fact, Ubuntu needs more install-time package options in general.  (Like tasksel in Debian)

---

