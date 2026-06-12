---
title: "Allow users to install into the /home directory"
date: 2008-12-15
forum: Testimonials &amp; Experiences
---

### Post by NCLI on 2008-12-15
[http://brainstorm.ubuntu.com/idea/16475/](http://brainstorm.ubuntu.com/idea/16475/)

I don't think this idea has received enough attention:

"I'd like to see a way for non-admin users to install programs via apt, into their home directory , so they don't need root access every time they even want tiny, succinct apps (like a fortune cookie program), and still have the convenience of a package manager

There would be no security risk or overall risk to system stability as apt would run with user privileges, so they would still not be able to do any worse then they normally could do.

Dangerous programs like VMware would still not be able to be fully installed (because kernel module installation requires root). And they would not be able to erase Xorg because they don't have write access to the Xorg directories.

But they could eliminate their reliance on tar.gz's from websites, and install programs such as vdrift or open office, using the standard package managers, without requiring root intervention.

A policy could be set in a config files to determine if local users should be able to use apt with local user permissions. The code for this is easy! That way you can still stop them using apt if you wish :D

PROS
1) Untrusted noobies can install or mess around in the full APT repo without ANY risk of system damage.
2) I can hand grandma a ubuntu laptop, without sudo/root access, allow her to install programs, without risk or giving her root.
3) This could technically be implemented now, with only a few changes to synaptic or adept. Apt is already ready
4) This is a way for users to step up to more advanced package managers, without screwing up the system.

CONS
1.1) A bit more hdd space usage. But people should be using quota's anyway to protect against this in most environments. " 

Even in Windows, you are allowed to install applications for your own user account, with no administrative privileges. Why is this a problem for *nix!?

---

### Post by wizard10000 on 2008-12-15
Just my opinion, but I don't *want* end users installing software on corporate machines.  In a corporate environment anything that's installed has to be supported so I really don't see the need to allow a user to install anything on a business machine.

Although it seems trivial in the enterprise where I work a helpdesk call costs about $25 and a deskside visit costs at least twice that.  The fortune cookie program you mention maybe be fairly benign but when the user calls the helpdesk because he doesn't know how to run it - or, heaven forbid the application breaks *another* application in the user context then lost user productivity and increased support costs do factor in.

Back in the OS8 days I used to admin an all-Mac network connected to a Novell server - users figured that corporate PCs were their PCs and consistently loaded crapware onto them, breaking the machines (older Mac users will remember extensions conflicts) and costing the company money.

My solution?  I had a floppy disk that contained all the extensions required to run all approved corporate applications - if I heard that reboot chime too many times in the course of a day I'd walk over and replace the user's extensions folder with the one on floppy disk and tell the user to go back to work  ;)

Don't get me wrong, I think that customizing a user's PC makes for increased productivity but when that customization interferes with productivity then it needs to stop - and I don't know a good way to pick and choose which applications users may install and which they may not.

I know you didn't mention business PCs but IME there's no business need for a fortune cookie application on a corporate PC so there's no business need to allow the user to install it or for the helpdesk to support it  ;)

---

### Post by solwic on 2008-12-15
> **NCLI said:**
> [http://brainstorm.ubuntu.com/idea/16475/](http://brainstorm.ubuntu.com/idea/16475/)

I don't think this idea has received enough attention:

"I'd like to see a way for non-admin users to install programs via apt, into their home directory , so they don't need root access every time they even want tiny, succinct apps (like a fortune cookie program), and still have the convenience of a package manager

There would be no security risk or overall risk to system stability as apt would run with user privileges, so they would still not be able to do any worse then they normally could do.

Dangerous programs like VMware would still not be able to be fully installed (because kernel module installation requires root). And they would not be able to erase Xorg because they don't have write access to the Xorg directories.

But they could eliminate their reliance on tar.gz's from websites, and install programs such as vdrift or open office, using the standard package managers, without requiring root intervention.

A policy could be set in a config files to determine if local users should be able to use apt with local user permissions. The code for this is easy! That way you can still stop them using apt if you wish :D

PROS
1) Untrusted noobies can install or mess around in the full APT repo without ANY risk of system damage.
2) I can hand grandma a ubuntu laptop, without sudo/root access, allow her to install programs, without risk or giving her root.
3) This could technically be implemented now, with only a few changes to synaptic or adept. Apt is already ready
4) This is a way for users to step up to more advanced package managers, without screwing up the system.

CONS
1.1) A bit more hdd space usage. But people should be using quota's anyway to protect against this in most environments. " 

Even in Windows, you are allowed to install applications for your own user account, with no administrative privileges. Why is this a problem for *nix!?

I think that's a great idea.  It'll never happen, sadly, but it's still an awesome idea.  

Best of luck getting it voted up!  :)

---

### Post by lpanebr on 2009-01-09
I think it is a good idea. 

Just like there is a group to allow users to "**Administer the system**" there should be a group to "**Allow user to use package managers on their home directory**". This way I could allow my wife an sons to install on their home directory while keeping my employees from trashing my corporate pcs.

best luck!

---

### Post by 3rdalbum on 2009-01-09
Why not knock up a preview version of it and we can try it out and see if it really does work?

---

### Post by hyperdude111 on 2009-01-09
I love this idea but it might make the already cluttered home directory worse, maybe in a sub - folder in home like "/home/user/appdata/"

But this would make it easier to fine apps and edit them without root privilages.

---

