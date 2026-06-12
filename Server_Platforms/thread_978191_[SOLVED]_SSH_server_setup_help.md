---
title: "[SOLVED] SSH server setup help"
date: 2008-11-10
forum: Server Platforms
---

### Post by DFord425 on 2008-11-10
I working on setting up my new server, im starting with SSH. Its all installed and i can connect to my desktop from my server. But when i try to connect from my desktop to my server, i get the message: ```
Read from socket failed: Connection reset by peer
```
What does this error mean? Is there something else i have to change in the config files?

---

### Post by tvtech on 2008-11-10
what does your ssh config file read like?   are you using a non standard port? how are you connecting via client or via terminal?

---

### Post by david_lynch on 2008-11-10
> **DFord425 said:**
> I working on setting up my new server, im starting with SSH. Its all installed and i can connect to my desktop from my server. But when i try to connect from my desktop to my server, i get the message: ```
Read from socket failed: Connection reset by peer
```
What does this error mean? Is there something else i have to change in the config files?

Well, ssh always "just works" here, out of the box. Not that much that could go wrong. Firewall maybe? Have you changed any settings from the defaults?

---

### Post by tvtech on 2008-11-10
on your client computer crack open a terminal 

```
ssh 192.168.1.2 
```  for a standard port

for a non standard port 
```
ssh 192.168.1.2 -p 1111
```

for the ip and the port substitute your server ip and port numbers.

as long as your ssh server is running on startup on your server you should be all set.  

if it's not running on start up there is an init script that you can edit and add it to start I'll try and remember the code exactly and post it it's been a while since I did it though.

ssh's default port is 22 so make sure that you have this enabled if your going through a firewall

- I gotta wake up my server to check the init script sorry bout the wait,  I'm at work it'll take a few minutes for it to turn on.

your code for the init script found in /etc/init.d/ssh  should look something like the following```
#! /bin/sh

### BEGIN INIT INFO
# Provides:		sshd
# Required-Start:	$network $local_fs $remote_fs
# Required-Stop:
# Default-Start:	2 3 4 5
# Default-Stop:		0 1 6
# Short-Description:	OpenBSD Secure Shell server
### END INIT INFO

set -e

# /etc/init.d/ssh: start and stop the OpenBSD "secure shell(tm)" daemon

test -x /usr/sbin/sshd || exit 0
( /usr/sbin/sshd -\? 2>&1 | grep -q OpenSSH ) 2>/dev/null || exit 0

if test -f /etc/default/ssh; then
    . /etc/default/ssh
fi

. /lib/lsb/init-functions

# Are we running from init?
run_by_init() {
    ([ "$previous" ] && [ "$runlevel" ]) || [ "$runlevel" = S ]
}

check_for_no_start() {
    # forget it if we're trying to start, and /etc/ssh/sshd_not_to_be_run exists
    if [ -e /etc/ssh/sshd_not_to_be_run ]; then 
	if [ "$1" = log_end_msg ]; then
	    log_end_msg 0
	fi
	if ! run_by_init; then
	    log_action_msg "OpenBSD Secure Shell server not in use (/etc/ssh/sshd_not_to_be_run)"
	fi
	exit 0
    fi
}

check_dev_null() {
    if [ ! -c /dev/null ]; then
	if [ "$1" = log_end_msg ]; then
	    log_end_msg 1 || true
	fi
	if ! run_by_init; then
	    log_action_msg "/dev/null is not a character device!"
	fi
	exit 1
    fi
}

check_privsep_dir() {
    # Create the PrivSep empty dir if necessary
    if [ ! -d /var/run/sshd ]; then
	mkdir /var/run/sshd
	chmod 0755 /var/run/sshd
    fi
}

check_config() {
    if [ ! -e /etc/ssh/sshd_not_to_be_run ]; then
	/usr/sbin/sshd -t || exit 1
    fi
}

export PATH="${PATH:+$PATH:}/usr/sbin:/sbin"

case "$1" in
  start)
	check_for_no_start
	check_dev_null
	log_daemon_msg "Starting OpenBSD Secure Shell server" "sshd"
	check_privsep_dir
	if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;
  stop)
	log_daemon_msg "Stopping OpenBSD Secure Shell server" "sshd"
	if start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd.pid; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  reload|force-reload)
	check_for_no_start
	check_config
	log_daemon_msg "Reloading OpenBSD Secure Shell server's configuration" "sshd"
	if start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  restart)
	check_privsep_dir
	check_config
	log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd"
	start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd.pid
	check_for_no_start log_end_msg
	check_dev_null log_end_msg
	if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  try-restart)
	check_privsep_dir
	check_config
	log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd"
	set +e
	start-stop-daemon --stop --quiet --retry 30 --pidfile /var/run/sshd.pid
	RET="$?"
	set -e
	case $RET in
	    0)
		# old daemon stopped
		check_for_no_start log_end_msg
		check_dev_null log_end_msg
		if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
		    log_end_msg 0
		else
		    log_end_msg 1
		fi
		;;
	    1)
		# daemon not running
		log_progress_msg "(not running)"
		log_end_msg 0
		;;
	    *)
		# failed to stop
		log_progress_msg "(failed to stop)"
		log_end_msg 1
		;;
	esac
	;;

  *)
	log_action_msg "Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart|try-restart}"
	exit 1
esac

exit 0
```

