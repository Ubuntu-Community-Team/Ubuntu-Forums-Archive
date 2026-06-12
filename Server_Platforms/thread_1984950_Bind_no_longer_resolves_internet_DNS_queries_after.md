---
title: "Bind no longer resolves internet DNS queries after upgrading to 12.04"
date: 2012-05-22
forum: Server Platforms
---

### Post by DarwinLabs on 2012-05-22
Hello, I am no longer able to query any external DNS names such as google.com or ubuntu.com after upgrading to 12.04 Server but I am still able to do internal ones. I noticed the following in the syslog:

error (no valid RRSIG) resolving 'ubuntu.com/DS/IN': 192.48.79.30#53
validating @0x7f249c0975e0: com SOA: no valid signature found
validating @0x7f249c0975e0: 88V0RT7EQ1MFFA632RRT4O1UDIU0GNQF.com

How do I fix this issue, I didn't have this problem before upgrading to 12.04 and haven't touched any configs I also made sure it didn't replace any configurations during the upgrade.

Thanks

---

### Post by hawkmage on 2012-05-22
I have a feeling you are falling victim of the switch from the standard libc based name resolution to the dnsmask that is not a plugin to NetworkManager.

To solve my issue with this I had to disable the dnsmask plugin in the NetworkManager config file and install the full dnsmask package and configure it.

It seams that there is no way, at least none that I could find, to configure the options of the NetworkManager dnsmask plugin.

There was a thread on these forums talking about this but I can not find it now, I will look a bit more and update this with what I find.

---

### Post by DarwinLabs on 2012-05-22
I figured out how to make it work.
inside named.conf.options to the following in red:
```

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        // forwarders {
        //      0.0.0.0;
        // };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
[COLOR="red"]dnssec-enable no;[/COLOR]
        [COLOR="Red"]// dnssec-validation auto;[/COLOR]

        auth-nxdomain no;    # conform to RFC1035
        // listen-on-v6 { any; };
};

```

---

### Post by hawkmage on 2012-05-22
Didn't realize you were running bind locally on the system.

---

