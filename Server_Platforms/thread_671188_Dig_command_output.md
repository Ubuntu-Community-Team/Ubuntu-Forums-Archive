---
title: "Dig command output"
date: 2008-01-18
forum: Server Platforms
---

### Post by sujathab on 2008-01-18
Hi all,

i am newbie to dns bind . Any help is very appreciated.

I am using dig command to view the records in the config. I am expecting the following comamnds to display all the A (Address records) in the zone data file. 
my zone data file looks like this
-------------------
$ORIGIN .
$TTL 86400      ; 1 day
example.com.            IN SOA  ns1.example.com. hostmaster.example.com. (
                                2008011801 ; serial
                                43200      ; refresh (12 hours)
                                900        ; retry (15 minutes)
                                1814400    ; expire (3 weeks)
                                10800      ; minimum (3 hours)
                                )

                        NS      ns1.example.com.
                        NS      hostmaster.example.com.
                        MX      10 mail.example.com.
ns1                     IN      A       10.2.125.68
hostmaster              IN      A       10.2.125.64
mail                    IN      A       10.2.125.69


When i execute dig example.com , i get the following output, not all a records are displayed..why is that any idea?
-------------------------------------------------------------------
; <<>> DiG 9.3.3rc2 <<>> example.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33402
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;example.com.                   IN      A

;; ANSWER SECTION:
example.com.            73070   IN      A       208.77.188.166

;; Query time: 0 msec
;; SERVER: 10.2.127.1#53(10.2.127.1)
;; WHEN: Fri Jan 18 14:40:15 2008
;; MSG SIZE  rcvd: 45
----------------------------------------------------------------------

---

### Post by MJN on 2008-01-18
Dig, without any arguments other than the domain, will simply request the A record(s) for the given name. Hence, it will not request other records such as NS, MX etc.

To get all the records you need to do one of the following:

i) Request each record individually, i.e. **dig example.com A**  ,  **dig example.com MX  **,  **dig example.com NS**  etc - this requires you to know the record types available.

or ii), Request a zone transfer giving you every record in the domain - **dig @server example.com axfr** - note you need to specify the nameserver to use (so, run **dig example.com NS** first) and even then the nameserver will likely not allow such a request (for privacy/security reasons).

The bottom line is that unless you run the nameserver there is usually no guaranteed way of getting all of its resource records. However, given that in this case you do then you're okay - but dig is not really the tool for the job (depending on why you're wanting to know these records).

Does that help?

Mathew

---

