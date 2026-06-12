---
title: "Does port knocking require ip-tables? Can it work with UFW?"
date: 2016-09-05
forum: Security
---

### Post by wh33t on 2016-09-05
I'm also curious: does the port stay open while the SSH session is active and then close when the SSH session ends?

---

### Post by HermanAB on 2016-09-08
Note that a Berkeley port is just a number.  There are 65000 of those numbers.

An 'open' port has a listener that reads the datagrams and respond to them.  The SSH Daemon is the program that listens on port 22/TCP.  

So, if sshd is running, then port 22 is open for business, if not, it isn't - simple as that.

---

### Post by kevdog on 2016-10-03
Sorry you didn't get a good answer on this one.  Port knocking I believe in general requires a firewall, since in general that's what a port knocker does -- knocks so a temporary hole in the firewall is opened to allow access.  The port can be later closed, however closing ports doesn't usually knock off active connections, it just doesn't allow new connections.  In general I believe the port knocker server needs to change the firewall automatically when the knock sequence is detected, and then it usually changes the properties of the firewall -- at least temporarily. This is usually done through direct interaction with iptables, although I'm uncertain if any port-knocker implementation could use UFW -- theoretically it could, however I'm doubting one does since the direct interaction with iptables is universal among all linux distributions.  The port knocker implementation I really enjoy is fwknop.  It's pretty complex and the author has been developing it for years.  I won't go into the details right now on why I enjoy this implementation however  it's much more sophisticated than just a simple replayable packet or combination.

---

### Post by ian-weisser on 2016-10-03
I agree with kevdog - use proper port-knocking software.
If you are operating a server listening on the internet, there is a price to pay - a price in security and time and infrastructure and hassle...including the time required to learn iptables properly.
While you can probably write a script or program that uses UFW to listen and react to port-knocking, it seems a lot of unnecessary work.

---

### Post by HermanAB on 2016-10-05
A port is just a number.  It doesn't do anything.  Speaking of an open port is just a figure of speech, meaning that there is an active listener for datagrams with that number in their headers.  Therefore, while sshd is running, it is listening on a port and that port is therefore 'open'.  

However, just to confuse the matter, the netfilter kernel module can route packets between processes and can be configure to forward or drop packets destined to/from a server process based on these numbers.  Therefore, even if sshd is listening to a certain port number, netfilter can be instructed to prevent sshd from receiving anything by dropping the packets on the floor, effectively forcing that port 'closed', but it is really bad style to do that, since it is arguably better to just stop sshd altogether and save the processing cycles.

To further confuse things, the Netfilter kernel module has multiple front-ends, notably iptables, ipchains, ufw, etc. which can all be used to configure what it does.

It is also possible to create iptables rules to implement port knocking by marking packets and counting packets and thereby determining whether to drop packets or not, but that is akin to writing a chess program in the printer language postscript - it has been done, but just as a mental exercise, not because it was particularly useful.

---

### Post by kevdog on 2016-10-05
I'll only speak my piece on port knocking.  Is it essential no.  However it provides a method to dynamically alter the iptables firewall from a remote source.  Honestly it could be more robust than altering a port status, however that's starting to get complex.  Is this dynamic manipulation of the iptables ruleset necessary??? I guess it depends on your needs.  If used, it should be only as one piece of the entire security puzzle.  

In the example above given by HermanAB he spoke about running an sshd behind the firewall.  He spoke about masquerading the listening ssh daemon process behind a firewall whereby you could intercept the packets destined for the firewall and divert them prior to the packet being passed to the ssh server.  In one example he stated it's probably better to stop the sshd altogether to save processing cycles if its not being used.  I agree with this statement to some extent, however there is a problem.  What if you're not sure when you want to use the service.  Meaning you want to use it, but just not all the time.  Unfortunately in the scenario, you'll have to keep it up and running all the time if you want to access the daemon at all.  One method of securing the ssh daemon is by altering the config file to limit it to certain source IP addresses and users, using net filter to limit the connection tries, using the concepts of blacklists with repeated failed attempts at connecting, etc.  You could also change the port the ssh server is run on, change the authentication mechanism of the user -- keys rather than passwords and possibly invoke the PAM module.  Another tool in the shed would to be also to use a port knocker to dynamically packets to be passed to the ssh daemon.   I'm not sure if a port knocker is necessary, however it just represents another method of securing the server.

To answer the original question -- with a port knocker -- no the original port usually doesn't stay open during the entire ssh connection.  The entire discussion focuses on the type of packet -- is it a NEW or INITIAL packet, or is it established.  Depending on how you've set up your firewall, you usually limit initial connections, but allow ongoing established connections.  This falls under the discussion of state tracking rules where you monitor the state of the packet.  This is usually a line like this:
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

With a line like this, usually the original port has been closed to new connections, however the port remains open for established packets.  One example of using a port knocker with ssh for example, would be to open the port for say 30 seconds.  Within the 30 seconds you have to establish communication with the ssh daemon of the packets will be dropped. In this case you would have to resend the port knocking sequence to reopen access to the ssh listening port.

---

