---
title: "Unknown IP Uploads"
date: 2012-02-28
forum: Security
---

### Post by CaptainofCrunch on 2012-02-28
Hi

I have  noticed over the past 2 months that my computer has been uploading  at high speeds of around 300-400 KBs when there is no programs running in the background that should be causing this.

I used Nethogs about a week ago and the results I got from that when I noticed that I was uploading was strange.

The first time it was chromium that was uploading. Then a couple of IP addresses.

72.21.194.22 which belongs to s3.amazonaws.com which is a cloud storage site run by Amazon.

72.52.7.84 which belongs to prolexic.com which is "Prolexic is the world's largest and most trusted Distributed Denial of Service (DDoS) mitigation provider"

and 

72.21.194.22 which again is from s3.amazonaws.com

Does anybody know why this is happening? Any help at all would be much appreciated.

Thank You.

---

### Post by kevdog on 2012-02-28
I have no idea, could be a background process.  Its possible to block these specific ip addresses using a firewall.  That's what I would do.

---

### Post by CaptainofCrunch on 2012-02-28
> **kevdog said:**
> I have no idea, could be a background process.  Its possible to block these specific ip addresses using a firewall.  That's what I would do.

Honestly I don't know. If somebody can help me with that I can give it a try.

There are more IP's though, they aren't using as much bandwidth but they are still uploading something.

209.85.143.136 - google.com (markmonitor.com -Brand protection, domain name management, domain registration, and anti fraud solutions.)

74.207.237.212 - linode.com (cloud storage)

95.172.94.18 
95.172.94.40 - both of these are from ripe.net (The RIPE NCC is one of five Regional Internet Registries (RIRs) providing Internet resource allocations, registration services and coordination activities that support the operation of the Internet globally.)

50.172.234.194 - ec2.amazonaws.com (amazon cloud storage)

64.215.255.89 - arin.net (American Registry for Internet Numbers)


Theres more but I haven't check who they are yet.

---

### Post by kevdog on 2012-02-28
The best thing to do is to just start blocking them incrementally.  You are never going to do it all in one sweep.  Block a few, look at the logs, block a few more, look at the logs, etc.

I've got to run right now, but later I'll post a basic script file you can use to configure your iptables against the offending addresses.  There are multiple ways to do this, however I'd recommend a script file since iptables needs to be repopulated after every boot.

---

### Post by CaptainofCrunch on 2012-02-28
> **kevdog said:**
> The best thing to do is to just start blocking them incrementally.  You are never going to do it all in one sweep.  Block a few, look at the logs, block a few more, look at the logs, etc.

I've got to run right now, but later I'll post a basic script file you can use to configure your iptables against the offending addresses.  There are multiple ways to do this, however I'd recommend a script file since iptables needs to be repopulated after every boot.

Excellent thank you very much

---

### Post by cariboo on 2012-02-28
The connection to the Amazon servers, is because you have Ubuntu One enabled, the Google connection is probably because you have a gmail or other account with Google, and you don't sign out from it before shutting down. The others may have something to do with the DNS servers your ISP uses.

---

### Post by unspawn on 2012-02-29
...and to determine whats actually going on just run tcpdump to capture packets and then analyze traffic in say Wireshark.

---

### Post by CaptainofCrunch on 2012-02-29
> **cariboo907 said:**
> The connection to the Amazon servers, is because you have Ubuntu One enabled, the Google connection is probably because you have a gmail or other account with Google, and you don't sign out from it before shutting down. The others may have something to do with the DNS servers your ISP uses.

when I run Ubuntu One the only results that come up in Nethogs are python and something else. I took a screen shot I'll attach it below.

As for Google I don't have an email client set up on this computer, so the only way it would be doing that would be through Chromium at I had it closed at the time. 

Its the speed that made me notice. My connections is only 0.4Mb/s so its basically using up all my bandwidth.

---

### Post by CaptainofCrunch on 2012-02-29
> **unspawn said:**
> ...and to determine whats actually going on just run tcpdump to capture packets and then analyze traffic in say Wireshark.

I did run Wireshark once when I noticed it, but to be honest I don't understand most of the stuff it say.

---

### Post by unspawn on 2012-02-29
> **CaptainofCrunch said:**
> I did run Wireshark once when I noticed it, but to be honest I don't understand most of the stuff it say.
Couple of ways about it: 0) learn about it (bit steep learning curve maybe ;-p) [here]("http://www.tcpipguide.com/content.htm") or [here]("http://www.learntcpip.com/") and [here]("http://www.danielmiessler.com/study/tcpdump/") and maybe check [here]("http://web.archive.org/web/20091203085657/http://www.private.org.il/tcpip_rl.html") (archive.org copy) if you can't get enough of that stuff or 1) ask specific questions or else 2) share the pcap for others to analyze. 
* In case of the latter you may want to [obfuscate]("http://scrub-tcpdump.sourceforge.net/docs.php") your IP address and scrub certain types of traffic (logins, cookies, destinations).

** Wrt your screen shot: running nethogs gives you process Ids. These PIDs you can then run through 'lsof' for more clues. For example running 'sudo lsof -Pwlnp 2085' should get you the process details from the second one listed in your screen shot. The caveat is the process has to be running, you can't do it afterwards.

---

