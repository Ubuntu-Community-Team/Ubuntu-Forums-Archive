---
title: "ubuntu rsync client-server configuration help"
date: 2012-11-19
forum: Server Platforms
---

### Post by fouadk on 2012-11-19
hey everyone...

here is the scenario...
i am trying to setup an rsync server that 12 clients needs to mirror in order to reduce bandwidth usage.
this rsync server is downloading using crontab from another rsync server.
i have accomplished this by using the following:
```

@daily rsync -rtlzv --log-file=/home/r/rsync.log --delete cran.r-project.org::CRAN /home/r/r-project/

```
and then i have setup this rsync server as follows:
in /etc/default/rsync i did the following
```

# start rsync in daemon mode from init.d script?
#  only allowed values are "true", "false", and "inetd"
#  Use "inetd" if you want to start the rsyncd from inetd,
#  all this does is prevent the init.d script from printing a message
#  about not starting rsyncd (you still need to modify inetd's config yourself).
RSYNC_ENABLE=true

# which file should be used as the configuration file for rsync.
# This file is used instead of the default /etc/rsyncd.conf
# Warning: This option has no effect if the daemon is accessed
#          using a remote shell. When using a different file for
#          rsync you might want to symlink /etc/rsyncd.conf to
#          that file.
RSYNC_CONFIG_FILE=/etc/rsync/rsyncd.conf

# what extra options to give rsync --daemon?
#  that excludes the --daemon; that's always done in the init.d script
#  Possibilities are:
#   --address=123.45.67.89              (bind to a specific IP address)
#   --port=8730                         (bind to specified port; default 873)
RSYNC_OPTS=''

# run rsyncd at a nice level?
#  the rsync daemon can impact performance due to much I/O and CPU usage,
#  so you may want to run it at a nicer priority than the default priority.
#  Allowed values are 0 - 19 inclusive; 10 is a reasonable value.
RSYNC_NICE=''

# run rsyncd with ionice?
#  "ionice" does for IO load what "nice" does for CPU load.
#  As rsync is often used for backups which aren't all that time-critical,
#  reducing the rsync IO priority will benefit the rest of the system.
#  See the manpage for ionice for allowed options.
#  -c3 is recommended, this will run rsync IO at "idle" priority. Uncomment
#  the next line to activate this.
# RSYNC_IONICE='-c3'

# Don't forget to create an appropriate config file,
# else the daemon will not start.

```
and in /etc/rsync/rsyncd.conf
i did the following:
```
motd file = /etc/rsync/rsyncd.motd

[r-project]
path = /home/r/r-project
log file = /home/r/rsyncd.log
read only = true
list = true

```

now on client machines i setup rsync inside a root crontab as follows
```
0 3 * * * rsync -avrz --delete --log-file=/var/log/rsync/rsync.log 172.16.50.222::r-project /var/www
```
however in client log files i get a lot of permission denied error like the following
```
rsync: opendir "/bin/macosx/leopard/contrib/2.13" (in r-project) failed: Permission denied (13)
```

what could the problem be given that i want my client machines to connect to the rsync server without a username and passowrd.

Thanks in advance.

---

### Post by Kirk Schnable on 2012-11-20
I believe by default,the rsync server daemon runs as the user "nobody".  The "nobody" user probably doesn't have read access to your files.

You should either change the permissions or owner\group of your files in such a way that the "nobody" user has access to read them, or change the user the rsync server daemon runs as, which there might be a configuration directive to do.

Cheers
Kirk

---

### Post by Lars Noodén on 2012-11-20
> **Kirk Schnable said:**
> I believe by default,the rsync server daemon runs as the user "nobody".  The "nobody" user probably doesn't have read access to your files.

You should either change the permissions or owner\group of your files in such a way that the "nobody" user has access to read them, or change the user the rsync server daemon runs as, which there might be a configuration directive to do.

Cheers
Kirk

[rsync](http://rsync.samba.org/how-rsync-works.html) runs as the user not as 'nobody', both as a client and as a server.  It can be made to run as other users with the help of sudo, but you have to go out of your way to do it that way.  The problem must be elsewhere.  I'm not sure at all how "/bin/macosx/leopard/contrib/2.13" comes into play.  Maybe running rsync with -v might give more clues.

---

### Post by SeijiSensei on 2012-11-20
You don't need sudo if you're running rsync in "daemon" mode.  You can use the "uid" and "gid" directives to determine the credentials the daemon uses to access a share.  For instance, a declaration like this in /etc/rsyncd.conf 

```

[system]
     path = /
     uid  = root
     gid  = root


```

would create a "system" share that encompasses the entire file system and is accessed as the root user.  

One thing you could do is set up separate shares for each of your twelve users.  Suppose you want to share a directory in bill's $HOME.  You could define a [bill] share like this:

```

[bill]
     path = /home/bill/rsync
     uid  = bill
     gid  = bill

```

Then when bill connects to server::bill, the filesystem operations will take place with his user credentials.

Tridge didn't include a generic [homes] share in rsync like he did with Samba to export all the users home directories, so you'll need to define individual shares as above.

For all this to work you have to launch the daemon as the root user, of course.  I just put the command "/usr/bin/rsync --daemon" in /etc/rc.local so it starts at boot.

---

### Post by Lars Noodén on 2012-11-20
> **SeijiSensei said:**
> 
```

[bill]
     path = /home/bill/rsync
     uid  = bill
     gid  = bill

```

Then when bill connects to server::bill, the filesystem operations will take place with his user credentials.


Thanks that's a new way to me for using rsync.  It seems to work unencrypted and unauthenticated.  I'm not able to get it to work over SSH though.  Do you have some example of tying it down more securely?

---

### Post by SeijiSensei on 2012-11-21
In the rsync [man page](http://rsync.samba.org/ftp/rsync/rsync.html), read the section entitled "USING RSYNC-DAEMON FEATURES VIA A REMOTE-SHELL CONNECTION".

For authentication, there's a simple password system that is described in the man page for [rsyncd.conf]("http://rsync.samba.org/ftp/rsync/rsyncd.conf.html").

I usually run transfers over OpenVPN tunnels so I don't worry much about authentication and encryption.

---

### Post by Lars Noodén on 2012-11-21
Thanks.  I saw that section yesterday but will give it another try today.  Using rsync not as a daemon works fine with SSH.  I use that all the time.  It's just when trying it as a daemon that I get this error:
rsync: failed to connect to xx.xx.xx.xx (xx.xx.xx.xx): Connection refused (111)
rsync error: error in socket IO (code 10) at clientserver.c(122) [Receiver=3.0.9]

---

