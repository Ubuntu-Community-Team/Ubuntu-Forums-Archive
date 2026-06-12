---
title: "Bind 9 DNS Server not accepting DNS client queries"
date: 2011-02-13
forum: Server Platforms
---

### Post by ajn1963 on 2011-02-13
I am sorry to drop this question and tried to search for the simple answer.  However I just built a 10.10 server, installed webmin, vmware, and the server is working perfectly.

I configured my bind 9 server using the latest webmin, and on the server everything resolves perfectly to both the interenet and lan.   I have it set to 127.0.0.1, the server ip address is 10.1.50.25.  

However, it will not accept dns client queries in which they cannot resolve to the lan or internet.  I have the dhcp giving out the dns server 10.1.50.25.  NSLOOKUPS from the client show query refused.  

I know there has to be some setting or config that will allow clients to query but I am not able to locate it, and I am not totally knowledgeable of named.conf and been all through the webmin module and configuration settings.  

Any advice would be greatly appreciated. 

Thank you, AJ...

---

### Post by elico on 2011-02-13
webmin >bind dns server> Access Control Lists
add to the list of allowed 10.1.50.0/24

save and then apply configuration.

---

### Post by ajn1963 on 2011-02-13
I will do that shortly when I get to my lab.   And I will be sure to post a follow up. 

Thank you.

---

### Post by ajn1963 on 2011-02-13
Did not work.  I still get Query refused and no name resolution for my clients which are on 10.1.40.0 which I added to the acl and restarted bind.  

my named.conf looks is below.

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
logging {
    };
key rndc-key {
    algorithm hmac-md5;
    secret "IJKvSRLEEcxHG/FXmgz5lQ==";
    };
controls {
    };
trusted-keys {
    };

---

### Post by ajn1963 on 2011-02-13
I tried everything and I found that local network address can be resolved by dns clients querying the dns server, but they cannot resolve public internet access.

I played with the resolvers, forwarders and I get Query Refused by the dns clients exept the dns server.  

My DNS server is 10.1.50.25 and my client configured with that dns server is 10.1.40.26.  The server has internet access and I have itself configured as it's dns server.  It does resolve both internet and local network addresses.

---

### Post by ajn1963 on 2011-02-13
I got it working I had to add

        allow-recursion { any; };
        allow-recursion-on { any; };

To the options of named.conf.  

Everything works now. I have local and internet name resolution for all my clients.

---

### Post by elico on 2011-02-14
hoo now it's understanble adding the settings that i gave you would help cause your network setup is different.
your current settings will give anyone that has access to the server the option to make dns queries and you dont want it.
just change the acl that i gave you to
10.0.0.0/8
and it will make everything you need.

change your named.conf  to like the below and it should make it ok.

```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local
acl lan {
        127.0.0.0/8;
        10.0.0.0/8;
        };

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
logging {
    };
key rndc-key {
    algorithm hmac-md5;
    secret "IJKvSRLEEcxHG/FXmgz5lQ==";
    };
controls {
    };
trusted-keys {
    }; 	
```


also make sure you do use forwarders in the file **name.options** as in this code and just change the dns server to your ISP ones.

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




        forwarders {
                8.8.8.8;
                208.67.222.222;
                };
};
```

---

