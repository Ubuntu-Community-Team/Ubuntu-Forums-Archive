---
title: "port forwarding to private ip (home computer)"
date: 2014-03-01
forum: Server Platforms
---

### Post by cylent on 2014-03-01
[COLOR=#000000][FONT=Helvetica Neue]I am basically trying to do something so simple thats becoming a difficult [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue]task for me ... [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]What i am trying to do is something silly. use my vps as a gateway and have [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue]it forward traffic on incoming ports to my private computer at home.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]so traffic that would come in on port 9003 (for example) to my VPS ip would [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue]be forwarded to my home ip via what i have setup which is the openvpn [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue]server.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]on the openvpn server i've given myself a static ip of 172.27.230.2 [/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]I want my vps public ip to be "mask" so to speak.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]So then traffic that comes to my pubip:9003 gets redirected to 172.27.230.2[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]in ubuntu server i tried to use ufw (ubuntus firewall software) to first [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue]open the port then i tried a nat redirect rule.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]i then used a tcp/ip program on my windows machine called Listen.exe [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue]<[/FONT][/COLOR][http://www.allscoop.com/tcp-listen.php>..]("http://www.allscoop.com/tcp-listen.php%3E..")[COLOR=#000000][FONT=Helvetica Neue]this is nothing more than a program that listens on a specified port .. i[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica Neue]then used port checking utility online to verify my work.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]yet all the time the ports are closed and the traffic is not coming through.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]i checked on ubuntu with netstat and i see the port 0.0.0.0:9003 is [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue]listening.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]again. i realize this is outside the scope of your work but i am desperate [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica Neue]and cant get this working.[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]please advise.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2014-03-01
I do this using a static OpenVPN tunnel between a server in my house and one of my virtual servers at Linode.  I can't help with UFW; I write all my firewall rules manually.

I've done this with iptables rules, but in general I find it easier to use a TCP proxy.  Currently I'm using [tcproxy](http://code.google.com/p/tcproxy/) for this task.  I had to compile this from source since tcproxy is not in the repositories.

In broad strokes, I set up the tunnel then open the port on the Linode server.  I then run tcproxy to listen on that port and forward the traffic to the port on the internal server.

I've also used iptables rules like this:

```

EXT=10.10.10.10
TARGET=192.168.1.1

iptables -A INPUT -p tcp -m tcp -d $EXT --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -d  $EXT -p tcp -m tcp --dport 80 -j DNAT --to-destination $TARGET:80
iptables -A FORWARD -d $TARGET -p tcp --dport 80 -j ACCEPT

```

However if you use iptables, you must enable forwarding of packets across interfaces in /etc/sysctl.conf.  Uncomment the line "net.ipv4.ip_forward=1" as described in the comments in that file, then use "sudo sysctl -p" to tell the kernel to reread the sysctl.conf file, or simply reboot.  See "man sysctl" for details.

---

### Post by cylent on 2014-03-01
i did everything as you described and yet i still get this error from canyouseeme.org

Error: I could not see your service on xx.xxx.xxx.24 on port (9003)
Reason: Connection timed out

I have the program listen.exe running on my windows box listening on port 9003 (With the firewall turned off!).

I am not sure what else could be wrong.

How can i see if the traffic is coming in? what util can we use to diagnose?

---

### Post by cylent on 2014-03-01
the only way i got it to work is disable iptables completely!
then use tcproxy!

it works. but its a dirty way. i'd prefer to go with iptables.

[COLOR=#ff0000][**edit**: never-mind. i got it working with the rules above. all is working now!]
Thank  you so much![/COLOR]

---

### Post by cylent on 2014-03-01
rebooted VPS.

and now it doesnt work!

only if i use tcproxy!

WTF!!!!!!!!!!!!!

netstat -a doesnt show the ports at all!

the rules DO exist in the firewall though!

---

