---
title: "[SOLVED] Dspam versions"
date: 2008-03-16
forum: Server Platforms
---

### Post by Stephen_at on 2008-03-16
I'm running Ubuntu 6 LTS. The Dspam version on that release is is 3.6.4.4 which dates from February 13, 2006.

Now I can download and compile the latest version from Nuclear Elephant but it doesn't have the "fix" put in the LTS version which allows it to go into the background properly.

Now I 've noticed that there are later versions for later Ubuntu releases. 

Can I use one of those or do I need to get the LTS 3.6.4.4 version from the Ubuntu source repositories and then get the 3.8 (March 2007) version from Nuclear Elephant and then work out what the Unbuntu background patch was and implement it?

---

### Post by Stephen_at on 2008-03-18
Here is the answer:

In dspam.c find the code that looks like:
[FONT="Courier New"]
DRIVER_CTX DTX;
char *pidfile;
__daemon_run  = 1;
__num_threads = 0;
__hup = 0;[/FONT]

and change it to:

[FONT="Courier New"]DRIVER_CTX DTX;
char *pidfile;
 
/* Fork dspam into the background */
if (fork()) {
 exit(EXIT_SUCCESS);
}

__daemon_run  = 1;
__num_threads = 0;
__hup = 0;[/FONT]

Compile it with the parameters you need.( If you want to find out what options your current dspam is compiled with use dspam --version.)

And it will now automatically fork into the background
when you use --daemon.

---

