---
title: "NX - Too many authentication failures for nx"
date: 2008-11-26
forum: Security
---

### Post by Endolith on 2008-11-26
Recently I started getting these errors when trying to connect to my desktop through NX from work.  Today I uninstalled all the commercial NX stuff and tried FreeNX instead.  Still doesn't work.  I can connect from the desktop to the laptop, but I can't connect from the laptop to the desktop.

```
NX> 203 NXSSH running with pid: 26486
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 192.168.1.131 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
Received disconnect from 192.168.1.131: 2: Too many authentication failures for nx


```

I can ssh normally between the laptop and the desktop using shared keys (which I only kind of understand, but it works)

I can ssh into either of them from the work computer using a password.

I have no idea how to solve this.  Any ideas?

---

### Post by lemming465 on 2008-11-28
ssh with *too many authentication failures* usually means that your clients is randomly trying more unlocked public keys than your server is patient enough to accept.  There are multiple evasive actions:

Delete all the current keys with "ssh-add -D" and see if you can log in successfully.

Add paragraphs to ~/.ssh/config along the lines of ```
host foo
  hostname foo.example.com
  identifyfile /home/YOU/.ssh/foo
```
so that it only tries the specific correct key.

Increase the MaxAuthTries value in /etc/ssh/sshd_config, say doubling it to 12.  I'd be on an alternate port though, as this allows faster guessing attacks by people trying to brute force their way in.

Use "-o PubkeyAuthenication=no" with the client to avoid cached public keys and insist on passwords.

---

### Post by Endolith on 2008-11-29
> **lemming465 said:**
> Delete all the current keys with "ssh-add -D" and see if you can log in successfully.

On server or client?

> Increase the MaxAuthTries value in /etc/ssh/sshd_config, say doubling it to 12.  That seems to have fixed it.  It was previously set to 2.

> I'd be on an alternate port though, as this allows faster guessing attacks by people trying to brute force their way in.I already am.

---

### Post by lemming465 on 2008-11-29
*ssh-add -D* would be run on the client; it deletes the cached ssh-agent entries.  I'm glad the MaxAuthTries helped.

---

### Post by Endolith on 2008-12-01
> **lemming465 said:**
> Increase the MaxAuthTries value in /etc/ssh/sshd_config

I'm confused.  Is this for trying passwords or trying keys?

It stopped working.  Now it says something like "The NX service is not available or the NX access was disabled on host".

Running ssh-add -D on the client works, but running it on the host gives an error: "Could not open a connection to your authentication agent."

---

### Post by lemming465 on 2008-12-01
> is **MaxAuthTries** for trying passwords or trying keys
I believe it's the total number of tries, which could be any mixture of public keys, passwords, NTLM, Kerberos, etc.

> It stopped working ... "The NX service is not available" 
That suggests you need to see whats running or not on the server.  In the /var/log/ directory check the *messages*, *daemon.log* and *auth.log* fles for errors.  See if **sudo netstat -tlnp** shows anything listening, or if **ps -elfH** shows anything related running.

You might be up against some of the bugs nomachines has described [against ubuntu 8.10 and fedora 10]("http://www.nomachine.com/news-read.php?idnews=252").  They describe a possible workaround for the Ubuntu bug.
> Running ssh-add -D on the client works, but running it on the host gives an error: "Could not open a connection to your authentication agent."
This is normal; the client is the one with the cached private keys being managed by the agent.  I think on ubuntu 8.10 it's the *seahorse-agent* rather than the older *ssh-agent*.

---

### Post by Endolith on 2008-12-01
> **lemming465 said:**
> I believe it's the total number of tries, which could be any mixture of public keys, passwords, NTLM, Kerberos, etc.

Huh.  I don't understand how that works.

> 
That suggests you need to see whats running or not on the server.  In the /var/log/ directory check the *messages*, *daemon.log* and *auth.log* fles for errors.  See if **sudo netstat -tlnp** shows anything listening, or if **ps -elfH** shows anything related running.

You might be up against some of the bugs nomachines has described [against ubuntu 8.10 and fedora 10]("http://www.nomachine.com/news-read.php?idnews=252").  They describe a possible workaround for the Ubuntu bug.Well it worked the other day when I changed the maxauthtries, and that was Intrepid, too.  I don't know what I've changed since then.  Just an upgrade and a reboot, but I don't remember it upgrading anything related to ssh or NX.

> 
This is normal; the client is the one with the cached private keys being managed by the agent.  I think on ubuntu 8.10 it's the *seahorse-agent* rather than the older *ssh-agent*.The "host" is used as an ssh client, too, though.  The two systems are very similar, so I don't know why it would be running on one but not the other.

---

### Post by lemming465 on 2008-12-01
> I don't understand how {login authentication} works.
By the time one gets done with the interactions between PAM (pluggable authentication modules), NSS (name service switch), and ssd_config, hardly anyone understands it.  Out of the box Ubuntu sshd will accept at least public key and password authentication.

> a reboot
I think something has to run **nxserver --start** when you reboot.    Check /etc/init.d for a system-V style start/stop script related to NX.  If you find it, try running it with an argument of "start". E.g. "sudo /etc/init.d/nx* start" if it's called something starting with nx, and there is only one such.

If that gets you back in, check for a symbolic link from /etc/rc2.d/S??nx* back to the /etc/init.d script.  If there isn't one, and your runlevel is the default to (check with "who -r"), make one so that it will happen automatically using update-rc.d, or sysv-rc-conf, or bum, or just plain "ln -s".

> The "host" is used as an ssh client, too, though. The two systems are very similar, so I don't know why it would be running on one but not the other.
It depends on what happens when you log in.  Most client logins are via GDM, so lots of stuff including seahorse-agent are kicked off by the default gnome session configuration.  Most server logins are terminal emulation via SSH, so only stuff in ~/.bash_profile or the like gets started.  So out of the box a server login doesn't start any kind of cryptological caching agent by default.

---

### Post by Endolith on 2008-12-01
> **lemming465 said:**
> By the time one gets done with the interactions between PAM (pluggable authentication modules), NSS (name service switch), and ssd_config, hardly anyone understands it.

That's what I figured.  :)  There should be a nice easy-to-use Gnome tool for setting up this stuff in common configurations.  I only discovered the seahorse interface today, called *Passwords and Encryption Keys* (under the *Accessories* menu for some odd reason...)

> It depends on what happens when you log in.  Most client logins are via GDM, so lots of stuff including seahorse-agent are kicked off by the default gnome session configuration.  Oh, ok.  I mostly use it as a headless server, so no one's logging into the GUI locally.  I don't know why it would have worked two days ago but not today.  I'll look into this later.

---

### Post by lemming465 on 2008-12-01
> There should be a nice easy-to-use Gnome tool for setting up this stuff That's one of the things the ubiquity installer does, I think.  I'm not sure if there is a GUI tool after that; there is a CLI helper tool *auth-client-config*.  Redhat has a GUI tool *system-auth-config*.  However, in corporate environments you'll have to tune things depending on your policies about where the LDAP directory is, what the split between local and network users is, whether or not you are using Kerberos, what your Microsoft interoperability strategy is, and so on.  No simple GUI tool is going to get the subtleties right.
> I don't know why it would have worked two days ago but not today.
I'm still wondering if **sudo nxserver --start** got run after the reboot, or not.

---

