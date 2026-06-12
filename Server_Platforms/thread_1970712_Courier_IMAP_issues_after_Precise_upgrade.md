---
title: "Courier IMAP issues after Precise upgrade"
date: 2012-05-01
forum: Server Platforms
---

### Post by potatochip on 2012-05-01
After upgrading  from 11.10 to 12.04 it seems as though Courier IMAP is having issues.
Once I log in it seems as though the connection is dropped.
See the output below showing that I can connect, can interact with the server but can't login.

sy@twistie [505] log >nc localhost 143
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2011 Double Precision, Inc.  See COPYING for distribution information.
1 LOGIN [email]my@email.com[/email] wrongpassword
1 NO Login failed.
1 LOGIN [email]my@email.com[/email] correctpassword
sy@twistie [505] log >

I've upped the debug level for courier and here's the output of a login attempt from the mail.debug log.

May  1 19:54:31 twistie imapd: Connection, ip=[::ffff:127.0.0.1]
May  1 19:54:33 twistie authdaemond: received auth request, service=imap, authtype=login
May  1 19:54:33 twistie authdaemond: authmysql: trying this module
May  1 19:54:33 twistie authdaemond: SQL query: SELECT email, password, "", 5000, 5000, "/home/vmail", CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/'), quota, "", "" FROM users WHERE email = 'my@email.com'
May  1 19:54:33 twistie authdaemond: password matches successfully
May  1 19:54:33 twistie authdaemond: authmysql: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/home/vmail, address=my@email.com, fullname=<null>, maildir=email.com/my/, quota=0, options=<null>
May  1 19:54:33 twistie authdaemond: Authenticated: sysusername=<null>, sysuserid=5000, sysgroupid=5000, homedir=/home/vmail, address=my@email.com, fullname=<null>, maildir=email.com/my/, quota=0, options=<null>

This looks to me as though it gets authenticated but then nothing happens and the connection drops.

The weird bit is this does work perfectly for a few hours but then I start getting this problem. Restarting the courier processes doesn't fix it but a reboot of the system does until it fails again after a few hours.

There's nothing obvious in the logs and this has worked for the past five years or so.
I'm stumped as to where to look next. Does anyone have any idea on what the issue could be?

---

### Post by credomane on 2012-05-01
I'm so glad I'm not the only person suffering from this! Upgraded my dev machine everything ran fine for several hours then pushed the same updates to my production machine.

~24 hours later I'm having this exact issue on both machines.


[edit]
Well rebooting the server really does work. Ubuntu is certainly getting windows down pretty good. -_-

Back on topic I have as much debugging turned on as I can. I'll see what it tells me if it goes down again tomorrow.

---

### Post by Jliax on 2012-05-02
I am having the same issue, it will work for a few minutes/hours, then it becomes unresponsive.

Roundcube and thuderbird are both failing so I don't think it is client related.

---

### Post by potatochip on 2012-05-02
At least I'm not the only one who has this problem and I'm not the only one who's stumped by it.

What set up do you guys have? I'm using virtual domains, stored in mysql. 

I also have SquirrelMail running. It seems to run longer when I don't use SquirrelMail but I may be imagining that.

POP seems unaffected and continues to work even when IMAP dies.

---

### Post by Jliax on 2012-05-02
Yeah, the courier mail server is also still running, so no e-mail gets lost fortunately (I see it coming in while imapd is down).

I also use virtual domains, with a mysql backend, my mail is stored here:
/var/mail/virtual/.../

/var/log/mail.err shows these but they seem unrelated:
Apr 30 19:45:16 cartman imapd: tlscache.c: removing /var/lib/courier/couriersslcache
Apr 30 19:45:16 cartman imapd: tls_cache_walk: : Invalid argument
Apr 30 19:45:16 cartman imapd: tlscache.c: : No such file or directory

I also noticed that it seems to live longer when i don't use roundcube.

Both roundcube and SquirrelMail are written in PHP, so maybe the PHP-Imap driver is crashing the deamon? I am using Apache/2.2.22 (Ubuntu) and PHP 5.3.10-1ubuntu3.

