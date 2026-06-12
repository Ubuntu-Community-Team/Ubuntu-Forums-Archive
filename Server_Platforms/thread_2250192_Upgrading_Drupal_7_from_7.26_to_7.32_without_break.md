---
title: "Upgrading Drupal 7 from 7.26 to 7.32 without breaking themes and modules"
date: 2014-10-27
forum: Server Platforms
---

### Post by Lars Noodén on 2014-10-27
How can I upgrade Drupal 7 from 7.26 to 7.32 without breaking themes and modules?   /usr/share/drupal7/sites is really a symbolic link to /etc/drupal/7/sites/ and the [official instructions for Minor Version Upgrades](https://www.drupal.org/node/1223018) chokes at the symlink when running "cp -R ..."

I tried using rysnc but that overwrote the symlink and when I restored the symlink, none of the non-default modules or themes were active.

---

### Post by tgalati4 on 2014-10-27
The comments at the bottom of that page indicate a lot of problems with that in-place upgrade procedure.  Since the procedure was originally written in 2011, I would suspect there have been enough changes to the Drupal frameworks, that an in-place upgrade is reasonably risky.  

Recursive copying of symbolic links can break if the links have characteristics that are different than the near neighbors.  What are the permissions/users of the symlinks?

*rync* has a similar issue:

>               Beginning with rsync 3.0.0, rsync always sends these implied directories as real directories in the file list, even if a path  element  is
              really a symlink on the sending side.  This prevents some really unexpected behaviors when copying the full path of a file that you didn&#8217;t
              realize had a symlink in its path.  If you want to duplicate a server-side symlink, include both the symlink via its  path,  and  referent
              directory via its real path.  If you&#8217;re dealing with an older rsync on the sending side, you may need to use the --no-implied-dirs option


You may need to reinstall the custom themes and modules after the upgrade to get them to work correctly.  Another risk of in-place upgrade.

---

### Post by Lars Noodén on 2014-10-27
Thanks.  What are the alternatives to an in-place upgrade?  I was kind of hoping to have an option to put the server in maintenance mode, do something easy, then take it out of maintenance mode with the new minor version upgrade all set.

---

### Post by tgalati4 on 2014-10-28
Yes, that would be the theory.  In practice, there are problems.  How you approach it depends on how many Agony Units you want to spend.  

1.  Get a second physical server, build a new Drupal 7.32 or be brave and go with 8.0 beta.  Migrate your themes, modules, and any other customizations.  Make sure the basic drupal engine works correctly.  Then migrate your content.  When you are satisfied that everything is working, shut down the first server, wipe it and get ready for Drupal 9.

2.  Get a second physical server, install a hypervisor (such as Xen) and create 2 virtual machines.  One has a snapshot of your current, working Drupal 7.26.  Now you have a failover in case your current server fails.  Rsync the content between them using a daily cronjob.  Install 7.36 on the second vm and get it working with your themes, modules, customizations.  Test it extensively to make sure the basic engine works, then migrate your content over.  Now you have 3 servers running.  Your original 7.26, a 7.26 snapshot, and a 7.32.  It might take a while to get everything fixed or it may go smoothly--you never know.  But at least you always keep a working server.  When you are satisfied, shut down the original server, then reimage it with a hypervisor, and create 2 vms.  So now you have 2 servers and 4 vms and use a "leapfrog" approach to upgrading.  

3.  Fix the upgrade script.  Do the upgrade in maintanence mode and bring it back online and hope everything works.

4.  Do nothing.  Have a beer.  Relax.  If things are working, why bother?

As far as your original problem with symlinks, it could be a simple problem in the upgrade script.  You will have to go through it line-by-line and run each command manually to see what is going on.  It's tedious, but unless someone does it, these problems don't fix themselves.

---

### Post by tgalati4 on 2014-11-05
Additional information concerning Drupal vulnerabilities and the upgrade to 7.32:  [http://www.linux-magazine.com/Online/News/Drupal-Advisory-Unleashes-a-Torrent-of-Attacks/%28language%29/eng-US](http://www.linux-magazine.com/Online/News/Drupal-Advisory-Unleashes-a-Torrent-of-Attacks/%28language%29/eng-US)

I don't know if this is related to the OP's issue, but the type of attacks seem to indicate changes to the drupal internals which may cause upgrade issues on compromised-but-undetected systems.

---

### Post by Lars Noodén on 2014-11-05
Thanks.  I saw that.  I'm kind of disappointed that any program would allow an injection attack these days even in PHP.  Basic programming skills include validating data and keeping track of taint.  

I was looking for an easier way to do the upgrade, but at least for a single, standalone site, there's not really a way around taking it off line for a longish while and then putting a lot of things back manually.

---

