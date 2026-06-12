---
title: "How to open a port"
date: 2008-07-30
forum: Security
---

### Post by RuleMaker on 2008-07-30
I need to open my port 80 for apache web server.
I tried with this:
```
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 80 -j ACCEPT
```
but it didn't worked, i forwarded it in my router but it's still closed somehow.

---

### Post by tuxxy on 2008-07-30
Firestarter will allow you to configure it from a GUI,

[http://ubuntuforums.org/showthread.php?t=263162](http://ubuntuforums.org/showthread.php?t=263162)

---

### Post by RuleMaker on 2008-07-30
Thank you for that link, i have installed firestarter and started it as root, but my "Add Rule" button is disabled, maybe I've missconfigured something?

EDIT:
Looks like it works now, but when I scan my ports 80 is still closed, apache is listening but not accessible from external network.

---

### Post by Tom--d on 2008-07-30
> **RuleMaker said:**
> Thank you for that link, i have installed firestarter and started it as root, but my "Add Rule" button is disabled, maybe I've missconfigured something?

EDIT:
Looks like it works now, but when I scan my ports 80 is still closed, apache is listening but not accessible from external network.

I would not use Firestarter.
Its Dead.
Its old (iptables is still being updated meaning that firestarter cannot use the new things in iptables)

I would use ufw. (uncompleted firewall)

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by jimv on 2008-07-30
So if you do localhost:80 in your browser, it comes up with a site?

---

### Post by bodhi.zazen on 2008-07-30
Firestarter is depreciated, you should use ufw :

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

Also keep in mind, the default settings on iptables is permissive, did you forward port 80 from your router ?

---

### Post by RuleMaker on 2008-07-30
Ok guys, I'll try ufw.
> So if you do localhost:80 in your browser, it comes up with a site?
Yes, but when i try to open it by my IP then it opens my router configuration page and prompts for password, I'll open a new topic for that.

---

### Post by bodhi.zazen on 2008-07-30
> **RuleMaker said:**
> Ok guys, I'll try ufw.

Yes, but when i try to open it by my IP then it opens my router configuration page and prompts for password, I'll open a new topic for that.

You need to configure your router to forward port 80 to your server. This is *usually* called "Virtual servers" on many routers.

Also, you should secure your router. I personally do not think you should NOT access your router remotely. Make sure you at a minimum change the default password.

---

### Post by jimv on 2008-07-30
Are you typing in the external IP address of your router, or the internal address?  Like is it 192.168.x.x?  Because that's the internal IP and won't work for trying to access your webserver from the net.  You want the external IP, which you can get off the router, or by going to [www.whatismyip.com](www.whatismyip.com).

---

### Post by brian_p on 2008-07-30
> **RuleMaker said:**
> I need to open my port 80 for apache web server.

The fact that you installed apache means it is listening for incoming connections on port 80. That is exactly the same as saying the port is open. So - you **do not** need to open port 80 **because you have already done it**.

> I tried with this:
```
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 80 -j ACCEPT
```
but it didn't worked, . . . . 

Using an iptables rule is not needed. The port is already open. Why? Because you have installed apache. This means any playing about with programs like firestarter or ufw is a complete waste of time. Remove them from your system and concentrate on understanding your problem.

You say

```
http://localhost:80
```

works. That means the port is open.

Get the IP of your machine from

```
ifconfig -a
```

and confirm port 80 is open with http://<IP>:80

> . . . . . i forwarded it in my router but it's still closed somehow.

Maybe you did not do this correctly. You can check if port 80 on the router is forwarding correctly by going to [www.grc.com](www.grc.com)

---

### Post by dexter.deepak on 2008-07-30
sorry to interrupt in this thread, but seems like i can get some help.
i have a direct internet connection, and am running apache at port 80. 
i looked up my ip from whatismyip and asked my friend to try opening that url from his pc (while he is connected to internet).
since i am not behind any proxy/router , i expected thistrial to be successful, but he couldnt open up my website.
can you people help me ?

---

### Post by jimv on 2008-07-30
> **dexter.deepak said:**
> sorry to interrupt in this thread, but seems like i can get some help.
i have a direct internet connection, and am running apache at port 80. 
i looked up my ip from whatismyip and asked my friend to try opening that url from his pc (while he is connected to internet).
since i am not behind any proxy/router , i expected thistrial to be successful, but he couldnt open up my website.
can you people help me ?

Go here and run the common ports scan to see if 80 is open on your connection:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by dexter.deepak on 2008-07-30
thanks for that link.
it would take me some time to go through that site.
for the immediated understanding can you explain what it means...i get a "stealth" status ...what does that mean ?

---

### Post by feistyfella on 2008-08-01
> **dexter.deepak said:**
> thanks for that link.
it would take me some time to go through that site.
for the immediated understanding can you explain what it means...i get a "stealth" status ...what does that mean ?

dexter.deepak, I'm having the exact same issue.  Will post my fix if I get one.  The definition of stealth can be found here:  [https://www.grc.com/su/portstatusinfo.htm](https://www.grc.com/su/portstatusinfo.htm)  so by reading the definition of "STEALTH" you'd assume that it's all about the firewall settings but when I run "sudo iptables --list" & webmin i'm showing no iptables filter rules whatsoever, the default policy (which is to ACCEPT on each chain).  The router is set to forward to the correct ip and DMZ is enabled. http://<ip>:80 works and [http://localhost](http://localhost) works but when i check to see if port 80 is open on a few different websites it says it's closed.  The grc.com site came up with more detail than just closed but it doesn't solve the problem, at least it's another piece added to the puzzle.  GRC.com and other websites say my port 21 is closed but gFTP is running fine.
](*,)

---

### Post by bodhi.zazen on 2008-08-01
"Stealth" is a bad term.

See this link :

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Table_14-2_Descriptions_Of_The_Most_Commonly_Used_Targets](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Table_14-2_Descriptions_Of_The_Most_Commonly_Used_Targets)

The options are "Reject" and "Drop"

Reject sends an error message, drop does not. Most people feel they are equal in security (security through obscurity is no security), although opinions vary.

Thus "stealth" == "drop" and a close port is as secure as a stealth port, you are worried about open ports or the "accept" option (unless you are running a public server ...)

---

### Post by feistyfella on 2008-08-01
> **dexter.deepak said:**
> thanks for that link.
it would take me some time to go through that site.
for the immediated understanding can you explain what it means...i get a "stealth" status ...what does that mean ?

Many residential ISPs Block port 80.

[_This link will walk you through on how to edit which port# apache listens on._]("http://www.debianadmin.com/apache2-web-server-with-php-support-in-ubuntu.html")

Let's say your ip is [http://123.123.123.123](http://123.123.123.123)
For your friend to access your server, he/she would enter..
[http://123.123.123.123:#####](http://123.123.123.123:#####)  where ##### equals whatever port number you changed from port 80.

:smile:

---

### Post by feistyfella on 2008-08-02
From [http://www.canyouseeme.org/](http://www.canyouseeme.org/) :

Most residential ISP's block ports to combat viruses and spam. The most commonly blocked ports are port 80 and port 25.

Port 80 is the default port for http traffic. With blocked port 80 you will need to run your web server on a non-standard port in conjunction with a port 80/web redirect from No-IP.com.

---

