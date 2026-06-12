---
title: "gufw - where are the rules stored?"
date: 2011-03-16
forum: Security
---

### Post by Hadeda on 2011-03-16
I wish to copy the many firewall rules from an existing configuration to many new computers - instead of spending hours entering them manually.

Does anyone know where the gufw rules are stored?

Thanks!

---

### Post by marquinos on 2011-03-16
Hi! The rules are get from ufw ;)
The rules in some files:
[http://serverfault.com/questions/198398/ubuntu-how-to-add-an-iptables-rule-that-ufw-cant-create](http://serverfault.com/questions/198398/ubuntu-how-to-add-an-iptables-rule-that-ufw-cant-create)
But I think that copy & paste will not work.
Best regards.

---

### Post by Hadeda on 2011-03-16
I found the   *after.rules*   file in * /etc/ufw/after.rules

1) I don't know how to open and edit after.rules. Any suggestions?

2) As they have old file dates, I am not sure if these are the files I need  to achieve my objective as stated above. What do you think?

Thanks!

---

### Post by gordintoronto on 2011-03-16
You would need to change the owner before you can access before.rules and after.rules. For user "gord," here goes:

cd /etc/ufw
sudo chown gord before.rules
sudo cp before.rules first.txt
sudo chown root before.rules
sudo chown gord first.txt
cp first.txt some.other.place
(Or you can copy it using Nautilus)
sudo rm first.txt

You might need to shut down the firewall before you can do it. If you copy the file onto another computer, I think you will need to do it while the firewall is not running.

There are several other files also used by ufw, and they seem to move around from version to version.

---

### Post by cariboo on 2011-03-16
Wouldn't it just be easier to use sudo? Press Alt-F2 and type:

```
gksu gedit /etc/ufw/before.rules
```

then use save-as to give it a different name.

---

### Post by gordintoronto on 2011-03-16
> **cariboo907 said:**
> Wouldn't it just be easier to use sudo? Press Alt-F2 and type:

```
gksu gedit /etc/ufw/before.rules
```

then use save-as to give it a different name.

Far out!  I thought it would fail due to ownership rules.

Ah, the saved file is still owned by root, so you need to chown it.

---

### Post by Hadeda on 2011-03-18
Thanks! Having opened the files, above does not solve my problem.

The before.rules do not contain the ACTUAL fw rules I need to copy, such as blocking specific IP addresses and ports 23456 and 1900 (2 of many examples).

Where would I find those rules?
Many thanks

---

### Post by cariboo on 2011-03-18
You can list the rules by using the following command:

```
sudo iptables -L
```

to get a listing in a text file you can pipe the output of the above command to a test file:

```
sudo iptables -L > iptables_rules.txt
```

---

### Post by Hadeda on 2011-03-20
Thanks cariboo!

I piped the test file iptables_rules.txt and it contains the data I am looking for  =D>

BUT, how do I get this data to my other, newly to be installed computers without copying it manually?
I did not find a file 'iptables'.

Perhaps my question is: Where must I 'paste' this data into the newly to be installed computers?
Thanks!

---

