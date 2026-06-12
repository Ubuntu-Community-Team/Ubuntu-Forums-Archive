---
title: "I messed up a DHCP.CONF file :("
date: 2008-06-02
forum: Server Platforms
---

### Post by w1z4rd on 2008-06-02
> #Label Printer
                host AP-1 {
                        hardware ethernet 00:00:00:00:00:00;
                        fixed-address 192.168.0.100;
                        }

#deborah
               host deborah-1 {
                        hardware ethernet 00:00:00:00:00:00;
                        fixed-address 192.168.0.65;
                       }


                {ignore unknown-clients;
                }
                   #end of file


I was updating a dhcp.conf file and was using putty. Used the numpad and a couple of things messed out. I added the deborag person, and now dhcp wont start.

I think I broke the last 3 lines... can anyone help me? :(

---

### Post by beniwtv on 2008-06-03
AFAIK, it should be:

```
ignore unknown-clients;
``` 

not

```
{ignore unknown-clients;
}
```

Additionally, you may also have to put this on the top of the file, along with other defines.

See here for an example file:
[http://forge.cnaf.infn.it/plugins/scmcvs/cvsweb.php/ig-installserver/dhcpd.conf.example?rev=1.2;content-type=text%2Fplain;cvsroot=igrelease;sortby=log;f=h](http://forge.cnaf.infn.it/plugins/scmcvs/cvsweb.php/ig-installserver/dhcpd.conf.example?rev=1.2;content-type=text%2Fplain;cvsroot=igrelease;sortby=log;f=h)

Cheers,

---

