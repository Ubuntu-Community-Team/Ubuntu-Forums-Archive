---
title: "VMware Server 2 error - Web service not available"
date: 2008-10-13
forum: Virtualisation
---

### Post by ZebCarnell on 2008-10-13
Hi Guys,
When I'm logging into VMware Server 2 web interface on Hardy I get "Web service not available."

I have got IPv6 disabled:

/etc/modprobe.d/aliases 
```
alias net-pf-10 off
```


/etc/hosts - 
```

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
```


When I run "sudo /etc/init.d/vmware restart" I get:
```
Starting VMware services:
   Virtual machine monitor                                            done
   Virtual machine communication interface                            done
   VM communication interface socket family:                          done
   Virtual ethernet                                                   done
   Bridged networking on /dev/vmnet0                                  done
   Host-only networking on /dev/vmnet1 (background)                   done
   DHCP server on /dev/vmnet1                                         done
   Host-only networking on /dev/vmnet8 (background)                   done
   DHCP server on /dev/vmnet8                                         done
   NAT service on /dev/vmnet8                                         done
   VMware Server Authentication Daemon (background)                   done
   Shared Memory Available                                            done
Starting VMware management services:
   VMware Server Host Agent (background)                              done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                                   done


```

Can anyone give me a hand with this one?

Cheers,
Zeb

---

### Post by ZebCarnell on 2008-10-20
Bump

---

### Post by KayEss on 2008-10-21
I get the same error and haven't worked out what to do about it yet.

---

### Post by ZebCarnell on 2008-10-26
Anyone else come across this issue and resolved it?

---

### Post by colinlr on 2008-10-28
VMware Virtual Infrastructure Web Access doesn't seem to have started up, I had a similar problem and used

/etc/rc.d/init.d/vmware-mgmt restart

and all worked fine

---

### Post by dmizer on 2008-10-29
Same problem here.

> **colinlr said:**
> VMware Virtual Infrastructure Web Access doesn't seem to have started up, I had a similar problem and used

/etc/rc.d/init.d/vmware-mgmt restart

and all worked fine

For Ubuntu, the command is /etc/init.d/vmware-mgmt restart

However, even that did not fix this issue for me. I am still unable to access the web interface either locally or remotely.

---

### Post by leopoldog on 2008-10-29
Hi, I've the same problem.

On my Core 2 Duo the VMWare 2.0.0 Build 116487 works correctly, on the old Pentium 4 I receive the "Web service not available" error.

I've installed the Ubuntu Hardy (last patches) on both machines.

I've tried disabling the IPv6 on the Pentium but I've the same error. Note that on the Core 2 Duo the IPv6 is activated!

On the hostd.log I have this error:
[2008-10-29 17:03:10.334 'Proxysvc' 3074156880 warning] SSL Handshake on client connection failed: SSL Exception: 
[2008-10-29 17:03:42.846 'Proxysvc Req00011' 3074156880 warning] PendingServerStrm: client write-completion error: SSL Exception: error:00000001:lib(0):func(0):reason(1)

But I don't known if this error and the "Web access not available" are related.

---

### Post by ask4jm on 2008-10-30
have u tried

[http://localhost:8222](http://localhost:8222)
or
[https://localhost:8333](https://localhost:8333)

thanks

---

### Post by leopoldog on 2008-10-30
> **ask4jm said:**
> have u tried

[http://localhost:8222](http://localhost:8222)
or
[https://localhost:8333](https://localhost:8333)

thanks

I don't know what have made the others but I've tried to connect with 127.0.0.1, localhost and the machine name and I've tried also with the LAN address but the answer was the same (on the Core 2 Duo all works).

Now I've downgraded the version to the 1.0.7 because I need a working VMware and I can't wait more time. But I can try on a pentium 4 at home to see if I have the same problems.

---

### Post by qlinux on 2009-01-13
It is possible that your system has received a kernel upgrade and vmware has to be reconfigured...

try running this..  

sudo /usr/bin/vmware-config.pl 

answer all the config questions (I leave all the default answers that are in the [square] brackets) and you should be good.

Hope this helps.

Q!

---

### Post by Elf-king on 2009-02-23
OK, while I am not running Ubuntu, I ran into a similar issue and as it turned out for me the problem was in the vmware-watchdog script; it was looking for setsid tool which I didn't have on my system so it kept on dying. Installing util-linux-ng helped.

Now this shouldn't really be a problem on most ubuntu systems but, a way to trace YOUR problem may be to remove the redirection to /dev/null from /etc/init.d/vmware-mgmt script around line 905 ... 

Specifically the line that says:

```

  $watchdog -s webAccess -u 30 -q 5 "$webAccess $webAccessOpts start" > /dev/null 2>&1 &

```

Should be replaced by 

```

  $watchdog -s webAccess -u 30 -q 5 "$webAccess $webAccessOpts start" > /tmp/webaccess.log 2>&1 &

```

You can then examine /tmp/webaccess.log to see what's actually going on

Hope this helps.

EK

---

### Post by Corsari on 2010-05-25
Happen to me too.

Tried to re-run vmware-config.pl , no way.

The log output of the watchdog, returns a huge 100Kb file with some java warnings and errors.

Any tip?

Thank you

R.

---

### Post by sbehnam73 on 2010-07-28
Hi all,

I had several issues with the VMWare Web UI and serveral browsers.
Most of the issues are caused by the browser settings.

For Firefox this fixed the problem for me:
Edit --> Preferences --> Privacy (Use custom settings for history) --> check Clear_history when Firefox closes.

For (German) IE the solution is:
Extras --> Internetoptionen --> Sicherheit --> Vertrauenswürdige Sites --> Sites ( add there the URL to the VMWare server just like [https://blabla](https://blabla).

Thats it :)

before I could see the following errors in "/var/log/vmware/hostd.log"
########################################################
endingServerStrm: client write-completion error: SSL Exception: error:00000001:lib(0):func(0):reason(1)
Exception while processing request: SSL Exception: error:00000001:lib(0):func(0):reason(1)
An error occurred reading the SOAP request: The HTTP client closed the stream prematurely.
......
########################################################

Hope this helps

Saman

The VMWare Console Plug-in is incompatible with Firefox 3.6 :(.
VMWare is some times a p... in the a...
I personally use KVM for production use and I am very happy with it.

---

### Post by speculatrix on 2010-09-09
> **leopoldog said:**
> 
On the hostd.log I have this error:
[2008-10-29 17:03:10.334 'Proxysvc' 3074156880 warning] SSL Handshake on client connection failed: SSL Exception: 
[2008-10-29 17:03:42.846 'Proxysvc Req00011' 3074156880 warning] PendingServerStrm: client write-completion error: SSL Exception: error:00000001:lib(0):func(0):reason(1)

But I don't known if this error and the "Web access not available" are related.

enable sslv2: [http://planetvm.net/blog/?p=1087](http://planetvm.net/blog/?p=1087)

---

### Post by curioshop on 2010-10-01
enable ssl v2 in firefox's about:config page.

---

### Post by sw34963 on 2011-01-05
> **curioshop said:**
> enable ssl v2 in firefox's about:config page.

:p This is the only thing that worked for me,  thanks Curioshop!

I spent ages looking through logs etc and reinstalling and it was mearly a setting in FF.!!  Thanks

---

### Post by EngineerBill on 2011-08-23
Same problem with Firefox version 6. Typed about:config in the address bar and found security.enable_ssl2, set it to true and the problem was solved! Thanks!

---