### Post by snek on 2011-10-28
I recommend you read this great howto from SliceHost.
They host VPS's and have great articles on how to set them up.
Mind you, it's all through command-line, but the tutorial is well documenten and easy to follow:
[http://articles.slicehost.com/2010/10/18/ubuntu-maverick-setup-part-1](http://articles.slicehost.com/2010/10/18/ubuntu-maverick-setup-part-1)

You will want to skip down to the section IPTABLES.

It will explain how to save your current iptables and how to setup ubuntu so it loads them again at boot.
Mind you I am not sure how compatible this is with UFW...

---

### Post by JKyleOKC on 2011-10-30
> **snek said:**
> Mind you I am not sure how compatible this is with UFW...UFW and gufw are simply front ends to create the iptables rules, and once the rules are in place the UFW programs are simply excess baggage.

You can save the entire set of iptables rules from your master installation with ```
sudo iptables-save >/home/youruser/iptables.rules
```You can then view or edit the iptables.rules file with any text editor (don't use a word processor, though), and you can copy the file to any other system -- even one using a different distro or a different version of the kernel.

To load the saved rules into a system at boot time, copy that file into /etc/iptables.rules and add this line into /etc/rc.local just ahead of the existing "exit 0" line: ```
/sbin/iptables-restore </etc/iptables.rules
```You can run this command manually using sudo to install without having to restart the system. And you don't need to install either UFW or gufw into that system to make things work. In fact, they simply offer a way for tinkerers to make things QUIT working!

It's actually just that simple. The things to watch out for are local ip addresses that may be different from one system to another and be embedded in some rules, but such situations are pretty rare...

---

### Post by Thewhistlingwind on 2011-10-31
Wrong approach. Do what you want to do in plain UFW or IPtables, and make it a shell script.

Of course, the above post is a good alternate method.

---

### Post by Hadeda on 2012-01-07
Thanks for your response! 

My silence is due to the fact that I couldn't get things to work as you suggested and other priorities distracted me...

I am still at a level where I don't know how to write a shell script, if that is the answer.

The main issue is that 
"copy that file into /etc/iptables.rules" 
does not work after I created iptables.rules through gedit as you suggested, Jim.

How can I get iptables.rules into the /etc folder?

Thanks!

---

### Post by JKyleOKC on 2012-01-07
> **Hadeda said:**
> I am still at a level where I don't know how to write a shell script, if that is the answer.Using a shell script is the long way around and will delay the boot process slightly.> **Hadeda said:**
> 
The main issue is that "copy that file into /etc/iptables.rules" does not work after I created iptables.rules through gedit as you suggested, Jim.

How can I get iptables.rules into the /etc folder?Try copying this and pasting it into a terminal window:```
sudo cp $HOME/iptables.rules /etc/iptables.rules
```The $HOME will automatically reference your home directory, and the sudo will allow you to copy the file into /etc. Sudo will ask for your login password, and won't show any indication that it's accepting your typing although it really is. You should get another terminal prompt almost immediately if everything has gone right.

You'll also need "gksudo " in front of "gedit" when adding the line to /etc/rc.local as I suggested previously. To gain root privilege for a single command, use "sudo" when launching a CLI app in terminal mode, and "gksudo" when launching a GUI app from the terminal. The difference is small, but can be critical in some cases. Strangely, gksudo will echo your password keystrokes although sudo does not.

---

### Post by Hadeda on 2012-01-08
Thanks, everything you suggested now works!

But...
There appear to be 2 iptables somehow:

The firewall was initially configured through GUFW.
The problem is that I do not see some basic rules I added such as blocking port 1900 (as an example) in iptables.rules created through the method you suggested.

Then, as a test and when not connected to anything, I disabled and immediately enabled the FW again using the tick box in the GUFW interface.

Then, when invoking code
sudo iptables -L
all of the rules I programmed (and a lot more which I do not yet understand) appear.

This does not make sense.

It might be of importance to mention that this is a rebuild as a result of  IP spoofing and router flooding - which might or might not be a different issue for the security forum.

Any feedback is welcome. Thanks

---

### Post by JKyleOKC on 2012-01-08
If you leave GUFW enabled, it will be fighting with your added rules and possibly nothing will work right. If you can post your /etc/iptables.rules file here (block out any IPs that you don't want to make public and be sure to surround it with the "code" tags via the "#" icon in the message editor) we can tell you what its content is doing. However GUFW might flush all of your rules out if it's started later in the boot process. The general rule is to run only **one** firewall package, just as for AV programs in Windows. With more than one, interference between them is quite likely.

If you had GUFW enabled when you ran the iptables-save program to create your iptables.rules file, all of its actions will be included in those rules. Consequently you can disable it, and prevent it from running at startup, since your loading of the rules via /etc/rc.local will put those rules back into effect.

EDIT: As for having "two iptables" there are actually a number of different filter routes in the kernel's netfilter package. When you do the "iptables -L" you should get all of them reported by default. Each route is called a "chain" in the iptables terminology, and by default you have three chains: INPUT, FORWARD, and OUTPUT. UFW and GUFW create additional chains, and they will also be listed. INPUT handles incoming packets destined for the current machine, FORWARD deals with packets (both incoming and outgoing) destined for other machines on your LAN if you have one, and OUTPUT handles outgoing packets from the current machine. If your iptables.rules file and the output from "iptables -L" differ significantly, post them both for us to examine.

---

### Post by Hadeda on 2012-01-09
Jim, I am grateful that you explained some basics and offered to check the IP tables. 

For easier reading I have attached the one after booting the computer and after following your instructions in the next post and hope that you find some flaws in the printout.

FYI, There is no LAN, no server and no shared printer, only 2 'stand alone' computers plugged into a router.


Just to make sure that I am on the right page, here is a simple question based on a simple situation:

When you build a brand new system and never touch firestarter nor GUFW, what should iptables.rules look like when using your suggested procedure?

At my level I prefer using GUFW which I thought was simply a *user interface to iptables* and not a separate 'firewall package' which could fight with the kernel rules.

---

### Post by Hadeda on 2012-01-09
IPTABLES after re-boot and after using Jim Kyle's method to create iptables.rules


  
 DNS =  8.8.8.8  8.8.4.4  207.69.188.186
 computer address =  192.168.1.1xx
   
 

 user@user:~$ sudo iptables -L 
 [sudo] password for user:  
 

 Chain INPUT (policy DROP) 
 target     prot opt source               destination          
 ACCEPT     tcp  --  8.8.8.8              anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN  
 ACCEPT     udp  --  8.8.8.8              anywhere             
 ACCEPT     tcp  --  8.8.4.4              anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN  
 ACCEPT     udp  --  8.8.4.4              anywhere             
 ACCEPT     tcp  --  207.69.188.186       anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN  
 ACCEPT     udp  --  207.69.188.186       anywhere             
 ACCEPT     all  --  anywhere             anywhere             
 LSI        udp  --  anywhere             anywhere            udp dpt:33434  
 LSI        icmp --  anywhere             anywhere             
 NR         all  -- !192.168.1.0/24       anywhere             
 DROP       all  --  anywhere             255.255.255.255      
 DROP       all  --  anywhere             192.168.1.255        
 DROP       all  --  224.0.0.0/8          anywhere             
 DROP       all  --  anywhere             224.0.0.0/8          
 DROP       all  --  255.255.255.255      anywhere             
 DROP       all  --  anywhere             0.0.0.0              
 DROP       all  --  anywhere             anywhere            state INVALID  
 LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5  
 INBOUND    all  --  anywhere             anywhere             
 LOG_FILTER  all  --  anywhere             anywhere             
 LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'  
  
 Chain FORWARD (policy DROP) 
 target     prot opt source               destination          
 LSI        udp  --  anywhere             anywhere            udp dpt:33434  
 LSI        icmp --  anywhere             anywhere             
 LOG_FILTER  all  --  anywhere             anywhere             
 LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'  
  
 Chain OUTPUT (policy DROP) 
 target     prot opt source               destination          
 ACCEPT     tcp  --  192.168.1.1xx        8.8.8.8             tcp dpt:domain  
 ACCEPT     udp  --  192.168.1.1xx        8.8.8.8             udp dpt:domain  
 ACCEPT     tcp  --  192.168.1.1xx        8.8.4.4             tcp dpt:domain  
 ACCEPT     udp  --  192.168.1.1xx        8.8.4.4             udp dpt:domain  
 ACCEPT     tcp  --  192.168.1.1xx        207.69.188.186      tcp dpt:domain  
 ACCEPT     udp  --  192.168.1.1xx        207.69.188.186      udp dpt:domain  
 ACCEPT     all  --  anywhere             anywhere             
 DROP       all  --  224.0.0.0/8          anywhere             
 DROP       all  --  anywhere             224.0.0.0/8          
 DROP       all  --  255.255.255.255      anywhere             
 DROP       all  --  anywhere             0.0.0.0              
 DROP       all  --  anywhere             anywhere            state INVALID  
 OUTBOUND   all  --  anywhere             anywhere             
 LOG_FILTER  all  --  anywhere             anywhere             
 LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'  
  
 Chain INBOUND (1 references) 
 target     prot opt source               destination          
 ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED  
 ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED  
 LSI        all  --  anywhere             anywhere             
  
 Chain LOG_FILTER (5 references) 
 target     prot opt source               destination          
  
 Chain LSI (54 references) 
 target     prot opt source               destination          
 LOG_FILTER  all  --  anywhere             anywhere             
 LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '  
 DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN  
 LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '  
 DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST  
 LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '  
 DROP       icmp --  anywhere             anywhere            icmp echo-request  
 LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '  
 DROP       all  --  anywhere             anywhere             
  
 Chain LSO (0 references) 
 target     prot opt source               destination          
 LOG_FILTER  all  --  anywhere             anywhere             
 LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '  
 REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable  
  
 Chain NR (1 references) 
 target     prot opt source               destination          
 LSI        all  --  0.0.0.0/8            192.168.1.0/24       
 LSI        all  --  1.0.0.0/8            192.168.1.0/24       
 LSI        all  --  2.0.0.0/8            192.168.1.0/24       
 LSI        all  --  5.0.0.0/8            192.168.1.0/24       
 LSI        all  --  10.0.0.0/8           192.168.1.0/24       
 LSI        all  --  14.0.0.0/8           192.168.1.0/24       
 LSI        all  --  23.0.0.0/8           192.168.1.0/24       
 LSI        all  --  27.0.0.0/8           192.168.1.0/24       
 LSI        all  --  31.0.0.0/8           192.168.1.0/24       
 LSI        all  --  36.0.0.0/8           192.168.1.0/24       
 LSI        all  --  37.0.0.0/8           192.168.1.0/24       
 LSI        all  --  39.0.0.0/8           192.168.1.0/24       
 LSI        all  --  42.0.0.0/8           192.168.1.0/24       
 LSI        all  --  46.0.0.0/8           192.168.1.0/24       
 LSI        all  --  49.0.0.0/8           192.168.1.0/24       
 LSI        all  --  50.0.0.0/8           192.168.1.0/24       
 LSI        all  --  100.0.0.0/8          192.168.1.0/24       
 LSI        all  --  101.0.0.0/8          192.168.1.0/24       
 LSI        all  --  102.0.0.0/8          192.168.1.0/24       
 LSI        all  --  103.0.0.0/8          192.168.1.0/24       
 LSI        all  --  104.0.0.0/8          192.168.1.0/24       
 LSI        all  --  105.0.0.0/8          192.168.1.0/24       
 LSI        all  --  106.0.0.0/8          192.168.1.0/24       
 LSI        all  --  107.0.0.0/8          192.168.1.0/24       
 LSI        all  --  108.0.0.0/8          192.168.1.0/24       
 LSI        all  --  109.0.0.0/8          192.168.1.0/24       
 LSI        all  --  110.0.0.0/8          192.168.1.0/24       
 LSI        all  --  111.0.0.0/8          192.168.1.0/24       
 LSI        all  --  127.0.0.0/8          192.168.1.0/24       
 LSI        all  --  link-local/16        192.168.1.0/24       
 LSI        all  --  172.16.0.0/12        192.168.1.0/24       
 LSI        all  --  175.0.0.0/8          192.168.1.0/24       
 LSI        all  --  176.0.0.0/8          192.168.1.0/24       
 LSI        all  --  177.0.0.0/8          192.168.1.0/24       
 LSI        all  --  178.0.0.0/8          192.168.1.0/24       
 LSI        all  --  179.0.0.0/8          192.168.1.0/24       
 LSI        all  --  180.0.0.0/8          192.168.1.0/24       
 LSI        all  --  181.0.0.0/8          192.168.1.0/24       
 LSI        all  --  182.0.0.0/8          192.168.1.0/24       
 LSI        all  --  183.0.0.0/8          192.168.1.0/24       
 LSI        all  --  184.0.0.0/8          192.168.1.0/24       
 LSI        all  --  185.0.0.0/8          192.168.1.0/24       
 LSI        all  --  192.0.2.0/24         192.168.1.0/24       
 LSI        all  --  192.168.0.0/16       192.168.1.0/24       
 LSI        all  --  197.0.0.0/8          192.168.1.0/24       
 LSI        all  --  198.18.0.0/15        192.168.1.0/24       
 LSI        all  --  223.0.0.0/8          192.168.1.0/24       
 LSI        all  --  224.0.0.0/3          192.168.1.0/24       
  
 Chain OUTBOUND (1 references) 
 target     prot opt source               destination          
 ACCEPT     icmp --  anywhere             anywhere             
 ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED  
 ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED  
 ACCEPT     all  --  anywhere             anywhere             
 -------------------------------------------------------------------------

---

### Post by JKyleOKC on 2012-01-09
> **Hadeda said:**
> FYI, There is no LAN, no server and no shared printer, only 2 'stand alone' computers plugged into a router.


Just to make sure that I am on the right page, here is a simple question based on a simple situation:

When you build a brand new system and never touch firestarter nor GUFW, what should iptables.rules look like when using your suggested procedure?

At my level I prefer using GUFW which I thought was simply a *user interface to iptables* and not a separate 'firewall package' which could fight with the kernel rules.If there's a router involved, you have a LAN, but it may not look like one. Specifically your two computers may not be able to talk to each other, as one would expect from a full-fledged LAN. This means that the FORWARD chain won't see much, if any, action on your machines.

For a brand new system that has never run firestarter or GUFW, the iptables.rules file should be very small, with the only rules being those that set policy for the three default chains, and the policies should all be ACCEPT. Since Ubuntu does not expose any services to the outside world by default, there's no need for any specific rules in the firewall.

I'll reply separately with discussion of your set of rules. When GUFW runs, it creates some additional chains to make its action more modular. When you do the iptables-save action, you save those added chains and their rules right along with the rules you've added manually, so there's no need at all to let GUFW create them again -- and it's possible that in doing so it can change what you originally saved (for instance, if you had edited one of the rules that it had added, your edit would be replaced). Your understand that it's an interface to iptables is correct but incomplete; it's actually an interface to _creating rules for_ iptables.

---

### Post by JKyleOKC on 2012-01-09
Here's my explanation of your rules file. I've added my comments in red.

> **Hadeda said:**
>  ```
Chain INPUT (policy DROP)     [COLOR="Red"]starts the built-in INPUT chain rule list; 
packets that don't meet any rule will be DROPped[/COLOR] 
 target     prot opt source               destination          
 ACCEPT     tcp  --  8.8.8.8              anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN  [COLOR="Red"]accepts tcp packets from primary name server[/COLOR]
 ACCEPT     udp  --  8.8.8.8              anywhere             [COLOR="Red"]accepts udp packets from primary name server[/COLOR]
 ACCEPT     tcp  --  8.8.4.4              anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN  [COLOR="Red"]accepts tcp packets from secondary name server[/COLOR]
 ACCEPT     udp  --  8.8.4.4              anywhere             [COLOR="Red"]accepts udp packets from secondary name server[/COLOR]
 ACCEPT     tcp  --  207.69.188.186       anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN  [COLOR="Red"]accepts tcp packets from this address[/COLOR]
 ACCEPT     udp  --  207.69.188.186       anywhere             [COLOR="Red"]accepts udp packets from this address[/COLOR]
 ACCEPT     all  --  anywhere             anywhere             [COLOR="Red"]accepts all other packets so no other INPUT rules will be tested

The above rule makes much of the file meaningless! 
None of the remaining rules will be reached.
[/COLOR]
 LSI        udp  --  anywhere             anywhere            udp dpt:33434  [COLOR="Red"]would transfer to the LSI chain if reached and packet was udp addressed to port 33434[/COLOR]
 LSI        icmp --  anywhere             anywhere             [COLOR="Red"]would transfer to the LSI chain if reached and packet was type icmp[/COLOR]
 NR         all  -- !192.168.1.0/24       anywhere             [COLOR="Red"]would transfer to the NR chain if reached and packet was from any 192.168.1.xxx address[/COLOR]
 DROP       all  --  anywhere             255.255.255.255      [COLOR="Red"]would transfer to the DROP chain if reached and packet was from global broadcast address[/COLOR]
 DROP       all  --  anywhere             192.168.1.255        [COLOR="Red"]would transfer to the DROP chain if reached and packet was from LAN broadcast address[/COLOR]
 DROP       all  --  224.0.0.0/8          anywhere             [COLOR="Red"]would transfer to the DROP chain if reached and packet was from multicast address[/COLOR]
 DROP       all  --  anywhere             224.0.0.0/8          [COLOR="Red"]would transfer to the DROP chain if reached and packet was to multicast address[/COLOR]
 DROP       all  --  255.255.255.255      anywhere             [COLOR="Red"]would transfer to the DROP chain if reached and packet was to global broadcast address[/COLOR]
 DROP       all  --  anywhere             0.0.0.0              [COLOR="Red"]would transfer to the DROP chain if reached and packet was from address 0[/COLOR]
 DROP       all  --  anywhere             anywhere            state INVALID  [COLOR="Red"]would transfer to the DROP chain if reached and packet state was invalid[/COLOR]
 LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5  [COLOR="Red"]would transfer to the LSI chain if reached but limits packets to 10 per minute[/COLOR]
 INBOUND    all  --  anywhere             anywhere             [COLOR="Red"]would transfer to the INBOUND chain if reached[/COLOR]
 LOG_FILTER  all  --  anywhere             anywhere             [COLOR="Red"]would transfer to the LOG_FILTER chain if reached[/COLOR]
 LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'  
  [COLOR="Red"]would transfer to the LOG chain if reached, writing entry to syslog[/COLOR]

 Chain FORWARD (policy DROP)     [COLOR="Red"]starts the built-in FORWARD chain rule list; 
packets that don't meet any rule will be DROPped.
This chain is checked only for packets not addressed to or sent from this machine.[/COLOR] 
 target     prot opt source               destination          
 LSI        udp  --  anywhere             anywhere            udp dpt:33434  [COLOR="Red"]would transfer to the LSI chain if reached and packet was udp addressed to port 33434[/COLOR]
 LSI        icmp --  anywhere             anywhere             [COLOR="Red"]would transfer to the LSI chain if reached and packet was type icmp[/COLOR]
 LOG_FILTER  all  --  anywhere             anywhere             [COLOR="Red"]transfers to the LOG_FILTER chain[/COLOR]
 LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'  [COLOR="Red"]transfers to the LOG chain, writing entry to syslog[/COLOR]
  
 Chain OUTPUT (policy DROP)      [COLOR="Red"]starts the built-in OUTPUT chain rule list; 
packets that don't meet any rule will be DROPped[/COLOR]
 target     prot opt source               destination          
 ACCEPT     tcp  --  192.168.1.1xx        8.8.8.8             tcp dpt:domain  
 ACCEPT     udp  --  192.168.1.1xx        8.8.8.8             udp dpt:domain  
 ACCEPT     tcp  --  192.168.1.1xx        8.8.4.4             tcp dpt:domain  
 ACCEPT     udp  --  192.168.1.1xx        8.8.4.4             udp dpt:domain  
 ACCEPT     tcp  --  192.168.1.1xx        207.69.188.186      tcp dpt:domain  
 ACCEPT     udp  --  192.168.1.1xx        207.69.188.186      udp dpt:domain  
 ACCEPT     all  --  anywhere             anywhere             
[COLOR="Red"]The above rule makes all those both before and after it meaningless since it will accept everything.[/COLOR]
 DROP       all  --  224.0.0.0/8          anywhere             [COLOR="Red"]Drops any packet from multicast address.[/COLOR]
 DROP       all  --  anywhere             224.0.0.0/8          [COLOR="Red"]Drops any packet to multicast address.[/COLOR]
 DROP       all  --  255.255.255.255      anywhere             [COLOR="Red"]Drops any packet from global broadcast address.[/COLOR]
 DROP       all  --  anywhere             0.0.0.0              [COLOR="Red"]Drops any packet to address 0.[/COLOR]
 DROP       all  --  anywhere             anywhere            state INVALID  [COLOR="Red"]Drops any INVALID packet.[/COLOR]
 OUTBOUND   all  --  anywhere             anywhere             [COLOR="Red"]Transfers any packet getting here to OUTBOUND chain.[/COLOR]
 LOG_FILTER  all  --  anywhere             anywhere             [COLOR="Red"]Transfers any packet to LOG_FILTER chain.[/COLOR]
 LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'  
  [COLOR="Red"]Transfers to the LOG chain, writing entry to syslog[/COLOR]

 Chain INBOUND (1 references)      [COLOR="Red"]Starts the INBOUND chain rule list possibly created by GUFW[/COLOR]
 target     prot opt source               destination          
 ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED  [COLOR="Red"]Accepts any RELATED or ESTABLISHED tcp packet[/COLOR]
 ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED  [COLOR="Red"]Accepts any RELATED or ESTABLISHED udp packet[/COLOR]
 LSI        all  --  anywhere             anywhere             [COLOR="Red"]Transfers any packet getting here to LSI chain.[/COLOR]
  
 Chain LOG_FILTER (5 references)      [COLOR="Red"]starts the LOG_FILTER chain rule list possibly created by GUFW[/COLOR]
 target     prot opt source               destination          
[COLOR="Red"]This chain has no rules so simply returns to the next rule following the one that called it.[/COLOR]
  
 Chain LSI (54 references)      [COLOR="Red"]starts the LSI chain rule list possibly created by GUFW[/COLOR]
 target     prot opt source               destination          
 LOG_FILTER  all  --  anywhere             anywhere             [COLOR="Red"]Transfers any packet to LOG_FILTER chain.[/COLOR]
 LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '  [COLOR="Red"]Transfers to the LOG chain, writing entry to syslog[/COLOR]
 DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN  [COLOR="Red"]Drops any tcp packet reaching here.[/COLOR]
 LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '  [COLOR="Red"]Transfers to the LOG chain, writing entry to syslog[/COLOR]
 DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST  [COLOR="Red"]Drops any tcp packet reaching here.[/COLOR]
 LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '  [COLOR="Red"]Transfers to the LOG chain, writing entry to syslog[/COLOR]
 DROP       icmp --  anywhere             anywhere            icmp echo-request  [COLOR="Red"]Drops any icmp echo-request packet reaching here.[/COLOR]
 LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '  [COLOR="Red"]Transfers to the LOG chain, writing entry to syslog[/COLOR]
 DROP       all  --  anywhere             anywhere             [COLOR="Red"]Drops any packet reaching here.[/COLOR]
  
 Chain LSO (0 references)      [COLOR="Red"]starts the LSO chain rule list possibly created by GUFW
Not referenced anywhere so will not be used at all.[/COLOR]
 target     prot opt source               destination          
 LOG_FILTER  all  --  anywhere             anywhere             
 LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '  
 REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable  
  
 Chain NR (1 references)      [COLOR="Red"]starts the NR chain rule list possibly created by GUFW
This chain transfers packets from the specified addresses to the LSI chain for testing.
If none of its rules match a packet, control returns to the rule that called it.[/COLOR]
 target     prot opt source               destination          
 LSI        all  --  0.0.0.0/8            192.168.1.0/24       
 LSI        all  --  1.0.0.0/8            192.168.1.0/24       
 LSI        all  --  2.0.0.0/8            192.168.1.0/24       
 LSI        all  --  5.0.0.0/8            192.168.1.0/24       
 LSI        all  --  10.0.0.0/8           192.168.1.0/24       
 LSI        all  --  14.0.0.0/8           192.168.1.0/24       
 LSI        all  --  23.0.0.0/8           192.168.1.0/24       
 LSI        all  --  27.0.0.0/8           192.168.1.0/24       
 LSI        all  --  31.0.0.0/8           192.168.1.0/24       
 LSI        all  --  36.0.0.0/8           192.168.1.0/24       
 LSI        all  --  37.0.0.0/8           192.168.1.0/24       
 LSI        all  --  39.0.0.0/8           192.168.1.0/24       
 LSI        all  --  42.0.0.0/8           192.168.1.0/24       
 LSI        all  --  46.0.0.0/8           192.168.1.0/24       
 LSI        all  --  49.0.0.0/8           192.168.1.0/24       
 LSI        all  --  50.0.0.0/8           192.168.1.0/24       
 LSI        all  --  100.0.0.0/8          192.168.1.0/24       
 LSI        all  --  101.0.0.0/8          192.168.1.0/24       
 LSI        all  --  102.0.0.0/8          192.168.1.0/24       
 LSI        all  --  103.0.0.0/8          192.168.1.0/24       
 LSI        all  --  104.0.0.0/8          192.168.1.0/24       
 LSI        all  --  105.0.0.0/8          192.168.1.0/24       
 LSI        all  --  106.0.0.0/8          192.168.1.0/24       
 LSI        all  --  107.0.0.0/8          192.168.1.0/24       
 LSI        all  --  108.0.0.0/8          192.168.1.0/24       
 LSI        all  --  109.0.0.0/8          192.168.1.0/24       
 LSI        all  --  110.0.0.0/8          192.168.1.0/24       
 LSI        all  --  111.0.0.0/8          192.168.1.0/24       
 LSI        all  --  127.0.0.0/8          192.168.1.0/24       
 LSI        all  --  link-local/16        192.168.1.0/24       
 LSI        all  --  172.16.0.0/12        192.168.1.0/24       
 LSI        all  --  175.0.0.0/8          192.168.1.0/24       
 LSI        all  --  176.0.0.0/8          192.168.1.0/24       
 LSI        all  --  177.0.0.0/8          192.168.1.0/24       
 LSI        all  --  178.0.0.0/8          192.168.1.0/24       
 LSI        all  --  179.0.0.0/8          192.168.1.0/24       
 LSI        all  --  180.0.0.0/8          192.168.1.0/24       
 LSI        all  --  181.0.0.0/8          192.168.1.0/24       
 LSI        all  --  182.0.0.0/8          192.168.1.0/24       
 LSI        all  --  183.0.0.0/8          192.168.1.0/24       
 LSI        all  --  184.0.0.0/8          192.168.1.0/24       
 LSI        all  --  185.0.0.0/8          192.168.1.0/24       
 LSI        all  --  192.0.2.0/24         192.168.1.0/24       
 LSI        all  --  192.168.0.0/16       192.168.1.0/24       
 LSI        all  --  197.0.0.0/8          192.168.1.0/24       
 LSI        all  --  198.18.0.0/15        192.168.1.0/24       
 LSI        all  --  223.0.0.0/8          192.168.1.0/24       
 LSI        all  --  224.0.0.0/3          192.168.1.0/24       
  
 Chain OUTBOUND (1 references)      [COLOR="Red"]starts the OUTBOUND chain rule list possibly created by GUFW[/COLOR]
 target     prot opt source               destination          
 ACCEPT     icmp --  anywhere             anywhere             [COLOR="Red"]Accepts any icmp packet getting here.[/COLOR]
 ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED  [COLOR="Red"]Accepts any RELATED or ESTABLISHED tcp packet getting here.[/COLOR]
 ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED  [COLOR="Red"]Accepts any RELATED or ESTABLISHED udp packet getting here.[/COLOR]
 ACCEPT     all  --  anywhere             anywhere             [COLOR="Red"]Accepts any other packet getting here.[/COLOR]
```It looks as if you may have used several tools, and consequently have a number of rules that can never be reached, plus others that are somewhat redundant. For example, the first three rules of the OUTBOUND chain could be deleted since they specify packets that would pass the fourth rule -- and in any event the accept-anything rule in the OUTPUT chain prevents OUTBOUND from being reached.

My comments may sound over-critical; at least some of the redundancy, I'm sure, is caused by the behind-the-scenes simplification of UFW as it interprets minimal commands. The huge number of options available in the iptables rules results in a very steep learning curve. I suspect that those "accept everything" rules in the INPUT and OUTPUT chains were inserted by UFW, probably when it was disabled.

I hope these detailed explanations help you climb that learning curve!

---

### Post by Hadeda on 2012-01-10
Wow, This is of great help and is plenty of food for thought!
The biggest hurdle in learning iptables is - at least for me - terminology. 


To move forward, and also for the benefit of those who follow this thread, may I ask you to answer the following clarifying questions?

1) Are iptables and UFW the same thing?

2) In order to avoid creating all the issues you kindly pointed out in my iptables.rules, Could you give 4 clarifying examples of how to set up protection using ANY method you might like to suggest after a brand new Ubuntu installation:
 
a) block e.g port 1900 
b) block all traffic from/to eg badguys.com 
c) block all traffic from/to eg xxx.xxx.000.000
d) block all traffic from/to eg range xxx.xxx.000.000 - xxx.xxx.256.256

