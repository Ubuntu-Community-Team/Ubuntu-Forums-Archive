---
title: "One-time server replication to dissimilar server"
date: 2015-08-30
forum: Ubuntu Cloud and Juju
---

### Post by d.vanheeckeren on 2015-08-30
Hello everybody...  been going at this in my spare time for weeks... but to absolutely no avail because of my specific situation.

So here's what I originally had:
A REALLY OLD Dell Dimension that has been running my email, web, ftp, ssh, vpn, and a couple proprietary items since forever ago.

Here's what I have now:
I upgraded one of my desktops and want to move my old server to machine not being used now.  (hp 3ghz w/4gb ram & gigabit nic).

Here's what I'm looking to do:
I have installed Ubuntu server (14.04) on the 'new' server where I want everything to move to.  The old server is the same version.  The problem is, the hardware is drastically different on both machines, as is the storage for the many websites it serves (those are stored on a separate SCSI disk mounted in '/media/data'.  Websites aren't huge, and it would be simple to move just those files over to the new machine.

Here's my problem:
I'm looking for an easy way to sync all the packages and configuration of the old server to the new one, and essentially 'clone' the services and configurations (users, email, virtual servers, entire home directories, etc.).

Is there any easy way to do this or am I just going to have to hunker down and spend three days installing packages and copying config files and data one bit at a time?

Thanks in advance for any help you may be able to provide.  :o)  And if I seem like a newbie, I'm sorry... I'm definitely not an expert, but am trying to present my problem and requirements for a solution in an easy to understand manner.  Hope I did!  :o)

[Edit]  This doesn't need to be synced permanently...  this is just a one-time migration I'm looking for, not cloud capability or HA or anything like that...  if I can just get everything moved over easily just one time, that's all I'm looking for.

---

### Post by SeijiSensei on 2015-08-30
Read the parts of the man page for dpkg that cover the --set-selections and --get-selections options.  They let you compile a list of installed packages on one machine and tell another to install the packages on the list.

You'll need to migrate parts of /etc as well depending on what you are running.  Directories like /etc/apache2 and /etc/postfix are good candidates.  Do you have anything in /usr/local?  And, of course, you'll need to migrate /home.

---

### Post by tgalati4 on 2015-08-30
One-at-a-time.  You will spend some Agony Units on this.  I would have just swapped hard drives to see if the new machine booted with the old disk--just for grins.  

Keep the old system running on your network.  Create new services on the new machine--one at a time and research migration methods for each service.  Once you have your new service configured the way you want, shut down the old service.  After a few months all of your services will be migrated.  But I would keep the old machine as a backup server, just clean it out and keep it off.  If it is out-of-support, then I would migrate to the next LTS that your old machine can handle.  Because it was running forever--it's a keeper.  It may not be shiny, but it works.

---

### Post by TheFu on 2015-08-30
I'd use dpkg as stated above and use rsync to mirror everything over to the new machine. Be certain to quiesce any running DBMS.  If the files are in the same place on the new machine as the old one - all should be fine.  

Honestly, I'd just connect a new disk to the old system and rsync the complete OS - then fix the fstab and udev/70-network rules. Lastly, I'd move it over to the new machine and boot.  I've done this at least 10 times over the years. The worst thing that would happen is grub would need to be fixed. If both machines are BIOS boot - it is trivial (because I know how to do it). Moving from a BIOS to UEFI boot system is harder, because I don't know all the difficulties.  My single UEFI boot system is running in BIOS-only boot mode. I didn't see any reason to switch.

Actually, this is the perfect time to get your backup + restore processes working perfectly. Use it.

---

### Post by d.vanheeckeren on 2015-08-30
Holy crap...  I'm pleasantly shocked!  :o)  Usually when I ask a question on a forum like this, it's usually days or weeks before I get any kind of response.  So right up front, THANK YOU!!

SeijiSensei-Thanks for the tip on the man pages... that will be VERY helpful to make sure all the packages are the same!  They're both running Ubuntu 14.04 LTS, and I keep them both updated while I'm playing with this, so I think this will fit part of what I want to do perfectly!

