---
title: "Dns server problem"
date: 2013-02-23
forum: Server Platforms
---

### Post by stand123 on 2013-02-23
:D:(:)Dear All,

I configured dns server on ubuntu desktop. and its working on 
public IPs properly but can work with nating (private )address
and give me the following error
C:\Users\SAMSUNG>nslookup
Default Server:  ns1.stantelecom.com
Address:  27.116.56.161

> cnn.com
Server:  ns1.stantelecom.com
Address:  27.116.56.161

*** ns1.stantelecom.com can't find cnn.com: Query refused
>

---

### Post by mapes12 on 2013-02-23
Can you explain what you are trying to achieve, that is why do you need the DNS service on your Desktop?

---

### Post by stand123 on 2013-02-24
hello

I working in ISP and i want configure my own DNS. I configure it and its working fine while using pulic IP,s.When i give a public ip 
to a router and nat them and give my own dns it cannot works and give the above error.

---

### Post by Doug S on 2013-02-24
It is difficult to know what your problem is, as we still have limited information.
I was sort of expecting a local address to be shown for your nslookup command. Example:```
C:\Users\Doug>nslookup
Default Server:  ns1.smythies.com
Address:  [COLOR=red]192.168.111.1[/COLOR]
> cnn.com
Server:  ns1.smythies.com
Address:  [COLOR=red]192.168.111.1[/COLOR]
Non-authoritative answer:
Name:    cnn.com
Addresses:  157.166.226.26
          157.166.255.18
          157.166.255.19
          157.166.226.25
> exit
C:\Users\Doug>
```Also, I get 75.125.2.90 for ns1.stantelecom.com. Example:> doug@s15:~$ [COLOR=red]nslookup ns1.stantelecom.com[/COLOR]
Server: 192.168.111.1
Address: 192.168.111.1#53
Non-authoritative answer:
Name: ns1.stantelecom.com
Address: [COLOR=red]75.125.2.90[/COLOR]

---

### Post by stand123 on 2013-02-24
27.116.56.161 is my DNS server Ip you can this to your router while in nating mode it cannot work.

---

### Post by stand123 on 2013-04-06
hello


I have configured DNS server on Ubuntu Desktop. I have Public IPs and i make some subnetting in this . My DNS server IP is 27.116.56.161 which is from the subnet of 27.116.56.128/25 and it working fine on that all IPs but
not working on my other subnets like 27.116.56.0/25-----27.116.58.0/25------27.116.58.128/25


kindly help me i shall be very thankfull to you for this act of kindnesss


Muhammad kazim

---

### Post by darkod on 2013-04-06
It is really confusing what you are trying to do. You say the DNS server works fine and the machine has an assigned IP of 27.116.56.161, right?

So, what's the problem? If you have the server set up and it's working, what do those other ranges have to do with it?

Besides ranges like 27.116.56.0/25 and 27.116.58.0/25 don't look correct to me. Did your provider gave them to you or you just "made them up"? You can't make IP ranges up, not for public IPs. When using the /25 mask you usually don't have IPs ending in .0 but in .128 like the other two you posted.

Are you trying to use your server as DNS? On the machines that you want to use that DNS simply configure the 27.116.56.161 as DNS server and that should be it.

---

### Post by Doug S on 2013-04-06
Yes, I am also confused as to what you are trying to do.
I tried your name server, and I suspect you have recursion issues for your clients. Please post your entire named.conf.options file. In particular, I am wondering what your file has for the two lines similar to:```
        recursion yes;
        allow-recursion {any;};
```If you are not using "any" does your list match the sub-nets you mentioned? While I mentioned two particular lines, please post the entire file, as the scope of what we need might well be larger.

---

### Post by stand123 on 2013-04-09
hello
this is my [COLOR=#000000] named.conf.options configuration
[/COLOR]he/bind";


        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)


        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.


        // forwarders {
        //0.0.0;
        // };


        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
        forwarders {
                208.67.222.222;
                               [ Read 24 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit[0;10;7m^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by Doug S on 2013-04-09
Well, your posting of your named.conf.options file is incomplete, so it is hard to know for sure what is acutally in it. But it seems it might not have the lines I was referring to, so add them.
For reference here is my named.conf.options file:```
options {
        directory "/var/cache/bind";
        [COLOR=#ff0000]recursion yes;
        allow-recursion {any;};[/COLOR]
        allow-query {any;}; // this is needed to override the default
        allow-transfer {"none"; }; // transfer will be allowed per zone below.
        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113
        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.
//      forwarders {
//              75.153.176.9;
//              75.153.176.1;
//      };
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { none; };
};

```

---

