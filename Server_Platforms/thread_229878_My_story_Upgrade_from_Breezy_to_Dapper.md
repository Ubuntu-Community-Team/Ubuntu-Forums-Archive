---
title: "My story: Upgrade from Breezy to Dapper"
date: 2006-08-05
forum: Server Platforms
---

### Post by Sam on 2006-08-05
I have a old box at home which runs Ubuntu (server install). I own a domain name, too, and I use this computer as mail server (my personnal mails go here), SSH and NFS (I store some files I access through local network and from the web), web server (which I never use) and MLDonkey client.

I've installed my server with Breezy. Last day I thought about dist-upgrading it, but I was septic. Although I use it only for personnal use, I didn't want to spend hours repairing if something goes bad.

After checking some apps for their new version number, I told myself that I REALLY need to do a dist-upgrade. Lots of them where totally outdated.

I did a dd of my system. Just in case of a big crash. Then I upgraded my system to the last Breezy version. 3 minutes of downloading, nothing special happens.

Now the big part. I updated the apt sources.list to dapper, then did apt-get upgrade. A lot was downloaded, packages were installing and during the installation of mldonkey-server, dpkg-reconfigure printed an error and exited, telling me that courier-imap and courier-imap-ssl weren't upgraded, too. Damn, why these one ? And why did MLDonkey crash ? The error message wasn't very explicit, so I tried to manually reinstall these three packages. Same problem. So I googled a bit and found that MLDonkey goes mad if the old app directory exists when upgrading. I renamed this directory, apt-get install --reinstall'ed only mldonkey-server and bingo, that worked. I diff'ed and updated the config files after that.

For Courier, it complained about a service already running on its tcp ports. So I stopped any courier daemon. I redo'ed the apt-get stuff, and the same error occured. I discovered that... courier was using the ports. Strange. This time I had to reboot the computer to get it work.

Ok, this time no more errors with apt-get. Everything is upgraded. Now the tests part.

SSH/NFS: Both ok.
Apache: No problems, but no major changes.
MySQL: Same as apache.
Postfix/Courier/Amavis stuff: Sending/receiving ok, mail filters ok.
MLDonkey: I was very impressed with this one. It was a major version update. Now I have a lot of sources for the files, and it download much faster than before.

I did only small checks, but everything I use is alright by now. The two problems I had were fixed very quickly. What a great feature is the package system !!

Thanks for reading !

---

