---
title: "SSH to server using GSSAPI/Kerberos prompts for password when using DNS alias"
date: 2010-01-15
forum: Security
---

### Post by cpdohert on 2010-01-15
I'm not sure if this is quite the right forum for this, please let me know if I'm in the wrong spot.

I have a Kerberos/LDAP/OpenAFS server running on Debian lenny, set up according to Davor Ocelic's  excellent guide here ([http://techpubs.spinlocksolutions.com/dklar/kerberos.html](http://techpubs.spinlocksolutions.com/dklar/kerberos.html)).  SSHd has ben configured to use GSSAPI auth and the clients have been configured to pass auth tokens through to the server.

My clients are all Ubuntu 9.10 x86 fully patched.  On the clients, OpenAFS has been compiled and installed as a kernel module and git 1.6.6 has been compiled from source and installed.  Otherwise, all software is stock Ubuntu repository-ware.

The setup is working fine as long as I connect to the primary server using its hostname:

peter@client01:~$ ssh nana
<connection goes through seamlessly without prompting>
peter@nana:~$

If I try to connect via a DNS alias (actually a second CNAME record), I get:

peter@client01:~$ ssh git1
peter@git1's password:
<connection completes>
peter@nana:~$

I need both passwordless auth *and *the DNS alias working, as it's internal policy that user connections are only ever made to service names, not real hostnames.

I have tried adding a second host principal to Kerberos for the alias (git1.darling.local) in addition to the host principal for the hostname (nana.darling.local).

If I turn off PasswordAuthentication in sshd_config, then "ssh git1" doesn't even fall through to passwords; it just denies logins.  So it looks like it's not even using GSSAPI for the DNS alias.

So:

1) Is what I want even possible?  I can't find anything that indicates that there's anything odd about DNS aliases such that this should happen.

2) Which config files should I post to help debug this?  There's a lot and I didn't want to start blarfing them here if they aren't helpful.

---

### Post by cpdohert on 2010-01-15
Found the problem.  All DNS related.

1) What I thought were CNAME records were actually A records; I changed these back to proper CNAME records.

2) There was no PTR record for the Kerberos KDC; I added this.

I suspect that the CNAME record was the most important issue, but anyway it works now.

---

