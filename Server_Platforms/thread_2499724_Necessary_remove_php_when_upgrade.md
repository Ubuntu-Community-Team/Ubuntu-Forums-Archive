---
title: "Necessary remove php when upgrade?"
date: 2024-08-08
forum: Server Platforms
---

### Post by toft6633 on 2024-08-08
Hello,

I plan to upgrade from 22.4 to 24.04 on August 15, which should be the date for 24.04.1.

My plan is to run "sudo add-apt-repository --remove ppa: ondrej/php" before upgrade and "sudo add-apt-repository ppa: ondrej/php" after upgrade.

I have also read that one should uninstall php and all php extensions and reinstall them after the upgrade. Is that really neccesary?

Fred

---

### Post by TheFu on 2024-08-08
You don't need to remove php before an upgrade, if you use the expected php package from Canonical's report.  If you used a PPA, then the **do-release-upgrade** process should remove all PPAs before attempting an upgrade.

If it was me, I wouldn't move any server to 24.04.1 for a few weeks after the release.  Being early is almost always a bad idea for production systems.

Also, ensure you have know-you-can-restore backups BEFORE attempting anything like this.  If you don't have backups, the chances of failure seem to increase 10x.  People with good backups seem to need them less often.  Of course, if you have a volume manager, then you can just create a snapshot, which can be restored during a reboot.  If you aren't using a volume manager and have an important server, I'd say you are doing this wrong.  Perhaps a fresh install with a volume manager installed would be a better choice?

---

### Post by toft6633 on 2024-08-08
Thanks a lot!

Unfortunately I don't have good backups. I'm on a VPS and the backup service is too expensive. I have a local copy of the important files in the /etc/ directory (nginx and php) and of course the the Drupal files. Even with the worst scenario I should be up again within a day! My server is not important, very low traffic. If my site is down for a day or two is no disaster.

---

### Post by TheFu on 2024-08-08
Why don't you have a good, minimal backup solution?  I've posted small, minimal scripts here a few of times that will do the job.  Push backups (from the VPS to your home server) aren't too hard. No need to pay anything.  Of course, "pull" backups are better, so when the VPS is hacked, you don't risk your home system too, but "pulling" takes a better understanding of ssh and client/server ideas.  I use "pulled" backups for all my servers - local and on VPS.  Setting up the ssh connection is the hard part and something you'd need to understand BEFORE doing the backups.

Of course, backups need to be run as root on both sides to maintain the metadata for every file (owner, group, permissions, ACLs, xattrs). Without the file metadata, you don't really have a backup. You have data that will manually need to be setup correctly.

I don't use Drupal.  I have a few internal-only php webapps. These run on their own VM.  Wallabag is one. Here's the backup part of my Wallabag VM backup (run from my backup server):
```
/usr/bin/sudo  /usr/bin/rdiff-backup  \
       --exclude-sockets --exclude-device-files --exclude-fifos \
       --exclude '**/.cache/mozilla' \
       --exclude '**/.cache/chromium' \
       --include "/usr/local" \
       --include /etc \
       --include /home \
       --include /var/www/wallabag \
       --include /root \
       --exclude '**' \
       $RUSER@$REMOTE::/  "$TGT"

# Remove older backups .... 
echo "INFO: Removing backups older than $DAYS"
/usr/bin/sudo  /usr/bin/rdiff-backup  --remove-older-than "$DAYS"  --force "$TGT"

```
You'll need to set the bash variables used above for your systems.