---

### Post by DFord425 on 2008-11-10
Thanks for your responses. Its not on the the standard port, 22. But im using the -p #### flag on the ssh command. And its set to that port in the /etc/ssh/sshd_config file. 
Also, i have not set up a firewall on the server or the client, unless the firewall is preconfigured. I dont think the port is blocked on my router firewall but i will check.

---

### Post by Philio on 2008-11-10
Can you login locally on the server?

ssh localhost -p 1234

Is the ssh server running?

ps aux | grep sshd

Add ssh to system start if nescessary:

update-rc.d ssh defaults

I assume you only changed the 'Port' line in the config, if you changed anything else perhaps it's that.

SSH usually works out of the box, no config required, all the above 'should' be setup for you but worth a try.

---

### Post by Philio on 2008-11-10
Sorry double post, the forum was acting funny!

---

### Post by hictio on 2008-11-11
Couple of things to test/ check.
Just to be sure, check that you are not blocking access via TCP wrappers, take a look at /etc/hosts.allow & /etc/hosts.deny.

Also, issue your connection adding verbosity flags, so you can see with more detail what's going on.

```

ssh -p xxxx -vvvvv host

```

Last one, try adding an entry on each of the boxes to the file /etc/hosts resolving each other Ip address to a hostname.

---

### Post by DFord425 on 2008-11-11
i checked, sshd is running on both. I cannot connect to the localhost from the server. and when i run in verbose mode, here is the output ```
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.142 [192.168.1.142] port 3333.
debug1: Connection established.
debug1: identity file /home/dfordgt/.ssh/identity type -1
debug1: identity file /home/dfordgt/.ssh/id_rsa type -1
debug1: identity file /home/dfordgt/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer
```

Does anyone know what that means or how to fix it?

---

### Post by hictio on 2008-11-11
> 
I cannot connect to the localhost from the server.


That's really, really bizarre, to say the least.
Did you try a regular SSH login like this: 'ssh localhost' ?
What error did you get? This is happening on the server, right? The same one you want to connect to?

Did you check the contents of the files '/etc/hosts.allow' & '/etc/hosts.deny' on your server, the one you can't connect to via SSH, they are plain text files, you can view them with gedit.

Have you checked the logs on the server?

---

### Post by DFord425 on 2008-11-11
I checked the hosts.allow and hosts.deny. I only added the host im trying to connect from the to hosts.allow.

When I try ssh localhost, I get the error, Read from socket failed, connection reset by peer.

Yes this is happening on the server i want to connect to, and where are the logs i shoudl check?

Thanks for your help.

---

### Post by DFord425 on 2008-11-11
double post

---

### Post by hictio on 2008-11-11
> **DFord425 said:**
> I checked the hosts.allow and hosts.deny. I only added the host im trying to connect from the to hosts.allow.

When I try ssh localhost, I get the error, Read from socket failed, connection reset by peer.

Yes this is happening on the server i want to connect to, and where are the logs i shoudl check?

Thanks for your help.

For the moment, I would remove any entry from the hosts.allow & host.deny files, first make it work.
The log is the file '/var/log/auth.log'.

---

### Post by DFord425 on 2008-11-11
I just tried to log on again and here is the /var/log/auth.log entry:
> Nov 11 21:21:53 MustangGT sshd[22463]: error: Could not load host key: /etc/ssh/ssh_host_rsa_key
Nov 11 21:21:53 MustangGT sshd[22463]: error: Could not load host key: /etc/ssh/ssh_host_dsa_key
Nov 11 21:21:53 MustangGT sshd[22463]: error writing /proc/self/oom_adj: Permission denied
Nov 11 21:21:53 MustangGT sshd[22464]: fatal: No supported key exchange algorithms

