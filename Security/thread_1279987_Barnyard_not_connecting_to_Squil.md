---
title: "Barnyard not connecting to Squil"
date: 2009-10-01
forum: Security
---

### Post by Spontan on 2009-10-01
I am running:
kernel 2.6.28-15-generic

I have installed Barnyard 2.1.6 to run the Database for Snort 2.8
On top of that, I am trying to run Squil .7 . 

Whenever I am connection to Squil with Barnyard I am seeing the following from Barnyard:

Initializing rule chains...
Found reference-map config directive (/etc/snort/reference.config)
Found class-map config directive (/etc/snort/classification.config)
Found gen-msg-map config directive (/etc/snort/gen-msg.map)
Found sid-msg-map config directive (/etc/snort/sid-msg.map)
Found hostname config directive (XXxxXX)
Found interface config directive (eth1)
Generating maps
Using waldo file '/var/log/snort/barnyard.waldo':
    spool directory = /var/log/snort
    spool filebase  = snort.log
    time_stamp      = 1254344348
    record_idx      = 86
sguil:  sensor name = Barnyard
sguil:  agent port =  7736
sguil:  Connected to localhost on 7736.
ERROR: sguil: Expected SidCidResponse and got 'SGUIL-0.7.0 OPENSSL ENABLED'
Fatal Error, Quitting..

On the other end, Sguil is saying:
pid(23116)  Sensor agent connect from 127.0.0.1:39636 sock13
pid(23116)  Validating sensor access: 127.0.0.1 : 
pid(23116)  Valid sensor agent: 127.0.0.1
pid(23116)  Sensor Data Rcvd: SidCidRequest Barnyard
pid(23116)  Ignoring cmd from unregistered agent: SidCidRequest Barnyard
pid(23116)  Sensor Data Rcvd: 
pid(23116)  Ignoring cmd from unregistered agent: 
pid(23116)  Socket sock13 closed


I've done quite a bit of googling about this issue but have not been able to determine anything so far. If anyone could help, I would appreciate it.

---

### Post by srslynrdy on 2010-10-26
did you find a solution??
im having this problem too

---

