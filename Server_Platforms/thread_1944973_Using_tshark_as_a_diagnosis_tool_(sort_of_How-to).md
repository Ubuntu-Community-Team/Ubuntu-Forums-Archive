---
title: "Using tshark as a diagnosis tool (sort of How-to)"
date: 2012-03-22
forum: Server Platforms
---

### Post by spynappels on 2012-03-22
Having seen many threads asking why a server cannot be seen from the internet, or why a service is not working as expected when some firewall rules are applied, or why a remote ssh login is not working, I've noticed that a common thread seems to be that the network aspect seems to be poorly understood or discounted very quickly.

This is a pity, as understanding and seeing the network traffic can be a very valuable troubleshooting tool, and can help diagnosis in many cases. This is all the more so when a powerful tool is readily available to help in this troubleshooting and can be used with very little coaching, although the more understanding is applied, the more powerful it becomes.

I'm talking about Wireshark, and more specifically (as we're on a server subforum) T-Shark.

Let me explain what I mean.

In the case that a webserver is not accessible from outside the network, and port forwarding appears to have been enabled, taking a tshark trace on the webserver will allow you to see which element in the chain you need to investigate. 
If you see incoming traffic requesting pages coming from the address of the router, you know that the inbound network path from the client, through the port forwarding on the router to the webserver is ok. 
Not seeing any incoming traffic suggests the problem lies somewhere between the client and the webserver, most commonly in the port used or the port forwarding setup.
If incoming traffic is seen, but no outgoing traffic, it means that the webserver is not processing the requests properly, and the webserver config needs to be investigated.
If both incoming and outgoing traffic are seen at the webserver but the client does not see the webpage, the problem lies somewhere in the outbound network path, and this needs to be investigated. Often this is a sign of incorrectly configured routes on the server or router.
This illustrates that a short (<30sec) tshark trace can narrow the area to troubleshoot considerably!

What makes tshark such a versatile tool? The fact that it has many options which can be used to narrow down the traffic you want to capture mean that it is possible to zero in on the traffic you want and to draw conclusions quickly. However, it can also be used to do much more in-depth analysis.

For example, you can filter and capture only packets to and from a specific IP or MAC address, a specific port or port range, using a specific protocol, and many of these filters can be combined.

Normally, it outputs to stdout, but there are switches which can make it write to a file in standard pcap format. These files can be automatically created and rotated and there is the ability to limit sizes and numbers of these files. You can also control the number of packets you want to capture, making taking small traces very simple without having to worry about filling up disk space.

Both tshark and Wireshark can be used to open previously captured traces saved in pcap format, and carry out further filtering and analysis. However. for the novice Wireshark certainly makes this easier.

So how can you get all this goodness?
```
sudo apt-get install tshark
```

I recommend looking at the man page to get an idea of what it is capable of (also available here [http://linux.die.net/man/1/tshark](http://linux.die.net/man/1/tshark)), but here are a few options to get you started.

You will need to run tshark as sudo to get full access to the network interfaces. The syntax is ```
sudo tshark <options> <filters>
```

Options:

-i   This will allow you to select the interface to capture on. Any interface listed in ifconfig is acceptable, so the following are all accepted interfaces: eth0, lo, tun0 where the 0 is the interface index as seen in ifconfig.

-c   This allows you to specify the number of packets to capture, useful for stopping the outfile becoming too large.

-w   This allows you to specify a file to write the captured packets to. It is good practise to append .pcap or .cap to the end of the filename so an example would be -w /var/tmp/sample_capture.pcap . If no outfile is specified, the captured packets will be written to stdout, normally the console or remote ssh session screen.


Filters: 

host  This allows you to specify a host (IP address or hostname) you want to capture traffic to and from. If traffic capture in one direction only is required you can place src or dst before the host statement like this "src host 10.0.0.1"

port  This allows you to specify a port you want to capture traffic to and from. the src and dst arguments can also be used for this filter. You can further narrow this down by specifying tcp or udp before src or dst if required.

net   Like the examples above, this allows you to filter for an entire network or range of IPs. This can be further tightened by the specification of a netmask.

All the above filters can be negated by putting "not" before them and they can be chained together by using "and|or" links too. So for an example, the filter to capture all telnet traffic not from host 10.0.0.5 would look like this:
```
tcp port 23 and not host 10.0.0.5
```

Adding this to the tshark syntax, to get a trace which has 50 packets in it on a machine which has an IP of 10.0.0.2 on eth0, you'd use the following syntax:
```
sudo tshark -i eth0 -c 50 tcp port 23 and not host 10.0.0.5
``` and to write this trace to the file we referenced above, you'd use
```
sudo tshark -i eth0 -c 50 -w /var/tmp/sample_capture.pcap tcp port 23 and not host 10.0.0.5
```
The resulting file can be transferred to another computer and opened using Wireshark for further analysis.

I will try to add some further examples of practical uses of tshark to diagnose a variety of issues soon.

As ever, comments and additions are gratefully received, it would be nice if this was to become a comprehensive and helpful resource on using tshark and wireshark to troubleshoot server issues. If this needs to be moved, sorry for posting it in the wrong place.

---

### Post by Insomn1a on 2012-03-22
Thank you for the contribution, wireshark and tshark are definitely great tools, it seems not enough people know about them. :)

---

### Post by jonobr on 2012-03-22
Hi There

tcpdump can also be used to create wireshark pcap files using the -w option and can also do that filtering or you can view the results realtime,
I always recommend to folks to use tcpdump as its on there by default and doesn't require installation. This allows people with the "cant ssh from the internet" problem to figure out if the packet is getting there.


Question I have is , (hopefully this question isnt too silly) is there a reason for installing an using tshark over tcpdump?

I know some consider tcpdump a bit too hard core, but as you said, we are in the server section here!


:p

---

### Post by winh8r on 2012-03-22
+1 to **spynappels**

Great intro to a very useful resource.

I didn't know about the "not" options, so I have learned something from it already!

Thanks.:p

---

### Post by spynappels on 2012-03-22
> **jonobr said:**
> Question I have is , (hopefully this question isnt too silly) is there a reason for installing an using tshark over tcpdump?


I guess I started using Wireshark first and then used tshark on headless gui-less systems. The commands and way of working transferred and I learned a powerful new skillset.

A secondary reason I choose tshark by default is that it allows much more in-depth analysis using all the same display filters as Wireshark. This is especially useful where I cannot take the capture files to a workstation running Wireshark.

No reason to not use tcpdump, I'm just more comfortable using tshark.

---

### Post by jonobr on 2012-03-23
Sounds good

Thanks for the response,
rereading my post it sounded like a "gotcha" which it wasn't.

Makes sense to go on using what your comfortable with.
I was thinking that if there was a reason and 'must have' to switch I may consider moving to tshark, but I think Ill stick.

Thanks a mill 

Jonobr

---

