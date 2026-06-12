---
title: "Locking down for child"
date: 2009-01-27
forum: Security
---

### Post by JGT on 2009-01-27
I'm using Ubuntu 8.10 with GNOME. I've had a couple of years with Linux but I'm still finding my feet. Apologies for noobie post but I need an accurate answer.

My 3 year old is getting good at Tetravex and I'd like to let her play with my PC "alone" at times. However, she's also keen to explore the menus, including different drives and to pop open the terminal.

I'd like to open a user account for her that is *totally* locked down once it's been set up at least as follows:

[LIST]
[*]no ability to mount any drives (no access to my Windows partition);
[*]no network (web) access whatsoever;
[*]no ability to edit the menus;
[*]no ability to alter the panel layout;
[*]no changes to any display properties;
[*]if possible, right clicking disabled.
[/LIST]


I just want some apps (Cheese, Abiword, Tetravex, etc.) to launch from a menu.

I'm not certain how to manage this.

Can I just set her up as a normal user, edit the desktop environment to how I think she'd like it, then exit and lock it down totally from the outside?

Is it safe enough to block web access by hiding the launcher and terminal?

It is possible to prevent any display changes as above or are the user preferences too "low level" for the systems admin to care about?

Cheers and thanks

John

---

### Post by skintythe1andonly on 2009-01-27
sounds like its more a kiosk mode you want without the internet access. I have set this up in xubuntu before for a custom guest account, as I had kids staying over christmas. Essentially I have a backup guest home directory saved in my root partition. On logout from this guest account i have a bash script that runs and the /home/guest account gets removed and replaced with the backup so all settings are reset. That leaves whoever do what they want, if they mess anything up, all you have do is log out and log back in, to disable internet accress, Im sure you could disable netork manager from starting or something for this account.

There is also pessulus, a lockdown editor in the repos but i never it was for gnome... so i never looked at it, it may suit you fine.

---

### Post by istoff on 2009-01-27
Hi,

No complete answer to your issues, but...

[http://projects.gnome.org/sabayon/](http://projects.gnome.org/sabayon/)

It allows you to edit create user profiles with specific lockdown settings.  Not sure how well it works on 8.10

[http://www.squidguard.org/](http://www.squidguard.org/) ( also google dansguardian )

Use squidguard to lockdown the http_proxy and web access.  Maybe you can still have a links active to sesamestreet, disney, etc, and block the rest

If you want to dig deeper, I used the search terms "gnome gconf lockdown" and 2 of the results I checked looked interesting...

[http://wiki.novell.com/index.php/Locking_Down_the_GNOME_Desktop](http://wiki.novell.com/index.php/Locking_Down_the_GNOME_Desktop)
[http://library.gnome.org/admin/deployment-guide/](http://library.gnome.org/admin/deployment-guide/)

Lastly, do some reading on PolicyKit.  I'm not too sure how well its implemented in 8.10, but it seems to be the future of desktop profile/permission management.

---

### Post by JGT on 2009-01-27
Thanks for your prompt replies. I'll try with Sabayon and Pessulus as a start.

Cheers.

---

