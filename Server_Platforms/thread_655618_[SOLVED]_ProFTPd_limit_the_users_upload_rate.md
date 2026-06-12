---
title: "[SOLVED] ProFTPd limit the users upload rate"
date: 2008-01-01
forum: Server Platforms
---

### Post by trymbill on 2008-01-01
How can I limit a users upload rate on ProFTPd?  I've searched for 2 hours now and found a few good articles about this but none of them say "Do this, then that and voila, your done!" ... I really need a good, simple and easy to understand tutorial on how I can accomplish this.

Can some one tell me:
1. How I can install the mod_shape module in ProFTPd?
2. How I can configure my ProFTPd so that the user "user1" has 30 kbits in download?
3. How can I do this with a VirtualHost on ProFTPd?

Please, some one, be nice :)

---

### Post by HermanAB on 2008-01-01
Hmm, did you check the proftpd web site?  The documentation is very good: [http://www.proftpd.org/localsite/Userguide/linked/x950.html](http://www.proftpd.org/localsite/Userguide/linked/x950.html)

Cheers,

Herman

---

### Post by trymbill on 2008-01-02
Hah, that page doesn't make any sens to me :)  It's all one big mess of words that sometime get repeated 2 or 3 times.  What I gathered from this text is "These only work on a per session basis with no scope for limiting on a VirtualHost basis" which tells me that I can't use Bandwidth control on a VirtualHost.

I'm wondering if I can some how just setup the bandwidth control for this one user with some code in the proftpd.conf file?

So can some one tell me; How can I accomplish this?

Can someone send in his / hers config file where they have put bandwidth control "on" and got it to work?

---

### Post by trymbill on 2008-01-09
Can anyone shed a light on this subject?

---

### Post by trymbill on 2008-01-09
I tried adding this:

```
<Global>
RateReadBPS 10000
MaxClients 6
</Global>
```

... to the bottom of my proftpd.conf file but when I try to restart the server I get this error:

```
Fatal: unknown configuration directive 'RateReadBPS' on line 168 of '/etc/proftpd/proftpd.conf'
```

RateReadBPS is relying on the mod_xfer module so I thought I just had to install that to get it working but in the ProFTPd install document it says:

> Note that the following modules are included by default and need not be added explicitly: mod_auth, mod_core, mod_log, mod_ls, mod_site, mod_unixpw and **mod_xfer**.

So, I should have the mod_xfer module installed (even though I don't know for sure because I don't know how to check) and RateReadBPS should work but it's giving me error when I try to run ProFTPd.

I'm running ProFTPd in standalone version and am also using Webmin.

Can someone please help me with this?

---

### Post by trymbill on 2008-01-09
I got it working! :)

I miss understood some of the information I read about this.  It seems like RateReadBPS is old and not used in version 1.3 of ProFTPd but TransferRate is used in stead.  So I just changed my proftpd.conf file and put this at the end of it:

```
<Global>
TransferRate RETR 20:0
MaxClients 6
</Global>
```

So now, each client, has a limit of 20 kb/s in download.  Very nice! :)

---

