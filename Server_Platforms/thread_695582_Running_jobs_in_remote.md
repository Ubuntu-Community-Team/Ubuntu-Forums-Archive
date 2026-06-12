---
title: "Running jobs in remote"
date: 2008-02-13
forum: Server Platforms
---

### Post by scamio on 2008-02-13
Hi guys 
a quick question for you. I managed to create a connection to my desktop at work (let' call it Computer A) from my laptop at home (let's call it Computer B) using ssh, and it works fine. I did that because I usually work with some long jobs and I don't want to do them on my laptop. However I have a problem. After launching the job on the Computer A from the Computer B, I need to turn off the computer B. If I do so the job that is running on computer A is stopped (I guess). When I log in the Computer A again from computer A I don't have any trace of the job I launched. How can I leave a job running even if I log out? Thanks for your help!!

---

### Post by BaseRunner on 2008-02-13
Hi scamio,

your script does not free the standard file descriptors and the tty i.e. session on A that was opened by sshd, that's why your ssh client on B waits for A and A stops the process when you cut the connection from B.
To get around this you could use a small wrapper like this:
#!/usr/bin/perl

use POSIX qw(setsid);

exit if fork;
close STDOUT;
close STDERR;
close STDIN;
POSIX::setsid();

exec @ARGV;

Call it sshexec for example. Then on B run "ssh A sshexec targetprogram". The ssh client on B will return immediately and your script runs alone on A.

Cheers
Batta

---