Of course, there are some pre-backup and post-backup things.  I store some system information in /root/backups to make not just recovery easier, but to have a daily view of how things were configured - like lists of installed packages, disk layouts, etc.  Sometimes, a partition table gets corrupted and that it. No data is at risk if you can just overlay the correct partition table, so having that data in a format that can be used to exactly match what was already there is helpful.  I capture these things:
```
# ls /root/backup/
apt-mark.auto    crontab.tf     crontab.www-data  inxi.txt   lvs.txt     vgs.txt
apt-mark.manual  crontab.munin  df.txt            lsblk.txt  parted.txt
blkid.txt        crontab.root   dpkg.list         lshw.list  pvs.txt
```
The filenames should be sufficient for what they contain.

 If you have a DBMS, you'll want to stop it before and restart it after ... or dump the DB to a text backup file if you don't want to stop it.  The best method would be to use a volume manager, create a snapshot of all the file systems you want to backup, then backup a read-only mount of the snapshot area.  If you don't have a volume manager, you can't do that.  But you can read more about it, it isn't difficult or hard, here:  [https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](https://tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)  <--- looks like their cert expired recently. They will fix it soon, I'm certain.  Lacking that, here's another how-to from a reputable source:  [https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/](https://www.tecmint.com/take-snapshot-of-logical-volume-and-restore-in-lvm/)

---

### Post by toft6633 on 2024-08-08
Thanks a lot TheFu! I will have a closer look your post!

---

### Post by deadflowr on 2024-08-08
As far as PPAs go release upgrades don't remove anything, they only disable all 3rd party repositories including those for PPAs.

Depending on the PPA you might want to read the PPA's home page notes and descriptions because sometimes they might mention the need to run ppa-purge before attempting an upgrade.

ppa-purge is a package you can install that will revert the PPA packages to the versions in the default repositories.
it also removed the PPA source entries as well.

Any PPA maintainer worth their salt will mention that if it is needed.

---

### Post by toft6633 on 2024-08-09
Thanks,

According to  Ond&#345;ej Surý's site [https://launchpad.net/~ondrej/+archive/ubuntu/php](https://launchpad.net/~ondrej/+archive/ubuntu/php), it would be as simple as manually edit  /etc/apt/sources.list.d/ondrej-ubuntu-php-jammy.list.

Sorry for a maybe dump question: I have installed the Ubuntu 22.04 Nginx version (1.18). Can I just add Ond&#345;ej Surý's Nginx ppa repository to get a more recent version? Do I have to uninstall Ubuntu's Nginx first? I don't want to mess upp my system.

---

### Post by TheFu on 2024-08-09
I use nginx.  I use the version that Canonical provides in their repos to get the patches from a company I trust.  I avoid using PPAs, unless absolutely necessary AND always research the team behind the PPA.

As nice as a private PPA person might be, I'd rather use a PPA from the actual team behind the software.  

For example, nextcloud makes a PPA for their software.  If I wasn't happy with the Canonical version, I'd use the Nextcloud project team's PPA.  I would not use anyone else's.  I like having a team, not an individual.  

BTW, I was a cross-platform software developer for over a decade.  Mistakes happen.  For example, I once shipped a software release to a client halfway around the world using overnight shipping (considering the flight time was 16 hours just to get there) ... only to be called by them on arrival that they'd gotten the optical disc case and installation instructions, but no optical disc with the softrware.  I'd burned the disc myself ... but forgot to go and pull it from the burner and put the disc into the case for shipping.  100% accidental, but the customer really needed those updates.  Stuff like that happens when just 1 person is responsible.

Using a PPA provides root access to your system.  Would you give Ond&#345;ej Surý root on your system?  Only you can answer that. He does have a good reputation in F/LOSS and is unlikely to intentionally do anything bad, but mistakes and accidents happen.

---

### Post by toft6633 on 2024-08-09
Thanks,

I am sure you are right. I'm not an expert. I use Ond&#345;ej Surý's PPA for php since Digital Ocean and other sites recomend it. The php version in Jammy is 8.1. Maybe I could run Drupal 9 with it (released I think 2020). I'm not sure. Drupal 11 is just out. If I could run Arch on my VPS I would do that.

---

### Post by TheFu on 2024-08-09
You have to look at the complete stack that the software you need to run requires, then consider each piece, how those pieces fit and whether supporting any non-standard part of the stack is worth your time and effort.  There is often a range of versions that will work, which provides some flexibility.

We each have different levels of "hassle" we are willing to have.  For example, I'd never use Arch on any production system. In my experience, it just isn't stable enough.  I've been burned by "new" far too many times.  "Stable" is more important to me.  Over the decades, I've run lots of different distros and remember when we didn't have package manager, so everything was installed from source with me doing the dependency management manually for years.  With the major server distros and their repos, 95% of that stuff is handled for me.  Makes me happy to know I don't need to do all that work manually any more.