I think that above 4 rules represent most situations lay people are exposed to (unless you feel that I am wrong with that assumption).

3) What does LSI and LSO stand for?

Once I get a feel for above open issues, I am sure that your efforts to condense complexity would perhaps be worth a separate sticky post =D>

---

### Post by JKyleOKC on 2012-01-10
I'm going to hold off on question 2 for a bit so that I'm certain what I provide will be useful. Meanwhile here are the other two:
> **Hadeda said:**
> 1) Are iptables and UFW the same thing?
Pretty much. UFW is a "wrapper" that translates your input to it into a set of rules for the netfilter procedures in the kernel to use. The iptables command itself is a super-user tool to list, create, and remove those same rules. When we talk about "iptables" in a context that's NOT using the word as a command, we're talking about those netfilter procedures in the kernel and more specically their list of rules.
> **Hadeda said:**
> 3) What does LSI and LSO stand for?
I don't really know for certain, but my best guess would be "Log Stuff In" and "Log Stuff Out." I believe these were created by UFW to deal with packets from or to specific addresses, and part of the *nix tradition is the use of very short and somewhat cryptic abbreviations. This tradition dates from the days when all communication with the software was via teletype machines at 10 characters per second. Typing "cat" was much less work than typing "catenate" (which is what the "cat" command does). Similarly it's faster to type "cd" rather than "chdir" or the full "change_directory" so the habit persists.

