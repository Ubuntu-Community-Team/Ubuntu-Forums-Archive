---
title: "check mark with iptables &amp; redirect the marked ones to a device"
date: 2011-10-23
forum: Server Platforms
---

### Post by smellwing on 2011-10-23
Hello,

I think this is my first post (however I use Ubuntu since 5.04)

Now I got a task:

1.I have 2 ISPs
a. An ISP with static IP, let's call it Vomistar, gw 146.47.200.73 IP 146.47.200.74 and 146.47.200.72 is the network of this isp, I guess
b. An ISP with dinamyc IP, let's call it VTRobo
2.I have an Out-of-the-box UBUNTU 10.04 as router with 3 network cards.
a. eth0 is VTRobo in External zone
b. eth2 is Vomistar in External zone
c. eth3 is my LAN (192.168.2.0/24) in Internal zone
3. IP Masquerading is active, however I have squid working, but stopped.

My Task goal is redirect from LAN to Internet some sites though VTRobo or Vomistar when the destinaton is a known site in a list.

for example: 
If some guy inside LAN checks google.com site, this conection must reach the internet, for default, throught VTRobo conection.
However if this guy check the enterprise web site, the conection must go throught Vomistar, becouse I now the IP of our website and I can recongize the destination.

And... how can I do that? The answer is easy, but the implemetation is hard as cancel SNL from air.

When UBUNTU gets incoming connection from LAN thought eth3, using iptables I can mark the tcp packet if the machine detect certain criteria on it. Before the outside of the tcp packet and the machine detect this mark, then redirect it to Vomistar. If it is there no mark, go to default ISP, VTRobo.

In comands (VTrobo is giving internet for deafault to the machine):
Code:
(As root)
# echo "200 vomistar" >> /etc/iproute2/rt_tables #This add a table
# ip route flush table vomistar
# ip route show table main | grep -Ev ^default \
>   | while read ROUTE ; do
>     ip route add table vomistar $ROUTE
> done #I clone main in vomistar table
# ip route add table vomistar default via 146.47.200.73 # so, I gave the gw number to this conection to make it work
# iptables -i eth3 -t mangle -A PREROUTING -p tcp --dst 69.163.223.20  -s 192.168.2.0/24 -j MARK --set-mark 2 #In prerouting in mangle table, I mark with "2" every thing using tcp protocol that coming from the LAN connected to eth3, when they decide to load a site like [http://www.smellwing.com](http://www.smellwing.com) becouse it has 69.163.223.20 ip
# iptables -t nat -A POSTROUTING -o eth2 -j SNAT --to-source 146.47.200.74  #This make present the vomistar conection in the nat table
# ip rule add fwmark 2 table vomistar #this is the rule to get every tcp transmision marked with "2" go to omistar table
# ip route flush cache
I get all this from [10.4. Multiple Connections to the Internet]("http://linux-ip.net/html/adv-multi-internet.html") and a few other extra thing from differents sites.

So... this didn't work. I think the process is right, but nothing happens. When I go [smellwing.com]("http://www.smellwing.com") I see it from VTRobo conection and no Vomistar.

I Try to use tcpdump And Wireshark to check if the tcp o http packets are marked "2" when I load this site.. but I don't know where to see for that mark. Also if I replace "--dst 69.163.223.20" with "--dport 80" (so every web transmition must go to vomistar) to test the sttings, didn't work either.

My 5 questions:

1.What am I doing wrong?
2 How can I correct it?
3. Where must I see to find the mark "2" on tcpdump?
4. How can I trace all the travel of te packet?
5. can I simplify this with anoter tool?

Thanks for help me!!

pd.:I guess you note my bad redaction and spelling, it is becouse english isn't my strong language, sorry  :(

---

