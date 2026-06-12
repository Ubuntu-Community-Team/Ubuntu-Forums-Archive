---
title: "FTP without root account"
date: 2011-03-03
forum: Server Platforms
---

### Post by Eszaraxe on 2011-03-03
Everywhere in the manuals and help topics it is recommended to not activate root user.
I try to use FTP to put new files and catalogs on my server and I always run into problems that I have not the right to create catalogs and files in the named catalogs and so on, it is very annoying.
Is there a way around this problem or do I have to activate root account to not run into these problems all the time?

I have worked with different UNIX-versions and variants for the last 15 years at least and have always had access to root account, why is it so dangerous to have access to root account in ubuntu?

---

### Post by MrEgg on 2011-03-03
On Ubuntu, the root account is not activated as a security measure. I think it's a pretty good one too, because any attack on the root user (ftp, ssh) will fail by definition. Ubuntu being Linux, you can set up a root password if you really have to.

Now, if you can't add files to folders, maybe you want to set up proper groups, group permissions and add yourself to those groups?

---

### Post by bsntech on 2011-03-03
MrEgg is right.  In order to activate the root account, you need to just set a password on it.  You'll then be able to login via ssh using the root account if desired.

You'll need to check the FTP configuration as well.  Some FTP servers will have a line that will not allow for root logins.  Ensure that is not the case.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/")

---

### Post by Lars Noodén on 2011-03-04
> **MrEgg said:**
> ...maybe you want to set up proper groups, group permissions and add yourself to those groups?

That's my first recommendation, too.  If you need different access for more than one group per directory, then you may want to activate ACLs for that one file system.

---

