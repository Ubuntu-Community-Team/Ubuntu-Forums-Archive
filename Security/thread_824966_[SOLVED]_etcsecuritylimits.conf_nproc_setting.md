---
title: "[SOLVED] /etc/security/limits.conf nproc setting"
date: 2008-06-10
forum: Security
---

### Post by DantePasquale on 2008-06-10
Hi,

I'm not sure this question belongs here, but since the limits.conf is under the security directory I thought I'd give this a try.

My question is, does nproc limit the number of concurrent processes for a given user or group? Or, is it the number of processes forked off by a given user or group?

My reason for asking this is, I can't find any documentation that states whether it's cumulative, concurrent or whatever. And, I have an application user that after the server has been up for 3 months or so runs into problems where it can no longer fork processes and increasing nproc for that user allows it to fork more processes. 

Some day I should probably just look into the source code and find out where the /etc/security/limits.conf file is actually used, but I'm hoping someone has done that already :)

Thanks, Danté

---

### Post by HalPomeranz on 2008-06-10
nproc is the maximum number of concurrent processes for a single user (i.e., the total number at any particular instant, not cumulative).

limits.conf is a configuration file for the pam_limits module.  As such, the settings in limits.conf are only applied to normal interactive user logins.  These settings don't apply to processes started at boot time, via cron, etc.  Also, these limits never apply to the root user.

If you wanted to set limits for boot processes, cron jobs, et al, you must use ulimit commands in the appropriate startup script, cron script, or whatever.  "man bash" for more documentation on the syntax of the ulimit command, but "ulimit -u 128" would be the equivalent of setting nproc to 128 in limits.conf.

---

### Post by Iotos on 2008-06-12
the nproc limits are defined on a per user or per group basis, and stack in the sense that if one user has a max of 500, another has a max of 300, and both users are logged in at once, that makes a total of 800 processes that can be running, but no individual user can exceed their limit.

But you probably shouldn't be upping the limits anyway. The limits exist to protect against the very situation you are describing. While every server program requires occasional maintenance, they are usually designed to run for extended periods without sapping the host system's resources.

Your server software or one of its components might be leaky or spawning zombie processes. Instead of upping your limits, you might want to consider choosing another server program or (since you seem to be able to look at source :)) try looking at the source of your program and components

---