### Post by CaptainofCrunch on 2012-02-29
> **unspawn said:**
> Couple of ways about it: 0) learn about it (bit steep learning curve maybe ;-p) [here]("http://www.tcpipguide.com/content.htm") or [here]("http://www.learntcpip.com/") and [here]("http://www.danielmiessler.com/study/tcpdump/") and maybe check [here]("http://web.archive.org/web/20091203085657/http://www.private.org.il/tcpip_rl.html") (archive.org copy) if you can't get enough of that stuff or 1) ask specific questions or else 2) share the pcap for others to analyze. 
* In case of the latter you may want to [obfuscate]("http://scrub-tcpdump.sourceforge.net/docs.php") your IP address and scrub certain types of traffic (logins, cookies, destinations).

** Wrt your screen shot: running nethogs gives you process Ids. These PIDs you can then run through 'lsof' for more clues. For example running 'sudo lsof -Pwlnp 2085' should get you the process details from the second one listed in your screen shot. The caveat is the process has to be running, you can't do it afterwards.

I will have a read over all that stuff, thank you.

---

### Post by kevdog on 2012-02-29
Here's a very simple script to do want you want.  I named it iptables.sh.  Please note that I usually set the default packet policy on firewalls as drop, but in this case I kept it ACCEPT since I only wanted to block OUTPUT from certain IPs:

IPTABLES=/sbin/iptables
LOGLIMIT="2/s"
LOGLIMITBURST=10

function clean() {

echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t mangle
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -X -t mangle
$IPTABLES -X -t nat

$IPTABLES -P INPUT ACCEPT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT
$IP6TABLES -P INPUT ACCEPT
$IP6TABLES -P OUTPUT ACCEPT
$IP6TABLES -P FORWARD ACCEPT

}


### flush existing rules and set chain policy setting to DROP

function Default_Policies() {

#Default Policies
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT

### this policy does not handle IPv6 traffic except to drop it.
$IP6TABLES -P INPUT DROP
$IP6TABLES -P OUTPUT DROP
$IP6TABLES -P FORWARD DROP

}



function firewall() {

###### OUTPUT chain ######
#
echo "[+] Setting up OUTPUT chain..."

BlockedIPs=( IPADDRESS1 IPADDRESS2 IPADDRESS3 )  #Spaces are important after and before ()

$IPTABLES -N LOGDROP
$IPTABLES -A LOGDROP -j LOG -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST --log-prefix "DROP OUT- " --log-ip-options --log-tcp-options
$IPTABLES -A LOGDROP -j DROP

for ip in "${BlockedIPs[@]}"
do
     $IPTABLES -A OUTPUT -d ${ip} -j LOGDROP
done
}

case "$1" in
   stop)
      echo "Shutting down firewall..."
      clean
      echo "...done"
      ;;
   status)
      echo $"Table: filter"
      iptables --list
      echo $"Table: nat"
      iptables -t nat --list
      echo $"Table: mangle"
      iptables -t mangle --list
      ;;
   restart|reload)
      $0 stop
      $0 start
      ;;
   start)
    echo "Starting Firewall..."
      clean 
      Default_Policies
      firewall
      ;;
    *)
      echo "Usage iptables.sh { start | stop | restart | status }"
      exit 1
      ;;
esac

exit
### EOF ###

---

### Post by CaptainofCrunch on 2012-02-29
> **kevdog said:**
> 
BlockedIPs=( IPADDRESS1 IPADDRESS2 IPADDRESS3 )  #Spaces are important after and before ()

Do I only need to change the above live and insert the IP's I want to block instead of 'IPADDRESS1 IPADDRESS2 IPADDRESS3'? 

Do I leave only spaces, no commas or full stops between each IP? 

Is there a limit to how many IP's I can put into that line?

And where do I put this file and how do I run it?

---

### Post by kevdog on 2012-02-29
Sorry I didn't give instructions.  There are other ways to do what I am proposing, so I don't want to tell you there is this way, and thats it.  What I'm doing is creating an array of IP values.  So yes you would put an IP address substituting for where I put IPADDRESS1.  There is no limit to the number of IP addresses you want to add.  

Save the file as iptables.sh and make sure the ownership is root and the group is root.  I usually save the file in /usr/local/sbin.  (That's just me however). 

If you want to run the file it would be:
sudo /usr/local/sbin/iptables.sh start

or 
sudo /usr/local/sbin/iptables.sh stop

or
sudo /usr/local/sbin/iptables.sh status

or 
sudo /usr/local/sbin/iptables.sh restart 

I believe /usr/local/sbin should be in your path so I don't think you have to type the full path (I think).  

Try it -- see if it works.  The blocked IP address are logged, so you could look at your syslog to confirm the IP addresses are getting blocked.  You can always elect to not log the dropped IP addresses at another time.

That's about all I know.

---

### Post by Dangertux on 2012-02-29
It might be important to add that blocking Amazon aws will likely break most websites you visit, well not most but probably a decent enough amount tp not be worth it.

---

### Post by kevdog on 2012-02-29
> **Dangertux said:**
> It might be important to add that blocking Amazon aws will likely break most websites you visit, well not most but probably a decent enough amount tp not be worth it.

I don't really follow this?  I don't have the problem discussed in this thread.  Amazon aws are that prevalent to actually make a difference?

---

### Post by Dangertux on 2012-02-29
Alot of sites use aws to host at least a portion of their content. I suppose as long as you only block some vps ips it wont be that bad. But if you hit a tld or load balancer it might cause issues.

---

