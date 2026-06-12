---
title: "Puppet agent problem"
date: 2011-06-21
forum: Server Platforms
---

### Post by vilvic on 2011-06-21
I'm in the process of setting up puppet and experiencing some issues.  I'm running Ubuntu 11.04 desktop and server in two seperate VM's.  I've installed puppet master (2.6.4) and puppet (2.6.4).  The puppet master and agent are happily working together.

I'm running the example in the book Pro Puppet.  This is the first example;

```
class sudo {
    package { sudo:
        ensure => present,
    }
    if $operatingsystem == "Ubuntu" {
        package { "sudo-ldap":
        ensure => present,
        require => Package["sudo"],
    }
    }
    file { "/etc/sudoers":
        owner => "root",
        group => "root",
        mode => 0440,
        source => "puppet://$puppetserver/modules/sudo/etc/sudoers",
        require => Package["sudo"],
    }
}
```On the agent I run the following command;

**puppet agent --server=<myserver> --no-daemonize --verbose --onetime**

The agent see's the change but I get an error;

info: Caching catalog for <agentServer>
info: Applying configuration version '123456789'
err: /Stage[main]/Sudo/Package[sudo-ldap]/ensure: change from purged to present
failed: Execution of '[B]/usr/bin/apt-get -q -y -o DPkg::Options::=--force-confold
install sudo-ldap[/B]' returned 100: E: Could not open lock file /var/lib/dpkg/lock
- open (13: Permission denied)
E: Unable to lick the administration directory (/var/lib/dpkg/), are you root?

I don't have another package manager open.

I understand what the problem is.  The agent is being run as the current logged in user and that user doesn't have permission to run apt-get.  Generally to run **apt-get** i have to do **sudo apt-get**.

I've thought about modifying the sudoers file and adding nopasswd for my user (as suggested in other posts) for apt-get but that doesn't solve the problem since the command in the puppet agent is not run with sudo.

I understand if I run the puppet agent as a daemon then it runs as user root which I guess would solve the problem.  I'm not sure it's best to run the agent as a daemon.  I might want to control when the agent pulls the updates from the puppet master (or through cron).

If I run;

**sudo puppet agent --server=<myserver> --no-daemonize --verbose --onetime**

I get a different error;

err: Could not request certificate: Retrieved certificate does not match private 
 key; please remove certificate from server and regenerate it with the current key

I've tried removing the ssl certs from both the puppet master and agent and run the command again.  I get the same problem.  When I remove the sudo from the start of the command the puppet agent is happy with the cert.

I though about adding my user to the root group as a test.  Even when I do that if I run **apt-get update** manually a permission denied.  I wondered if this has something to do with the root user being disabled by default on Ubuntu.

I'm a novice when it comes to these sorts of things.  Has anyone got this working or have any suggestions of how I might solve this issue?

---

### Post by masteinhauser on 2012-03-03
This is most likely too late for you, but I ran into this exact same problem this morning and was able to figure it out.

The fix that I found was to either run puppet by itself with sudo, or run the daemon. Without sudo, it looks into your home directory for certificates. This is, to me, expected behavior.

As you stated in Pro Puppet, I started the command without sudo and signed the certificate on the master server. When running puppet with sudo or as a daemon, this fails as it does not read or look for the certificate files in your home directory. 

To fix this you need to only run puppet on the node with sudo and/or as a daemon/service but first you need to revoke the certificate on the puppet master and then re-sign the certificate on the node you're now running.

First on Puppet Master:
```

puppet cert clean <node hostname>

```

Second on Puppet Node:
```

# One of the following
sudo puppet agent --server=puppet.example.com --no-daemonize --verbose
# OR
sudo service puppet start

```

Lastly on Puppet Master:
```

puppet cert sign node.example.com

```

References:
[http://docs.puppetlabs.com/man/cert.html](http://docs.puppetlabs.com/man/cert.html)

---

