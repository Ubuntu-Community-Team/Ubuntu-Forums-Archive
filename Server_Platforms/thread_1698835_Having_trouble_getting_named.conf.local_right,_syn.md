---
title: "Having trouble getting named.conf.local right, syntax error"
date: 2011-03-02
forum: Server Platforms
---

### Post by MechaMechanism on 2011-03-02
EDIT:  SOLVED.  I consolidated my logging into one statement.


I'm getting syntax error.  What am I doing wrong with my named.conf.local file.

> //
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

logging {
    channel query.log {
        file "/var/log/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity dynamic;
    };
};

logging {
    channel query.log {
        file "/var/log/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity debug 3;
    };

    category queries { query.log; };
};

---

### Post by Vegan on 2011-03-02
Read the manual, 

```
man bind
```

---

### Post by MechaMechanism on 2011-03-03
> **Vegan said:**
> Read the manual, 

```
man bind
```
RTFM huh.  You obviously have never seen the man page because if you had, you would realize it has nothing to do with bind9, the DNS server.  My problem is that I'm most likely using the ; character wrong.  I need help with knowing how to close the option properly.  It's just like HTML markup.  I looked online at the syntax and don't understand it very well and hence I'm here.

We here at the Ubuntu Forums don't appreciate people saying RTFM.  If you have nothing to contribute then stay quiet and say nothing at all.

For your future reference.
```
$man named
```

---

### Post by James78 on 2011-03-03
Does this work?
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

logging {
    channel query_log {
        file "/var/log/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity dynamic;
    };
    channel query_log1 {
        file "/var/log/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity debug 3;
    };

    category queries {
        query_log;
        query_log1;
    };
};

```I don't see why you want 2 query logs though. It says set the severity to dynamic to see all debug messages, which is done in channel query_log, so setting channel query_log1 to debug 3 seems like overkill.

Or this.
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

logging {
    channel query.log {
        file "/var/log/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity dynamic;
    };

    category queries { query.log; };
};

logging {
    channel query.log {
        file "/var/log/query.log";
        // Set the severity to dynamic to see all the debug messages.
        severity debug 3;
    };

    category queries { query.log; };
};                      
```By the way, the syntax error message you got would be really helpful in helping us figure out your problem. ;)

[http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html)

---

### Post by mciverza on 2011-03-03
You might be missing a };
they should be in pairs.

Try:

//
// Do any local configuration here
//

> // Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

logging {
channel query.log {
file "/var/log/query.log";
// Set the severity to dynamic to see all the debug messages.
severity dynamic;
};
};

logging {
channel query.log {
file "/var/log/query.log";
// Set the severity to dynamic to see all the debug messages.
severity debug 3;
};
};  // that was the line I added
category queries { query.log; };
};


Or else just comment all the lines out?

---

### Post by James78 on 2011-03-03
> **mciverza said:**
> You might be missing a };
they should be in pairs.
I used my syntax highlighting Kate editor and it shows the ending brackets to be all in order. From my first glance though, it did look like you were right.

---

### Post by dam0cles on 2011-03-03
Is there a reason for logging the same set of messages (with different filters) to the same file? Would also query the use of 2 logging clauses.

Not sure if it's the approved method but mine seems to work set up like this.

```

logging {
category "resolver" { "monitor"; };
category "queries" { "monitor"; };
category "general" { "generic"; };
category "lame-servers" { "lame"; };
category "client" { "def"; };
category "default" { "def"; };
category "database" { "def"; };
category "security" { "def"; };
category "config" { "def"; };
category "xfer-in" { "def"; };
category "xfer-out" { "def"; };
category "notify" { "def"; };
category "unmatched" { "def"; };
category "network" { "def"; };
category "update" { "def"; };
category "dispatch" { "def"; };
category "dnssec" { "def"; };

channel "monitor" {
file "/var/log/named/monitor" versions 3 size 20k;
severity debug 1;
print-severity yes;
print-time no;
print-category yes;
};

channel "lame" {
file "/var/log/named/lame" versions 3 size 20k;
print-time no;
print-category yes;
};
channel "generic" {
file "/var/log/named/generic" versions 3 size 20k;
print-time no;
print-category yes;
};
channel "def" {
file "/var/log/named/def" versions 3 size 20k;
print-time no;
print-category yes;
};
};

```
Of course I'm still new to this so I could be well off target.
This may also be useful [http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html)

---

### Post by MechaMechanism on 2011-03-03
> **James78 said:**
> Does this work?
I don't see why you want 2 query logs though. It says set the severity to dynamic to see all debug messages, which is done in channel query_log, so setting channel query_log1 to debug 3 seems like overkill.

Or this.By the way, the syntax error message you got would be really helpful in helping us figure out your problem. ;)

[http://www.zytrax.com/books/dns/ch7/logging.html](http://www.zytrax.com/books/dns/ch7/logging.html)
Thanks for the link.  Thats just what I needed.  I have logging now.  Except that the apparmor profile is preventing the logging.  But I can handle apparmor no problem.  The reason I wanted so much logging is to learn about bind.  I figured after looking at the logs and seeing what happens I would send all logs to null.  Right now I send lame servers to null.  Thanks again.  I'll be signing up for the bind mailing list too.

---

