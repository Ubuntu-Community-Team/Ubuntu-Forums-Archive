---
title: "Sendmail &amp; iptables/netfilter rules (Sending mail)"
date: 2010-10-08
forum: Server Platforms
---

### Post by metcarob on 2010-10-08
Hi,
I have an ubuntu server virtual machine with a webhost. I am trying to configure the firewall. I am having a problem with sendmail and the required firewall configuraiton

If I type the command:
iptables -F

Then sendmail works perfectly. I can see the emails sent in my googlemail inbox.

I then configure my firewall as follows:
iptables -F
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -p tcp --dport 2252 -j ACCEPT
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -p icmp -s 195.194.62.10 -j ACCEPT
iptables -A INPUT -p icmp -s 89.200.136.76 -j ACCEPT
iptables -A INPUT -p icmp -s 89.200.136.31 -j ACCEPT
iptables -A INPUT -j DROP

(I have moved SSH to a diffrent port)

Once this is setup sendmail no longer works.
I had assumed that sendmail will establish a tcp connection and the first rule will allow all established connections to pass.

Can anyone suggest why this iptables/netfilter config stops sendmail from working.
Thanks
Robert

---

### Post by SeijiSensei on 2010-10-08
If the problem is sending out mail, we need to see the OUTPUT rules as well.  How about posting the result of "sudo iptables -L -nv"?

---

### Post by metcarob on 2010-10-08
Hi,
I do not have any output rules at all and the default output is accept.
My best guess at what is happening is the sendmail is sending something out and expecting a response which is getting blocked by the input rules.
Robert

---

### Post by metcarob on 2010-10-08
Hi,
I have done some more tests and I have output the terminal results below.
I have noticed that the options you gave me display byte counts. 
I have run iptables -L -nv, then I tried to send an email then I ran iptables -L -nv again.
I can see that OUTPUT bytes goes from 60037 to to 60044

The final DROP all rule on my input chain goes from 1524 to 1890.
Now this could be normal internet background traffic or it could be to do with the test.

The bytes next to my accept rule goes from 11528 to 12088. So in that period something got through.  (It wasn't the SSH that goes to a diffrent rule)

After analysising the results I ran iptables -F and tried to send an email. This arrived in my googlemail account in seconds.

The detail of my test is below, any help would be apriciated:
Robert


[FONT=Courier New]root@metcaac1:~# iptables -L -nv
Chain INPUT (policy ACCEPT 4467 packets, 524K bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
  149 11528 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:2252
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443
    0     0 ACCEPT     icmp --  *      *       195.194.62.10        0.0.0.0/0
    0     0 ACCEPT     icmp --  *      *       89.200.136.76        0.0.0.0/0
    3   252 ACCEPT     icmp --  *      *       89.200.136.31        0.0.0.0/0
   16  1524 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)[/FONT] [FONT=Courier New]
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 60037 packets, 54M bytes)[/FONT] [FONT=Courier New]
 pkts bytes target     prot opt in     out     source               destination
root@metcaac1:~# ./test_sendmail.sh
root@metcaac1:~# iptables -L -nv
Chain INPUT (policy ACCEPT 4467 packets, 524K bytes)
 pkts bytes target     prot opt in     out     source               destination
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0
  157 12088 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:2252
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:80
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:443
    0     0 ACCEPT     icmp --  *      *       195.194.62.10        0.0.0.0/0
    0     0 ACCEPT     icmp --  *      *       89.200.136.76        0.0.0.0/0
    3   252 ACCEPT     icmp --  *      *       89.200.136.31        0.0.0.0/0
   18  1890 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0[/FONT]

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 60044 packets, 54M bytes)
 pkts bytes target     prot opt in     out     source               destination

---

### Post by SeijiSensei on 2010-10-08
I think the rule to accept return traffic is wrong. On my machines it reads:

iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

You'll notice that your rule for ESTABLISHED,RELATED doesn't appear in the output from 'iptables -L -nv'.

---

### Post by metcarob on 2010-10-09
Hi,
Thanks very much you have solved the problem. It was the diffrence between -m conntrack and -m state.
I don't remember which website suggested the -m conntrack.
Thanks again
Robert

---

