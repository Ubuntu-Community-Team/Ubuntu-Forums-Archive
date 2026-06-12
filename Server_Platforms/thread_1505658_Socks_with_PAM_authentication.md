---
title: "Socks with PAM authentication?"
date: 2010-06-09
forum: Server Platforms
---

### Post by DouglasK on 2010-06-09
Does anyone here have Danted (or any other socks5 server) working with PAM authentication?  My basic goal is that users need to use their system user/password to use the Socks server.  

The server is Ubuntu Server x86 10.04 with the Xbuntu desktop added in.

If anyone's got it running with PAM, please reply with a sample config or a link to a howto.  Again, I'm not a die hard fan of Danted.  I'm open to other options.

Here's the config:

```


# $Id: sockd.conf,v 1.43 2005/12/26 16:35:26 michaels Exp $
#
# the server will log both via syslog, to stdout and to /var/log/lotsoflogs
logoutput: syslog

# The server will bind to the address 10.1.1.1, port 1080 and will only
# accept connections going to that address.
#internal: 10.1.1.1 port = 1080
# Alternatively, the interface name can be used instead of the address.
internal: eth0 port = 1080

# all outgoing connections from the server will use the IP address
# 195.168.1.1
external: 192.168.1.100

# list over acceptable methods, order of preference.
# A method not set here will never be selected.
#
# If the method field is not set in a rule, the global
# method is filled in for that rule.
#

# methods for socks-rules.
# method: pam username none #rfc931
method: pam none
# methods for client-rules.
# clientmethod: pam # username none

# when doing something that can require privilege, it will use the
# userid:
user.privileged: proxy

# when running as usual, it will use the unprivileged userid of:
user.notprivileged: nobody

# If you compiled with libwrap support, what userid should it use
# when executing your libwrap commands?  "libwrap".
user.libwrap: nobody


# enable the bind extension.
extension: bind

# how many seconds can pass from when a client connects til it has
# sent us it's request?  Adjust according to your network performance
# and methods supported.
connecttimeout: 60

# how many seconds can the client and it's peer idle without sending
# any data before we dump it?  Unless you disable tcp keep-alive for
# some reason, it's probably best to set this to 0, which is
# "forever".
iotimeout: 86400 # or perhaps 86400, for a day.

#
# The actual rules.  There are two kinds and they work at different levels.
#

# Allow our clients, also provides an example of the port range command.
client pass {
    from: 192.168.0.0/16 port 1-65535 to: 0.0.0.0/0
#    method: pam # rfc931 # match all idented users that also are in passwordfile
}



# drop everyone else as soon as we can and log the connect, they are not
# on our net and have no business connecting to us.  This is the default
# but if you give the rule yourself, you can specify details.
client block {
    from: 0.0.0.0/0 to: 0.0.0.0/0
    log: connect error
}


# the rules controlling what clients are allowed what requests
#

# you probably don't want people connecting to loopback addresses,
# who knows what could happen then.
block {
    from: 0.0.0.0/0 to: 127.0.0.0/8
    log: connect error
}


# everyone from our internal network, 10.0.0.0/8 is allowed to use
# tcp and udp for everything else.
pass {
    from: 192.168.0.0/16 to: 0.0.0.0/0
    protocol: tcp udp
}

# last line, block everyone else.  This is the default but if you provide
# one  yourself you can specify your own logging/actions
block {
    from: 0.0.0.0/0 to: 0.0.0.0/0
    log: connect error
}


```Thanks,
   Douglas

---