There is the /etc/ssh/ssh_host_rsa_key and /etc/ssh/ssh_host_dsa_key files. I did not change them except the change the permissions, but it was not able to connect before i changed the permissions.

---

### Post by hictio on 2008-11-11
> **DFord425 said:**
> 
There is the /etc/ssh/ssh_host_rsa_key and /etc/ssh/ssh_host_dsa_key files. I did not change them except the change the permissions

Let's see the current perms on those.
cd to /etc/ssh/ and type:

ls -lsht ssh_host_dsa_key ssh_host_rsa_key

EDIT:
The snip from the log is from the server you are trying to connect, right?

---

### Post by DFord425 on 2008-11-11
Here is what i get from the ls -lsht command
> 
4.0K -rw------- 1 root root  668 2008-11-10 20:13 ssh_host_dsa_key
4.0K -rw-r--r-- 1 root root  604 2008-11-10 20:13 ssh_host_dsa_key.pub
4.0K -r-------- 1 root root 1.7K 2008-11-10 20:13 ssh_host_rsa_key
4.0K -rw-r--r-- 1 root root  396 2008-11-10 20:13 ssh_host_rsa_key.pub


I changed the ssh_host_rsa_key permissons to chmod 400, it was the same as ssh_host_dsa_key.

---

### Post by hictio on 2008-11-11
Yes, that's right, please put back as it was, this is the one on the server you want to connect to, right?

---

### Post by DFord425 on 2008-11-11
yes these are the files on the server. I cahnged it back, tried to connect, get the same error. Both when i try to connect to the localhost on the server and when i try to connect from the client.

---

### Post by hictio on 2008-11-11
Ok, you have console, or physical access right? If yes, try stopping and starting the service sshd.

Another thing, just re-read a bit the start of the thread, are you still trying to connect to a non standard port? Is the sshd daemon started listening to that port?

---

### Post by oneloveamaru on 2008-11-11
Just for giggles do a "netstat -a | grep ssh". Also, do you have password authentification turned off?

---

### Post by DFord425 on 2008-11-12
I switched the port in the config files to port 22 and it worked. Thank you for your help.

---

### Post by madverb on 2008-11-13
This isn't really actually solved. I am having the same problem where I actually need to have the port set to non-standard ssh port. There is already a server using the 22 port.
When I change from port 22 to something else it fails to work. When I try to hit the box via port 22 when it is changed I get an instant reply saying "Unauthorised Access".
When I try to connect to it via the new port it just takes a long time and then fails.
I have checked netstat and made sure that the listening port is correct.
Any ideas?
Cheers

---

### Post by hictio on 2008-11-13
Ok, you have your standard sshd on port 22, and want another?
How are you starting the non standard one?
Try this, on the Ubuntu box you want to have the second sshd listening on non standard port, first off, get the regular sshd up & running, once that is running, type this:

```

sudo /usr/sbin/sshd -p xxxx (ENTER)

```

Where, xxxx, is the non standard port, of course. And test the connection from localhost:

```

telnet localhost xxxx (ENTER)

```

And from another box on your LAN

```

telnet private.IP.address xxxx (ENTER)

```

You'll see something like this:
```

Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1

Protocol mismatch.
Connection closed by foreign host.

```

Type a few Enters to get out of that screen.

---

### Post by madverb on 2008-11-15
Nah, just ended up doing port redirection on the router. Would be nice to actually have it listening on a different port.

---

### Post by andrebrown on 2008-12-19
This issue isn't really solved.  What the problem preventing all these people from running sshd on a non-standard port?  Is there an extra configuration step that is missing?

My ssh server is configured to use key based authentication and a non-default port.  I'm testing it by attempting to login locally (ssh localhost).  When I use the default port, I can login fine.  When I change to a non-default port (eg. 4300) I get: Read from socket failed: Connection reset by peer.

```
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /home/user/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 4200.
debug1: Connection established.
debug3: Not a RSA1 key file /home/user/.ssh/user.rsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/user/.ssh/user.rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer

```

Here is the auth.log:

```
Dec 19 11:42:15 firefly sshd[14346]: error: Could not load host key: /etc/ssh/ssh_host_rsa_key
Dec 19 11:42:15 firefly sshd[14346]: error: Could not load host key: /etc/ssh/ssh_host_dsa_key
Dec 19 11:42:15 firefly sshd[14346]: error writing /proc/self/oom_adj: Permission denied
Dec 19 11:42:15 firefly sshd[14347]: fatal: No supported key exchange algorithms
Dec 19 11:48:17 firefly sshd[14411]: error: Could not load host key: /etc/ssh/ssh_host_rsa_key
Dec 19 11:48:17 firefly sshd[14411]: error: Could not load host key: /etc/ssh/ssh_host_dsa_key
Dec 19 11:48:17 firefly sshd[14411]: error writing /proc/self/oom_adj: Permission denied
Dec 19 11:48:17 firefly sshd[14412]: fatal: No supported key exchange algorithms

```

The permissions on the host key files:

```

-rw-r--r-- 1 root root 125749 2008-10-13 13:50 moduli
-rw-r--r-- 1 root root   1595 2008-10-13 13:50 ssh_config
-rw-r--r-- 1 root root   1891 2008-12-19 10:30 sshd_config
-r--r--r-- 1 root root   1873 2008-12-19 09:19 sshd_config.original
-rw------- 1 root root    672 2008-12-19 09:12 ssh_host_dsa_key
-rw-r--r-- 1 root root    602 2008-12-19 09:12 ssh_host_dsa_key.pub
-rw------- 1 root root   3239 2008-12-19 10:49 ssh_host_rsa_key
-rw-r--r-- 1 root root    734 2008-12-19 10:49 ssh_host_rsa_key.pub

```

My setup works when I use port 22.  When I make the change to 4300, it doesn't work.  Thats the only change I make, so the key is the port number.

---

### Post by fozzyuw on 2009-03-02
Yes, I'm having the same issue as presented by others in this thread.

I'm trying to change the port on OpenSSH to something like 1900. I did this by adding:```
Port 22
**Port 1900**
```
to the *sshd_config* file.

I then restarted OpenSSH and tried to connect via port 1900.  No dice.  netstat shows SSH listening on both ports and I can still connect via 22.

I was following this thread hoping to find an explanation, I'm guessing it has something to do with having to update the public keys to use the new port?

But I'm still trying to troubleshoot this issue.  I've got OpenSSH running on both port 22 and 1900, only 1900 won't connect with the same errors listed above.  I'll see if I can solve it and report it back here for others who find this thread looking for the same issue.

---

### Post by fozzyuw on 2009-03-03
Ok, the issue I was having, and possible the other people, is the simple fact that the port number I used was already in use by another application.

I pretty much discovered this doing some more research on Google and finding some pieces of details on multiple threads.

To find out more, change your sshd_config log detail to verbose, restart the server and then check your auth.log file to see if the server could bind to the port.
```
sudo /etc/ssh/sshd_config
[...]
LogLevel VERBOSE
[...]
sudo /etc/init.d/ssh restart
vim /var/log/auth.log
```
Scroll down to the end of the file and look for the restart command entry and see if you have the follow error:
```
error: Bind to port 1900 on :: failed. Address already in use.
error: Bind to port 1900 on 0.0.0.0 failed. Address already in use.
```
This will tell you if the port is already in use.  Or it might give you more clues as to why changing the port to a non-standard port isn't working when port 22 works.

Then test it locally if you can connect.
```
ssh localhost -p xxxx
```
Where 'xxxx' is the port number to use.

If it connects locally, then you know the OpenSSH server is working fine.  If you cannot connect remotely, it's most likely a Firewall issue.

Cheers!
Fozzy

---

### Post by Kepesk on 2009-09-12
> **DFord425 said:**
> i checked, sshd is running on both. I cannot connect to the localhost from the server. and when i run in verbose mode, here is the output ```
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.142 [192.168.1.142] port 3333.
debug1: Connection established.
debug1: identity file /home/dfordgt/.ssh/identity type -1
debug1: identity file /home/dfordgt/.ssh/id_rsa type -1
debug1: identity file /home/dfordgt/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
Read from socket failed: Connection reset by peer
```

Does anyone know what that means or how to fix it?

I discovered another cause for this exact same message.  When I was getting this, restarting SSH complained that the permissions for my host key files were too open.  So do:

```
sudo /etc/init.d/ssh restart
```

and if it complains about the permissions on any files, do 'sudo chmod -r' on those files.  Fixed it right up for me.

Thought I'd mention the possible alternate cause and solution for this problem so others can find it here.

---

