---
title: "tcpdump"
date: 2012-05-16
forum: Security
---

### Post by kabukiM0n0 on 2012-05-16
Hi.
I'm recently getting more and more involved with the terminal as it has some superb abilities. 
After some extensive reading and informing myself of things I didn't really have knowledge about before using Linux. Anyway ... I came across tcpdump, read about it and am interested. I have one problem though . When I run it ... I get this - see image attached. 
I more or less understand what's going wrong, yet I don't know how to put it right. 
I'm **not** looking for someone to tell me how it's done - but was looking to be pointed in the right direction so I can sort it out myself, so I understand what and how to deal with the problem - that is the only way to learn right?

Thanking you'se!

K.m

---

### Post by Soul-Sing on 2012-05-16
Just my little input. Tcpdump comes with a lot of lines/info.(Because you to run it for a while.)
Please gezip the output:

tcpdump.txt gzip tcpdump.txt

parexample:
```
tcpdump -n -i eth0 > tcpdump.txt gzip tcpdump.txt

```

I should go very much into the possibilities of tcpdump or wireshark. They are extrem. complicated progs, with endless possibilities. Another tip: apparmor tcpdump, ubuntu comes with a standard profile, just enable that one for tcpdump.

lots of success!

---

### Post by HermanAB on 2012-05-17
Tcpdump defaults to using eth0, but your ethernet port may be named something else.

Use ifconfig to see what your port names are, then specify the port as a parameter for tcpdump.

---

### Post by unspawn on 2012-05-17
> **leoquant said:**
> I should go very much into the possibilities of tcpdump or wireshark.
Agree. Best save packets with
```
tcpdump -s0 -i eth0 -w /path/to/tcpdump.pcap
```
and load that capture later on in Wireshark for analysis. Beware to kill the process in time or set a file size limit or your file system will be filled. Wireshark allows you to apply filters to traffic with which you for instance can single out RFC 793 handshake states like SYN or CLOSE_WAIT or ports or addresses, follow traffic streams between addresses, extract payloads and much more. 
I wouldn't say it's "extremely complicated" but like all tools it does have a learning curve. 

There's also command line tools you can analyze traffic with. Here's some capinfos, tcpstat, tcptrace and snort commands I use:

Get file and capture specs like file size, amount of packets, data rate:
```
capinfos /path/to/tcpdump.pcap
```

