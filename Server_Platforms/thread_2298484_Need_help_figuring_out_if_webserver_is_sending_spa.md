---
title: "Need help figuring out if webserver is sending spam"
date: 2015-10-11
forum: Server Platforms
---

### Post by darkod on 2015-10-11
Hi all,

Please help with trying to figure out if a friend's webserver is sending spam or not. I don't know apache in such detail. I was googling around and tried few things but things have not gotten clearer.

What is happening: In the catch-all mailbox he gets returned undelivered mails supposedly coming from his domain. Sender address is unexistent mailbox of course, but the domain is correct, hence he is getting the returned messages. He has a web server (web1) and mail server (mail1) on different VMs.

Here is the catch. The undelivered message claims to have come from his domain.com, not web1.domain.com or mail1.domain.com. I think I have ruled out mail1 sending any spam checking the mail.log and there is really no suspicious activity on mail1. Plus the undelivered message never mentions it.

My first feeling, and still strong, is that the domain is simply spoofed. Anyone can claim sending from his domain.com, no? I have set a SPF record for the domain.com (earlier there was none) allowing only his MX to send mails, "v=spf1 mx -all". That didn't help stopping the spam though.

Further more, I am trying to figure out if apache or php have something to do with it, since basically that's the only thing running on web1, plus mysql. As per some google advice, I tried enabling mail.log in php.ini and restarted apache2, but the log file is still empty, not even single entry. I am not sure if that rules out the php mail function or logging is not working correctly.

I looked in apache2 access.log and there are no GET or POST lines that look like the culprit, or I don't know how to find them.

Can someone give me a hand please, before things get out of hand. Thanks in advance.

PS. Thee is nothing related to mail installed on web1, no postfix, no sendmail, etc. Also netstat -plunt doesn't show any services related to mail running.

I guess I could do iptables -A OUTPUT -p tcp --dport 25 -j DROP if he confirms he does not need any mail sending from any website, but it looks like sort of a harsh decision. I would like to see if something can be found first.

---

### Post by SeijiSensei on 2015-10-11
You need to examine the complete headers of the messages that are being sent. Look at the Received headers at the top of the message. The last of these will identify the originating server.

---

### Post by darkod on 2015-10-11
I was just about to post this... Making sense?
```
Received: from domain.com (x.x.37.251) by BN1BFFOxxxxx.xxxxxxxx (x.x.x.x) with Microsoft
 SMTP Server id x.x.x.x via Frontend Transport; Fri, 9 Oct 2015 20:10:35
 +0000
Date: Fri, 9 Oct 2015 23:10:34 +0300
To: <blah@blah>
From: Henrietta Spencer <henrietta_spencer@domain.com>
Subject: One New SexCall From a Stranger
Message-ID: <76980dbf38b883107ab6b58b0a2a2c94@domain.com>
X-Priority: 3
X-Mailer: PHPMailer 5.2.9 (https://github.com/PHPMailer/PHPMailer/)
MIME-Version: 1.0
Content-Type: multipart/alternative;
	boundary="b1_76980dbf38b883107ab6b58b0a2a2c94"
Content-Transfer-Encoding: 8bit
Return-Path: henrietta_spencer@domain.com
```

Since there is no postfix on the machine I have no mail logs to check message ID or similar... It does look like PHPMailer doing damage but I can't figure it out, and from where (which folder/script/code).

Suggestions?

---

### Post by Habitual on 2015-10-12
is web1.domain.com hosting some sort of CMS (Wordpress or Joomla!)?
Is it/they updated to current versions? How about plugins? Are they up-to-date?
Any 777 directories 'under' the DocumentRoot?
```
find /var/www/html -type d -perm 777
```

There shouldn't be any, but some CMSs may have 1 for uploads, And regardless of the CMS package,
all 777 directories should be inspected closely.

---

### Post by darkod on 2015-10-12
Thanks, let me look into it. For WP I am not sure but Joomla is definitely there I think. Part of the problem is that the web developer has ftp access and often does things against my recommendation, like playing with permissions if he runs into a problem and is in a hurry. I know for sure he made lots of folders 777 again against my protests and said he will put them back, but I doubt he removed the 777 from everything. So there is probably a big mess on the server.

