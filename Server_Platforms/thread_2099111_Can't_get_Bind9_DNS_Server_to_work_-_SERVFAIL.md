---
title: "Can't get Bind9 DNS Server to work - SERVFAIL"
date: 2012-12-28
forum: Server Platforms
---

### Post by exabyssus on 2012-12-28
Hello, 
I'm trying to set up DNS server for several days, but can't get it to work.

So I have Ubuntu web server (95.100.5.115) where I host all my sites. 
For DNS server I made another virtual server (95.100.5.117) with Ubuntu 12.04 and installed Bind9 and disables Network manager.

Here are the files:
**/etc/bind/named.conf.local**
```

zone "agw.lv" {
        type master;
        file "/etc/bind/db.agw.lv";
};

zone "6.100.95.in-addr.arpa" {
     type master;
     file "/etc/bind/db.95";
};

```


**/etc/bind/db.agw.lv**
```

;
; BIND data file for example.com
;
$TTL    604800
@       IN      SOA     ns1.agw.lv. agw.agw.lv. (
                              8         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
        IN      A       95.100.5.115
;
@       IN      NS      ns1.agw.lv.
@       IN      A       95.100.5.115
@       IN      AAAA    ::1
ns1     IN      A       95.100.5.115

```


**/etc/bind/db.95**
```

;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns1.agw.lv. agw.agw.lv. (
                              8         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.
115     IN      PTR     ns1.agw.lv.

```

**/etc/network/interfaces**
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 95.100.5.117
netmask 255.255.255.240
network 95.100.5.112
broadcast 95.100.5.127
gateway 95.100.5.113
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 95.100.5.117
dns-search ns1.agw.lv

```


**/etc/resolv.conf**
```
nameserver 95.100.5.117
search ns1.agw.lv
```


When I try use dig or nslookup server returns SERVFAIL.

Can anyone see where is the problem?
Thank you!

---

### Post by ranger12 on 2012-12-28
Hello, my first question is the file named db.agw.lv or agw.lv.db? You have it one way in your named.conf.local file and the path to the file you posted has it the other way. I also noticed you still have "example.com" and "root.example.com" in your first file.

---

### Post by exabyssus on 2012-12-28
I recently started all over again and apparently made some errors. 
Ok, I changed name to db.agw.lv and changed that line with ns1.agw.lv. agw.agw.lv.

Thanks, server started to show some sign of hope :) But it still isn't working like I think it should.

When I try **nslookup ns1**
response is:
```
Server:         95.100.5.117
Address:        94.100.5.117#53

Name:   ns1.agw.lv
Address: 95.100.5.115
```

How do I point other sites to my web server?
Do I have to make zone for every site?

---

### Post by ranger12 on 2012-12-28
It looks like your dns server is working now. I believe the repsonse you got to your nslookup on your dns server is behaving correctly. Can you try doing a reverse lookup to see if that is working? You need to add a record in your zone files to be able to do name resolution for each one of your sites.  Pointing it to your web server is a different matter. Is this for a local lan like mine or is this something you want to make public to the Internet? Perhaps if you be a little more detailed about your setup and what you mean to do perhaps someone can be of more assistance.

---

### Post by exabyssus on 2012-12-28
I have server with Hyper-V on which are hosted virtual servers with Ubuntu 12.04, one development web server, one production server and DNS server. On another server virtual server for slave DNS. 

On web servers I use virtual hosts, and would like to add nameservers (ns1.agw.lv) to all my sites and get them to dev or prod servers. I've never used nameservers and have no idea how to set them up and where to add records.

For example I have site disco.lv, with ns records for ns1.agw.lv and ns2.agw.lv, what do I need to do on DNS server to send http request to production server?

---

### Post by ranger12 on 2012-12-28
Do you mean you want your production server to be able to resolve fqdn names to ip addresses? If that is what you mean, than your production server needs to have the ip addrress of your dns server so it knows where to go to resolve names. Maybe I am misunderstanding which machines you want to do what.

---

### Post by exabyssus on 2012-12-28
No, I believe it would be more convenient to do that on DNS server.

I just don't know how to add sites to DNS server correctly and couldn't find any good examples.

I tried adding site in **/etc/bind/db.agw.lv**
```
disko.lv     IN      A       95.100.5.115
```

but server returns NXDOMAIN.

---

### Post by tenmoi on 2012-12-28
> **exabyssus said:**
> No, I believe it would be more convenient to do that on DNS server.

I just don't know how to add sites to DNS server correctly and couldn't find any good examples.

I tried adding site in **/etc/bind/db.agw.lv**
```
disko.lv     IN      A       95.100.5.115
```

but server returns NXDOMAIN.

You forgot the dot (.) right behind disko.lv so it resolves to disko.lv.awg.lv, which doesn't exist anyware. Hence NXDOMAIN.

cheers,

---

### Post by ranger12 on 2012-12-29
Well I think after looking at my last post I misspoke. I didn't mean that your production server do the name resolution but that your production server needs to have the ip address of your dns server so that your production server can use the dns server.

Just for kicks add this to your db.agw.lv file:

[www]("http://www.disko.lv")        IN         A            95.100.5.115

and than add this to your db.95 file:
115          IN         PTR        [www.disko.lv]("http://www.disko.lv").

rrestart bind and than do a nslookup on [www.disko.lv]("http://www.disko.lv") and see what happens.
This is the manner I have my zone files set up and it works no problem. Don't forget to incresase the Serial number in both files when you do this. You might, if you have not already, try here:
[https://help.ubuntu.com/community/BIND9ServerHowto#DNS_Record_Types](https://help.ubuntu.com/community/BIND9ServerHowto#DNS_Record_Types)

---

### Post by exabyssus on 2012-12-29
It seems that now my configs are correct, but something still isn't working correctly. Now when I write **nslookup ns1** or **nslookup disko.lv** server responds with [COLOR="Red"]NXDOMAIN[/COLOR]

And I find those in log. 
Dec 29 18:00:03 ns1 named[924]: /etc/bind/db.agw.lv:17: ignoring out-of-zone data (disko.lv)
Dec 29 18:00:03 ns1 named[924]: /etc/bind/db.agw.lv:18: ignoring out-of-zone data ([www.disko.lv](www.disko.lv))

What else could cause NXDOMAIN?

---

### Post by ranger12 on 2012-12-29
Maybe if you post your db.agw.lv and db.95 files again and let's see what you have in there just to be sure.
Actually, I think although I could be wrong, if that is a different domain name pointing to a different site I beileve you have to set up another zone definition for that. Try changing the reocrd in your db.95 to:

115           IN        PTR            [www.agw.lv]("http://www.agw.lv").

Restart bind and than try nslookup. I also noticed you have in your interfaces file for your dns-nameservers the ip address is 95.100.5.117 but you have it defined in your zone files as 95.100.5.117. You might want to look at this thread as well: [http://ubuntuforums.org/showthread.php?t=1271929](http://ubuntuforums.org/showthread.php?t=1271929)

---

### Post by exabyssus on 2012-12-30
Ok, everything works fine. It just seems quit complicated that for each domain I have to add record in named.conf.local on both servers and create zone file. 
**Anyway, it works, thank you very much! Happy new year!**

---

### Post by ranger12 on 2012-12-30
Great! I am glad you got it working. Happy New Year.

---

