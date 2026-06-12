---
title: "internet security, closing ports"
date: 2007-03-07
forum: Server Platforms
---

### Post by hosk on 2007-03-07
Is there a way to force close some ports I find open on my system?

Also, ipp is keeping a port open, and isn't that solely if I want my computer to function as a print server?  So, how do I shut down ipp?

I find a few ports that have unknown processes keeping them open, and I'm not sure how to find out what exactly is keeping them open, if anything.

---

### Post by Mr. C. on 2007-03-07
Stop the services listening on those ports.

```
netstat -l -t 
```

will tell you what services are listening.  Look under Local Address.  If you don't know what they are, let us know, and we can help.  There are tersely listed in /etc/services as well.

MrC

---

### Post by hosk on 2007-03-07
wow, just earlier today i tried using SUSE, had problems, posted on *their* forums last night, and never got a reply. I want to hug somebody.

---

### Post by hosk on 2007-03-07
[quote="netstat -l -t"]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN     
tcp        0      0 localhost:2225          *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
[/quote]

that's probably pretty misaligned, I know one of them is for ipp, but I don't know how to shut it down and turn it off for good. Maybe edit an rc startup file?

the other two seem to be magical listening ports for some unknown service.

I'm running ubuntu on VPC2007, if that makes a difference....

thanks!

---

### Post by Mr. C. on 2007-03-08
First, lets clarify something.  If you have a firewall between you and the big, bad Internt, and its inbound ports are closed (which they would be by default), the services on your system won't be seen externally.

Yes, IPP is internet printing.  2208 is the hpiod, and I don't know what 2225.  But here's how you find out:

```

lsof -i
```

Once you know what services those are, you can disable the startup scripts and shut down the services you don't want.

MrC

---

### Post by hosk on 2007-03-08
This is a pretty standard ubuntu install, so I'm not sure about firewalls, my Windows OS doesn't have one.  I also really have no idea what gets routed from Windows to VPC and what doesn't...

I didn't know much about those two commands you showed me, but now I can putter around my system until I gain a greater understanding of what's going on!

Thanks a lot Mr. C!

---

### Post by gaten on 2007-03-08
An easier way to see what process is using that open port is:
```
gaten@BIGBLUE:~/$ sudo netstat -tupl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.1.1:netbios-ssn *:*                     LISTEN     5342/smbd
tcp        0      0 *:5900                  *:*                     LISTEN     5628/vino-server
tcp        0      0 localhost:8118          *:*                     LISTEN     5327/privoxy
tcp        0      0 localhost:ipp           *:*                     LISTEN     9272/cupsd


```

As you can see, the last 2 values on the line are PID/process. This should help you get the name of the process

The flags (-tupl) are:

t: show tcp connections
u: show udp connections
p: show PID/name of process
l: show listening sockets

The first process, smbd, is listening on my internal interface, indicated by "192.168.1.100" in the 4th column, on port name "netbios-ssn" (or 139). I don't need to worry about this port because its onyl listening on my internal network; no one from the outside COULD connect to it, even if my firewall didn't block the port from the outside.

In contrast the second process, vion-server, shows a "*:5900" in the 4th column, this tells us that the process is listening on all interfaces (the *) on port 5900. If I didn't have a firewall up, this service would be a problem. 

I hope this helps you out a little, good luck.

---

### Post by hosk on 2007-03-08
wow, thanks!! 

```

hosk@hosk-linux:~$ cat netstat.txt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 localhost:2208          *:*                     LISTEN     3851/hpiod          
tcp        0      0 localhost:3885          *:*                     LISTEN     3854/python         
tcp        0      0 localhost:ipp           *:*                     LISTEN     3832/cupsd          
udp        0      0 *:1024                  *:*                                3972/avahi-daemon:  
udp        0      0 *:bootpc                *:*                                5214/dhclient3      
udp        0      0 *:5353                  *:*                                3972/avahi-daemon:  
udp        0      0 192.168.0.105:ntp       *:*                                4906/ntpd           
udp        0      0 localhost:ntp           *:*                                4906/ntpd           
udp        0      0 *:ntp                   *:*                                4906/ntpd           
udp6       0      0 *:1025                  *:*                                3972/avahi-daemon:  
udp6       0      0 *:ntp                   *:*                                4906/ntpd           

```

how many of those can i shut down?

---

### Post by Mr. C. on 2007-03-08
All but the dhcliient.  Configure a static IP, and it will go away too.

But really, what's your goal here?  Seems a bit arbitrary to me, like you're following some general rule of thumb "close down all services you can... because that's more secure", but without proper context and goal.

MrC

---

### Post by hosk on 2007-03-08
I never really had a goal, other than I wanted to learn a little more about what my computer was doing.  I remember once or twice I had installed a redhat system, and I had an http server and ftp server daemon running in the background, which seemed a little silly.

