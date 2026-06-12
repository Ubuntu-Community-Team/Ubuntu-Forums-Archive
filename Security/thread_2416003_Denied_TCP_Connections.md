---
title: "Denied TCP Connections"
date: 2019-04-03
forum: Security
---

### Post by goochweb on 2019-04-03
Hello Everyone,

First time posting here, so I apologize if this is not the correct forum for this question.   I am having a connectivity issue with a Ubuntu server and I have exhausted all places to look within my and google's knowledge.
See description below:


Server Operating System:  Ubuntu 16.04.1 LTS 
Virtualized Server running on Citrix XenServer


Problem Description:    I am not able to establish communication from a new network/subnet that was added into our MPLS to this Linux server.   When I attempt to telnet from a Windows Server on the new network to the Ubuntu server, it will not accept inbound connection.    

Notes:
- I can successfully ping to and from the Windows Server to the Linux and vice versa in both directions.   
- I can telnet to the SSH port (TCP 22) from a Windows Server on the SAME network/subnet as the Linux server.  
- I cannot telnet to SSH port (TCP 22) from a Windows server on the NEW network/subnet.
- There is no network firewall between the two networks/subnets.    
      - I ruled this out because I can telnet from the new network to ANY other server including other Linux servers and it works just fine.

Items checked already:

-Looked at the status of the UFW and it is "Inactive"
-Looked at the IPTABLES list and all three sections state "Accept"
-It's doesn't appear to be a routing issue, because I can ping the server(s) in both directions
-I also ruled out IP conflict, but shutting the Ubuntu server down and ensuring ICMP dropped.


Other Notes:

IP of the Ubuntu Server:   192.168.5.67
IP of the Window Server:   10.248.1.101  **This server cannot telnet to port 22**
IP of a local Windows Server:    192.168.5.100  **This server can telnet to port 22**

 

From my troubleshooting it only appears to be this Linux server that is denying the connection from this new network.    Any guidance on things or places I can look that could be denying inbound traffic from a particular network.
Thank you for your help in advance!

-Chris

---

### Post by TheFu on 2019-04-04
Fewer descriptions.
More commands which prove what you believe.

Please.

Why would you expect telnet to work to an sshd connection?

---

### Post by Doug S on 2019-04-04
> **TheFu said:**
> Why would you expect telnet to work to an sshd connection?Some use telnet just as a TCP debugging tool, without actually expecting it to work completely. It can make a TCP connection which will eventually get dropped, but proving that a connection is possible, which is very useful. Example:
```
doug@s15:~/idle/k51$ telnet s17 22
Trying 192.168.111.120...
Connected to s17.smythies.com.
Escape character is '^]'.
SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.3

Protocol mismatch.
Connection closed by foreign host.

```

---

### Post by SeijiSensei on 2019-04-04
Install [Putty]("https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html") on the Windows machine and try to connect with SSH.  What happens?

---

### Post by TheFu on 2019-04-04
I'll try to help.  For troubleshooting ssh, setup debug mode on the server-side (need root/sudo and it can't be run as a daemon) and increase the verbosity from the client connect-side using -vvv.  Even if you don't control the sshd server, getting the client-side verbose output is extremely helpful.

```
$ ssh -vvv userid@server
```
If an ssh connection is begun, the output will show hints, usually extremely good hints, for the issue.  If no connection happens, then it isn't ssh, look at routing and firewalls.

If routing is believed to be the issue, please post the routing tables as the client sees it.  **route -n** is preferred, inside "code tags" - I've done that in this post.  Adv Reply, select the code button (#) in the controls above the text entry block.   Or you can cheat - I like using the 'quote' block on the normal reply, then just change the QUOTE --> CODE in the front and back. These are case insensitive tags on these forums.  Makes things line up with a monospaced font.

I haven't used Xen in about 8 yrs, but doesn't the networking usually depend on the host system's PCI passthrus for each NIC or a bridge setup?  Scratch that - if the other networking is working, then that isn't likely the problem.  However, I did have an issue where 1 VM guest out of 12 on the same host refused to access any internet IPs, by IP, for a few days.  I didn't change anything, it corrected itself the next day. All the other hosts, most configured similarly kept working. It happened again a few months later, so I moved that VM to a different VM host. No issues since.  I haven't a clue what happened or why it is working and has been working all this time.

---

### Post by The Cog on 2019-04-04
I would be inclined to use tcpdump to view the traffic passing over the interface. Run the command **sudo tcpdump**, and watch while a connection attempt is made. You should hopefully see the TCP connect request arriving and the response going out. If you see neither, do the ping (which works) and make sure you can see those packets.

If you're not sure what the trace means, post it here and we can have a look. My first intention would be to see does the connnect request arrive, and if so does a response get sent back. I am guessing that you will see either both connect and response, or neither. The tcpdump output will tell us.

---

