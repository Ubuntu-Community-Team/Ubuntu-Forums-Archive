---
title: "Hacked Server"
date: 2011-10-22
forum: Security
---

### Post by hill180 on 2011-10-22
I have an Ubuntu 8.04.4 LTS server fully patched.  Server is a webserver.

Someone hacked the CMS which was unpatched by the maintainer.  As such now I have a spambot 

.  I was able patch the CMS and remove the PHP.ShellExec virus found in the code.

Problem is I clear out the email and it appears to be fine, then after 2 hours or so it starts (sometimes sooner) spaming again.  I am pretty sure it is a service or software that is running causing this.  

So Far:

Reinstalled Postfix with --purge (clears temp)
all updated
Changed all root passwords
changed CMS password
deleted all PHP.ShellExec scripts

To prevent more spam going out I have set the relayhost to localhost so it can't send email out (obviously this is just a temp fix)

I have also stopped cron jobs. 

Any Advise to find the process creating these emails.  They are coming from root.

mail.logs only show from now where.

Thanks!

---

### Post by CharlesA on 2011-10-22
They only way to get rid of something like that is to wipe the machine and reinstall. It's too hard to find what got modified and to put it back to how it was.

---

### Post by masgeeks on 2011-10-22
CharlesA is right - if that happened to my hosting server, I would wipe it, too.  It will be less work in the long run, honestly, than to chase around the "remnants"...

---

### Post by ashwinrao on 2011-10-22
> **hill180 said:**
> 
So Far:

Reinstalled Postfix with --purge (clears temp)
all updated
Changed all root passwords
changed CMS password
deleted all PHP.ShellExec scripts

To prevent more spam going out I have set the relayhost to localhost so it can't send email out (obviously this is just a temp fix)

I have also stopped cron jobs. 

Any Advise to find the process creating these emails.  They are coming from root.

mail.logs only show from now where.

Thanks!

Have you changed MySQL passwords and changed in your scripts? It is the most common way of hacking. Also, it is better to upgrade the CMS to latest stable version. Just my thoughts!

---

### Post by rexrino on 2011-10-22
It would be nice to find out exactly how the hijacker got into your system so we could all be safe.

---

### Post by CharlesA on 2011-10-22
> **rexrino said:**
> It would be nice to find out exactly how the hijacker got into your system so we could all be safe.
They got in via CMS exploit, as said in the OP. ;)

---

### Post by hill180 on 2011-10-22
I agree with wiping out, but sometimes that is just not an option.  It isn't just a hosted site, and if the virus is in the cms hidden somewhere, it will move with us.  At least if I can find the emails then I can trace it back to the script.  (ps yes we have a backup to compare but goes back 30 days and it looks like the server was infiltrated > 30 days ago)

Just FYI, I added a script and modded the php.ini to see if the emails were coming from the web.   Now I'll be able to see if the email is coming from the php mail() function.
  

Needle in a haystack is an understatement.

---

### Post by Dangertux on 2011-10-22
> **hill180 said:**
> I agree with wiping out, but sometimes that is just not an option.  It isn't just a hosted site, and if the virus is in the cms hidden somewhere, it will move with us.  At least if I can find the emails then I can trace it back to the script.  (ps yes we have a backup to compare but goes back 30 days and it looks like the server was infiltrated > 30 days ago)

Just FYI, I added a script and modded the php.ini to see if the emails were coming from the web.   Now I'll be able to see if the email is coming from the php mail() function.
  

Needle in a haystack is an understatement.

Couple of things here

First what CMS? (more for curiosity sake)

You need to do the following in my opinion.

-- Double check that you have in fact gotten rid of all web shells. 
-- Start looking for other user accounts, make sure there aren't any that shouldn't be there.
-- You need to find out what services are running and if there is anythign suspicious or any hidden processes. Hidden procs are a huge sign something bad is happening. 
-- Also check bash profiles to make sure that a script isn't being triggered when a user opens a console. 

