---
title: "exim4 - Security perspective"
date: 2013-09-13
forum: Security
---

### Post by rollyah on 2013-09-13
Setting my box up as a gateway.
i have shorewall,snort on it.
my sole purpose of using exim4 is having all notifications to be sent to my external e-mail

with that in mind, is exim4 an over kill ? 
i'm acustomed to using sendEmail in my scripts, but not when it comes to server notifications

i've set exim4 as such:
/etc/exim4/update-exim4.conf.conf 
dc_eximconfig_configtype='internet'
dc_other_hostnames='`hostname`'
dc_local_interfaces='127.0.0.1'
dc_readhost=''
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost=''
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname=''
dc_mailname_in_oh='true'

Any security concerns in running such a service on a gateway ?

i came across this url: [http://www.cyberciti.biz/tips/linux-use-gmail-as-a-smarthost.html](http://www.cyberciti.biz/tips/linux-use-gmail-as-a-smarthost.html)
where it suggests to use ssmtp instead of exim (or any other service)

PS: if you have any other suggestion than using exim4 i'd appreciate a heads up

---

### Post by CharlesA on 2013-09-18
As long as you limit Exim to localhost connections only, you should be fine as far as external attacks go.

---