Earlier you asked what "sudo iptables -L" would produce on a brand new system. I ran that last night in a virtual machine where I'm testing Debian and have never done anything with its firewall. Here's the result:```
jim@deb6:~$ sudo iptables -L
[sudo] password for jim: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
jim@deb6:~$ 
``` I hope these help a bit, while I'm mulling over the example for question 2...

---

### Post by JKyleOKC on 2012-01-10
> **Hadeda said:**
> 2) In order to avoid creating all the issues you kindly pointed out in my iptables.rules, Could you give 4 clarifying examples of how to set up protection using ANY method you might like to suggest after a brand new Ubuntu installation:
 
a) block e.g port 1900 
b) block all traffic from/to eg badguys.com 
c) block all traffic from/to eg xxx.xxx.000.000
d) block all traffic from/to eg range xxx.xxx.000.000 - xxx.xxx.256.256

I think that above 4 rules represent most situations lay people are exposed to (unless you feel that I am wrong with that assumption).Here's the sample iptable.rules set that I've worked up to handle your second question. It's not tested, so there might be errors in it, and it definitely requires some editing to replace the "xxx" items with valid IP octets. Incidentally, "256" isn't such a valid octet; the maximum value is 255!```
#
# set chain policies for "filter" table
*filter
:INPUT DROP [0:0]
:OUTPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
# define optional chain to log dropped packets
:LOG_DROP - [0:0]
#
# define rules for INPUT chain
# these do a, b, c, and d for incoming packets
#    change LOG_DROP to DROP to skip logging
# [COLOR="Red"] delete this line
-A INPUT -p tcp --sport 1900 -j LOG_DROP
-A INPUT -p udp --sport 1900 -j LOG_DROP
-A INPUT -p tcp --dport 1900 -j LOG_DROP
-A INPUT -p udp --dport 1900 -j LOG_DROP
# delete this line also[/COLOR]
-A INPUT -s badguys.com -j LOG_DROP
-A INPUT -s xxx.xxx.0.0 -j LOG_DROP
-A INPUT -s xxx.xxx.0.0/16 -j LOG_DROP
# accept all loopback and icmp (ping) traffic
-A INPUT -i lo -j ACCEPT
-A INPUT -p icmp -j ACCEPT
# accept packets for established connections
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# log all other packets
# omit if LOG_DROP chain not defined; policy will do DROP
-A INPUT -j LOG_DROP
#
# define rules for optional LOG_DROP chain
-A LOG_DROP -j LOG  --log-prefix "[IPTABLES DROP] : " 
# next rule not needed; policy for INPUT will handle it
-A LOG_DROP -j DROP
#
# define rules for OUTPUT chain
# these do a, b, c, and d for outgoing packets
#    change LOG_DROP to DROP to skip logging
# [COLOR="Red"]delete this line
-A OUTPUT -p tcp --dport 1900 -j LOG_DROP
-A OUTPUT -p udp --dport 1900 -j LOG_DROP
-A OUTPUT -p tcp --sport 1900 -j LOG_DROP
-A OUTPUT -p udp --sport 1900 -j LOG_DROP
# delete this line also[/COLOR]
-A OUTPUT -d badguys.com -j LOG_DROP
-A OUTPUT -d xxx.xxx.0.0 -j LOG_DROP
-A OUTPUT -d xxx.xxx.0.0/16 -j LOG_DROP
# next rule not needed; policy will handle it
-A OUTPUT -j ACCEPT
#
# put above into effect; end of "filter" module's list
COMMIT
#
# set chain policies for "mangle" table; needs no rules
*mangle
:PREROUTING ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
#
# put above into effect; end of "mangle" module's list
COMMIT
#
# set chain policies for "nat" (network address translation) table; needs no rules
*nat
:PREROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
#
# put above into effect; end of "nat" module's list
COMMIT
```To use this, first copy it from the forum and paste it into an empty text document using gedit, kate, mousepad, nano, or any other text editor of your choice (but NOT a word processor). 