What am I actually looking for in the folders? php files? I know the culprit might be called whatever, it certainly won't say "spam script". :) I'll try to dig into it...

---

### Post by Habitual on 2015-10-12
clamscan can find nefarious scripts.
I use it like so, 
```
clamscan -ir /path/to/scan
```

clamscan won't clean them, but it can delete anything it finds suspect, or move them also.

---

### Post by darkod on 2015-10-12
Cool. From a quick search on the net, I need to install the clamav package for that, right?

As for the 777, there are at least 3 folders under the document root that have 777, plus there are other folders that have rwx for Others but do not have W for Group so the find command looking for 777 did not find them because the permissions are like 757.

PS. I am already negotiating with my friend who owns the machine to do -R o-w for the document root to remove W for Others. I am little nervious if that breaks any code/forms but the way I see it no web design should need o+w.

---

### Post by SeijiSensei on 2015-10-12
One of my clients just had such a problem with a Joomla developer who had no idea about security. They're using a new developer now.  When I looked at the server, the whole Joomla installation had 777 privileges.  Their server was compromised; what a surprise!

The new developer uses read/write/execute permissions for the developer's account, and read/execute privileges for the group that Apache is in, www-data on Ubuntu.  There are no "world" permissions.

Your developer does have a separate account, right, and cannot become root?

I have a couple of WordPress blogs.  The only write-enabled directory is wp-content/uploads/2015 and its monthly subdirectories.  I enable write privileges when I need to update WP, and turn them off immediately afterwards.  Before updating I run this script from the top of the WordPress tree:
```

#!/bin/sh
chmod g+w wp-admin wp-includes wp-content -R
chmod g+w *
echo "Run update now"

```
After the update I run
```

#!/bin/sh
chmod g-w wp-admin wp-includes wp-content -R
chmod g-w *

```
The entire WP installation is owned by the developer account and group www-data. There are no "other" privileges (770).

---

### Post by Habitual on 2015-10-12
> **darkod said:**
> Cool. From a quick search on the net, I need to install the clamav package for that, right?

As for the 777, there are at least 3 folders under the document root that have 777, plus there are other folders that have rwx for Others but do not have W for Group so the find command looking for 777 did not find them because the permissions are like 757.

PS. I am already negotiating with my friend who owns the machine to do -R o-w for the document root to remove W for Others. I am little nervious if that breaks any code/forms but the way I see it no web design should need o+w.
Yes, you need to install the clamscan package and also run
```
sudo freshclam
``` immediately after, before the actual scan.

