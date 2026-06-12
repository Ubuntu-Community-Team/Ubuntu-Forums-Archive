---
title: "Problems after using crontab with /etc/crontab"
date: 2010-08-26
forum: Server Platforms
---

### Post by grittyminder on 2010-08-26
I have a question about using crontab with /etc/crontab...

I had a cron job that I needed to run as root. At the time I thought that sticking it in /etc/crontab would be a good idea. However, I used the crontab command to edit /etc/crontab, which I guess is not standard procedure? Specifically, I configured /etc/crontab as my local user's crontab (i.e. sudo crontab /etc/crontab) then added my cron job as I would a local user crontab (i.e. sudo crontab -e). 

Originally, my cron job looked like this:

30 *    * * *   root   /my/batch/script &> /dev/null

After adding the new cron job I started seeing errors. Something to the effect of "can't find command root" or something similar. So I removed the 'root' user definition from the cron job and the job started running fine. However, because this is /etc/crontab, there are other system related cron jobs that have been defined to run under the root account (e.g. "17 * * * * root cd / && run-parts --report /etc/cron.hourly" runs as root, etc.). So these pre-existing system cron jobs, which up until now have been running smoothly, are now generating "can't find command root" errors. But I think that the system cron jobs _are_ successfully being run someplace because logrotate seems to be working.

So what I _think_ is happening is that /etc/crontab is being run twice: once as the system crontab, and once as my sudoed local user's crontab. When I run crontab -l I see nothing, but when I run sudo crontab -l I can see the contents of /etc/crontab. I am reluctant to delete my sudoed local user's crontab, because then in the process I would be deleting the system crontab, and I do not know how I should restore the system crontab's contents. (I am still not sure as to the most appropriate way to edit the system crontab).

How can I get out of this mess? I want /etc/crontab to go back to the way it was before--running _once_ as the system crontab. As for my new cron job, I'm willing to reconfigure it anywhere so long as I am still able to run it as root. Any ideas? (I am using Ubuntu 8.04 Server LTE)

---

### Post by Vishal Agarwal on 2010-08-26
> **grittyminder said:**
> 
30 *    * * *   root   /my/batch/script &> /dev/null
17 * * * * root cd / && run-parts --report /etc/cron.hourly

It looks like that there is some problem with the cron entry. is the script is executable ? Otherwise it should work because crontab is very simple scheduler.

---

### Post by grittyminder on 2010-08-27
Hi there,

> It looks like that there is some problem with the cron entry. is the script is executable ? Otherwise it should work because crontab is very simple scheduler. 

I really, really appreciate your reply, but did you read the post until the end? The cron entry "works" after I delete the run-as user (i.e. root), which means that cron is, I think, treating /etc/crontab as a local user crontab in addition to the system crontab. And this is happening (I think) because I assigned /etc/crontab as my local user crontab.

---

