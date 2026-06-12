---
title: "What is the best domain root directory permission for shared hosting?"
date: 2016-04-18
forum: Security
---

### Post by RavenLX on 2016-04-18
I'm working on a shared hosting LAMP server using Ubuntu 14.04. I am assuming that I should have each domain's root directory (ie. /var/www/public_html/domain.com for example) as 0755 (owner read/write/execute, group and world read/execute). And the fact I want to allow FTP to files I have the folders set as user ftp and group ftp with apache www-data a member of ftp group and ftp a member of www-data's group. 

Right so far?

But, someone I know is telling me that scripts will not work well unless the root directory (ie. /var/www/public_html/domain.com) is not set to 0777 (all writeable). I don't want to do this but well... who is right? Me at setting 0755 or they say 0777?

And can someone explain what the problem is for setting the domain root directory at 0777? What can happen? Why is that so wrong? I know it's "Not the right thing to do" but I am at a loss to explain to said friend as to why?

Can someone help me with explanations and proper settings please?

---

### Post by TheFu on 2016-04-18
No. That is not correct, but the true answer is "it depends."

The short answer for 777 perms - [https://askubuntu.com/questions/20105/why-shouldnt-var-www-have-chmod-777](https://askubuntu.com/questions/20105/why-shouldnt-var-www-have-chmod-777)
I have **never** come across any reason that 777 must be used. Not once, since I learned about file/directory permissions. This is just for lazy people who don't care about security or get frustrated (I was) that things seemed so complicated.  Over time, as more understanding happens, that complication will become clearer.

Don't use plain FTP if you care about security.  FTP should have died in 1994 - never to be used again. Definitely DO NOT MIX FTP and WWW directories - never, ever. There are many, many, many, reasons this is bad for security.  Until you grasp Unix file and directory permissions at the next level, it is impossible to explain why.

As with all things related to a web server, permissions need to be exactly the minimal required for the webserver to serve the files/data you want served. Nothing more. That could be read-only permissions with ownership by a different account OR it could be the more dangerous, read-write owned by the webserver uid.  Just depends on the application and how poorly it was written.  Which do you think is more secure?  A well-written application will place data outside the webserver document root and not require 777 permissions.  If I see any install/README saying to make a directory 777, I know the programmer is a noob or just doesn't care about security at all.

If you allow other people access to the server, perhaps through ssh, permissions need to be tighter.
If you allow plain FTP uploads with logins, permissions need to be VERY tight - and you should explain to your users that all their login credentials (userid/passwords) are sent in clear text.
If you allow plain FTP, anonymous connections for download only, why not use a firewall friendlier protocol like sftp or HTTP instead which use specific ports instead of multiple, random, ports?

Scripts should be outside the normal web-site structure, inaccessible from the "document root", IMHO.  Where is up to you, but most web servers (which are you using?) - have a cgi-bin alias that should be used just for this purpose.  BTW, different scripting languages have different ways to secure their code.  I believe the perl guys are the best at this, then python, ruby, and last, PHP.  I think the average skill level for the programmers in a language is also part of the security question.  Php is very easy to get started, so make people use that language.  Just because something works, that doesn't mean it is secure.  I know that is obvious, but it is worth saying.

So - in the end, security comes down to understanding that Unix is a multi-user OS from the ground up and that different processes run with different userids.  File and directory permissions are the corner of all Unix security.  Any discussion of Unix security begins with that understanding.  My signature has links for basic security. If you are really interested, get Bob Toxen's book.  The learning curve is steep and hard, but after things start to "click", you'll see the genius of the permissions and overall architecture of Unix systems. It is elegant and brilliant, you'll see.

Plain FTP is non-secure - BY DEFAULT - and I don't know how to make it secure, but I would try by 
a) running just FTP in a chroot alone. Other high-risk processes should run in their chroots or on different machines.
b) anonymous uploads that are moved out of the upload directory to an directory that is NOT accessible via FTP or HTTP, immediately (scripted)
c) Making the uploaded files inaccessible to the uploader until processed.
d) If you make these files available for general download, they need to have been processed (re-encoded to prevent dangerous payloads) and only available from a different TLD.

