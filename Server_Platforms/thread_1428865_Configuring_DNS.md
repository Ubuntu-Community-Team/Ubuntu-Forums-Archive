---
title: "Configuring DNS"
date: 2010-03-13
forum: Server Platforms
---

### Post by t.choi on 2010-03-13
Hello

I have configure DNS by editing 

i)  /etc/bind/named.conf.local 

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone ¨example.com¨ {
type master;
file ¨etc/bind/example.zone¨;
};
zone ¨1.168.192.in-addr.arpa¨ {
type master;
file ¨/etc/bind/example.local¨;
};

and editing /etc/bind/example.zone
;
; BIND data file for local loopback interface
;
$TTL    604800
@    IN    SOA    example.com. root.example.com. (
                  2        ; Serial
             604800        ; Refresh
              86400        ; Retry
            2419200        ; Expire
             604800 )    ; Negative Cache TTL
;
@        IN    NS    example.com.
@        IN    A    192.168.1.3
@        IN    AAAA    ::1
example.com    IN    A    192.168.1.3

after then , I  restarted the DNS by
root@VUbuntu:~# invoke-rc.d bind9 restart

and got this error message:
 * Stopping domain name service... bind9                                       
 rndc: connect failed: 127.0.0.1#953: connection refused
                                                                         [fail]
 * Starting domain name service... bind9                                 [fail] 

Could Someone help on this , connection failed.


Thank you for helping

Thomas

---

### Post by joberly on 2010-03-13
Is named running and listening on port 953?

sudo netstat -punta | grep named

Chances are it is just a typo. named is very particular about the config files...make sure you don't have ANY extra lines at the end of all configuration files, and that all ;'s are correctly placed.

Running named -p -g 53 will run it in the foreground with errors output to stderr, and will help you diagnose problems.

---

### Post by RealPSL on 2010-03-13
rndc is failing to connect. There should be an rndc.conf file that will help. If not you should be able to generate one with rndc-confgen. Take a look at the man pages for rndc.conf. If that does not work post the file and someone will help you just leave out the secret key.

---

### Post by t.choi on 2010-03-14
> **joberly said:**
> Is named running and listening on port 953?

sudo netstat -punta | grep named

Chances are it is just a typo. named is very particular about the config files...make sure you don't have ANY extra lines at the end of all configuration files, and that all ;'s are correctly placed.

Running named -p -g 53 will run it in the foreground with errors output to stderr, and will help you diagnose problems.

hello joberly

I ran your command :sudo netstat -punta | grep named

nothing shown
 and if I ran sudo netstat -punta | grep 53
it shown
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      4176/dnsmasq    
tcp6       0      0 :::8009                 :::*                    LISTEN      4553/jsvc       
tcp6       0      0 :::8080                 :::*                    LISTEN      4553/jsvc       
udp        0      0 192.168.122.1:53        0.0.0.0:*                           4176/dnsmasq    
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           3837/avahi-daemon: 


I m not sure the problem as checked all edited files no extra lines and ; in right places

---

### Post by t.choi on 2010-03-14
> **RealPSL said:**
> rndc is failing to connect. There should be an rndc.conf file that will help. If not you should be able to generate one with rndc-confgen. Take a look at the man pages for rndc.conf. If that does not work post the file and someone will help you just leave out the secret key.


I can only found a rndc.key file in /etc/bind
which shown
root@VUbuntu:/etc/bind# cat rndc.key
key "rndc-key" {
    algorithm hmac-md5;
    secret "i5QkMFkDTiztiV5GOk+muw==";
};

I dont know should be check the rndc.conf 

Could any one help the DNS still can not make connection

Thank you

Thomas

---

### Post by joberly on 2010-03-14
> **joberly said:**
> 
Running named -p -g 53 will run it in the foreground with errors output to stderr, and will help you diagnose problems.

Run that and see what errors you get. That will help diagnose.

---

### Post by t.choi on 2010-03-15
> **joberly said:**
> Run that and see what errors you get. That will help diagnose.

joberly,

I running the below command and got :

thomas@VUbuntu:~$ named -p 53 -g
15-Mar-2010 20:57:38.467 starting BIND 9.5.0-P2.1 -p 53 -g
15-Mar-2010 20:57:38.468 found 1 CPU, using 1 worker thread
15-Mar-2010 20:57:38.474 loading configuration from '/etc/bind/named.conf'
15-Mar-2010 20:57:38.475 /etc/bind/named.conf.local:10: expected quoted string near '¨etc'
15-Mar-2010 20:57:38.502 loading configuration: unexpected token
15-Mar-2010 20:57:38.502 exiting (due to fatal error)