---

### Post by satosh on 2012-05-02
Same here, after upgrade to 12.04.
In mail.log, everything seems to function, except after a while, when not functioning any more, the last line in the batch never show up:
"imapd-ssl: LOGIN, user=xxxxxxx, ip=[::ffff:xxx.x.x.xx], port=[51730], protocol=IMAP"
That line is there when connecting now, after a reboot, but after some hours, like you wrote, it's not there, and my email client says it could not connect to the server.

Whats happening?
Reboot has always been the trick with windows, but never once, in the last ten years I've been using linuxes as servers.

---

### Post by satosh on 2012-05-02
Seems like an old bug, reported [here]("https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756") and [here]("https://bugs.launchpad.net/ubuntu/+source/courier/+bug/987823").

Will try the supposedly working fix: to replace package "gamin" with "fam". Anxious to see the result.

---

### Post by potatochip on 2012-05-02
Thanks Satosh,

I've run;

sudo apt-get install fam
sudo apt-get install courier-pop-ssl courier-imap-ssl courier-ssl courier-pop courier-imap courier-base

I'll report back if this does the trick.

---

### Post by potatochip on 2012-05-02
Unfortunately, it seems like this didn't fix it. 

Lasted about 50 minutes before it crashed again.

Any more ideas?

---

### Post by potatochip on 2012-05-02
I'm now trying uninstalling gamin and reinstalling all the courier packages as above.
I'll report back.

---

### Post by potatochip on 2012-05-02
Only lasted 11 minutes after removing gamin before the dreaded closed connection.

Does anyone have any further ideas or any success in solving this?

---

### Post by pot_roast on 2012-05-02
No fix, unfortunately, but I am having the same problem. I first noticed it with my iPhone not being able to get mail. Then a couple hours later, it's my mail client that can't get it. Then Squirrelmail. This is a very lightly used server too, and I know that nobody else has been using webmail.

Postfix
Courier-IMAP.

I can always SEND mail just fine. Postfix is completely unaffected.

Here's what my logs look like, regardless of the device that's connecting:


May  2 22:11:24 heap imapd-ssl: Connection, ip=[::ffff:214.157.157.101]
May  2 22:11:25 heap imapd-ssl: LOGIN: ip=[::ffff:214.157.157.101], command=LOGIN
May  2 22:11:25 heap imapd-ssl: LOGIN: ip=[::ffff:214.157.157.101], username=redacted@redacted.net
May  2 22:11:43 heap imapd-ssl: Connection, ip=[::ffff:214.157.157.101]
May  2 22:11:45 heap imapd-ssl: LOGIN: ip=[::ffff:214.157.157.101], command=LOGIN
May  2 22:11:45 heap imapd-ssl: LOGIN: ip=[::ffff:214.157.157.101], username=redacted@redacted.net

I can tail the log and see the device trying to log in, but I don't get anything from it.

Mine worked longer than a few hours though.. it has been about 30 hours since I finished the 12.04 update.

Also to note that this exact same setup has worked flawless for 5 years now. I also had zero problems with 11.10.

I have disabled ipv6 entirely. I was having problems with it elsewhere. We'll see if that works.

---

### Post by potatochip on 2012-05-03
Here's a list of what's accessing IMAP. It may be worth checking to see if we have any commanalities;

Evolution
Android Mail
Squirrel Mail
Mutt
Perl scripts using Mail::IMAPClient

---

### Post by potatochip on 2012-05-03
After a bit more investigation it seems as though gamin is back on my system after I uninstalled it.

I noticed during the gamin uninstall that it uninstalled all the courier packages and also apachetop.

After reinstalling courier I also reinstalled apachetop and didn't notice that part of the apachetop installation unistalls fam and reistalls gamin.

This is probably my problem. Once again I'll feedback on if this has fixed it.

---

### Post by Jliax on 2012-05-03
Wladimir Mutel already noticed this:

"courier-imap has hardcoded dependency on gamin which asks to remove fam
when courier packages are reinstalled."

