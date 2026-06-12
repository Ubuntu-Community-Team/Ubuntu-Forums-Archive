---
title: "Ubuntu 10.04 Server switching to static IP"
date: 2010-09-27
forum: Server Platforms
---

### Post by Calcipher on 2010-09-27
(Cross posting this from [http://ubuntu.stackexchange.com](http://ubuntu.stackexchange.com))

I am running an Ubuntu 10.04 server installation and I recently had to switch it from DHCP to static ip. I edited /etc/network/interfaces file and switched

"iface eth0 inet dhcp"
to
"iface eth0 inet static
address 192.168.1.167
netmask 255.255.255.240
network 192.168.1.160
broadcast 192.168.1.175
gateway 192.168.1.161"

You'll notice the IPs are a little strange. This is because the sever is now on a special subnet dedicated to isolating specific servers. I also edited the resolv.conf file to include the proper DNS servers (including one of Google's just in case all hell broke lose).

The problem is that, seemingly randomly, the machine will lose the ability to talk to the outside world. I know the machine is still up, but it acts like it has no networking at all. I think part of the issue is that there is no DHCP running to this subnet (nor will there be) and the dhclient seems to still be running on occasion which causes some sort of conflict (no idea what) which causes networking to die. I cannot, however, remove the dhcp3-client package as it also causes the ubuntu-minimal package to be removed and that would be bad.

So, any ideas? What might be calling the dhclient and what can I do to stop it from running?

---

### Post by CharlesA on 2010-09-27
Have you already rebooted the server/restarted networking?

When I had my server set for DHCP and then set it for a static ip, it would lose connectivity when the lease was up and grab an ip from dhcp.

---

### Post by Calcipher on 2010-09-27
> **CharlesA said:**
> Have you already rebooted the server/restarted networking?Yes, this fixes things every time (so far).  

> **CharlesA said:**
> When I had my server set for DHCP and then set it for a static ip, it would lose connectivity when the lease was up and grab an ip from dhcp.
This sounds almost identical to my situation, what did you do to fix it?

---

### Post by lisati on 2010-09-27
Here's my $0.02:

I have a relatively simple setup on my home network, with all of my machines hooking up to the one router. I've never had to tinker with the settings for any of my Ubuntu boxes when setting static IP addresses. I've found that setting my router to issue static IP addresses is sufficient when using a default installation of Ubuntu/Ubuntu server/Windows/whatever.

Maybe I've been lucky. :D

---

### Post by pricetech on 2010-09-27
This works for me also.  Granted, I'm not isolating a subnet, but then I wouldn't try that without a separate router anyway.

---

### Post by lisati on 2010-09-27
> **pricetech said:**
> This works for me also.  Granted, **[COLOR="Red"]I'm not isolating a subnet[/COLOR]**, but then I wouldn't try that without a separate router anyway.
I missed that on first reading of the first post: a separate router for the subnet *might* be something to look into.

---

### Post by CharlesA on 2010-09-27
> **Calcipher said:**
> Yes, this fixes things every time (so far).  


This sounds almost identical to my situation, what did you do to fix it?

I cannot recall off the top of my head, but I think I just rebooted and it worked off the static ip. Might have had to clear the lease on the router tho.

---

### Post by Calcipher on 2010-09-27
Ok, first a bit more background and then I'll explain some testing I just did.

The server in question is hosted at a co-location facility.  It is on a router just for its own subnet, but I really have no control over any of that.  

Anyhow, this is what I've done to test (all within VBox):
1. I created a near replica of the co-located server in VBox and set it to have a dynamic IP.
2. I installed Astaro Security Gateway in another virtual machine with two network interfaces.
3. I gave one interface (eth0) of Astaro access to the outside world and the second (eth1) I set up as a private network with DHCP enabled (and told VBox to make this an internal network).
4. I set the virtual server to be on the internal network and confirmed it was able to access the outside world via DHCP.
5. I disabled DHCP in Astaro
6. I set the virtual server to have a static IP and confirmed that it still had access to the outside world.
7. I manually ran dhclient.

Step 7 is where things get interesting.  dhclient attempts to ask for the various network information and absolutely trashes things.  It obviously fails to contact a DHCP server and eventually times out, but it sets eth0 to have no information (ie. no IP, Gateway, Broadcast Address, etc.).  The route command confirms that there is absolutely no networking functioning.  Oddly, running ifconfig eth0 down/up doesn't fix it, but running ifdown eth0, ifup eth0 does.  Restarting networking also fixes the problem.  Clearly this is all a situation where the DHCP client is attempting to set up eth0 even though it is not set as a dynamic interface.  

Why is dhclient running at all?  I believe that, as CharlesA said, the reason is due to the lease time expiring on eth0 - though this makes little sense in a static IP situation.  Maybe this is not the case and someone can give me some idea of what else might cause it to run.  

So, is there a way to disable dhclient without killing ubuntu-minium, is there a way to configure dhclient to ignore eth0, and/or is there some other solution someone can dream up?  Right now, I've done a very bad thing as a temporary fix, I removed execute from /sbin/dhclient.

---

### Post by Calcipher on 2010-09-28
Well, I'm still hoping someone has a clue as to what is going on here, but I wanted to share a few new details.  I was reading the spec files for the dhclient.conf file and ran across mention that dhclient does the following:
1. If no interfaces are specified in dhclient.conf, it grabs a list of interfaces (no idea how) and then attempts dhcp discover on each of them.
2. If, however, interfaces are specified in the conf file, it only does dhcp for those interfaces.  
3. If something specifically calls dhcleint on an interface, no matter what the configuration dhclient runs dhcp on that interface.
I was rather proud of myself for figuring this out, so I gave execution rights back to dhclient and added an interface rule to eth1 (eth0 is the interface with static configuration).  I tested the system by calling dhclient and confirmed that it did not mess with eth0 and called it good for the night.  Unfortunately, this morning, the system has again lost its network connection.  What this leads me to believe is that something, somewhere, is calling dhclient on eth0 specifically and, whatever it is, is driving me crazy.  

I know this is still a long shot, but does anyone have any idea?  Is there a way to blacklist an interface in dhclient.conf?  It seems that one can set a fixed-address in dhclient.conf, but it doesn't seem to prevent dhcp from running - any ideas?

---

### Post by CharlesA on 2010-09-28
Can you post the contents of /etc/network/interfaces please.

Also: How are you checking if dhclient is running?

Post the output of this as well:

```
ps aux | grep dhclient
```

---

### Post by Calcipher on 2010-09-28
> **CharlesA said:**
> Can you post the contents of /etc/network/interfaces please.
(Note, X's are to protect the innocent)
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
      address   XX.XXX.44.167
      netmask   255.255.255.240
      network   XX.XXX.44.160
      broadcast XX.XXX.44.175
      gateway   XX.XXX.44.161

```

> **CharlesA said:**
> Also: How are you checking if dhclient is running?
Post the output of this as well:
```
ps aux | grep dhclient
```
Well, here is the thing.  DHCLIENT isn't a service.  Something, somewhere, is calling it.  The ps aux doesn't show that it is running at the moment.

---

### Post by CharlesA on 2010-09-28
The interface file looks good.

I'm setting a server install for DHCP and seeing if dhclient is running on it.

It's running on a desktop install:

```
charles@lynx:~$ ps aux | grep dhclient
root       546  0.0  0.1   2232   984 ?        S    07:31   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-8727395a-6105-412f-b916-f54e3e140fc0-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0

```

EDIT: Checked the server install with DHCP set:

```
charles@atlantis:~$ ps aux | grep dhclient
root       716  0.0  0.0   6556   344 ?        Ss   07:53   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
```

Set it back to a static IP and restarted networking. dhclient was still running.

Rebooted and dhclient wasn't running. :|

---

### Post by Calcipher on 2010-09-28
Not sure what to make of that honestly.  I know dhclient isn't running, but something must be calling it.  Or, hell, maybe dhclient isn't the issue and it is actually something else that is causing networking to drop.  It just seems that calling dchlient eth0 causes the exact problem I'm seeing.

---

### Post by CharlesA on 2010-09-28
Is there anything listed here:

```
cat /var/lib/dhcp3/dhclient.leases
```

The only thing I can think of, is that Astaro Security Gateway is screwing with the networking.

---

### Post by Calcipher on 2010-09-28
> **CharlesA said:**
> Is there anything listed here:

```
cat /var/lib/dhcp3/dhclient.leases
```

The only thing I can think of, is that Astaro Security Gateway is screwing with the networking.
I'll have to check the main server later (if you'll recall, it is co-located and, as it is now without networking, I'll need to take a trip to the co-location facility and access it).  The Astaro system is only my testbed and not the main server.  That being said, there is nothing in the test system's dhclient.leases file.

Edit: Maybe something that would be useful is a cron job to check if eth0 has an IP and/or that route goes somewhere.  If not, it could touch a file in my home directory (to let me know about when things died) and then restart networking.  Only problem is that I'm not quite sure I know enough to detect if eth0 has an ip and/or that route goes somewhere.

---

### Post by CharlesA on 2010-09-28
You could write a script that'll ping an ip and echo text to a file if it doesn't get a response.

```
#!/bin/bash

IP=192.168.1.1
COUNT=`ping -c 1 $IP | grep received | awk -F ',' '{print $2}'| awk '{print $1}'`

if [ $COUNT -eq 0 ]; then
echo "Network Down on `date`" >> /home/user/somefile
fi

```

---

### Post by Calcipher on 2010-09-28
Ok, this is a nasty hack, but I'm in a hurry and I want more information on the problem.  So, here is the script I wrote:
```

#!/bin/bash
while true; do
  if ( ps aux | grep -v grep | grep -i dhc )
  then
    echo "Start of Incident" >> /root/nmecFixOut.txt
    date >>  /root/nmecFixOut.txt
    echo >> /root/nmecFixOut.txt
    ps aux >> /root/nmecFixOut.txt
    echo >> /root/nmecFixOut.txt
    ifconfig >> /root/nmecFixOut.txt
    echo >> /root/nmecFixOut.txt
    route -n >> /root/nmecFixOut.txt
    echo >> /root/nmecFixOut.txt
    echo "End of Incident" >> /root/nmecFixOut.txt
    echo >> /root/nmecFixOut.txt
    killall -9 dhclient
    sleep 15
  else
    if ( ! route -n | grep -vi Kernel | grep -vi Destination )
    then
      echo "Restarting Networking" >> /root/nmecFixOut.txt
      date >> /root/nmecFixOut.txt
      bash -c '/etc/init.d/networking restart'
      echo "Done" >> /root/nmecFixOut.txt
    fi
  fi
done

```
(nmec is the name of the server if you were wondering).

---

### Post by CharlesA on 2010-09-28
You are way better at shell scripting then me. :P

Hope it helps you narrow down the problem.

---

### Post by Calcipher on 2010-09-28
Well, good news and bad news.  The good news is I can now say dhclient is likely not the problem.  On my test system, I have always observed that the effects of dhclient (when there is no dhcp server to be accessed) is that all network interfaces are a) brought up (even ones that are not up at boot), b) that these interfaces are all lacking any configuration (even ones with static IP mappings), c) that dhclient is still running (thus the kill in my script) and d) that route shows no routes.  I finally got physical access to my machine (while it was unable to access the internet) and found that a) only eth0 is up (the only auto configured interface other than the loopback), b) eth0 is fully configured, c) dhclient is not running, and d) that route is still valid.

But, wait, didn't I say that I had no networking?  How can route still work?  Turns out I have (and I shudder to type this) *some* networking; I can ping random servers by IP, but I cannot seem to ping any DNS servers AND random other servers by IP are not accessible (e.g. one server on our local network was ping-able, another was not).  

So, I've added a crontab entry that restarts networking ever 30 minutes.  My question is now, I guess, what does this networking restart flush that might be confused?  I'm now unwilling to rule out that the horribly complicated network that exists between my server and the real work is the source of the problem, but why would restarting networking fix things?  I can't pay anything for a solution, but I can give you my unyielding gratitude.

---

### Post by CharlesA on 2010-09-28
What the heck.

I've never heard of this problem happening and the only thing that (I know of) restarting networking does is bring up all the interfaces listed as auto in /etc/network/interfaces after bringing them down.

If the route was correct, and you were unable to ping a dns server or whatever on the same subnet, it sounds like there's something else going on. Especually if you were able to ping a random website (meaning DNS was working)

---

### Post by Calcipher on 2010-09-28
> **CharlesA said:**
> What the heck. Indeed, though I think my speech bubble would look more like Q*Bert's.

> **CharlesA said:**
> Especually if you were able to ping a random website (meaning DNS was working)To clarify, I was only able to access random websites by IP, I was not able to get DNS even through Google's DNS.

I have emailed the numerous systems administrators over at the computing center to see if they have any ideas.  I really think this problem is not mine, but I wanted to exhaust every option open to me before I called down the wrath of their systems group.  So, I'm not quite sure what to do.  I suppose the problem still might be with my server (hence why I'm hesitant to close this thread - maybe some magical person will have an idea of what is going on), but if it is with their stuff than there is little more people here can do to help me.  You guys have been very helpful and I will be sure to detail the final solution if one (beyond crontab stupidity) ever comes to light.

---

### Post by CharlesA on 2010-09-28
I see now. If DNS isn't working, then there is definitely some sort of problem with network communications, but if the network was down, how could get ping a website in the first place?

I'd suggest the admins swap out the network card. Could be that it's actually failing, who knows.

---

### Post by Calcipher on 2010-11-03
I realize few if any are following this, but we finally (yes, finally) found a solution to the problem we were having.  It turns out that there was a misconfiguration with one of the routers at our co-location facility that was causing it to drop its arp table and not route traffic to or away from our server correct.  It might be helpful to others to know that I discovered this fact almost a month ago by taking long term logs with tshark (a text based version of wireshark).  Despite the fact that I had clear logs showing that the router was ignoring us, it took a long time to convince their systems administrators, but we finally were able to show them that it was unequivocally their fault.  Lesson learned, tshark is awesome and co-location facilities suck.

---

### Post by CharlesA on 2010-11-03
Glad you got it worked out.

Don't forget to mark the thread as solved from the thread tools menu. :)

---