There is a basic tenant to computer security - if a file can be uploaded and other users can see it, that makes it dangerous. NEVER trust anything uploaded by an end-user.  Since we can't trust anything uploaded, we shouldn't make those files available either, not without verifying they are fine, clean, safe.  This is the main reason why the FTP upload area and HTTP/FTP download areas cannot be the same.  There are other reasons and other dangers.  Almost any Unix security book will get into those.

If you make any directory 777 in either the web-server area or FTP areas, you've just opened the server to being used for unintended purposes.  This is basic file/directory permissions stuff. 

Get some background knowledge, play with a few userids, groups and permissions for about an hour.  Do weird things. Mix and match groups. Play with g+s, +t, u+s and leaving +x, but removing -r. That is always fun.  That will provide some of the multi-user background that seems to be missing.  Don't forget to learn about the umask, which can have profound impacts on default file/directory creation permissions.  Change the umask and redo all the stuff you already did. There are tutorials for this, but usually they don't get into the stranger, but highly useful settings, like preventing a group file/directory access, while allowing "other" read access.  

While you don't need to know about/understand ACLs, these are extremely powerful - and can override the normal permissions (which will drive hackers crazy).  getfacl/setfacl is fun too. Not suggesting they be used, but just to open some eyes. 

I find it is easier to just use a read-only NFS mount for static files to be served by a web server.  Hard to hack a file system where the way it sees storage is controlled by another server (exported as read-only file system) that isn't available over the internet.  In that case, 777 is fine. ;)

Shared hosting - ouch. Hard to secure that at all, IMHO.  I wouldn't put anything there I didn't want to share with the entire world.  How the hosting provider has setup the userids, groups and file ownership will determine the more secure settings.  If only 1 userid is to be used for everything, 700 permissions are really the only choice.  But I don't have enough information to know what is really needed or possible. 50 different shared-hosting providers could do it 50 different ways.

We all started just like you.  I realize the question seems like it is easy, but it isn't.  Unix is extremely flexible, so there are 500 different ways that this could be setup. Sorry. You can look around on the system at how other people sharing the box secure their stuff.  It is likely there are 300 others there, IME.  You'll also see 295 non-secure setups, probably.

For now, for you and your friend, just accept that 777 is bad (there are 2 exceptions) until more background knowledge has been earned. Practice and experience tend to be the way that experience is earned.

Don't forget to check out the security links in my signature. Hope they are helpful.

---

### Post by RavenLX on 2016-04-19
Thank you. Lot to look into and try to understand there. Can you give me two exceptions where 777 is not bad? Just curious.

---

### Post by SeijiSensei on 2016-04-19
I'd give each customer a separate account and put the websites in a directory like /home/user/web/ with ownership user:www-data and 2750 perms. The "2" makes all files added to the directory inherit the group's permissions so the www-data user can read and distribute them. You don't want 755 since users can then browse other users' code. 

Add a separate configuration file to /etc/apache2/sites-available/ for each customer with a DocumentRoot directive that points to /home/user/web/.

---

### Post by TheFu on 2016-04-19
> **RavenLX said:**
> Thank you. Lot to look into and try to understand there. Can you give me two exceptions where 777 is not bad? Just curious.

Already provided 1 example above - read-only NFS mount.
The other one is on every single Unix system running - /tmp.

There actually is a 3rd reason - training for security pros.  People learning to be professional penetration testers need to practice the "cracking" skills, so for those competitions, systems are setup in non-secure ways. There are many how-to guides on youtube, if this interests you.  Knowing how the bad guys will break into your system is a good way to learn how to prevent it, IMHO.  But forum rules don't allow much talk about that.

Some ISPs setup shared hosting this way - search for "perfect server." Falco works for an ISP.

But the first rule for an ISP, IMHO, is not to allow plain FTP. That sets the wrong idea about security. Use sftp and encourage keys for authentication.

---

### Post by RavenLX on 2016-04-19
Thank you all for the great info. I think I have ideas now on what needs to be done.

---