Next, edit the lines with "xxx" in them to reflect valid IP values[COLOR="Red"], and delete the four "delete this line" lines; they contain "COLOR" commands[/COLOR] that have no effect in iptables rules. Note that the "/16" in the "d" samples means that only the leftmost 16 bits of the address will be tested. You can have any value from 8 to 29 in place of 16, depending on the specific IP address you want to block. This can be quite useful in blocking off entire countries!

You can also copy and paste entire lines within the sample, to specify different addresses or ports. Ports can also be specified as ranges, such as "20:80" to specify ports 20 through 80 inclusive. IP addresses cannot be specified as ranges, so there are separate rules for source address and destination address. And the "badguys.com" examples are mentioned on the MAN page for iptables as "a really bad idea" since they require DNS lookups for the named domain each time the rule is processed, which can slow the fastest broadband down to a very slow crawl. I would delete them and use the numeric IP address instead.

Note that I've left out lots of the option specifiers that were in the sample we examined earlier. The system provides defaults for all of them; the "-p" option defaults to "all" while the "-i" one defaults to "any," as do the address and port specifiers. The only time you need to have a rule is for cases that these defaults don't handle. [COLOR="Red"]However sometimes the -p option is necessary, such as when a port is specified. That was my original "large error."[/COLOR]

Note, too, that these rules set up a firewall that will not allow ANY external machine to initiate a connection to your system. That gives a maximum of security; you can still contact your email server and browse the web, since you initiate those connections. However if you want to run a game server and let others use it, additional rules will be needed.