I would also spend some time digging through your logs to try to determine exactly what happened. It's a safe bet if the machine wasn't rooted (which if it was just a CMS that was compromised it shouldn't have been). That it's going to be pretty easy to see exactly what was done.

Also as stated above start looking into your dbms , that is the next logical place an attacker could go from compromising a CMS. 

Were you reusing passwords? Could they have escalated easily? 

You said the system was fully patched. So local escalation shouldn't have been too much of a threat, though still possible. 

Might want to check for common 8.04 kernel series rootkits Jinx would be the place I'd start. Run rkhunter it can detect most also will aid in finding hidden processes.

Those are my suggestions hope they help.

---

### Post by hill180 on 2011-10-22
> **Dangertux said:**
> Couple of things here

First what CMS? (more for curiosity sake)

You need to do the following in my opinion.

-- Double check that you have in fact gotten rid of all web shells. 
-- Start looking for other user accounts, make sure there aren't any that shouldn't be there.
-- You need to find out what services are running and if there is anythign suspicious or any hidden processes. Hidden procs are a huge sign something bad is happening. 
-- Also check bash profiles to make sure that a script isn't being triggered when a user opens a console. 

I would also spend some time digging through your logs to try to determine exactly what happened. It's a safe bet if the machine wasn't rooted (which if it was just a CMS that was compromised it shouldn't have been). That it's going to be pretty easy to see exactly what was done.

Also as stated above start looking into your dbms , that is the next logical place an attacker could go from compromising a CMS. 

Were you reusing passwords? Could they have escalated easily? 

You said the system was fully patched. So local escalation shouldn't have been too much of a threat, though still possible. 

Might want to check for common 8.04 kernel series rootkits Jinx would be the place I'd start. Run rkhunter it can detect most also will aid in finding hidden processes.

Those are my suggestions hope they help.

Thanks for the advise.  

Joomla was the CMS.  I used clamav/chkrootkits and rkhunter.  Nothing. (except for the PHP scripts I removed

No new accounts and I did check the bash scripts with nothing.  all passwords have been changed.  No the passwords were unique, nothing reused.

Odd thing though.  After I created a sendmail php script they seem to stop.  

If all is good for 24 hours, i know there is a php script in the system which is pushing email to sendmail directly.  then I have to review the apache logs and cross reference the first appearance of the emails.


Right know I am suspecting a php script that is dropping emails using mail().  PS if this is the case, then reloading the server would not have fixed the issue.

Fun fun fun...

---

### Post by OpSecShellshock on 2011-10-23
Might be worth checking Joomla support forums for reports of similar activity. It may help identify code that's easily overlooked. A manual code audit might be called for.

---

### Post by hill180 on 2011-10-23
> **OpSecShellshock said:**
> Might be worth checking Joomla support forums for reports of similar activity. It may help identify code that's easily overlooked. A manual code audit might be called for.

I am getting the following in the mail.log file 

Oct 22 10:55:05 XXXXXXX postfix/pickup[2303]: XXXXXXXXX: uid=33 from=<www-data>

This means user ID www-data is sending the email.  Is there any way to see how? in postfix?

---

### Post by jramshu on 2011-10-23
You need to check the exploit database against the version number of your joomla. Then check the modules you are using against the exploit db. It could be either, outdated joomla or a vuln module. 

It could also be inadequate character escaping that is allowing sql injection, very common way of grabbing user names and passwords from the mysql database. Though crackers are generally only after the admins information. Once admin privileges are obtained they upload the shell and you are owned.  

Depending on version of joomla, there are also some xss vulnerabilities out there. Search for the joomla vulnerability scanner and run it against your server. It may help you out.

EDIT: OWASP has a scanner that's free.

---

### Post by hill180 on 2011-10-23
Thank you everyone for the great ideas.  I just wanted to post this as it may help someone else.

In my case the server wasn't technically hacked.  There was php code that shouldn't have been there which was removed.  The emails were coming from a really bad php script which was not secured.  I am working now to lock them down.

Thank you all!


Happy hacking (in the good way)

---