Thank you
Thomas

Thank you joberly, I solved it 

In the named.conf.local file &#347; content ¨used different ¨ which is not same as in the orginal. I don t know why my keyboard come out such format in ubuntu .

after changed the content and got below

thomas@VUbuntu:/etc/bind$ sudo named -g -p 53
15-Mar-2010 21:11:34.140 starting BIND 9.5.0-P2.1 -g -p 53
15-Mar-2010 21:11:34.141 found 1 CPU, using 1 worker thread
15-Mar-2010 21:11:34.155 loading configuration from '/etc/bind/named.conf'
15-Mar-2010 21:11:34.171 listening on IPv6 interfaces, port 53
15-Mar-2010 21:11:34.177 listening on IPv4 interface lo, 127.0.0.1#53
15-Mar-2010 21:11:34.179 listening on IPv4 interface eth1, 192.168.1.42#53
15-Mar-2010 21:11:34.182 listening on IPv4 interface vnet0, 192.168.122.1#53
15-Mar-2010 21:11:34.184 binding TCP socket: address in use
15-Mar-2010 21:11:34.198 default max-cache-size (33554432) applies
15-Mar-2010 21:11:34.208 automatic empty zone: 254.169.IN-ADDR.ARPA
15-Mar-2010 21:11:34.218 automatic empty zone: 2.0.192.IN-ADDR.ARPA
15-Mar-2010 21:11:34.220 automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
15-Mar-2010 21:11:34.220 automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
15-Mar-2010 21:11:34.220 automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
15-Mar-2010 21:11:34.220 automatic empty zone: D.F.IP6.ARPA
15-Mar-2010 21:11:34.221 automatic empty zone: 8.E.F.IP6.ARPA
15-Mar-2010 21:11:34.221 automatic empty zone: 9.E.F.IP6.ARPA
15-Mar-2010 21:11:34.221 automatic empty zone: A.E.F.IP6.ARPA
15-Mar-2010 21:11:34.221 automatic empty zone: B.E.F.IP6.ARPA
15-Mar-2010 21:11:34.224 default max-cache-size (33554432) applies: view _bind
15-Mar-2010 21:11:34.229 none:0: open: /etc/bind/rndc.key: permission denied
15-Mar-2010 21:11:34.239 couldn't add command channel 127.0.0.1#953: permission denied
15-Mar-2010 21:11:34.240 none:0: open: /etc/bind/rndc.key: permission denied
15-Mar-2010 21:11:34.240 couldn't add command channel ::1#953: permission denied
15-Mar-2010 21:11:34.240 ignoring config file logging statement due to -g option
15-Mar-2010 21:11:34.278 zone 0.in-addr.arpa/IN: loaded serial 1
15-Mar-2010 21:11:34.280 zone 127.in-addr.arpa/IN: loaded serial 1
15-Mar-2010 21:11:34.282 zone 255.in-addr.arpa/IN: loaded serial 1
15-Mar-2010 21:11:34.285 /etc/bind/example.local:14: example.com.\194\1681.168.192.in-addr.arpa\194\168: bad owner name (check-names)
15-Mar-2010 21:11:34.285 zone \194\1681.168.192.in-addr.arpa\194\168/IN: loading from master file /etc/bind/example.local failed: bad owner name (check-names)
15-Mar-2010 21:11:34.295 zone \194\168example.com\194\168/IN: loading from master file etc/bind/example.zone failed: file not found
15-Mar-2010 21:11:34.296 zone localhost/IN: loaded serial 2
15-Mar-2010 21:11:34.298 running
^C15-Mar-2010 21:11:52.676 shutting down
15-Mar-2010 21:11:52.677 no longer listening on ::#53
15-Mar-2010 21:11:52.677 no longer listening on 127.0.0.1#53
15-Mar-2010 21:11:52.677 no longer listening on 192.168.1.42#53
15-Mar-2010 21:11:52.677 no longer listening on 192.168.122.1#53
15-Mar-2010 21:11:52.716 exiting



BTW
the connection fail shown is 
rndc: connect failed: 127.0.0.1#953: connection refused

why I go to check the port 53 as named -g -p 53

Thank you

Thomas

---

### Post by debianfan on 2010-04-06
How did you get the RNDC permissions problem fixed, I am having the exact same issue?  Thanks.

---

### Post by t.choi on 2010-04-06
I did  not solve the RNDC  permissions problem.

I solved my problem by running the command as suggested by joberly:named -g -p 53

and then I found  my named.conf.local file format is not like usual it made the DNS do not run proprely

---