tgalati4- Well I don't want to just swap hard drives...part of that is because I want to keep the larger drive in the newer one for more space.  That doesn't mean, however, that I can't bring down the runlevel and dd the old disk to the new and resize it later if it boots on the new machine.  In fact, I think I might have a 1TB Barracuda laying around somewhere, seem to remember somebody had given me one...if that's the case, I'll image to that and see if it works...  if it does, then hey, more space on the new server.  *LOL*  However, I definitely don't want to be doing this for months...  There's nothing critical on this machine, it just makes my life and my work very convenient.  So if it really came down to it, I'd rather spend three days installing/configuring everything manually than deal with it for months.  But I will definitely try your suggestion (with the imaging exception) to see if it works...if it does, that would be the quickest, simplest solution.

TheFu- I'm not sure I'm familiar enough with fstab to fix it.... and I've seen udev before, but have no practical knowledge in working with it.  Now grub I've done many times before, that I can handle.  *LOL*  The new system was originally UEFI boot, but that's the first thing I did when I got it was re-enable the BIOS boot.  When I first got the machine, it had Windows 8.  As you can imagine, the very first thing I did was downgrade to seven with half the hard drive...and then ubuntu'd the other half of it.  :D

Thank you guys so much for your help!  You've helped me put a plan of action into place, which I will begin on this evening.  You guys are awesome!

---

### Post by TheFu on 2015-08-30
You got the "A" team here with SeijiSensei and tgalati4.  I wouldn't use dd for copying files from different disks to a single disk.  I'd use **rsync -avz**.  Because it works at the file level, not the partition level, you don't need to make partitions.

If you want to keep the exact same partitions as currently spread across other disks, then dd (rather ddrescue) is a great way to go.

If you'd like more detailed help, please post the output from **sudo parted -l** and **df -h** and **lsblk** from the old server. I think those should answer any questions we might have about the storage.

Avoiding UEFI for this transition is probably easier. fstab is pretty easy. There is a manpage for it. ;)  /etc/udev/rules.d/70-persistent-net.rules just needs the old line with the old MAC removed so the old eth? interface can be used. Otherwise it will be held and a new interface will be generated.  That isn't a big deal, but remembering to type eth1 instead of eth0 all the time will get old.

BTW, I use the dpkg --get-selections/--set-selections trick for my daily backups - I store that output in a place that gets backed up.

---

### Post by SeijiSensei on 2015-08-31
> **TheFu said:**
> You got the "A" team here with SeijiSensei and tgalati4.
Can I be Hannibal?  I always liked George Peppard though that wasn't one of his better roles.

I'd recruit you for our team, too!

---

### Post by d.vanheeckeren on 2015-08-31
*LMAO*

Well, since Murdock here is a n00b when it comes to dpkg, I didn't get hardly anything from reading the manpages... however, after much reading on Google, I finally figured out how to create the list, move it, and the packages are installing now on the new server.  Once this is done, I'll begin my delve into rsync.  Thanks for all the help so far, gentlemen!  I'll keep you updated!  :)

---

### Post by d.vanheeckeren on 2015-08-31
Ok, so far so good up until now...

rsync doesn't want to sync files because of my user permissions.  Everybody always warns everywhere to leave root login disabled, and that's the only thing I can think of that would let it happen.  Any workable suggestions on that?

---

### Post by TheFu on 2015-08-31
sudo -s
rsync ....

---

### Post by d.vanheeckeren on 2015-08-31
Ah, I see what you mean.  I had already sudo su'd to root, and was operating as root on the old server.  The new server, however, doesn't allow login as root, and therefore limits permissions outside of my username's home directory.  I did add my username on the new machine to the root group, but with all the warnings I've seen everywhere, didn't think I should enable root login.
I may have found a different way, though...  just doing some research before I do it.  :)  Again, I'll keep everyone updated.

---

### Post by tgalati4 on 2015-08-31
"I pity the fool who wants to migrate his server. . ."  The only reason it takes months is because things crop up with the migration that you won't see right away.  Sure, 3 days you can have it up and running, but when something breaks 2 months later--and you have dismantled your old server, so now you are stuck trying to fix a service without a working/familiar backup.

