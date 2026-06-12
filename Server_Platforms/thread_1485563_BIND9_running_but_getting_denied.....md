---
title: "BIND9 running but getting denied...."
date: 2010-05-17
forum: Server Platforms
---

### Post by wgregori on 2010-05-17
I would appreciate a little assistance... I just installed BIND9 and have been playing around with it (learning)... 

I have created a zone file for wayne-jill.com and have a friend performing secondary. The error message below is coming from my secondary providor... odd that is doesn't reference an attempted zone-transfer.... Any ideas why I'm getting this error message?

May 16 20:49:25 ubuntuMaster named[818]: client 204.233.235.33#6541: query (cache) 'wayne-jill.com/SOA/IN' denied


my zone file allows for the zone transfer

zone "wayne-jill.com" {
             type master;
            file "/etc/namedb/db.wayne-jill.com";
		allow-transfer { 204.233.235.33; };
        };


Thanks!

---

### Post by terazen on 2010-05-17
Try adding this to named.conf and then reload bind:
```
     allow-query-cache { any; };
```

Also I don't think that error has anything to do with zone transfer.  I think it's just for regular lookups to the server.

When you're updating bind are you updating the serial number in the zone file before reloading?

---

### Post by wgregori on 2010-05-17
hummm... still receiving all these denies...  Tried your idea

	allow-query { any; };
      allow-recursion { any; };
     allow-query-cache { any; };

named[818]: client 204.233.235.33#2456: query (cache) 'wayne-jill.com/SOA/IN' denied

Still getting all these denies... can someone tell me what this entries means?

Thanks,
Wayne

---

### Post by terazen on 2010-05-18
Can you post more of your configuration?

---

### Post by wgregori on 2010-05-19
thanks for asking :)

Here is my entire config


options {

	directory "/etc/namedb";
	pid-file "/var/run/named.pid";
	statistics-file "/var/run/named.stats";
  

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	// forwarders {
	// 	0.0.0.0;
	// };
     
	allow-query { any; };
    // allow-recursion { trusted; };
     allow-recursion { any; };
     allow-query-cache { any; };


	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};



acl "trusted" {
     192.168.1.0/24;
     192.168.2.0/24;
     10.153.154.0/24;
     localhost;
     localnets;
     204.233.235.33/32;
 };


logging {
    channel query.log {      
        file "/var/log/query.log" versions 3 size 20m;
    	print-time yes;
    	print-category yes;


        // Set the severity to dynamic to see all the debug messages. 
        severity debug 3; 
        }; 

    category queries { query.log; }; 
};


zone "localhost" {
	type master;
	file "/etc/namedb/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/namedb/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/namedb/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/namedb/db.255";
};



zone "wayne-jill.com" {
             type master;
            file "/etc/namedb/db.wayne-jill.com";
		allow-transfer { 204.233.235.33; };
        };

---

### Post by terazen on 2010-05-19
Did you leave out the root hint on accident or is it not there?

```
        zone "." {
                type hint;
                file "/etc/namedb/db.root";
        };
```

I don't think that would cause your error though...

---

### Post by doas777 on 2010-05-19
you might want to test your config with:
```

named-checkzone <zone file path>

```

I'm not seeing an SOA block

---

### Post by wgregori on 2010-05-21
the named-checkzone does not work....

here's another issue I'm having that may have something to do with accessing my zone files.

No matter how I try to path to these files below I get file not found during Bind startup.   These are the directories, the permissions are set to 0777... any ideas why BIND can't find them?


include "/chroot/named/etc/named.conf.options";
include "/chroot/named/etc/named.conf.local";
include "/chroot/named/etc/named.conf.default-zones";

Thanks,
Wayne

---

### Post by doas777 on 2010-05-21
well, the chroot in that path gives me a few clues as to what is going wrong, though I have no idea what to do about it.

---

### Post by wgregori on 2010-05-21
Okay... this is a Linux problem rather than BIND at this point.

my bind config file has a number of includes that just are failing

include "/chroot/named/etc/named.conf.options";


Syslog:
May 21 17:46:52 ubuntuMaster named[21268]: loading configuration from '/etc/named.conf'
May 21 17:46:52 ubuntuMaster named[21268]: /etc/named.conf:4: open: named.conf.options: file not found
May 21 17:46:52 ubuntuMaster named[21268]: loading configuration: file not found
May 21 17:46:52 ubuntuMaster named[21268]: exiting (due to fatal error)


But the file is there:
root@ubuntuMaster:/chroot/named/etc# ls
namedb  named.conf  named.conf.local  named.conf.options


Any insight would be great.

Thanks,
Wayne

---

### Post by terazen on 2010-05-22
Do you have an /etc/named.conf and a /chroot/named/etc/named.conf?  You could maybe put all your files in the same directory and start named with the -t option in addition to your current options.

---