Should I have a more admirable goal? Or perhaps find a better way to make my system snug and secure?

Also... I'm running ubuntu on a virtual machine, and I don't have a lot of RAM I'm giving it(220MB); so I figured it couldn't hurt to shut down processes I don't need anyway.

Speaking of which... I learned that VPC2007 emulates a wired connection and pulls packets through my windows box to connect to the internet... But now it doesn't seem to do that; if I **ifdown eth0;ifup eth0** it waits for a DHCP assignment and never gets one. Any suggestions?

Sorry to be such a bother, you guys are being a huge help to me.

Thanks!

---

### Post by hosk on 2007-03-08
Hey, I determined and solved my own problem. I just had to change some settings to "Shared Networking"; as it turns out my schools wireless setup did not feel like granting me 2 IPs :)

---

### Post by Mr. C. on 2007-03-08
All sound like fine goals to me ! :-)

And my apologies for allowing my focus to better understand the root of your concerns and questions overcome tact and diplomacy with brevity and haste.

I'm happy to read you resolved your issues!
Cheers,
MrC

---

### Post by jerremy-tamlin on 2008-04-02
Hi I have a similar goal, I want to understand what all the open ports are so I know there aren't gaping holes in my system. I am running apache2 and mysql on my laptop for web page testing and have found it easier to transfer files to my sisters windows machine that has a printer via http, I've installed but not set up a basic ftp client too.

This thread has been really helpful but what do I do when a PID/Program name comes up "-"

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
**tcp        0      0 *:nfs                   *:*                     LISTEN     -                   **
tcp        0      0 *:46564                 *:*                     LISTEN     7395/skype          
tcp        0      0 *:56872                 *:*                     LISTEN     6353/rpc.mountd     
**tcp        0      0 *:43720                 *:*                     LISTEN     -                   **
tcp        0      0 localhost:mysql         *:*                     LISTEN     5974/mysqld         
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     6539/smbd           
tcp        0      0 *:sunrpc                *:*                     LISTEN     4897/portmap        
tcp        0      0 *:www                   *:*                     LISTEN     7015/apache2        
tcp        0      0 *:ftp                   *:*                     LISTEN     6639/vsftpd         
tcp        0      0 localhost:ipp           *:*                     LISTEN     5818/cupsd          
tcp        0      0 *:41753                 *:*                     LISTEN     4916/rpc.statd      
tcp        0      0 localhost:9050          *:*                     LISTEN     6616/tor            
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     6539/smbd           
udp        0      0 *:32768                 *:*                                4916/rpc.statd      
**udp        0      0 *:nfs                   *:*                                -                   **
**udp        0      0 *:32770                 *:*                                -                   **
udp        0      0 *:32771                 *:*                                6353/rpc.mountd     
udp        0      0 *:32772                 *:*                                6804/avahi-daemon:  
udp        0      0 localhost:32774         *:*                                7395/skype          
udp        0      0 Unknown-00-1:netbios-ns *:*                                6488/nmbd           
udp        0      0 *:netbios-ns            *:*                                6488/nmbd           
udp        0      0 Unknown-00-:netbios-dgm *:*                                6488/nmbd           
udp        0      0 *:netbios-dgm           *:*                                6488/nmbd           
udp        0      0 *:bootpc                *:*                                6979/dhclient       
udp        0      0 *:852                   *:*                                4916/rpc.statd      
udp        0      0 *:46564                 *:*                                7395/skype          
udp        0      0 *:mdns                  *:*                                6804/avahi-daemon:  
udp        0      0 *:sunrpc                *:*                                4897/portmap        
udp        0      0 *:ipp                   *:*                                5818/cupsd             

```

My families window's machine is getting old and having problem which often makes me think it has viruses and trojans especially when there is network activity for no particular reason. I've set up COMODO on the windows machines and this seemed to help. But I'm still a bit jumpy when I see internet activity that I don't recognise. And I need to sort out the firewall on my ubuntu laptop.

---

### Post by gaten on 2008-04-02
You're seeing the '-' because you don't have the right permissions to see what process is listening on that port. So run the command as root via sudo

```
sudo netstat -tupl
```

Also for apache, and your other server daemons, if you're just using it for internal use, either make sure your router blocks all access to those ports or configure the servers to only accept traffic from the local internet. 

You could also do this on your firewall.

---

### Post by jerremy-tamlin on 2008-04-02
Did sudo netstat -tupl  but still get same output with '-'

---

### Post by gaten on 2008-04-02
That's odd. Try this and see what you get:

```
sudo lsof -i
```Also, I noticed that one of the processes with the '-' is listening on the nfs port, so one could conclude its the  nfs server. Check your init.d directory for a nfs start/stop script and try stopping nfs and seeing if that helps with those.

---

