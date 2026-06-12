---
title: "Server with planned short uptime?"
date: 2010-07-27
forum: Server Platforms
---

### Post by HankB on 2010-07-27
I've installed Ubuntu server on a small box with a couple of large hard drives to use as a remote backup server. Since my backups will run nightly in the wee hours, I'm configuring this to use Wake-on-LAN to start the server and run the backup. Once the backup completes - probably on the order of an hour later - another script shuts the server down.

Once in a while I'll remote in to update packages and check on the status of the system, though I can check backup logs to insure that is still running.

Need I be concerned about the various cron jobs that periodically run to tidy things up? Should I periodically - say once/month - leave the system up for a full day to make sure that everything that needs to happen will run?

thanks,
hank

---

### Post by Thirtysixway on 2010-07-27
Personally I wouldn't be too worried.  The server is only being used to store backups.  You could leave it on say the first of every month just to let things run and install software/security updates.

---

### Post by drdos2006 on 2010-07-27
Check this out, it may answer a lot of your questions.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood



regards

---

### Post by arrrghhh on 2010-07-27
> **drdos2006 said:**
> Check this out, it may answer a lot of your questions.


regards

Ugh, these cookie cutter posts you put up drive me crazy.  This how-to I'm sure is good, but it can't possibly be the answer to everyone's questions!!

Sorry, just had to say something about it.  Back to the OP's question...

What do you have listed in cron?  Is it mysql cleanup stuff or what?  It really depends on what you have scheduled to run there.  It sounds like it may not be necessary, but it really depends on what services you're running/what cron jobs are scheduled to run.

---

### Post by drdos2006 on 2010-07-27
Use Webmin once a month to update security.

regards

---

### Post by HankB on 2010-07-27
Thanks for the replies folks.

This is 'server' only in that it doesn't include any X/desktop stuff. It's headless. No Apache, Mysql, etc. The only thing out of the ordinary is rsync running as a daemon along with ssh to provide the connection.

thanks,
hank

---

### Post by arrrghhh on 2010-07-27
> **HankB said:**
> Thanks for the replies folks.

This is 'server' only in that it doesn't include any X/desktop stuff. It's headless. No Apache, Mysql, etc. The only thing out of the ordinary is rsync running as a daemon along with ssh to provide the connection.

thanks,
hank

So I'm confused... you said this in the first post: > Need I be concerned about the various cron jobs that periodically run to tidy things up? - So do you not have any cron jobs listed?  Not sure why you even mentioned this part.  This is what made me think you had cron jobs in the first place :P

So yea, if the only cron job is your rsync backup script, then there really isn't anything to worry about!!

---

### Post by CharlesA on 2010-07-27
As long as the only services running are rsync and ssh, you should be fine with using Wake-on-LAN and then having it shutdown after the backup is done.

Personally, I would just leave it on 24/7 to help keep thermal shock down, but that would increase cost and whatnot due to it running all the time.

Sounds like your idea will work well. :-)

---

### Post by HankB on 2010-07-27
> **arrrghhh said:**
> So I'm confused... you said this in the first post:  - So do you not have any cron jobs listed?  Not sure why you even mentioned this part.  This is what made me think you had cron jobs in the first place :P

So yea, if the only cron job is your rsync backup script, then there really isn't anything to worry about!!I think I'm the one confused. I thought that there were process that run periodically to do things like roll over log files, renaming and/or deleting old ones. But I don't see anything listed in cron for root. That's the kind of stuff that I was worried about.

thanks,
hank

---

### Post by arrrghhh on 2010-07-27
> **HankB said:**
> I think I'm the one confused. I thought that there were process that run periodically to do things like roll over log files, renaming and/or deleting old ones. But I don't see anything listed in cron for root. That's the kind of stuff that I was worried about.

Ah, I see!  No worries at all then, you are fine.

---

### Post by tgalati4 on 2010-07-28
acron takes  care of postponed (asyncronous) cron jobs.  Used for laptops after they come out of suspend.

---

### Post by kevinthecomputerguy on 2010-07-29
arrrghhh hates me :- )

---

### Post by arrrghhh on 2010-07-29
> **kevinthecomputerguy said:**
> arrrghhh hates me :- )

Huh?  Where'd that come from.  I don't like a lot of people, but I don't think I've ever had a problem with you.

Also, why the heck would you even post this?  Even if I did in fact hate you, it's a little off-topic don't you think?

---

### Post by kevinthecomputerguy on 2010-07-29
Just trying to make you laugh.
 
I am woodel.com 
 
Seemed funny at the time, sorry for the off topic joke. I need to stop replying from my backberry during happy hour :- )
 
take care
-Kevin

---

### Post by arrrghhh on 2010-07-29
> **kevinthecomputerguy said:**
> Just trying to make you laugh.
 
I am woodel.com 
 
Seemed funny at the time, sorry for the off topic joke. I need to stop replying from my backberry during happy hour :- )
 
take care, laugh once and awhile
-Kevin

...

---

### Post by kevinthecomputerguy on 2010-07-29
I apologies, seemed funnier a few minutes ago.

---

