---
title: "Pure-FTPd, authentication modules, and wrapper"
date: 2007-05-10
forum: Server Platforms
---

### Post by baggachipz on 2007-05-10
Hi everyone,

I'm a relative newcomer to Ubuntu, and am trying to get pureftpd running on my local machine.  In my case, I'd like to authenticate using a custom authentication module that I'll write, and would like to run pureftpd using the wrapper script.  When using that wrapper script, it looks like I can just drop a file in the /etc/pure-ftpd/conf directory whose name is the command-line paramter, and its contents is the value to set for that parameter.  Seems easy enough.  However, when I create a file called ExtAuth (which I think is the parameter that states to use authentication modules) and set its value to /var/run/ftpd.sock I get the following error when executing the startup script (/usr/sbin/pure-ftpd-wrapper):

 Invalid configuration file /etc/pure-ftpd/conf/ExtAuth~: No corresponding directive

Does anyone know how to get this working?  I've seen plenty of examples of people running pureftp with mysql authentication, user lists, and the like, but none with their own authentication module.  I appreciate any help or pointers.

Thanks!

---

### Post by baggachipz on 2007-05-11
Update:

So, it looks like I'm able to put the ExtAuth file (parameter) in the conf directory, and create a sym link in the /auth directory.  Now, when I try to start the server with the wrapper, it reports that it can't find /var/run/ftpd.sock.  Which makes sense, because it's not there.  However, this is the location that all of the manual files specify for this socket.  As it turns out, ftpd.sock is nowhere to be found on my system.  I installed Pure-FTPd via synaptic; perhaps it didn't create this socket and it should?  Does anyone know how I would go about creating/getting that?

Any help is much appreciated, thanks.

---

### Post by baggachipz on 2007-05-11
Final Update:

After stabbing around like a drunk Stevie Wonder in the dark, I figured out how this all works.  I'm putting it here for anyone else who wants to accomplish the same, and doesn't feel like making himself look like an idiot like I have.  

First, install pure-ftpd and pure-ftpd-common from synaptic or apt.  The example provided with the PureFTPd documentation at [http://download.pureftpd.org/pub/pure-ftpd/doc/README.Authentication-Modules](http://download.pureftpd.org/pub/pure-ftpd/doc/README.Authentication-Modules) is actually quite helpful, once you understand what it actually means.  

In order to allow pureftpd to communicate with pure-authd (the daemon that allows scriptable authentication), a socket between the two must be created.  This is accomplished with the line:

  pure-authd -s /var/run/ftpd.sock -r /usr/bin/ftp-auth-handler &

where "-s /var/run/ftpd.sock" is what you'll be naming the socket and "-r /usr/bin/ftp-auth-handler" is your actual script that handles authentication.  This must be done before you start pureftpd server.  If it's already running, stop it before running the above command.

Then, once the socket is created, start the pureftpd server with the next line in that document:

  pure-ftpd  -l extauth:/var/run/ftpd.sock &

where the extauth:/... part is the path to the socket file you created.  Notice that in the documentation there is a typo, which I've corrected in the line above.  That is, there is a space between -l and extauth.  

Using the example script in the documentation, the ftp server now authenticates!  I hope this helps clear up any confusion for others trying this route.

---

