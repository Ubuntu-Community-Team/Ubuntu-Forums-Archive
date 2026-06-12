---
title: "How to do specific denyhost subnet settings"
date: 2008-09-18
forum: Security
---

### Post by Diskdoc on 2008-09-18
Hi!

I´m running a Edubuntu LTSP server and I´d like to have our router forward a port to the server so I can connect to the server from anywhere via SSH. That´s easy to set up - the problem is security.

Denyhost was chosen to shield sshd from attacks. The problem is Denyhost keep putting terminals (along with potental hackers from the external network) on the /etc/hosts.deny-list so noone can log in from them! I need different strictness in rules for the terminals (running on their own subnet on a separate NIC on the server). How do I do that?

Also, sshd is needed for the terminals so any user can log in on them - but I´d like to give only specific users access from the external network. How do I do that?

/ Olle

---

### Post by geovani on 2008-09-18
When run as a cron job, DenyHosts checks the end of the authentication log for recent failed login attempts. It records information about their originating IP addresses and compares the number of invalid attempts to a user-specified threshold. If there have been too many invalid attempts it assumes a dictionary attack is occurring and prevents the IP address from making any further attempts by adding it to /etc/hosts.deny on the server. DenyHosts 2.0 and above support centralized synchronization, so that repeat offenders are blocked from many computers.

geovani

[one time ads]("one time ads")

---

### Post by amac777 on 2008-09-18
I have no idea about DenyHosts.....

But regarding configuring sshd to allow users to login from local network but not from a remote network, I think this is possible.

From the man page for sshd_config:

> AllowUsers
             This keyword can be followed by a list of user name patterns,             separated by spaces.  If specified, login is allowed only for             user names that match one of the patterns.  Only user names are             valid; a numerical user ID is not recognized.  By default, login             is allowed for all users.  If the pattern takes the form             USER@HOST then USER and HOST are separately checked, restricting             logins to particular users from particular hosts.  The allow/deny             directives are processed in the following order: DenyUsers,             AllowUsers, DenyGroups, and finally AllowGroups.

             See PATTERNS in ssh_config(5) for more information on atterns

And from the man page for ssh_config(5):

> PATTERNS
     A pattern consists of zero or more non-whitespace characters, ‘*’ (a     wildcard that matches zero or more characters), or ‘?’ (a wildcard that     matches exactly one character).  For example, to specify a set of decla&#8208;     rations for any host in the “.co.uk” set of domains, the following pat&#8208;     tern could be used:
           Host *.co.uk

     The following pattern would match any host in the 192.168.0.[0-9] network range:

           Host 192.168.0.?

     A pattern-list is a comma-separated list of patterns.  Patterns within
     pattern-lists may be negated by preceding them with an exclamation ark
     (‘!’).  For example, to allow a key to be used from anywhere within an
     organisation except from the “dialup” pool, the following entry (in
     authorized_keys) could be used:           from="!*.dialup.example.com,*.example.com"


So I think you could modify /etc/ssh/sshd_config to add an **Allowusers** list of the accounts you want to allow ssh access. Include your username with no @host part so you can login from anywhere. But for all the other users, add something like @192.168.1.? after their login name. (obviously change that ip address if your internal network is something different.)

I think this will work, but I can't test it easily so not 100% sure. Hopefully I'm not misreading the man pages.

---

### Post by Diskdoc on 2008-09-18
Thanks for your replies! Amac777, your solution looks smooth! I am already using AllowGroups to narrow down possible usernames to brute force. Unfortunately, the @host-pattern doesn´t seem to work with AllowGroups (although possibly with AllowUsers).

I tried a few of theese:

(AllowGroups) students@192.168.2.? / students@192.168.2.255 / students@192.168.2.*

Even students@192.168.2.159 (the specific host I experimented with) wouldn´t let me log in. Only "AllowGroups students" works.

Geovani, I know what Denyhost is supposed to do - the problem is I need more control over to which host it does it, and when. I´m looking into fail2ban now but one downside of that program is it doesn´t have hostlist-syncing, which is a nice feature in Denyhost.

Maybe the best things would be to have two sshd running - one for the terminals in our internal network (port 22, specified groups) and one sshd for the external network (odd port for security through obscurity and only allowing on or two specific users). But how do I do that?

---

### Post by amac777 on 2008-09-18
Yeah, from the man page for sshd_config, it doesn't say anything about using @host for the AllowGroups section..... If you have too many users so don't want to list them all individually in AllowUsers then sshd_config is probably not going to help you.

Maybe you can do something with pam_access. There is a little tutorial I found here that seems to be pretty easy to follow:

[http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html](http://www.cyberciti.biz/tips/openssh-root-user-account-restriction-revisited.html)

You might be able to setup a rule where all users are allowed to login from the local network, except for your user, who is thereby allowed to login from anywhere. However, unless someone else tells you how to write that rule, you'll have to figure it out on your own from that tutorial or post a new thread about pam_access. I've never used it so not 100% sure.

---