In my years of building linux systems, I have a personal rule:  "Never trash a working linux system."

And I do wear a gold chain.

---

### Post by d.vanheeckeren on 2015-09-03
Hi guys!

I wanted to thank you all for your help! I ended up using a combination of advice here, and eventually got everything moved.

What I ended up doing was making a tarball of all the data I had on the server, copied it to the new machine, and untar'd it (after replacing the hard drive with a 1TB I had laying around and reinstalling Ubuntu Server on it).  I didn't copy the system directories, just the data. I then took the suggestion of the --set-selections and --get-selections in dpkg to make sure all the required packages were installed, even though it took me a bit of research to figure out how to use that feature in dpkg.
Now all my configuration files I thought were going to be the tricky/time consuming part. BUT, Webmin came in VERY handy with that, with the backup/restore configs feature.  I simply backed up configs on the old machine, downloaded it through the browser, and then uploaded it to the new one and restored using the restore feature.  It copied all the users and groups for me, too!
The only thing that took me forever was the email... I didn't want everyone to lose the emails they'd already had. And man, I fought with this for a couple days! All because everywhere I'd read kept telling me that mail was stored in /var/spool/mail. I was so deep into the problem that I couldn't see the obvious...the 'spool' part of the path. That should have told me that it's a TEMPORARY holding place for mail. I didn't realize until much later while exploring the /var directory that my mail file in /var/mail was 48mb, while the one in /var/spool/mail was only something like 4K.

But immediately after kicking myself in the ashtray for not realizing that 'spool' never clicked with me (that's a rookie mistake even for my 30+ years of Windows experience), I tarred and transferred those files over as well, rebooted, and voila! Did one final check to make sure everything was up to date (mainly the sql databases I had to transfer individually because I didn't want to up my php upload limit because of other users), then redirected all the necessary forwarded ports in my router to the new server and shut down the old one, but left it connected just in case.  And so far, so good! Haven't found anything yet that I've missed... but will give it a few weeks to see if anything crops up before I disconnect that old powered-down server and stick it in my office closet.

So it was quite an adventure, and I couldn't have done it without you guys, so thanks for all the help! I know it gets irritating when people won't do research and try to figure things out for themselves, and I did my best not to be one of those people...so hopefully I didn't irk anyone.

Thanks again!

---

### Post by TheFu on 2015-09-03
30+ yrs with Windows means next to nothing with Unix.
Tar - ouch. Guess people still use that and still teach it. Think the last time I created a tar/tgz file was about 8 yrs ago.  rsync is easier for me and behaves like I'd expect.

Did you mention it was an email server?  There are many different types of email servers. Old school ones use /var/spool/mail and store messages in each userid's HOME. My mail system doesn't do that and keeps messages in mariaDB. I wouldn't want to assume anything about an email server here. There are just too many possible ways to accomplish it. Flexibility is a cornerstone for Unix. 

If you'd like to preempt the next time something complex happens and have a leg up - [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good book to start. Free, no-hassle, download. Read the 1st 240 pgs and skim the rest just to see what it has.

Webmin - I'll just say, I don't know **any** Linux gurus who use it and there is a good reason.

---

### Post by tgalati4 on 2015-09-03
"I pity the fool who uses webmin."  Glad you got it sorted out.  Let us know what other server mishaps happen in a few months.  When you haven't used Windows in 10 years, you forget how the rest of the world thinks.

---

### Post by d.vanheeckeren on 2015-09-03
TheFu:  Yeah I definitely know what you mean... only been using linux the last few years, and most of my use has been with a gui on the desktop version. Which I do love, BTW! But I'm definitely not a guru. *LOL* I didn't know that Webmin was bad... any info on what's bad about it? So far, it's only made my life easier. As you can imagine, with seven boys, three girls, a local business, an online business, and a wife that works overnight (but doesn't drive) gives me precious little spare time.  :/  But I'm with linux to stay... just have a lot of learning to do.  :)
And not sure if I mentioned it was an email server or not, but it runs postfix as the transport and dovecot as the imap/pop3/smtp. And many of my users wanted webmail, so I set up RoundCube which took some reading but I wasn't in a rush then (last year) because the kids were all gone for a week on vacation.  *LOL*  Best vacation I've ever had, sitting at home doing whatever I want in complete and utter peace and quiet.  :D
[Edit] Side note... I couldn't get rsync to work. I'm sure it was something I wasn't doing right, though, it obviously wouldn't be so popular if it didn't work...