See: [https://bugs.launchpad.net/bugs/890756](https://bugs.launchpad.net/bugs/890756)

I don't think you can get rid of this, unless you compile from source yourself. I am not really familiar with strace, reporting/reopening a bug would be our best chance I think.

---

### Post by potatochip on 2012-05-03
So far so good.

It looks like courier works fine with fam. What you need to do is;

sudo apt-get purge gamin
sudo apt-get install fam
sudo apt-get install courier-pop-ssl courier-imap-ssl courier-ssl courier-pop courier-imap courier-base

Make sure you don't accidently reinstall gamin as I did by installing apachetop!

Is there a way to blacklist a package so it doesn't get installed?

---

### Post by pot_roast on 2012-05-03
The following NEW packages will be installed:
  courier-base{a} courier-imap{a} courier-imap-ssl courier-ssl{a} gamin{ab} libgamin0{a} 
0 packages upgraded, 6 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/534 kB of archives. After unpacking 1,727 kB will be used.
The following packages have unmet dependencies:
 gamin : Conflicts: fam but 2.7.0-17 is installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     fam                         



Accept this solution? [Y/n/q/?] n

---

d'oh. Fortunately, it gives an option. It will then allow you to install libfam and continue on.

I now have courier (re)installed, and we'll see what happens.

---

### Post by potatochip on 2012-05-03
Hey pot_roast how did you install courier? I didn't get asked to uninstall fam when I reinstalled the courier packages.

My mail is still working about eight hours later so looking good so far.

---

### Post by pot_roast on 2012-05-03
I try to stick to aptitude for consistency sake. :-) 

It's been a couple hours and I can still get mail. So maybe this worked.

---

### Post by credomane on 2012-05-03
I haven't had mine go down yet since I restarted the server two days ago.
I'm running postfix and courier with ssl only authentication. User logins and forwardings are stored in mysql.

```

May  3 16:11:23 srv1 imapd-ssl: Connection, ip=[::ffff:205.201.126.66]
May  3 16:11:23 srv1 authdaemond: received auth request, service=imap, authtype=login
May  3 16:11:23 srv1 authdaemond: authmysql: trying this module
May  3 16:11:23 srv1 authdaemond: SQL query: SELECT email, "", password, 999, 999, "/var/vmail", CONCAT(SUBSTRING_INDEX(email,'@',-1),'/',SUBSTRING_INDEX(email,'@',1),'/'), quota, "", "" FROM users WHERE email = 'credomane@somewhere' 
May  3 16:11:23 srv1 authdaemond: authmysql: sysusername=<null>, sysuserid=999, sysgroupid=999, homedir=/var/vmail, address=credomane@somewhere, fullname=<null>, maildir=somewhere/credomane/, quota=10485760, options=<null>
May  3 16:11:23 srv1 authdaemond: authmysql: clearpasswd=StopLookingAtMyPassword, passwd=<null>
May  3 16:11:23 srv1 authdaemond: Authenticated: sysusername=<null>, sysuserid=999, sysgroupid=999, homedir=/var/vmail, address=credomane@somewhere, fullname=<null>, maildir=somewhere/credomane/, quota=10485760, options=<null>
May  3 16:11:23 srv1 authdaemond: Authenticated: clearpasswd=StopLookingAtMyPassword, passwd=<null>
May  3 16:11:23 srv1 imapd-ssl: LOGIN, user=credomane@somewhere, ip=[::ffff:205.201.126.66], port=[60896], protocol=IMAP

```

Sadly the is the most I seem to be getting from the logging I have enabled. I'll let things run for a week before I turn the logging off again.

---

### Post by speedy400 on 2012-05-04
Same problem here. I dist-upgraded one server and it lasts about an hour or two. 
Did a fresh install on another server with 12.04 and it is also showing the problem after about 8 hours- unable to login.

I tried:
sudo apt-get purge gamin
sudo apt-get install fam
sudo apt-get install courier-pop-ssl courier-imap-ssl courier-ssl courier-pop courier-imap courier-base
 