Generate traffic rate stats (if you're say looking for spikes):
```
tcpstat -l -o "Time:%S\tPkt_tot=%n\tPkt_ps=%p\tPkt_avg_sz=%a\tbps=%b\n" -r /path/to/tcpdump.pcap
```

Dissect traffic into IP and TCP components:
```
tcpstat -l -o "Time:%S\tIPv4_nr=%I\tIPv6_nr=%V\tTCP_nr=%T\tUDP_nr=%U\tICMP_nr=%C\n" -r /path/to/tcpdump.pcap
```

Extract payload (TCP only):
```
tcptrace -e -n /path/to/tcpdump.pcap
```
(or use tcpflow or 'tcpxtract -f /path/to/tcpdump.pcap -o /path/to/existing/directoryname'.)

Quick plain text IDS alert generation:
```
snort -A fast -c ./snort.conf.prep -k all -K none -U -l $PWD -r /path/to/tcpdump.pcap
```
(best with current Snort or Emerging Threats rule sets or create your own.)

//Also see [http://www.forensicswiki.org/wiki/Network_forensics](http://www.forensicswiki.org/wiki/Network_forensics)

---

### Post by The Cog on 2012-05-17
As HermanAB says: 
> Tcpdump defaults to using eth0, but your ethernet port may be named something else.

Use ifconfig to see what your port names are, then specify the port as a parameter for tcpdump.
ifconfig will list all your interfaces and tell you their ip addreses. If you're on a laptop you may well be using interface wlan0 rather than eth0, so your command would be:
> sudo tcpdump -i wlan0

---

### Post by kabukiM0n0 on 2012-05-20
Excellent! thank you very much.  :D

K.m

---

### Post by spynappels on 2012-05-23
You can also use tshark (from the Wireshark suite) and this may give some more options when decoding.

Have a look here for some tips:
[http://ubuntuforums.org/showthread.php?t=1944973](http://ubuntuforums.org/showthread.php?t=1944973)

Regards,
Stefan

---

### Post by SparTacux on 2012-05-23
Great Posts Guys.

Don't forget  apparmor on tcpdump :-)
It seems some bogeymen can intercept traffic and modify it on the fly.

---

### Post by SparTacux on 2012-06-04
Those tcpdump commands worked a treat - especially using wireshark to view the pcap files created by tcpdump :-)

tcpdump -s0 -i eth0 -w /path/to/tcpdump.pcap

I put a script file in the /etc/network/if-up.d folder to run tcpdump on bootup. It seems to work ok. Tcpdump appears to write to the new capture file every 4K of data it captures. If the network is disconnected then reconnected then the same capture file is continually appended to. A reboot of the computer deletes the capture file and creates a new one with zero bytes and the process starts all over again. 

 Is there a way to rotate the capture file so I can save network data for a period of a week or so?

Also if tcpdump has a vulnerabilty to malformed packets wouldn't it lose 4K of file data if it crashed before it had chance to write to the capture file? I also take it tcpdump run from the if-up-d folder would be running as root user and could compromise the system if not using apparmor.

---

### Post by Doug S on 2012-06-04
> 
Is there a way to rotate the capture file so I can save network data for a period of a week or so?
Yes, tcpdump can be set to change the output file periodically. I change the file every 10 minutes (I often look at the files via wireshark from another computer, so 10 minutes keeps the file size manageble.) Examples (eth1 is external, eth0 is internal):```
sudo tcpdump -i eth1 -w 'eth1-%F-%H-%M-%S.bin' -G 600
sudo tcpdump -i eth0 not port 22 and not port 139 and not port 445 -w 'eth0-%F-%H-%M-%S.bin' -G 600
``` You can also add post-processing, Example:```
sudo tcpdump -i eth1 -w 'eth1-%F-%H-%M-%S.bin' -G 600 -z /home/doug/scripts/packet_post_processor
```Note that you will need to make an apparmor rule to allow what I have shown. Note also and [older bug ]("https://bugs.launchpad.net/ubuntu/+source/tcpdump/+bug/722856")(now fixed, but maybe not on 10.04) with apparmor and the -z option.
> Also if tcpdump has a vulnerabilty to malformed packets wouldn't it lose 4K of file data if it crashed before it had chance to write to the capture file?If you are worried about it use the -U option for packet-buffered output rather than only for each buffer full.

---

### Post by SparTacux on 2012-06-05
> **Doug S said:**
> Yes, tcpdump can be set to change the output file periodically. I change the file every 10 minutes (I often look at the files via wireshark from another computer, so 10 minutes keeps the file size manageble.) Examples (eth1 is external, eth0 is internal):```
sudo tcpdump -i eth1 -w 'eth1-%F-%H-%M-%S.bin' -G 600
sudo tcpdump -i eth0 not port 22 and not port 139 and not port 445 -w 'eth0-%F-%H-%M-%S.bin' -G 600
``` You can also add post-processing, Example:```
sudo tcpdump -i eth1 -w 'eth1-%F-%H-%M-%S.bin' -G 600 -z /home/doug/scripts/packet_post_processor
```Note that you will need to make an apparmor rule to allow what I have shown. Note also and [older bug ]("https://bugs.launchpad.net/ubuntu/+source/tcpdump/+bug/722856")(now fixed, but maybe not on 10.04) with apparmor and the -z option.
If you are worried about it use the -U option for packet-buffered output rather than only for each buffer full.

Thanks Doug S

I got the -U option :-)

I couldn't get those filename format strings to work though. I tried running tcpdump from terminal with those lines and the file created was named "capture-%F-%H-%M-%S.pcap" using capture instead of 'eth0' as you used. I was playing around with the format of those lines and couldn't get the file created to display date and time details in the filename as you suggested. I'm doing something wrong here but don't know what.

---

### Post by Doug S on 2012-06-05
I guess that you don't have strftime installed. You can check via:```
man strftime
```I did not realize that strftime is not installed by default. I have 3 ubtuntu computers, one for real stuff and two for testing. The one without the c compiler doesn't have the strftime function available, and on that computer the file name formatting does not work.

---

### Post by SparTacux on 2012-06-05
> **Doug S said:**
> I guess that you don't have strftime installed. You can check via:```
man strftime
```I did not realize that strftime is not installed by default. I have 3 ubtuntu computers, one for real stuff and two for testing. The one without the c compiler doesn't have the strftime function available, and on that computer the file name formatting does not work.

I think the problem was me but did get it to work with a few tweaks to the command line:

sudo tcpdump -s0 -w capture-$(date +%a-%d%m%y-%H%M-%S).pcap

That worked. The file created looked something like this:
capture-mon-050612-0920-43.pcap

I could have used -C 50 to create a new file every 50MEG captured. I created a shell script file in if-up.d to run tcpdump on boot up using the above line. It worked EXCEPT for some weird reason it's creating two capture files and writing to both of them !!  One of the files was created about two seconds after the first one and both get the same network data written to them.

I need a barrel of beer !

---

