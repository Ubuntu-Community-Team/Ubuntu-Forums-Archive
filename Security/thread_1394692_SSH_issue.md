---
title: "SSH issue"
date: 2010-01-30
forum: Security
---

### Post by cromble1 on 2010-01-30
I'm having an issue with ssh clients choosing not to start a shell/command when connecting to my ssh server.  This is a problem for my situation and I have tried using ForceCommand /path/totheirshell in sshd_config but it doesn't appear to force them to run anything at all.

Is there another way around this?  It is a shame there isn't a 'ForceShell' option there somewhere...

Thanks in advance.

---

### Post by falconindy on 2010-01-30
What do their corresponding entries look like in /etc/passwd? Are they assigned a shell there? I assume when you're making changes to sshd_config you're restarting the ssh server to let them take effect, yes?

---

### Post by cromble1 on 2010-01-30
Thanks for your response.  Yes they have shells set in /etc/passwd and I had restarted the ssh server after making the changes to sshd_config.  The problem arises from a checkbox in Putty that lets them choose not to run a shell/command when connecting and I think the *nix ssh client equiv. is the -N option.

I tested to make sure the ForceCommand option was working by logging in normally and its command was forced on me yet by not requesting a shell/command I could connect like before and not run a shell.

---

### Post by cromble1 on 2010-02-01
Is this worth reporting as a bug to the openssh team?

---

### Post by Lars Noodén on 2010-02-01
> **cromble1 said:**
> Is this worth reporting as a bug to the openssh team?

Sounds like  it is an Ubuntu issue if anything.  What is the server configuration (sshd_config) like?

---

### Post by cromble1 on 2010-02-01
Pretty standard...default port changed, usePAM enabled, strictmodes, X11fordwarding disabled.

Has anyone tried connecting to their own ssh server with ssh -N or putty with the 'do not execute command/shell' option ticked while having ForceCommand set in sshd_config?

---

### Post by bodhi.zazen on 2010-02-01
What are you trying to do exactly ? What command are you trying to force ?

Can you post your configuration file ?

What options are you giving ssh on the command line ?

-N == do not execute a command. -N is typically used when you are port forwarding, but, the N option prevents you from executing your forced command.

It seems you are chasing you tail, forcing a command in sshd_config, then using the -N to prevent the command from running ???

---

### Post by cromble1 on 2010-02-01
Clients are using this server for port forwarding which is the intended use but when they connect with the -N option from their SSH client it causes little issues elsewhere that I am trying to avoid and having trouble working around.  One issue is some clients are on 'timed' accounts and need to be forcefully disconnected which is done by setting their shell to a custom script and another smaller issue is these clients don't show up when running 'w'.

I need to be able to force them to run their shell when they login and as the server I should be able to disregard their request to not execute  their shell on connecting.  The ForceCommand option in sshd_config is useless if the client can simply bypass it by requesting not to execute anything.  

I have tried setting the clients shell to bash and using ForceCommand to run a script which determined the clients 'timer' shell and executed it for them but this obviously fails.

---

### Post by bodhi.zazen on 2010-02-01
Odd scenario.

Personally I force commands with ssh keys, perhaps that would work for you?

Hard to know as your set up sounds a bit odd.

---

### Post by cromble1 on 2010-02-01
Basically it is a type of proxy server using SSH instead of something like Socks server 5(I would almost prefer to be using SS5 but I couldn't find a way to get proxy authorization and timed accounts working well enough).

SSH just ended up being the most complete/reliable/secure option at the end of the day to get the job done with this one exception.  This issue actually effects a number of providers setup in this manner whether they are aware of it or not.

---

### Post by Lars Noodén on 2010-02-03
> **cromble1 said:**
> Basically it is a type of proxy server using SSH instead of something like Socks server 5(I would almost prefer to be using SS5 but I couldn't find a way to get proxy authorization and timed accounts working well enough).

SSH just ended up being the most complete/reliable/secure option at the end of the day to get the job done with this one exception.  This issue actually effects a number of providers setup in this manner whether they are aware of it or not.

What do you mean by timed accounts?  
What kind of protocols do you want to use the SOCKS proxy for?

SSH + SSHd can work as a SOCKS proxy.  See 'Dynamic' forwarding. That would give you authentication, and with use of Kerberos if needed.  

Restricting access to certain times of the day can be done by not running sshd as a daemon, but instead using [xinetd](http://linux.die.net/man/5/xinetd.conf) to invoke it on-demand.  If you work at it, you can probably even give different groups different restrictions.

---

### Post by Lars Noodén on 2010-02-03
Stop sshd from running as standalone daemon:

```

 sudo update-rc.d ssh remove
 sudo /etc/init.d/ssh stop

```

Set up xinetd.conf and reload:

```

service ssh
{
	socket_type     = stream
	protocol        = tcp
	wait            = no
	user            = root
	server          = /usr/sbin/sshd
	**server_args     = -i**
	per_source      = UNLIMITED
	log_on_failure  = USERID HOST
	**access_times    = 08:00-15:25**
	banner          = /etc/banner.inetd.connection.txt
	banner_success  = /etc/banner.inetd.welcome.txt	
	banner_fail     = /etc/banner.inetd.takeahike.txt

	# log_on_success  = PID HOST DURATION TRAFFIC EXIT
	# instances       = 10
	# nice            = 10
	# bind            = 192.168.0.100
	# only_from       = 192.168.0.0
	# no_access       = 192.168.54.0
	# no_access       += 192.168.33.0
}

```

Don't lock yourself out while experimenting.

---

### Post by cromble1 on 2010-02-07
Thank you for the replies.  I haven't tested your suggestion yet  as it makes no mention of fixing the main problem I am facing of clients connecting with ssh -N or Putty's option to not execute a shell/command.

The 'timed' accounts have a basic shell script set as their shell that sleeps for a duration and exits to disconnect the user once their time is up.  By using ssh -N they can bypass their shell and stay connected for an unlimited amount of time and don't show up when the admin runs 'w'.  ForceCommand in sshd_config does not force a client using ssh -N to run their shell/command.

---

