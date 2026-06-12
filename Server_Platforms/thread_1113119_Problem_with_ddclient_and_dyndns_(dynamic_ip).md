---
title: "Problem with ddclient and dyndns (dynamic ip)"
date: 2009-04-01
forum: Server Platforms
---

### Post by mobbbx on 2009-04-01
Hi,

My ddclient does not seem to be notifying dyndns.com of my ip change. 

My configuration for /etc/default/ddclient:
run_ipup="false"
run_daemon="true"
daemon_interval="300"

Configuration for /etc/ddclient.conf 
pid=/var/run/ddclient.pid
protocol=dyndns2
use=web, web=checkip.dyndns.org/, web-skip'=IP Address'
server=members.dyndns.org
login=login
password='password'
yogiaman.blogsite.org
ssl=yes
daemon=300
syslog=yes

I have checked alot of forums and it seems that my ddclient configurations are correct. However, when my ip changes, ddclient fails to notify dyndns.com of the ip change. i checked the host ip through [https://www.dyndns.com/account/services/hosts/](https://www.dyndns.com/account/services/hosts/)

Please help!

thanks!

---

### Post by BkkBonanza on 2009-04-01
Try to run ddclient directly on the console in debug mode. It should give you more info,

ddclient -daemon=0 -noquiet -debug

You could post output here if it makes no sense.

---

### Post by cdenley on 2009-04-01
Do you have the domain configured with 60 second TTL or 4 hour TTL. If it is the latter, then it can take up to 4 hours for any IP changes to take effect.

EDIT:
Nevermind. I just checked, and you seem to have a 60 second TTL. Did you allow 60 seconds for the DNS changes?

---

### Post by mobbbx on 2009-04-02
Hi BkkBonaza,

I tried to debug ddclient as per your advice and this is what i got:

sudo ddclient -daemon=0 -noquiet -debug 
DEBUG:    get_ip: using ip, ip reports <undefined>
WARNING:  unable to determine IP address

So apparently, ddclient is unable to retrieve my IP address. How can i solve it? i use a 2Wire ADSL router (2701HGV-E) to connect to internet. My server connects to the internet through the 2Wire router. 

thanks!

---

### Post by mobbbx on 2009-04-02
Hi cdenley,

thanks for your reply. I'm fairly new to linux and ubuntu so can you explain your question in layman's terms? 

60 seconds TTL?
And how can i check to see whether i have allowed 60 seconds for DNS changes?

thanks!

---

### Post by bluefrog on 2009-04-02
If your router has no way to send the info itself to dyndns (did you check that?), you certainly have an interface to configure your router. In that case your WAN IP is visible somewhere in that interface. then use that page to configure ddclient instead of using web.dyndns

When I used it my config was:

pid=/var/run/ddclient.pid
protocol=dyndns2
fw-login=router-user, fw-password=router-user-pwd
use=fw, fw=192.168.0.1/info.html, fw-skip='ppp_8_35_1'
server=members.dyndns.org
login=dyndns-login
password='dyndns-pwd'
mydomain.dyndns.org

NOTE
use=fw, fw=192.168.0.1/info.html, fw-skip='ppp_8_35_1'
is the page where you can see your WAN IP. will certainly not be the same for you. fw-skip is the field right before your IP

---

### Post by cdenley on 2009-04-02
> **bluefrog said:**
> If your router has no way to send the info itself to dyndns (did you check that?), you certainly have an interface to configure your router. In that case your WAN IP is visible somewhere in that interface. then use that page to configure ddclient instead of using web.dyndns

When I used it my config was:

pid=/var/run/ddclient.pid
protocol=dyndns2
fw-login=router-user, fw-password=router-user-pwd
use=fw, fw=192.168.0.1/info.html, fw-skip='ppp_8_35_1'
server=members.dyndns.org
login=dyndns-login
password='dyndns-pwd'
mydomain.dyndns.org

NOTE
use=fw, fw=192.168.0.1/info.html, fw-skip='ppp_8_35_1'
is the page where you can see your WAN IP. will certainly not be the same for you. fw-skip is the field right before your IP

The line
```

use=web, web=checkip.dyndns.org/, web-skip'=IP Address'

```
definitely works. I just used that to configure my server.

---

### Post by BkkBonanza on 2009-04-02
When you ran debug mode you have to let it run for long enough to attempt an update?

Keep in mind that every packet leaving your router has your ip in it. Otherwise no site in the world could ever get data back to you. When ddclient accesses checkip.dyndns.org it is trivial for dyndns to return to you the ip. It is impossible it doesn't have it. However, there may be some reason that ddcleint is not able to get to dyndns.org. 

I would have expected to see much more info from the debug output. Since the -daemon=0 option is set, ddclient will stay in the foreground and run until you stop it, but it should output info as it tries to update. I expect it would do that right away but I'm not sure - maybe it waits 300 seconds and then udpates.

It goes without saying that you have replaced login and pwd with correct values...

I read somewhere that order of some statements matters. So you might try putting your url to update last in the file.

---

### Post by mobbbx on 2009-04-06
Guys...

i have finally figured out what the problem was.... 

Previously, my ddclient.conf is:

```
use=web, web=checkip.dyndns.org/, web-skip'=IP Address'
```

I have changed it to the following:

```
use=web, web=checkip.dyndns.org/, web-skip='IP Address'
```

The web-skip'=IP Address' is causing the problem.

thanks everyone!

---

### Post by BkkBonanza on 2009-04-06
Looks the same to me...

---

### Post by cdenley on 2009-04-06
> **BkkBonaza said:**
> Looks the same to me...

Yes, I completely missed it, too. The single quote before "IP Address" was before the equals sign. This is obviously incorrect, but easy to miss at a glance. It was probably a typo made by the original poster when editing the configuration file.
```

use=web, web=checkip.dyndns.org/, web-skip[COLOR="Red"]**'=**[/COLOR]IP Address'
use=web, web=checkip.dyndns.org/, web-skip[COLOR="Red"]**='**[/COLOR]IP Address'

```

---

### Post by BkkBonanza on 2009-04-06
Ah, yes. Obvious now.
Simple errors that cause you to pull your hair out for hours. Grrr.
Reminds me of programming.

---