and so far it is working on one system but need to give it a day or two. 

Is an update available yet?

Is this an apparmor, courier-imap, fam or gamin issue?

---

### Post by potatochip on 2012-05-04
I've been up now for over a day which is the longest since I upgraded so this looks good to me.

Speedy I'd say this is probably a gamin issue as replacing gamin fixes the problem.

I'm going to mark this as solved. Thanks for all your help guys!

---

### Post by credomane on 2012-05-05
This is indeed a gam_server issue!!! My server just did it again. ```
sudo killall gam_server
``` Then attempting to login again worked! Didn't even have to restart any of the services. I also noticed that restarting all of the mail services does NOT restart gam_server.

So for everyone here that is replacing gam with fam and it doesn't work make sure you kill off gam_server manually or just restart your server.


[edit]
Seems this bug has been around for awhile.
[https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756](https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756)

---

### Post by Jliax on 2012-05-08
I've used there commands:

sudo apt-get purge gamin
sudo apt-get install fam
sudo apt-get install courier-imap-ssl courier-ssl courier-imap courier-base

And am running stable for 4 days now.

But then again, Wladimir Mutel on [https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756?comments=all](https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756?comments=all), has 12293 files in his ~/Maildir/cur , and gets FAM timeouts, so watch out.

Also gamin is said to be better than FAM.

---

### Post by pot_roast on 2012-05-08
> **Jliax said:**
> 
But then again, Wladimir Mutel on [https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756?comments=all](https://bugs.launchpad.net/ubuntu/+source/courier/+bug/890756?comments=all), has 12293 files in his ~/Maildir/cur , and gets FAM timeouts, so watch out.

Also gamin is said to be better than FAM.


I only have 144 files in my /cur folder and was getting the timeouts with gamin. Almost 1 week now and no issues once I went to fam.

---

### Post by potatochip on 2012-05-15
Still up and running after over a week :)
Thanks again guys!

---

### Post by mlentink on 2012-05-19
I don't know what I was doing, but this did get my server back up again. 

Thank you guys!

---

### Post by cdean on 2012-06-10
Encountered this problem on a new 12.04 server after moving a configuration over from an old 8.04 server. Troubling and frustrating!

---

### Post by cjmoretti on 2012-06-12
ok, tks

---

### Post by Malac on 2012-06-13
Same issue here after upgrade from 11.10 to 12.04 the courier and gamin worked perfectly on 11.04. I also use another program that relies on gamin and have had to do a workaround for that one as well.

Installing fam got me up and running but now I get loads of:```
imapd-ssl: pmap_getmaps.c: rpc problem: RPC: Unable to receive; errno = Connection reset by peer
imapd-ssl: last message repeated ....[number].... times
``` in my mail.log and messages when picking up mail in Thunderbird complaining "Filesystem notification initialization failure -- contact your mail administrator (check for configuration errors with the FAM/Gamin library)". Though at least mail is being picked up.

---

### Post by jmaccelari on 2012-06-18
Ditto here on upgrading from 10.04. The fix appears to have worked.

Thanks.

---

### Post by nikaein on 2012-06-29
it's enough to install libfam0 not fam
in this way, you can install them with aptitude too

---

### Post by nikaein on 2012-07-02
hi,

but fam needed for notification initialization. so you need to install fam too :) :-"

---

### Post by markvalley on 2012-07-13
This is strange... 

I had the same problems here and solved it purging gamin as said.
Now, about 1 month later it is happening again! Killing gam_server would solve it. 

As i purged gamin, gam_Server should not disapear?

---

### Post by lister171254 on 2012-07-14
Have not had any problems until about two days ago. 

Running sudo killall gam_server fixes this temporarily, but wish there was a proper suported fix

Cheers

---

### Post by bluexmas on 2012-07-16
amazing, I have a fresh install of ubuntu server 12.04 and I encounter this issue. I have to reboot daily in order to have my squirrel mail working. is there any bug reported?

---

### Post by bluexmas on 2012-07-16
eventually can somebody notify canonical about this issue? or I have to reboot in cronjob like twice a day? :)

