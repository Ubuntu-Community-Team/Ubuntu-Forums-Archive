---
title: "ircd-hybrid and hybserv errors"
date: 2011-03-05
forum: Server Platforms
---

### Post by googleworldblog on 2011-03-05
Alright, so I'm trying to set up hybserv with ircd-hybrid and I keep getting this error:

```
*** Notice -- Attempt to re-introduce server 
          *servername* SID  from [unknown@127.0.0.1]

```

This is the relevant portion of my hybserv.conf file:

```
# The .include directive is available so you can store
# additional configuration lines in separate files.
# Syntax: .include "filename"

#.include "opers.conf"

# This should contain the name(s) and email(s) of the services
# administrator(s) - just to tell users who to contact w/ questions

A:Jonathan Frederickson <*email*>

# The first field is the name you want the services server to be.  It
# should match the C/N lines of the hub server.  The second field is
# the text info for the services (it corresponds to the third field
# in a server's M line)

N:*servername*:bhg-irc

# This line should contain three fields. In order, the password for
# the connection, the hostname (or IP address) of the hub server to
# connect to, and the port to connect at. If no port is specified,
# DefaultHubPort, specified in settings.conf, is used.  You may put
# as many S: lines as you wish. If services cannot connect to the
# first server, or gets disconnected, it will move onto the next one
# and so on.
# (The password must match the C/N lines of the hub server).

S:*password*:127.0.0.1

# V: lines specify a virtual hostname to bind to when connecting to
# a remote site. IP Addresses can be used as well. If multiple V:
# lines are given, only the first is used

V:127.0.0.1

```

This is the relevant portion of my ircd.conf file:

```
connect {
        /* name: the name of the server */
        name = "*servername*";

        /* host: the host or IP to connect to.  If a hostname is used it
         * must match the reverse dns of the server.
         */
        host = "127.0.0.1";

        /* passwords: the passwords we send (OLD C:) and accept (OLD N:).
         * The remote server will have these passwords reversed.
         */
        send_password = "*password*";
        accept_password = "*password*";

        /* encrypted: controls whether the accept_password above has been
         * encrypted.  (OLD CRYPT_LINK_PASSWORD now optional per connect)
         */
        encrypted = no;

        /* port: the port to connect to this server on */
        port = 6666;

        /* hub mask: the mask of servers that this server may hub. Multiple
         * entries are permitted
         */
        hub_mask = "*";

        /* leaf mask: the mask of servers this server may not hub.  Multiple
         * entries are permitted.  Useful for forbidding EU -> US -> EU routes.
         */
        #leaf_mask = "*.uk";

        /* class: the class this server is in */
        class = "server";

        /* autoconnect: controls whether we autoconnect to this server or not,
         * dependent on class limits.
         */
        autoconn = no;

        /* compressed: controls whether traffic is compressed via ziplinks.
         * By default this is disabled
         */
        #compressed = yes;

        /* lazylink: controls whether this server is a LazyLink.  LazyLink
         * servers may NOT hub.  see doc/LazyLinks.as.implemented.txt
         */
        #lazylink = yes;

        /* masking: the servername we pretend to be when we connect */
        #fakename = "*.arpa";
};


```

And this bit at the top which may be relevant:

```
/* serverinfo {}:  Contains information about the server. (OLD M:) */
serverinfo {
        /* name: the name of our server */
        name = "*servername*";

        /* description: the description of our server.  '[' and ']' may not
         * be used here for compatibility with older servers.
         */
        description = "ircd-hybrid 7.2-debian";

        /* network info: the name and description of the network this server
         * is on.  Shown in the 005 reply and used with serverhiding.
         */
        network_name = "bhg-irc";
        network_desc = "i am a network short and stout";

        /* hub: allow this server to act as a hub and have multiple servers
         * connected to it.  This may not be changed if there are active
         * LazyLink servers.
         */
        hub = yes;

        /* vhost: the IP to bind to when we connect outward to ipv4 servers.
         * This should be an ipv4 IP only.
         */
        #vhost = "*IP*";

        /* vhost6: the IP to bind to when we connect outward to ipv6 servers.
         * This should be an ipv6 IP only.
         */
        #vhost6 = "3ffe:80e8:546::2";

        /* max clients: the maximum number of clients allowed to connect */
        max_clients = 512;
};

```

---

