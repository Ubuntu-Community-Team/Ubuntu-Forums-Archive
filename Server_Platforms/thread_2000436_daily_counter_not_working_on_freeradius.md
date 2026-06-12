---
title: "daily counter not working on freeradius"
date: 2012-06-09
forum: Server Platforms
---

### Post by alieblice on 2012-06-09
Hi
problem : daily counter not working on freeradius
ihave squid connected to freeradius and 
i did this config on users file of freeradius
```
"alice" Cleartext-Password := "passme", Max-Daily-Session :="100"
        Reply-Message = "Hello, %{User-Name}"

``` and uncomment daily in accounting and authorize section of sites-enabled/default file  of freeradius and uncommented the daily in instantiate section of radiusd.conf  and added this to moduls/counter
```
counter daily {
        filename = ${db_dir}/db.daily
        key = User-Name
        count-attribute = Acct-Session-Time
        reset = daily
        counter-name = Daily-Session-Time
        check-name = Max-Daily-Session
        reply-name = Session-Timeout
        allowed-servicetype = Framed-User
        cache-size = 5000
        return-attribute = Session-Timeout
        }

```but after 100 second the user doesn't disconnect and noting wrote  in output of radius -X command

any help is really appreciated

---

