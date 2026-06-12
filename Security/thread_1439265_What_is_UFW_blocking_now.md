---
title: "What is UFW blocking now?"
date: 2010-03-26
forum: Security
---

### Post by chaopoch on 2010-03-26
I can see what Firestarter is blocking in the Firestarter/Events tab, but after reading all the man pages of UFW, I still don't know how to check what the UFW is blocking.

Thanks for help.

---

### Post by adam814 on 2010-03-26
```
sudo ufw status
```

That should do the trick.  If you prefer something more graphical try gufw.

---

### Post by chaopoch on 2010-03-26
> **adam814 said:**
> ```
sudo ufw status
```

That should do the trick.  If you prefer something more graphical try gufw.

I know this command, but it does not show what is blocking.

[COLOR="SeaGreen"]$ sudo ufw status

Status: active

To                         Action      From
--                         ------      ----
4662/tcp                   ALLOW       Anywhere
6881/tcp                   ALLOW       Anywhere[/COLOR]

---

### Post by bodhi.zazen on 2010-03-26
I suggest you look at this wiki page for details :

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/UFW") 

You can see the exact rules with 

```
sudo iptables -L -v
```

But unless you are familiar with both iptables and ufw it is hard to read them.

The rules listed with```
sudo ufw status
```are the rules you added.

---

### Post by chaopoch on 2010-03-26
> **bodhi.zazen said:**
> I suggest you look at this wiki page for details :

[Uncomplicated Firewall - UFW - Community Ubuntu Documentation]("https://help.ubuntu.com/community/UFW") 

You can see the exact rules with 

```
sudo iptables -L -v
```

But unless you are familiar with both iptables and ufw it is hard to read them.

The rules listed with```
sudo ufw status
```are the rules you added.

Here is the screenshot of Firestarter/Events tab, I just want to know if UFW can show **[COLOR="Red"]Blocked Connections[/COLOR]** or not? 

Thanks.

[ATTACH]151495[/ATTACH]

---

### Post by dogdo on 2010-03-26
+1 it is really annoying the way you cant see what ufw is blocking in terms of attacks.

---

### Post by a.walker on 2010-03-26
> **dogdo said:**
> +1 it is really annoying the way you cant see what ufw is blocking in terms of attacks.

```
cat /var/log/messages | grep UFW
```

---

### Post by bodhi.zazen on 2010-03-26
> **chaopoch said:**
> Here is the screenshot of Firestarter/Events tab, I just want to know if UFW can show **[COLOR=Red]Blocked Connections[/COLOR]** or not? 

Thanks.

[ATTACH]151495[/ATTACH]

> **dogdo said:**
> +1 it is really annoying the way you cant see what ufw is blocking in terms of attacks.

GUFW does not do that. If you want that feature stay with firestarter.

You will get many opinions on that, personally I would tell you that I get thousands of blocked packets on my firewall and there are better tools for NIDS, ie snort. Snort will at least look through the thousands of packets and alert you to network traffic that is potentially worrisome. A Flash or an alert from Firestarter will overwhelm you with false positive alerts in short order, IMO at least.

But, as I said, if you prefer firestarter I would use that over GUFW.

If you want to "know" if your firewall is working, scan it from a second computer on your LAN. Be aware that Ubuntu does not have open ports by default so you may not see much a difference depending on what services your are running, if any.

You can also see dropped packets in your logs.

---

### Post by cariboo on 2010-03-26
One thing I have noticed is if you use:

```
nmap -PN <ip address>
```

the port scan takes much longer, than if you have the firewall turned off.

---

### Post by The Cog on 2010-03-26
The reason for that is that if you are running a firewall, the scanners requests get dropped and the scanner has to wait for a timeout before knowing the connection request was unsuccesful. If you're not running a firewall, the request reaches the computer which immediately responds with a connection refusal (ICMP destination unreachable:port unreachable) because the port is closed - the scanner doesn't have to wait for the timeout to know the connection attempt failed.

---

### Post by bodhi.zazen on 2010-03-26
> **dogdo said:**
> +1 it is really annoying the way you cant see what ufw is blocking in terms of attacks.

I should have asked in my last post, perhaps it is best to ask why you feel more secure because you see such a notification in Firestarter ?

I am suggesting to you there are better ways to test your firewall and analyze your network traffic :twisted:

---

### Post by doas777 on 2010-03-26
> **bodhi.zazen said:**
> I should have asked in my last post, perhaps it is best to ask why you feel more secure because you see such a notification in Firestarter ?

I am suggesting to you there are better ways to test your firewall and analyze your network traffic :twisted:
well, i have known many peices of infrastructure software (stuff that just runs for years with little attention) that are working one day, and not the next, with no warning.

I'm with you on external testing, but i do have to say, the lack of output in gufw is a big turn off for me.

---

### Post by bodhi.zazen on 2010-03-26
> **doas777 said:**
> well, i have known many peices of infrastructure software (stuff that just runs for years with little attention) that are working one day, and not the next, with no warning.

I'm with you on external testing, but i do have to say, the lack of output in gufw is a big turn off for me.

/me points to out ufw has a very rich logging options and iptables -L -v will show packet analysis.

I agree, security is certainly not install and forget to monitor. I would point out I did not suggest such a strategy (I am not suggesting one blindly configure a firewall and neglect to monitor it).

Those of us who have some security experience may not always agree, but we should at least point out the potential weaknesses of any particular strategy and that there are alternate tools available, in this case, NIDS.

---

### Post by OpSecShellshock on 2010-03-26
Surely a connection that gets blocked isn't anything to worry about unless it wasn't supposed to be?

---