---

### Post by potatochip on 2012-07-16
Just remove gam as instructed above then you won't need to kill all or reboot. Just ask if you need help to do this.

---

### Post by bluexmas on 2012-07-16
what are the exact steps to do this again, please? thank you.

---

### Post by bluexmas on 2012-07-17
hello again. I don't think replacing gamin with fam is a final solution. but as I checked, there seems to be a proposed update on gamin that will fix the issue (correct me if I am wrong, please) :

[http://www.ubuntuupdates.org/package/core/precise/universe/proposed/gamin](http://www.ubuntuupdates.org/package/core/precise/universe/proposed/gamin)

in this case, can the affected guys try to install 0.1.10-4ubuntu0.1 version of gamin from proposed and see if the issue is fixed?

I haven't encountered the issue yet, from the reboot I did last evening. I am still waiting for it to appear, in order to debug it.

Here's the guide to install the proposed gamin package:

[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

---

### Post by paulinoruiz on 2012-07-17
I have same problem after update these solutions not works:

[LIST]
[*]use fam instead gamin
[*]reduce amout of message in mailboxes
[/LIST]

Now I am restarting fam and courier each 5 min with the script:

```

while [ 1 ]; do
  /etc/init.d/fam restart
  /etc/init.d/courier-imap restart
  /etc/init.d/courier-imap-ssl restart
sleep 600
done

```

I will try proposed gamin

---

### Post by potatochip on 2012-07-17
Just remove gam as instructed above then you won't need to kill all or reboot. Just ask if you need help to do this.

---

### Post by bluexmas on 2012-07-17
> **paulinoruiz said:**
> I have same problem after update these solutions not works:
I will try proposed gamin

it still didn't crashed yet , since yesterday evening. and this with old gamin. I am looking forward about your result with proposed gamin.

---

### Post by paulinoruiz on 2012-07-17
Using new gamin courier does not lock but I have other problems. Some accounts cannot read imap folder, outlook respond:

"Fatal error: Invalid argument using IMAP"

I think the problem is in courier, courier imap crashes with some emails.

I have removed one file in maildir/cur, after this Outlook, Thunderbird and webmail can read inputbox.

When put the file it crash again and any IMAP client can read the folder. I have detected more files in others maildir folders. I am finding out if it is an old courier bug related with UTF encoding...

I'm a bit lost, from saturday I cannot solve the problem. I am thinking use dovecot instead of courier, my server uses virtual mail accounts based on mysql and it is hard to change.

Any idea? I dislike dovecot...

---

### Post by bluexmas on 2012-07-17
these problems didn't appeared with old gamin version? eventually of you backup all folders and then erase them, to create fresh new ones doesn't solve the issue you now have?

I reinstalled my server with a fresh precise version, but copied old folders of vmail from 10.04. I didn't encountered any issue, until yesterday with the lock. weird thing, after 2 reboots, it doesn't lock anymore...

---

### Post by paulinoruiz on 2012-07-17
Hi,

 The problem with IMAP folders happens with the two versions of gamin.

 I deleted some Maildirs and created it again and the problem persists.

 I have installed and configured dovecot and the IMAP folders can be read by clients. I confirm that there was an message with not valid characters in subject, but the message is retrieved by outlook without error.

Now I'm going to wait one day with this configuration.

---

### Post by bluexmas on 2012-07-17
thank you for your feedback, I understand the new gam version solves the lock issue. 

regarding your problem, I have no solution in mind. if you try with 777 permissions all folders, it still persists? if yes, it's possible to enable imap logging and get more clues from mail.log?

LE: now I see you switched to dovecot. I have 0 experience using dovecot, so I can't say more. hope all will work well now.

now with the lock issue confirmed as solved in the proposed gamin version, I'll wait for the canonical good folks to push it to the main repo. :)

Thank you,

---

### Post by bluexmas on 2012-07-20
gamin is fixed, for precise :)

Changed in gamin (Ubuntu Precise):
status:	 Fix Committed &#8594; Fix Released

---