Once you've finished editing, you can simply save the file. I called it "new_iptables.rules" here but you can give it any name you like. Then install it by using "sudo iptables-restore xxx" where "xxx" is the name you gave the file, and copy it to /etc/iptable.rules as I described in an earlier message. The file is already in the format that "iptables-save" creates, so it's compatible with the restore actions.

That's all you need to do; for most home uses there's no need to deal with a simplified interface such as UFW, firestarter, or their GUI wrappers. Only if you want to allow outsiders to initiate connections will additional rules be needed, and even in such cases only a few in the INPUT chain will be necessary.

Hopefully this will help, not only you, but as you suggest, others who come across this thread. And by all means if anyone finds errors in this sample, let me know so that we can correct them!!!

---

### Post by spynappels on 2012-01-11
Well done Jim, that is a very comprehensive answer. 

Hadeda, if you have not done so already, have a look at BodhiZazen's iptables introduction as referenced in the security sticky as well, it explains it very well also, but Jim's rules above are absolutely spot on and first class.

---

### Post by Hadeda on 2012-01-11
This is extraordinary and invaluable work and I would like to echo spynapples' comments, Jim. Thank you very much.  :D


1) To make things simple I assumed that we start off with a brand new system.
When having a 'contaminated' system created through various 'packages', such as Firestarter and GUF, will 

