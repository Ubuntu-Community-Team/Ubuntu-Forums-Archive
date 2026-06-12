---
title: "OSSEC detecting WEIRD IP address"
date: 2013-02-05
forum: Security
---

### Post by Stonecold1995 on 2013-02-05
```
**2013 Feb 04 21:16:37** Rule Id: **1002** level: 2
**Location:** kubuntu->ossec-keepalive 
**Src IP:** : Ze@rIdr2kFxJ3ZK/EfQ2L66FATalB62[sHl0K*!UqbM)0-z/,^0+.A8#Br=2=TeXIqrBb]Dr,^Teo(QkkkNV;3B7_6*t7+&kfPLUKwuV-(5O$9GKeV$tGa[wze^%.(78gV%B,Q-A&e^fvp.aZt]DSN1%'NP1bT=&.+oxn6gs]!39.IrejmIjid=P/+k?IP^F(.k?m55hJCysz&7x5z!hwT[i?SVlru6iX?K^.*ZhZd%H).max=VbKPY=QnQ7IryN48w19tTyuMwgs1*Qj$1Q'PgjlDPRi8/?9va10U68NP^oZi4q-zoxwuHHfEGngEmyZ1'7pZKlX7z4(D#O_]-TtDrKh(.Lcg(TWUPt@8#eKs%@eUt;.j'r[k1PKg[Mn#?
**Unknown problem somewhere in the system.**
** Alert 1360041661.120034: - web,accesslog,
2013 Feb 04 21:21:01 kubuntu->/var/log/apache2/access.log
Rule: 31101 (level 5) -> 'Web server 400 error code.'
Src IP: 127.0.0.1
127.0.0.1 - - [04/Feb/2013:21:21:00 -0800] "GET /announce?peer_id=[removed]&port=6881&uploaded=0&downloaded=0&left=7864320&compact=1&numwant=200&key=[removed]&event=started&info_hash=[removed] HTTP/1.1" 404 489 "-" "KTorrent/4.3.0"
```

I'm not sure what this is, but this appeared in OSSEC's web interface.  I cut off random parts of it in case it has any sensitive information.  But why is the source IP a bunch of seemingly random symbols?

Also, in general OSSEC seems to be getting a LOT of errors, like many lines "Web server 400 error", etc, and Apache saying "common web attack" but from localhost.

Does anyone else here using OSSEC have this problems?

---

### Post by cprofitt on 2013-02-05
well,...

127.0.0.1 is the server itself. That IP address is used by every server as 'localhost'.

You may want to whitelist that IP address.

edit your configuration file - /var/ossec/etc/ossec.conf

> <global>
  <white_list>127.0.0.1</white_list>
  <white_list>^localhost.localdomain$</white_list>
  <white_list>8.8.8.8</white_list>
  <white_list>192.168.1.254</white_list>
</global>

I hope this helps.

---

### Post by Stonecold1995 on 2013-02-06
> **cprofitt said:**
> well,...

127.0.0.1 is the server itself. That IP address is used by every server as 'localhost'.

You may want to whitelist that IP address.

edit your configuration file - /var/ossec/etc/ossec.conf



I hope this helps.
Yes yes I know that.  But the IP was showing up as "Ze@rIdr2kFxJ3ZK/EfQ2L66FATalB62[sHl0K*!UqbM)0-z/,^0+.A8#Br=2=Te..." etc.

---

### Post by SeijiSensei on 2013-02-06
I've never used this software so ignore me if this doesn't make sense, but is it configured to handled IPv6 addresses?  Perhaps the interface is announcing itself with its [IPv6 address]("http://www.tldp.org/HOWTO/Linux+IPv6-HOWTO/x476.html"), and the software doesn't know how to deal with that as currently configured?

---

### Post by ddpbsd on 2013-02-07
You're using an old and known bad version of the WUI. The alert format changed with OSSEC 2.6, and since the WUI is technically a dead project, it wasn't officially updated.

Some users were awesome and provided patches. We've started collecting them in a repository on bitbucket. Download the new source here: [https://bitbucket.org/jbcheng/ossec-wui](https://bitbucket.org/jbcheng/ossec-wui)

---

### Post by Stonecold1995 on 2013-02-08
> **ddpbsd said:**
> You're using an old and known bad version of the WUI. The alert format changed with OSSEC 2.6, and since the WUI is technically a dead project, it wasn't officially updated.

Some users were awesome and provided patches. We've started collecting them in a repository on bitbucket. Download the new source here: [https://bitbucket.org/jbcheng/ossec-wui](https://bitbucket.org/jbcheng/ossec-wui)
Will this get rid of all the 400 server errors and the weird IPs?

---

### Post by Stonecold1995 on 2013-02-08
Upgrading to 3.0+ hasn't solved the web server 400 errors, but I haven't seen that weird IP address so far.

But all the 400 errors are making it nearly unusable anyways.  Even though the screenshot only captured the top of the page, the entire page was 400 errors that seemed to have been caused by KTorrent (which I don't understand because KTorrent doesn't use Apache...).  Is there a way to either fix whatever is causing the errors or at least to hide them so I don't get hundreds of irrelevant warnings per day?

[[IMG]http://www.pictureshack.us/thumbs/57003_ossec.png[/IMG]](http://www.pictureshack.us/images/57003_ossec.png)

---

