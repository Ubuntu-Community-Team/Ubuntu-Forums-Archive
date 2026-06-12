---
title: "Trying to use unbound for DNSSEC, end up with ISP's DNS server"
date: 2014-04-05
forum: Security
---

### Post by vajorie on 2014-04-05
I'm trying to properly set up DNSSEC via unbound but when I check my stuff at [https://www.dnsleaktest.com/](https://www.dnsleaktest.com/), it shows me using my ISP's DNS servers (which I do not want)... 

I tried adding this bit but then my DNS requests never get resolved (I don't want to use Google's DNS servers but there were no alternatives): 

```

local-zone: "localhost." static
local-data: "localhost. 10800 IN NS localhost."
local-data: "localhost. 10800 IN SOA localhost. nobody.invalid. 1 3600 1200 604800 10800"
local-data: "localhost. 10800 IN A 127.0.0.1"
local-zone: "127.in-addr.arpa." static
local-data: "127.in-addr.arpa. 10800 IN NS localhost."
local-data: "127.in-addr.arpa. 10800 IN SOA localhost. nobody.invalid. 2 3600 1200 604800 10800"
local-data: "1.0.0.127.in-addr.arpa. 10800 IN PTR localhost."

forward-zone:
  name: "."
  forward-addr: 8.8.8.8
  forward-addr: 8.8.4.4

```

Here's my configuration: 

```

server:	verbosity: 1	
interface: 127.0.0.1	
access-control: 127.0.0.1 allow	
username: "unbound"	
use-syslog: yes 	
log-time-ascii: yes		
root-hints: "/etc/unbound/named.cache"	
hide-identity: yes	
hide-version: yes	
harden-short-bufsize: yes	
harden-large-queries: yes	
harden-glue: yes	
harden-dnssec-stripped: yes	
harden-below-nxdomain: yes	
module-config: "validator iterator"	
auto-trust-anchor-file: "/etc/unbound/root.key"	
control-enable: no

```

---