I'd rather have broken code than a compromised server.
IMO if the code doesn't 'work' with secure permissions, then the coder needs to write better code. :)
75**[COLOR=#ff0000]7[/COLOR]** is insecure as it opens it up to [COLOR=#ff0000]**anyone**[/COLOR].
rwx is 7 so you'll need to clarify that statement.
I'm guessing it's the second 7 as the first would be drwx, unless you omitted the d.

---

### Post by darkod on 2015-10-12
That's the thing, during one situation when ftp was having issues instead of them being patient for me to solve them, the owner gave him the root account. So he was able to upload files which then had "wrong" owner because uploaded with root so he started chopping away the permissions etc. And now it will take long time to figure out what I can remove and what not... :( I don't want to break his websites...

As next step I will do the clamscan and also in the next few days start to remove write for "world". Lets see where that gets us.

---

### Post by darkod on 2015-10-12
@Habitual

Yes, I omitted the leading d. What I wanted to say is that I noticed folders that have 757 and as such are security risk but the find search didn't find them because I used it with parameter -perm 777. I will scan for other permission types too.

PS. > Yes, you need to install the clamscan package and also run

This is a typo, right? The package is clamav and according to apt-cache policy there is no clamscan package.

---

### Post by Habitual on 2015-10-12
Well. "owners", go figure. 

But, without mistakes, users,owners and devs/coders, we'd all be out of work. ;)

Subscribed with interest...

---

### Post by SeijiSensei on 2015-10-12
The developer's account should own the web tree.  That should eliminate any need for root privileges.  Set the developer's default group to www-data (GID=33) and the default umask to 027 so that newly-created files have full privileges for the user, read/execute privileges for group www-data, and no privileges for anyone else.

---

### Post by darkod on 2015-10-12
Weeeelllll.... Clamscan says:
```
----------- SCAN SUMMARY -----------
Known viruses: 4025183
Engine version: 0.98.7
Scanned directories: 2179
Scanned files: 9493
Infected files: 63
Data scanned: 166.84 MB
Data read: 72.87 MB (ratio 2.29:1)
Time: 46.419 sec (0 m 46 s)
```

Let me dig into it. At least I have full path and filename now... Thanks a lot guys for getting me so far...

---

### Post by Habitual on 2015-10-12
Glad to be of help.

---

### Post by darkod on 2015-10-12
Here it is:
```
/var/www/clients/client1/web22/web/libraries/f0f/toolbar/ajax.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/f0f/integration/joomla/dirs.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/f0f/form/info.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/cms/installer/xml.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/cms/library/start.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/cms/component/router/search.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/cms/pagination/menu.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/cms/module/inc.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/fof/platform/files.php.suspected: Php.Malware.Mailbot-1 FOUND
/var/www/clients/client1/web22/web/libraries/fof/model/behavior/config.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/joomla/application/proxy.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/joomla/mail/list.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/libraries/joomla/route/wrapper/object.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/joomla/google/db.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/libraries/joomla/database/iterator/blog.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/legacy/controller/options.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/themes.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/libraries/vendor/phpmailer/help.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/layouts/joomla/links/system.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/components/com_users/views/profile/page.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_users/views/registration/dirs.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_users/help.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_users/press.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_content/views/article/article.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_contact/test.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_jce/media/js/search.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_jce/editor/extensions/css.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_finder/helpers/model.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_akeeba/models/file.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_xmap/views/html/error.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/components/com_sppagebuilder/models/template.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_sppagebuilder/models/diff.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_sppagebuilder/views/page/page.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_sppagebuilder/language/en-GB/error.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_sppagebuilder/addons/accordion/header.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/components/com_sppagebuilder/addons/tab/inc.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/components/com_sppagebuilder/assets/js/article.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/modules/mod_login/dir.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/modules/mod_finder/tmpl/lib.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/modules/mod_articles_archive/user.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/modules/mod_articles_popular/tmpl/footer.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/modules/mod_search/ajax.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/modules/mod_banners/lib.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/language/en-GB/dirs.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/plugins/system/helix3/fields/db.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/plugins/system/helix/css/utf.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/plugins/editors-xtd/readmore/view.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/plugins/xmap/utf.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/plugins/xmap/com_mtree/alias.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/templates/beez3/language/defines.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/templates/shaper_helix3/images/gallery.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/templates/protostar/less/files.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/templates/protostar/language/en-GB/model.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/templates/protostar/language/search.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/templates/protostar/menu.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/media/cms/css/diff.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/media/cms/css/sql.php.suspected: Php.Trojan.StopPost FOUND
/var/www/clients/client1/web22/web/media/editors/tinymce/langs/view.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/media/com_akeeba/js/global.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/media/com_contenthistory/ini.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/media/plg_quickicon_extensionupdate/header.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/media/media/images/mime-icon-16/file.php.suspected: PHP.Trojan.Uploader FOUND
/var/www/clients/client1/web22/web/media/media/images/stats.php.suspected: PHP.Trojan.Uploader FOUND
```

I'll double check with the developer if he objects me deleting all these files but I guess none of these is his. Or even if it is, when infected we have to delete it and he can upload a clean version after.

---

### Post by Habitual on 2015-10-12
Well, now you know the what, where and who, you are on your way to a clean webserver.
UNLESS one of those is a backdoor, then the whole server is suspect.

---

### Post by SeijiSensei on 2015-10-12
I wouldn't try and clean things up given how compromised this machine appears to be, but that's your call.  Before you put it back online, please fix those permissions.

---

### Post by darkod on 2015-10-12
I have already started working on the permissions. In most cases the W is removed.

I also prefer clean slate after web server has been compromised but in this case it's not my call since there are various sites hosted. clamscan found infections on only one though. My next step would be to delete the infected files and monitor how things go after that. If suspicious activity continues, probably the owner needs to think about formatting the machine.

---

### Post by Habitual on 2015-10-12
Does the owner now know that giving out the root password is an unnecessary risk?

---

### Post by darkod on 2015-10-14
OK guys, here is an update...

1. Infected files removed. New scans show no infected files in whole document root. Will scan complete server root this weekend at night (less load).

2. As temporary fix while investigating, I did today "iptables -A OUTPUT -p tcp --dport 25 -m string --string domain.com --algo bm -j DROP" and 7hrs later that rule has blocked 2.6MB of data. All of that might not be spam but it seems it helps. Need more time to make a statistics though...

3. Looking at apache access.log I found a possible suspicious POST entry that repeats a lot. It goes like:
"POST /components/com_config/controller/modules/cancel.php HTTP/1.0" 200 619 "-"

I don't know yet how to filter for two strings at the same time (to include both POST and cancel.php), but I did a simple "grep -o 'cancel.php' filename | wc -l" and it came back with 2827 hits. The log started just over 3 days ago. So that's 2827 hits for cancel.php in access.log in just over 3 days. I see that as too many hits for that file for that website (that particular website is barely marketed and visited).

This cancel.php file was not detected as infected by clamscan. And it looks as part of Joomla but I wouldn't know by looking at the content if anything was "added" compared to "original" file. Am I on the right track? What do you think?

PS. After a few tries I think I figured out how to use nested grep to filter by more strings. I did:
"grep 'cancel.php' access.log | grep 'POST' | grep -o 'domain.com' | wc -l"

and it returned 2844 hits. 17 more compared to less than half an hour ago.

---

### Post by SeijiSensei on 2015-10-14
One of the most common attempts against my WordPress blogs are POST requests for login.php.  I've cut down on these by adding <Limit> statements to my Apache configuration:
```

<VirtualHost *:80>
     [stuff]

     DocumentRoot /path/to/wordpress
     <Directory "/path/to/wordpress">
       <Limit POST PUT DELETE>
        order Deny,Allow 
        Deny from All
        Allow from 12.34.56.78
        Allow from 10.10.10.0/24
        </Limit>
        
     [more stuff]
     </Directory>

[etc.]
</VirtualHost>

```

Now any attempts to POST to the site from addresses not specifically allowed get a 403 Denied error.  Since I'm the only one posting to this blog, this is an easy fix.  If you have to support sites with multiple registered users, that's harder to do.

A quick Google search doesn't identify any known exploits against cancel.php, but that doesn't mean they don't exist.

---

### Post by Habitual on 2015-10-15
> **darkod said:**
> This cancel.php file was not detected as infected by clamscan. And it looks as part of Joomla but I wouldn't know by looking at the content if anything was "added" compared to "original" file. Am I on the right track? What do you think?
If the domain.com/wherever/this/is/cancel.php page has an input box *of any kind* (like a 'reason' for canceling...)
components that don't have good input sanitation can be leveraged against the server to exploit it.

clamscan with a current freshclam database 'set' surely would have caught it, if it was infected.
so I see no need to examine the file visually, but if the 'hits' continue in access.log, I'd dig a little deeper.
Did you correct directory perms from 757 to 755 under this particular DocumentRoot?

Yes, I typo'd [clamscan]("http://ubuntuforums.org/showthread.php?t=2298484&p=13371806#post13371806") . Sorry about that.

Reference: 
[http://www.cvedetails.com/cve/CVE-2008-5332/](http://www.cvedetails.com/cve/CVE-2008-5332/)
this page references 1 exploit in the wild.
and that reference is/was **Exploit!** [http://www.milw0rm.com/exploits/7221](http://www.milw0rm.com/exploits/7221)
I cannot view it from here.

I wish you continued success.

---

### Post by darkod on 2015-10-15
I also wasn't able to find any confirmation of cancel.php as exploit. The link you posted does mention it as file but it also says the location as /lib/action which in this case is not.

But this is still my primary suspect because of the almost 3000 POST entries in access.log in barely 4 hrs when this domain is so little published that it shouldn't have 3000 visitors for the whole month, let alone in few hours.

Also I confirmed that only this site on the server has joomla which might explain why spam mails are sent only from this @domain.com as origin.

---

### Post by Habitual on 2015-10-15
Your suspicion of the file warrants further investigation, regardless of its location under DocumentRoot.
Any one of those suspects from the clamscan could have uploaded it, recorded its location and modified a crafted url to take advantage of the system.

Again. It is possible that a backdoor is on the system from one of those files in the results of clamscan.
and if in doubt, take action *assuming* it is backdoor'd

I always have and it has served me well.

---

### Post by darkod on 2015-10-15
Actually, things might have improved and cancel.php might not be the culprit. He reported to me that the spam almost came to a halt. But lets give it a day before we make a statistics.

Here is the latest:
1. The iptables rule I had to try block spam is not active right now.
2. I have not deleted cancel.php yet.

According to the above, everything is the same except that the infected files were removed. But spam seems to have came (almost) to a stop.

What could have been the reason, is that joomla was wide open:
1. Was not upgraded to the latest 3.4.4 (I did that now)
2. Extensions were not updated (sorted now)
3. SHOCKED!!! After joomla was installed they left the default credentials admin/admin and the login is accessible from internet! I changed the pass immediately.

That last action might have something to do with spam dropping noticeable. Lets see after a while...

---

### Post by Habitual on 2015-10-15
Joomla! was not current? shocking! not. ;)
[https://www.itsupportguides.com/joomla-tips/joomla-how-to-use-htaccess-to-protect-the-administrator-directory/](https://www.itsupportguides.com/joomla-tips/joomla-how-to-use-htaccess-to-protect-the-administrator-directory/)
[http://geekflare.com/joomla-security/](http://geekflare.com/joomla-security/)

what version of apache?
```
sudo dpkg -l | grep apache
```

You could also download the cancel.php to your localhost and upload that to virustotal.com

See what that says.

also, since the site is accessible to the public,
[http://www.unmaskparasites.com/security-report/?page=www.domain-in-trouble.tld]("http://www.unmaskparasites.com/security-report/?page=www.domain.com")

I never thought about re-using passwords, as folks sometimes do. :)
I always generate new passwords for login pages than those used to install CMS products (database connectors)

---

### Post by darkod on 2015-10-15
apache should be latest offered by 14.04.3 LTS. I do dist-upgrade regularly, I have that under control. But I will check later.

---

### Post by Habitual on 2015-10-15
should be apache2 **2.4***.x*
I have 2.4.7 here but I am NOT on Ubuntu specifically.

any hoos, dist-upgrade should give you the latest.

2.4.7-1ubuntu4.6 on one of my 14.04.3 LTS hosts.

---

### Post by darkod on 2015-10-15
Yes, 2.4.7 also here.

---

### Post by Habitual on 2015-10-15
groovy.
I'll leave you alone and I hope for a better report  "after a while"...

Peace.

---

### Post by darkod on 2015-10-17
Further update...

Patching up joomla and changing the pass seems to have helped and lowered the spam level but there was still some sent (returned mails received). In the apache access log new type of POST commands started showing up, with path /administrator/components/com_extplorer/libraries/geshi/geshi/bf.php

Googling extplorer it seems it is an extension that does file management and that it even has its own built-in user coming with default credentials like admin/admin. Not sure if this extension was installed by the owner or by the spammers using the joomla admin user. Anyway, I disabled the extension and deleted the whole geshi folder in .../libraries.

Right now there are still POST entries in the access log (I assume scripted from their end) but now they are getting reply HTTP 404 instead of HTTP 200.

The website owner reported spam has stopped. Lets see how it goes from now on...

Honestly, this joomla looks like developed by spammers. It has so many security holes that I started wondering who created it, the good guys or the bad guys... :)

---

### Post by QIII on 2015-10-17
It's probably not Joomla! itself, but the fact that anyone can put a Joomla! template or a bunch of extensions out on the web for any unsuspecting sucker to use.  Like many things out there on the big, bad interwebz, there's no central quality control.

Add to that stuff like leaving default logins and passwords, terrible iptables rules, unfinished apache (I use nginx) setup ...

---

### Post by Habitual on 2015-10-17
You upgraded Joomla! but you left the old (**cough)** perms (**cough**) ?

```
find  /var/www/clients/client1/web22/web/ -type d -not -perm 755
```

Please share those results.

Thank you.

---

### Post by darkod on 2015-10-17
No, no. The W for world was removed right away at the beginning. In most cases even W for group. Only for user was left.
```
root@web1:~# find /var/www/clients/client1/web22/web/ -type d -not -perm 755
/var/www/clients/client1/web22/web/
/var/www/clients/client1/web22/web/__MACOSX
/var/www/clients/client1/web22/web/tmp/distributives
```

---

### Post by Habitual on 2015-10-17
Thanks.
and finally, 
```
ls -ld /var/www/clients/client1/web22/web
```

---

### Post by darkod on 2015-10-17
```
root@web1:~# ls -ld /var/www/clients/client1/web22/web
drwx--x--x 21 web22 client1 4096 Oct 15 12:15 /var/www/clients/client1/web22/web
```

---

### Post by Habitual on 2015-10-19
711? How bizarre, but erm. OK ;)

---

### Post by Habitual on 2015-10-19
darko:
> **SeijiSensei said:**
> I wouldn't try and clean things up given how  compromised this machine appears to be, but that's your call.  Before  you put it back online, please fix those permissions.
I have to agree.

I would assume this box in fully p0wn3d.
It would be unprofessional for me to pretend it's not.

---

### Post by darkod on 2015-10-19
Yeah. I checked another site that did not have modifications of the permissions to compare them, and it also has 711. Obviously that is what the system (control panel) sets.

On another note, the spam still seems to be stopped. I'll give it one more day and mark it Solved. :)

---

### Post by Habitual on 2015-10-19
did you remove those [suspect files]("http://ubuntuforums.org/showthread.php?t=2298484&p=13371825#post13371825")?

---

### Post by darkod on 2015-10-19
Yes, ages ago. All of them, using clamscan --remove. Did a few scans of the document root in the next few days, all reported 0 infected. Also did a full scan of the root partition, 0 infected.

---

### Post by Habitual on 2015-10-19
Great, but as I [said]("http://ubuntuforums.org/showthread.php?t=2298484&p=13371836#post13371836") one of those files may have planted a backdoor, not a rootkit necessarily, but another means to get in.
If the server is spam-free for a few days, I'd might relax that it's p0wn3d, but...

IF there is a "next time" suspect files or not, I'd take the position that it is.

---

### Post by darkod on 2015-10-19
Of course, I am also giving it some time to throw in the final verdict. Knock on wood, it doesn't look as taken over so far... And spam has stopped like 2-3 days ago, ever since I disabled extplorer extension and deleted that geshi folder.

I am still keeping an eye on it though...

---

### Post by Habitual on 2015-11-18
darko:
How is this going?

---

### Post by darkod on 2015-11-18
Hey, thanks for the continued interest. Sorry there was no update...

I would say it is going very good, closer to great. There were few culprit files that I think they were using, but as soon as I noticed POST entries in the access log it gives them away. :) And after I delete the file(s), they don't come back, so that makes me optimistic they do not have a way in any more.

Looking from this perspective now, I think this is what happened: They used a default login in joomla to plant files, some that could be identified by clamav, some not (because they don't contain viruses or trojans, just php code).

The infected files were sorted out by clamav, and there has been no new infections after that as far as I can tell.

The php files can't be easily identified, until they use them to send span, when they appear in the access log immediately and are easy to locate and delete. As I said, they don't seem to be coming back.

So, bit by bit it looks like the server is clean-ish... And there is no significant spam for weeks now.

I'll probably mark this as solved in a couple of weeks more. Thanks for all the help so far.

Because it looks like we have it under control (no new infections, easily deleted identified php files, no new php files to replace them) and because it seems they don't have access to the server any more, we have decided for the time being not to format the machine and go through the whole setup process again. Lets hope it stays that way...

Also, I noticed one IP from Ukraine doing weird entries in the access log once and it looked to me like looking for a way in. So I just iptables dropped the whole /16 subnet. :) My friend has no customers in Ukr, they won't be missed.

---

### Post by Habitual on 2015-11-18
Always good to hear Good News.
Glad it worked out.

---

### Post by Vegan on 2015-11-18
i suggest putting clamscan into a cron job so its constantly checking for any signs of more trouble

---

