---
title: "gnome-panel Connected Out?"
date: 2010-11-04
forum: Security
---

### Post by guimaster on 2010-11-04
Hello,

 According to Firestarter, gnome-panel is connected out to an IP address on Port 80. Is this normal? I can't say I have seen such a thing before.

 If this is not necessary, is there a way I can prevent gnome-panel from connecting?

 Thanks

 (Dell Laptop running Ubuntu 9.10)

---

### Post by Enigmapond on 2010-11-04
Well I have no idea why the panel is accessing the port but you can always just deny that port....and I would also get rid of Firestarter as there hasn't been any updates on that in years...install instead gufw.

The code to deny the port would be..
```
sudo ufw 80 deny
```

---

### Post by cariboo on 2010-11-05
Use:

```
nststat -t
```

to see where it is connecting to, it could just be the weather applet.

This is what I get on my system:

```
[noparse]netstat -t
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 Alexis-Natty:60339      pv-in-f138.1e100.ne:www ESTABLISHED
tcp        0      0 Alexis-Natty:53482      feijoa.canonical.co:www ESTABLISHED
tcp        1      0 Alexis-Natty:54127      xml.weather.com:www     CLOSE_WAIT 
tcp        1      0 Alexis-Natty:57996      xml.weather.com:www     CLOSE_WAIT 
tcp        0      0 Alexis-Natty:34431      px-in-f125.:xmpp-client ESTABLISHED
[/noparse]
```

---

### Post by guimaster on 2010-11-14
> **Enigmapond said:**
> Well I have no idea why the panel is accessing the port but you can always just deny that port....and I would also get rid of Firestarter as there hasn't been any updates on that in years...install instead gufw.

The code to deny the port would be..
```
sudo ufw 80 deny
```

Thanks for your response.

I don't think blocking the port is going to do much good, unless I want to stop surfing the web also. As for your gufw suggestion, I have actually begun using a firewall called: GuardDog, which I find to be quite amazing. I want more simplicity and more control, as you get with Windows firewalls, and GuardDog provides that. The only problem with it is that I can an error message on the next boot everytime after I have changed the firewall's configuration. But I found an easy fix for that.

Take care

> **cariboo907 said:**
> Use:

```
nststat -t
```to see where it is connecting to, it could just be the weather applet.

This is what I get on my system:

```
[noparse]netstat -t
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 Alexis-Natty:60339      pv-in-f138.1e100.ne:www ESTABLISHED
tcp        0      0 Alexis-Natty:53482      feijoa.canonical.co:www ESTABLISHED
tcp        1      0 Alexis-Natty:54127      xml.weather.com:www     CLOSE_WAIT 
tcp        1      0 Alexis-Natty:57996      xml.weather.com:www     CLOSE_WAIT 
tcp        0      0 Alexis-Natty:34431      px-in-f125.:xmpp-client ESTABLISHED
[/noparse]
```

 Thanks, that would be a logical explanation, but I haven't seen this happen again since that day. RKHunter and Chkrootkit both came back okay as did Avast.

---

