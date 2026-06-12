---
title: "Cloud backup service accessible through the file system or FTP?"
date: 2015-05-09
forum: Ubuntu, Linux and OS Chat
---

### Post by AleveSicofante on 2015-05-09
I'm researching the best backup cloud service for my needs. I'm leaning towards Crashplan, but iDrive, SpiderOak and SOS Online Backup all look good to me for different reasons.

However, what I dislike about all these systems is that they force me to use their own tools for backup (and some of them don't support Linux, by the way). I'd like to use Ubuntu's default backup tool, or whichever I like. That would be easily done if I could just mount a remote folder in my system and use it for backup or if it was accessible via FTP or other standard way.

Does anybody know about any service that will allow me to simply put the proper line in the fstab file and backup to it?

---

### Post by papibe on 2015-05-09
Hi AleveSicofante.

How much data are we talking about? What is your budget?

A couple of thoughts...

You can roll your own solution on the cloud. You can get a VPS/droplet and use standard tools to backup to it (rsync/sftp/scp/ftp etc).

You may also set up [Owncloud]("https://owncloud.org/") (on the repos), or use one of their official [providers]("https://owncloud.org/providers/"). If I remember correctly, you can use WebDAV to mount a remote directory and then use any tool to backup to it.

Hope it helps. 
Regards.

P.S.: you can also take a look at Amazon services, I believe you can rsync to S3 .

---

### Post by AleveSicofante on 2015-05-10
> **papibe said:**
> How much data are we talking about?
1TB is more or less the typical offer from these services and I would aim for that, but I could live with half of that perfectly well.

 > What is your budget?
Some $50/year, 10% up or down.

> You can roll your own solution on the cloud. You can get a VPS/droplet and use standard tools to backup to it (rsync/sftp/scp/ftp etc).
I'd do that if my budget was a little higher. A reliable VPS with enough storage won't go below twice as much as my budget. At least I haven't found any I can trust enough for about $5/month.

> You may also set up [Owncloud]("https://owncloud.org/") (on the repos), or use one of their official [providers]("https://owncloud.org/providers/"). If I remember correctly, you can use WebDAV to mount a remote directory and then use any tool to backup to it.

That sounds interesting and exactly what I would like to do. Past Owncloud releases were terrible IMO, but I just tried version 8  last week on its demo site and found it very fast and much nicer in  general than last year. I'm not convinced by Owncloud's security model (server side only), but it might be outweighted by the convenience of its web access. I'll check that list of providers and see what I can find.

Another two requirements I have are "no file size limit" and "no  throttling" (I have a 200 Mbps symetrical fiber connection and I want to  use it fully!)

> you can also take a look at Amazon services, I believe you can rsync to S3 .
Don't quite like the pricing model, but I'll try to simulate my usage and see what the cost would be.

Thank you very much for your suggestions!

---