There are a few specific services that aren't packaged, so doing a manual install is still necessary.  When it comes to php webapps, I don't allow those onto the public internet. Access to them requires using our VPN. That drastically changes the attack surface from nearly everyone on the internet, to just our trusted employees. Of course, the VPN server has 1 port open, but we watch it for attacks very carefully.

You mentioned Digital Ocean docs recommending something.  You shouldn't take it that way.  DO pays writers for their articles, so it isn't necessarily a recommendation, just what the article author did.  Same goes for Linode, Vultr, and most other VPS providers too.

Just because someone got something to work a specific way, that doesn't mean it is secure or even a good idea.  There are lots of those articles that leave me shaking my head, no, no, no.  Admins look at things 1 way. Security people look at it a different way. Developers see it even another way.  What you want is someone with all three hats providing advice that has been reviewed by experts in each of those different areas.

Anyone can put up a blog and write articles.  Heck, my blog has over 1500 articles.  Most aren't long or all that interesting. It is a blog, after all. I try to avoid step by step instructions and concentrate on "why" different choices are important and "why not" to do certain things. Said all I had to say years ago.  Around 2008-2010, I was posting multiple articles every week.  Was on the cusp of having the site take off, but decided it was too much work for the effort. I earn more stock investing for about 10 hours of effort a month, at most.

---

### Post by toft6633 on 2024-08-13
I notice that Ond&#345;ej Surý is member of Debian developer team. [https://nm.debian.org/members/](https://nm.debian.org/members/)

---

### Post by TheFu on 2024-08-13
> **toft6633 said:**
> I notice that Ond&#345;ej Surý is member of Debian developer team. [https://nm.debian.org/members/](https://nm.debian.org/members/)

Great! Then when Debian makes a package, that's what I'd prefer over his personal PPA.  If you've validated that his PPA has exactly the same files/packages as the Debian package, then perhaps it is worth using?

I've just been burned by being on the bleeding edge and like that Canonical has a security team to look over security patches and provide their expertise to it.  Unless my server is down, I don't want to be on the newest code.  But I don't use php webapps on the internet where there seem to be high risk of compromise.

---

### Post by #&amp;thj^% on 2024-08-13
From the man himself:,  It is safe to install php from ondrej/php ppa.
[list]
WHO AM I?

   [*] I am a Debian Developer since year 2000, and I have been packaging PHP for Debian since PHP 5. That means the official packages in Debian and Ubuntu are either my work or they are based on my work. The PHP packages in my Ubuntu PPA and Debian DPA matches the official packages in Debian. Basically I am saying that you can&#8217;t get any closer than that.

Askubuntu : @oerdnj

   [*] I am a Director of DNS Engineering at ISC, Debian Developer since 2000, Ubuntu Member since 2005, founding member of Ubuntu &#268;eská Republika since 2004.

    [*] I (co-)maintain Apache2, PHP, MariaDB, Cyrus SASL, Cyrus IMAP, Berkeley DB and all things DNS in Debian and also have semi-official PPAs for those packages (PHP). I have been member of Debian GNOME GTK+ packaging team. (In other words I've seen things you people wouldn't believe. :-))[/list]

The developer is preparing a newcomer package debsuryorg-archive-keyring to automatically update the PGP key.

The apt-key list should print:
```

pub   rsa1024 2009-01-26 [SC]
      14AA 40EC 0831 7567 56D7  F66C 4F4E A0AA E526 7A6C
uid           [ unknown] Launchpad PPA for Ond&#345;ej Surý
```
Source: [https://askubuntu.com/questions/1333214/can-i-trust-a-repo-i-am-unfamiliar-with-to-provide-me-a-secure-php-8-0-package](https://askubuntu.com/questions/1333214/can-i-trust-a-repo-i-am-unfamiliar-with-to-provide-me-a-secure-php-8-0-package)

I still agree with TheFu unless you can verify the stack is identical, then it is like playing a game of chance.

---