tgalati4:  ^^ see above for Webmin question... *LOL*. So far, haven't had any kinds of problems other than having to remove the volume group data from the old server, otherwise it would just wait for the device to become ready instead of booting, and I'd have to hit 's' to skip it. Beyond that, everything is working so far...hopefully it lasts!  *LOL*

---

### Post by SeijiSensei on 2015-09-04
> **d.vanheeckeren said:**
> I didn't realize until much later while exploring the /var directory that my mail file in /var/mail was 48mb, while the one in /var/spool/mail was only something like 4K.
Actually both /var/mail and /var/spool/mail point to the same location.  /var/spool/mail is a "symbolic link" to the directory /var/mail. (Think of "symlinks" as a more sophisticated version of a Windows "shortcut.")

---

### Post by TheFu on 2015-09-04
Windows shortcuts aren't part of the file system.  Symbolic links ARE.  I remember being excited when MSFT added "libraries" thinking they'd finally added symlinks.  They hadn't and nothing worked in the cmd.exe shell. Fail.

Symbolic links are really stupid, but that is their genius. Hardlinks are great too, but only work on a single filesystem/partition. Symbolic links are only 1-sided - don't track what they point at. Of the target of the symlink is gone, it will fail.  OS/2 had 2-way links which was amazing for the time. These were more than hardlinks, which is just a reference count for file handles pointing to data on disk. If the link was removed on 1 side, then the other side was removed too. Different than hardlinks, but hardlinks have limitations - they only work within the same file system.

---

### Post by d.vanheeckeren on 2015-09-09
Yeah, symlinks are something I'm pretty sure I understand for the most part.  That's how I'd used my SCSI 15K drive in the old server to store backups of the websites and databases on a daily basis.

But tgalati, it does still kind of concern me that you mentioned you pity people who use webmin.  Are there security concerns I should know about?  Of the research I've done since you said that, I haven't found any security holes so far that haven't been fixed.  Are there some I don't know about, or other problems with webmin that would give me reason not to use it?

---

### Post by d.vanheeckeren on 2015-09-09
Oh, and SeijiSensei, thanks for the heads up that /var/spool/mail is a symlink.  That does concern me also, because if I recursively copied the directory, I would have thought that the symlink target directory would have been copied too.  Unless I made a mistake there too, which is entirely possible.  *LOL*

---

### Post by TheFu on 2015-09-09
Recursive copies handle links differently - it depends on the tool used. Check the manpage to see how symlinks are handled or which options need to be added/removed to get the handling you want, from which ever program used.

Symbolic links are just a file to most of those programs, so the link would be copied, not the contents it points at. Some tools may handle links differently by default - i dunno. Again, review the manpage for the tool used - look for "link" and/or "dereference" inside.

Some file systems do not support symlinks - sshfs for example.

---

### Post by tgalati4 on 2015-09-10
[Webmin]("http://www.webmin.com/security.html") is only as secure as the web-server that runs it.  So, if you are running a personal webpage that is exposed to the world, then running webmin does not add a lot of additional security risk to the server.  If you are not serving web pages, then adding webmin adds another vector of attack to your system.  

If your server is for in-home use only, and you only need to access it remotely when traveling, then using ssh with RSA keys and passwordless login and port knocking which moves ssh's Port 22 to some random port for a short period of time gives you better security than having webmin running all the time and port 80 being left open to the world.  Even if port 80 is closed to the outside, an inside breach of a Windows machine could allow that machine to hack into webmin from inside your LAN.  So for these and other reasons, webmin is not the first choice for server admininistration.

And if you didn't understand anything I said above.  Don't worry about it.

I haven't used webmin for years, so perhaps it has been patched and is no longer a security issue.  I'm just comfortable with using the command line for server administration.  Use what works for you.

---

