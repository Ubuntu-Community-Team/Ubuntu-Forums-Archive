---
title: "Problem with sending/receiving emails (Postfix/dovecot)"
date: 2016-11-02
forum: Server Platforms
---

### Post by sobeksson on 2016-11-02
Hi Everybody,

I have a problem with sending and receiving emails on my old Ubuntu 10.04.4 LTS mail server. Im using postfix/dovecot there.

Problem started when I overlooked that the /var is already full and there is no free space.

So, I deleted some old emails (apx. 1GB) I didnt need, but still even though I rebooted whole server, It didnt start working.

---------------------------------------------------------------
Souborový systém            Velikost Užito Volno Uži% P&#345;ipojeno do
/dev/mapper/server-root
                      9,2G  1,6G  7,2G  18% /
none                  2,0G  228K  2,0G   1% /dev
none                  2,0G     0  2,0G   0% /dev/shm
none                  2,0G  308K  2,0G   1% /var/run
none                  2,0G     0  2,0G   0% /var/lock
none                  2,0G     0  2,0G   0% /lib/init/rw
/dev/mapper/server-home
                       28G   28G     0 100% /home
/dev/mapper/server-var
                      413G  391G 1007M 100% /var
/dev/md0p1             97M   81M   11M  89% /boot
------------------------------------------------------------------

So I checked the mail.log and there are these logs. And I dont know what to do next.

Nov  2 13:51:44 mailsrv postfix/tlsmgr[2938]: fatal: open database /var/lib/postfix/smtpd_scache.db: Invalid argument
Nov  2 13:51:45 mailsrv postfix/master[2933]: warning: process /usr/lib/postfix/tlsmgr pid 2938 exit status 1
Nov  2 13:51:45 mailsrv postfix/master[2933]: warning: /usr/lib/postfix/tlsmgr: bad command startup -- throttling

Thanks for help! :)

Jirka

---

### Post by SeijiSensei on 2016-11-02
Do you have mail folders under your home directory, e.g, /home/user/mail?  If so, I'd move /var/mail/user to /home/user/mail/oldmail since /var is still 100% full.

10.04LTS Server reached [end-of-life]("https://wiki.ubuntu.com/Releases") in April, 2015, and no longer receives application and security updates.  You should really consider upgrading to 14.04 or 16.04.

Whoops, it looks like /home is full too.  How about adding a new disk drive?  You can buy a [160 GB or larger SATA drive for $50]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&N=100167523%204026").  Newegg has cheaper refurbished drives, but I'd stick to new items when it comes to disks.

You might try running the command
```
cd /var
sudo du -s *

```
to see what's taking up all that space in /var.  Maybe you have a lot of old logs that you can dispose of.  If you don't use [logrotate]("https://linux.die.net/man/8/logrotate"), you should definitely give that a whirl.

---

### Post by QIII on 2016-11-02
I would strongly recommend installing or upgrading to a supported release before you bother to do anything.

10.04 is well past End of Life (EOL) and the security issues associated with that likely trump any fix you may find for your stated issue.

---

### Post by sobeksson on 2016-11-02
Yes, unfortunately both of them are already full. And yes, I know it is out of support, but I didnt find time to move it to newer version. I guess that it will be now.. :)

But I wanted to run it again, just to get time to make a new mail server. Therefore I deleted 1GB of old mails, so I have time till the weekend when I could create the new mail server.

Problem is that when I created 1GB free space and rebooted the server, it didnt start working as I expected. And it shows these errors in mail.log

Unfortunately, I dont know what does it mean and how to fix it. Please help.. :)

[COLOR=#000000]Nov 2 13:51:44 mailsrv postfix/tlsmgr[2938]: fatal: open database /var/lib/postfix/smtpd_scache.db: Invalid argument[/COLOR]
[COLOR=#000000]Nov 2 13:51:45 mailsrv postfix/master[2933]: warning: process /usr/lib/postfix/tlsmgr pid 2938 exit status 1[/COLOR]
[COLOR=#000000]Nov 2 13:51:45 mailsrv postfix/master[2933]: warning: /usr/lib/postfix/tlsmgr: bad command startup -- throttling

[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by SeijiSensei on 2016-11-02
As I said, clean out the cruft in /var and /home, then reboot and see if things go better.  Nothing is going to fix a system with no space in key directories like those.

Did you run "sudo du -s *" in /var as I suggested?  Did you try deleting some old logs in /var/log?  Repeating the same request for advice without trying the advice that has already been offered isn't going to gain you many friends here.

---

