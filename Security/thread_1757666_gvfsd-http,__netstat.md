---
title: "gvfsd-http,  netstat"
date: 2011-05-13
forum: Security
---

### Post by mI13eo6PUn3CN0eP on 2011-05-13
Ubuntu 10.04.2  x64 w/ Gnome 

When I look at connections on netstat, with sudo netstat -anp | grep -e tcp -e udp, there is something interesting: 

tcp        1      0 10.0.0.45:44650         91.189.89.31:80         CLOSE_WAIT  
3176/gvfsd-http

 Gvfsd-http is habitually doing something and starting to make me uncomfortable. 

I've found that gvfsd is 'GNOME Virtual File System' from searching here and on Google; however, I don't understand why it is listening, trying to connect, or contacting 91.189.89.31 (Canonical Ltd).  While I understand it would be worse if it were connecting to RBN, I still want to know more about what it is doing. 

Has anyone had similar experiences or know if it's a problem?

---

### Post by earthgecko on 2011-05-25
Yip it is up to something...

Mine is at Level3, telefonica and Akamai.. Are you running an encrypted home directory?

All mine are in a CLOSE_WAIT state, but you are correct, what is it doing?

```

tcp        1      0 1.1.1.1:48030      198.78.205.126:80       CLOSE_WAIT  6987/gvfsd-http  off (0.00/0/0)
tcp        1      0 1.1.1.1:52635      195.57.152.42:80        CLOSE_WAIT  6987/gvfsd-http  off (0.00/0/0)
tcp        1      0 1.1.1.1:48070      198.78.211.126:80       CLOSE_WAIT  6987/gvfsd-http  off (0.00/0/0)
tcp        1      0 1.1.1.1:54550      195.57.152.49:80        CLOSE_WAIT  6987/gvfsd-http  off (0.00/0/0)
tcp        1      0 1.1.1.1:49832      195.57.152.49:80        CLOSE_WAIT  6987/gvfsd-http  off (0.00/0/0)
tcp        1      0 1.1.1.1:43270      195.57.152.42:80        CLOSE_WAIT  6987/gvfsd-http  off (0.00/0/0)
tcp        1      0 1.1.1.1:33512      195.57.152.49:80        CLOSE_WAIT  6987/gvfsd-http  off (0.00/0/0)
tcp        1      0 1.1.1.1:49281      195.57.152.49:80        CLOSE_WAIT  6987/gvfsd-http  off (0.00/0/0)

```


```
uname -a
Linux xxxxxx 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux

netstat -anop |grep -v unix | grep gvfsd-http | sed -e 's/replace\.my\.ip\.add/1\.1\.1\.1/g' > netstat.gvfsd-http.log

# Count connections
wc -l netstat.gvfsd-http.log
# 218 netstat.gvfsd-http.log

# Unique IPs
cat netstat.gvfsd-http.log | cut -d':' -f2-2 | sed -e 's/.* //g' | sort | uniq > netstat.gvfsd-http.unique.ips.log

cat netstat.gvfsd-http.log | cut -d':' -f2-2 | sed -e 's/.* //g' | sort | uniq
192.221.115.126
194.224.66.120
194.224.66.35
195.57.152.42
195.57.152.49
198.78.205.126
198.78.211.126
4.23.48.126

whois 192.221.115.126   # OrgName:        Level 3 Communications, Inc.
whois 194.224.66.120    # netname:        AKAMAI
nslookup 195.57.152.42  # 2.0.152.57.195.in-addr.arpa    name = 42.red-195-57-152.customer.static.ccgg.telefonica.net.
whois 198.78.205.126    # OrgName:        Level 3 Communications, Inc.

```

---

### Post by earthgecko on 2011-05-25
As per Debian forum - [http://forums.debian.net/viewtopic.php?f=30&t=60750](http://forums.debian.net/viewtopic.php?f=30&t=60750)

Maybe your Update Manager, but it is not mine as mine is set to not collect statistics.

---

### Post by earthgecko on 2011-05-25
or Rhythmbox getting album art...... hmmm

[http://ubuntuforums.org/showthread.php?t=1450889](http://ubuntuforums.org/showthread.php?t=1450889)

---

### Post by earthgecko on 2011-05-25
Not rhythmbox although it is a bit of a busy body connecting to:

```

nslookup 209.85.146.102
102.146.85.209.in-addr.arpa     name = bru01s01-in-f102.1e100.net.

nslookup 94.127.72.60
Non-authoritative answer:
60.72.127.94.in-addr.arpa       name = LB140.AMST.COTENDO.NET.

nslookup 91.189.89.218
Non-authoritative answer:
218.89.189.91.in-addr.arpa      name = one-ubuntu-com.calamansi.canonical.com.

```

Not firefox either, I think this may be a likely candidate with an encrypted home directory, but firefox-bin does not kick off the gvfsd-http process.  So what, will update if I find out....

---

### Post by earthgecko on 2011-05-25
Right, my gvfsd-http netstat mystery solved.

rhythmbox when the last.fm plugin is used, not certain why.  However it makes sense from the networks that gvfsd-http is connecting to.

It does not seem to be album art related with mine, seems specifically last.fm related.

I can also confirm that the gvfsd-http connections that rhythmbox initiates are not closed and remain in CLOSE_WAIT state (reported elsewhere - [http://ubuntuforums.org/showthread.php?t=1450889](http://ubuntuforums.org/showthread.php?t=1450889))

Also see [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/760344](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/760344)

---

### Post by smiliebg on 2011-08-30
A bit late - but may help someone;

I found same proccess, however I do run Apache server and Apache document root is located on mounted volume.

Therefore, Apache needs to get data from the mounted volume and probably starts this procces? Just a guess from my side :)

---

