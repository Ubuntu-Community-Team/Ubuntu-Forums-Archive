---
title: "Linux (Ubuntu) Dynamic DNS client questons."
date: 2006-11-08
forum: Server Platforms
---

### Post by bobsta63 on 2006-11-08
Hi all,

I plan to run my own webserver from home using Ubuntu Server 6.06 (Dapper) my IP Address provided by my ISP is Dynamic and therefoe I plan to use Dynamic DNS.

I plan to register a TLD (Top Level Domain) xxxxxx.com and then want to update my IP to my Dynamic DNS provider when my IP address changes.

If someone could advise on the following two questons I would be very greatful:-

[INDENT]1. Does anyone know of a good Dynamic DNS Service Provider that has good/FREE update client compatible with Linux (Ubuntu)?

2. Can you use APT-GET to install a Dynamic Update Client like ddclient? Or does anyone have a good tutorial how to setup and configure the required Update Client?[/INDENT]

Thanks in advance, :-D 

Kindest regards,

Bobby

---

### Post by Jussi Kukkonen on 2006-11-08
Not sure if this is what you're looking for, but all these are available in the repositories:
```
ddclient
ddns3-client
ez-ipupdate
ipcheck
no-ip
```
Take a look and see the providers they support and select out of those. Personally I use dyndns.org and ddclient. It's not perfect, but good enough (if you wanted 100% 24/7 accessibility, you shouldn't be thinking of dynamic dns anyway).

EDIT: just realized that I haven't cheked if dyndns.org will route to your own domain (I'm using something.dyndns.org )... Can't think why they wouldn't though.

---

### Post by bobsta63 on 2006-11-08
Brilliant thank you for that :)

So does this mean I can install ddclient using:-

*apt-get install ddclient*

Also where is the configuration files kept if you install using APT? IS it...

*/etc/ddclient*

Thanks for your reply, It was very helpful :)

---

### Post by bluenova on 2006-11-08
You can also use [no-ip](http://www.no-ip.com/)

sudo aptitude install no-ip

---

### Post by bobsta63 on 2006-11-08
> **bluenova said:**
> You can also use [no-ip](http://www.no-ip.com/)

sudo aptitude install no-ip


Ok, I have looked into No-IP and the price is right etc. I have also installed No-IP update client using the above command (Thank you bluenova) :) 

I now just need to create the config file 'no-ip.conf' and place it into /etc/no-ip.conf.

Does anyone know or have a template for this file?

Also how can I make the IP update client boot on startup or will it automatically as I used 'sudo aptitude install no-ip'

Thanks all :)

---

### Post by MJN on 2006-11-08
I would personally recommend [www.zoneedit.com]("http://www.zoneedit.com") for your DNS, using the zoneeclient (available at [http://zoneclient.sourceforge.net/](http://zoneclient.sourceforge.net/)) python script (run as a cron job) to keep it updated.
 
Have been using this arrangement for around 5 years now without a single known hiccup.
 
Mathew

---

### Post by Jussi Kukkonen on 2006-11-08
> **bobsta63 said:**
> 
I now just need to create the config file 'no-ip.conf' and place it into /etc/no-ip.conf.

Does anyone know or have a template for this file?

Also how can I make the IP update client boot on startup or will it automatically as I used 'sudo aptitude install no-ip'


You can find info on config files and such with *man* after you've installed the package, e.g.:
```
man no-ip
```

---

### Post by bobsta63 on 2006-11-08
> **Jussi Kukkonen said:**
> You can find info on config files and such with *man* after you've installed the package, e.g.:
```
man no-ip
```

Brilliant, Thanks for that I am now looking at the manual!

Thanks to all for your help guys :)

---

### Post by punong_bisyonaryo on 2007-02-08
Hi!,

I'm using ipcheck with dyndns.org. It works ok when i run it manually from the terminal. But I tried putting it in a cronjob and it doesn't work.

The script i use to update:
```
cd /root/
if [ if /root/ipcheck.dat ]; then
    ipcheck -r checkip.dyndns.org:8245 $USERNAME $PASSWORD $HOSTNAME
else
   ipcheck --makedat -r checkip.dyndns.org:8245 $USERNAME $PASSWORD $HOSTNAME
fi

echo -n "ipcheck executed "
date

```

And in my cron i used:
```
*/5 * * * * sh /etc/ppp/ip-up.d/dyndns-update.sh >> /home/me/cronlog
```

It echos into the cronlog just fine, but it doesn't seem to be updating my ip. No errors, no nothing, just my echos in the cronlog.

By the way, i'm not logged in as root, but i run the cron as root using sudo crontab -e. if that helps.

---

### Post by punong_bisyonaryo on 2007-02-08
Well, i kinda solved my own problem by adding sudo to the ipcheck commands. But I'm still wondering why it needed sudo? Since the script is already in the sudo crontab, shouldn't it already be run as root even without the additional sudo inside the script?

---