> iptables -F suffice or do you suggest much more to start afresh?

2) The remaining issue is one which I noticed has been asked in other posts, but without a resolution: How can I monitor the firewall in realtime without using Firestarter?[INDENT]Open posts re: firewall monitor
[http://ubuntuforums.org/showpost.php?p=1787005&postcount=1](http://ubuntuforums.org/showpost.php?p=1787005&postcount=1)
and
[http://ubuntuforums.org/showpost.php?p=11075785&postcount=1](http://ubuntuforums.org/showpost.php?p=11075785&postcount=1)
[/INDENT]spynapples - Thanks for pointing out Bodhi's work.

---

### Post by JKyleOKC on 2012-01-11
> **Hadeda said:**
> 1) To make things simple I assumed that we start off with a brand new system.
When having a 'contaminated' system created through various 'packages', such as Firestarter and GUF, will ```
iptbles -F
``` suffice or do you suggest much more to start afresh?That ought to suffice, since it flushes all of the existing rules and resets the counters. I believe that the iptables-restore program does this automatically, so just trying that first might be interesting.
> **Hadeda said:**
> 2) The remaining issue is one which I noticed has been asked in other posts, but without a resolution: How can I monitor the firewall in realtime without using Firestarter?[INDENT]Open posts re: firewall monitor
[http://ubuntuforums.org/showpost.php?p=1787005&postcount=1](http://ubuntuforums.org/showpost.php?p=1787005&postcount=1)
and
[http://ubuntuforums.org/showpost.php?p=11075785&postcount=1](http://ubuntuforums.org/showpost.php?p=11075785&postcount=1)[/INDENT]The only simple way I know of to do this is to open a terminal window and there issue the command "tail -f -n=1 /var/log/syslog", then resize the window to leave just enough room for a one-line log entry, and move it to a corner of your screen. This only works if you include the LOG_DROP chain in your rule set, so that iptables will write an entry to syslog every time it drops a packet. This command causes the "tail" program to display the last "n" lines (in this case, one) of the named file, and to follow the file until you use Ctrl-C to tell it to quit.

I've done this from time to time when trying out new rules, or verifying that a troublesome IP address really is getting dropped, but if you do it you'll quickly get tired of all the "internet noise" as dozens of packets may get dropped every minute you are connected to the net. I even quit logging DROP actions here, since doing so was nearly doubling the size of my log files and very little information from the entries meant anything significant.

---

### Post by Hadeda on 2012-01-11
Jim, you should be congratulated for having the skills and patience to explain complex issues to newbies. It was like having a private tutor but I hope that many others benefited through this steep learning curve.

In order to contribute something, I have compiled your key instructions about "HOW TO COPY IPTABLES" in the post below. I would like to forward this to a few Ubuntu fans just like me - but only after your approval,,. THANKS!

:guitar:

---

### Post by Hadeda on 2012-01-11
[CENTER]**HOW TO COPY IPTABLES**


courtesy of Jim Kyle
compiled by Hadeda
[/CENTER]

Once you have built a firewall you might want to copy it for transferring it to other systems.

Note: Replace *youruser* with your proper user name.

Start with

```
sudo iptables-save >/home/youruser/iptables.rules


```this will create the file iptables.rules in *youruser* home folder

then

```
sudo cp $HOME/iptables.rules /etc/iptables.rules
```

this will copy iptables.rules from youruser to the /etc folder.

then, to ensure that the table is loaded on boot:

```
gksudo gedit /etc/rc.local
```

this will open up the rc.local file in gedit for editing.

Add this line into /etc/rc.local just ahead of the existing "exit 0" line:

```
/sbin/iptables-restore </etc/iptables.rules
```

save the rc.local file.

Reboot.

To test iptables

```
sudo iptables -L
```

Done

---

### Post by JKyleOKC on 2012-01-11
Looks fine to me! FYI, the "$HOME" always expands to "/home/youruser" so you could replace the longer version in your first instruction with the shorter one, and no longer have to edit the example -- you could then just copy and paste it.

Feel free to distribute this as you desire.

I've spent more than half a century as a professional writer, and got into computers back in the mid-1960s after quite a few years as an electronics hobbyist. Along the way quite a few people have helped me, and very early in my writing career, a magazine editor pointed out that I had a knack for making instructions understandable. Now I do almost all my writing in forums such as here, "paying forward" for all the help I've received from others. You can find out more about my background at my web site, [http://www.jimkyle.com/](http://www.jimkyle.com/).

---

### Post by spynappels on 2012-01-12
> **Hadeda said:**
> 

2) The remaining issue is one which I noticed has been asked in other posts, but without a resolution: How can I monitor the firewall in realtime without using Firestarter?[INDENT]Open posts re: firewall monitor
[http://ubuntuforums.org/showpost.php?p=1787005&postcount=1](http://ubuntuforums.org/showpost.php?p=1787005&postcount=1)
and
[http://ubuntuforums.org/showpost.php?p=11075785&postcount=1](http://ubuntuforums.org/showpost.php?p=11075785&postcount=1)

 Hi Hadeda,

While realtime monitoring can be useful in troubleshooting problems, doing it when no problems are present may cause an increase in paranoia. There will more than likely always be hits which are dropped or rejected, this is the background radiation from the Internet and monitoring it can be an exercise in futility unless you are looking for something specific. If you want a more general flavour of this background radiation, it might be a useful exercise to script a parse of the logs on a schedule (cron) which can give you some analysis without causing heart failure in real time!

There is nothing wrong with realtime monitoring, you just may find it unsettling and/or a waste of time depending on the amount of (bad) traffic you get.

---

### Post by Hadeda on 2012-01-15
Jim, your post was very interesting, thank you! I was holding off my reply because I could not access your website - and still can't, although I checked my firewall settings.
It just sits as if it is one of those network-side blocked sites - it doesn't even try to connect to your IP address. Traceroute gets stuck after a few hops. 
You might like to ask a friend to check it out as well. Are you happy with your ISP?

Although it is not a topic for this thread, I am beginning to wonder if the issue of our IP spoofing and firewall- and router flooding has not been fully resolved as of yet  :-(

---

### Post by Hadeda on 2012-01-15
spynapples, Your assessment is spot on, thank you. Too many checks will distract the user. 

It's history now, but if it wouldn't have been for the firestarter realtime logs we would not have known the source of the flooding as mentioned above. Moving forward, parsing a script is certainly a better idea.

But how do you tell this to someone who simply wants to use a computer without having to know what a script is - especially after few pints of Ale or Guinness? :lol:

---

### Post by JKyleOKC on 2012-01-15
> **Hadeda said:**
> You might like to ask a friend to check it out as well. Are you happy with your ISP?My ISP is AT&T, and I don't have much choice here; the alternative is Cox cable service, and their rules would make it impossible for me to operate my data recovery service. However all I get from AT&T is the Internet connection; my mail server and web site are elsewhere.

My web site is hosted by GoDaddy, as is my mail server, and I'm not at all happy with them but have not yet found a better alternative for a web presence provider and Email server.

I have no problem accessing my web site from here, and if your traceroute result (or, alternatively, a "ping -c 3 www.jimkyle.com") shows the IP address as 184.168.248.1 you're getting the right address via DNS. I suspect that somewhere along the way one of the intermediate connections on the route is blocking GoDaddy IPs.

If you're not getting the 184.168.248.1 IP address, try putting it directly into your browser address bar instead of the domain name and see if that works. It's a static IP and does not change over time.

And if anyone has suggestions for a better site to host my web pages and serve my Email, I'm open to them. My account at GoDaddy is up for renewal next month and I'd really like to move everything away from there (including my domain registration, which doesn't expire for another year) before giving them another $58 for another year.

---

### Post by Hadeda on 2012-01-16
When I type Jimkyle.com or 184.168.248.1 into the browser my current realtime monitor tells me that there is no connection attempt by the browser and the connection times out.
The same happens to many other credible websites such as USPS.com and, as an example, Americanexpress.com which is perhaps a different issue for another thread.


Godaddy:
I dumped them long ago and will only say that I did it "within minutes" of discovering certain problems. Enough said. Moving forward, I will check with a friend who is heavily relying on the integrity of their host server. Before I mention names, I will check the latest reference and let you know.


When using traceroute in the terminal and networktools, after many timeouts in between I end up at godaddy after hop 12 but after that it is timeout only.

13 * * ip-208-109-112-2.ip.secureserver.net (208.109.112.2)

Either you or me, perhaps both of us have a problem!

---

### Post by JKyleOKC on 2012-01-16
> **Hadeda said:**
> When I type Jimkyle.com or 184.168.248.1 into the browser my current realtime monitor tells me that there is no connection attempt by the browser and the connection times out.
The same happens to many other credible websites such as USPS.com and, as an example, Americanexpress.com which is perhaps a different issue for another thread.It sounds as if you could still have a DNS issue. Try setting 8.8.8.8 as your primary name server and see whether that makes any difference; this is Google's primary DNS server and is highly recommended by many security folk in another forum I monitor daily.

If your browser won't attempt to connect using the IP address, though, it's more likely a problem in the browser itself (or maybe in your security settings for it) since using a direct IP address should totally bypass the DNS lookup.

As for "secureserver.net" that's the actual domain name of at least some of the GoDaddy servers. It's where I must go to get my mail messages from that account. The timeouts once you get to that point could be caused by GoDaddy simply ignoring icmp requests; many servers are configured to do just that.

I look forward to recommendations for better places to host my pages and serve my email needs. My ISP subcontracts the mail services to Yahoo and their performance is even less reliable than GoDaddy's...

---

### Post by Hadeda on 2012-01-17
I have flushed Firefox DNS, system DNS (nscd), used google and openDNS and there is no difference (I have used googleDNS for a while). I have even tried Arora to eliminate FF as a problem source: no difference: I cannot connect to 184.168.248.1 

It is of concern that this blocking occurs only for targeted addresses such as yours and other credible IPs and URLs such as americanexpress, USPS etc - I can connect to this forum without hassle.

:evil:

---

### Post by JKyleOKC on 2012-01-17
It sounds as if someone upstream from you might have an over-enthusiastic spam filter at work. If so, there's not a lot that you can do about it other than changing ISPs, and that might not be an option...

---

### Post by JKyleOKC on 2012-03-24
Did you ever manage to get through to my web site?

---

### Post by Hadeda on 2012-03-25
I am glad that you ask that question.

Here is your answer:


The connection has timed out
The server at 184.168.248.1 is taking too long to respond

and
          
The connection has timed out
The server at [www.jimkyle.com](www.jimkyle.com) is taking too long to respond


This is after applying your new firewall rules and after changing ISP's  :-(

---

### Post by JKyleOKC on 2012-03-25
Strange...

There must be a block of the 184.x.x.x group in place somewhere upstream. I can ping the site from here, usually with about 112 msec latency; I use that to verify that my DSL is working. It also indicates that GoDaddy itself is allowing pings through their servers. However with the bad reputation GoDaddy has earned, I would not be amazed to learn that other providers have blocked all access to them...

Have you tried "traceroute" to see how far along the route you are getting before the block?

---

### Post by Hadeda on 2012-03-26
Yes, both, the url and IP.
They get stuck after hop 13:

13  * be100.125.trmd0215-01.ars.mgmt.phx3.gdg (216.69.188.30)  68.414 ms *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *


216.69.188.30 resolves to a godaddy address.
I tried it in both, terminal and network tools :-(

---

