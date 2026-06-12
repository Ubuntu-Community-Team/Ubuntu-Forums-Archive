---
title: "DSL on USB at School"
date: 2006-06-30
forum: The Cafe
---

### Post by rowanparker on 2006-06-30
Hello,
I have put Damn Small Linux on my USB stick (Ubuntu wouldn't fit :() and today I booted it up at school and it worked fine, apart from the internet. Our school uses Windows and RM.

I told me teacher what I was doing and he gave me some infomation:
> DNS: abcdefghijkl.mnopqr
IP: xxx.xxx.xxx.xxx
Subnet: xxx.xxx.xxx.xxx
Default: xxx.xxx.xxx.xxx
He said something about pinging and using that infomation to get the internet in DSL.

Can I get on the internet this way?
If so, how?

Thanks, Rowan.

P.S. I have been given permission to do this so it is not illegal at all.

---

### Post by PapaWiskas on 2006-06-30
If I were you, I would edit my post.
Just because I am an admin myself and just out of habit would not want that information for the whole world to see.
Its just good security practice is all, not that anyone could do anything with the information in the first place.

Maybe change it to this?

DNS: abcderfg.hijklmno
IP: xxx.xxx.xxx.xxx
Subnet: xxx.xxx.xxx.xxx
Default: xxx.xxx.xxx.xxx / xxx.xxx.xxx.xxx

You should be able to input that information into your network config file on DSL, save it, and that should do it.

---

### Post by rowanparker on 2006-06-30
I edited it now, thanks.

Where is the config file as I've never set up a network in Linux, its always been done for me (cos Linux is so good)?

Do you know what he was on about the pinging? he said something about finding a free address or something like that.

Thanks, Rowan.

---

### Post by PapaWiskas on 2006-06-30
I think you would need to add the static IP information to the /opt/bootlocal.sh file. This file is backed up in the /home/dsl/.filetool.lst file by default. For this step you will need to know the static IP, Default Gateway and DNS nameserver. With this information your /opt/bootlocal.sh file should have the following entries. 

ifconfig eth0 xxx.xxx.x.xx 
route add default gw xxx.xxx.x.x 
echo nameserver xx.xx.xxx.xx > /etc/resolv.conf 
ifup eth0 
-----------------------------------------

With these two steps you should have your static connection up and running the next boot. Make sure you back them up! 

What he meant by pinging is opening up a terminal or comman prompt if you are on a windows machine and enter some IP addresses that fall in the correct range.

For example in windows after opening a command prompt you would type

ping 192.168.86.1

If you get no response then you know that addresses is open for your use.  Now keep in mind that address I just listed is just an example.
If you do get a response, then you need to try another number...i.e.

ping 192.168.86.2  and so on until you dont get a response.

I took the above information from the DSL website, I hope it helps.

Good Luck!!:D

---

### Post by rowanparker on 2006-06-30
Thanks, I'll give it a try next week.
I'll tell you if it works or not.

---

### Post by rowanparker on 2006-07-07
Erm, I could not get on the internet.
I did everything suggested and ran networkcard config or somet like that. Just couldn't get online at all. I pinged to find an free IP and used that. DHCP (or DCHP) is there on the network but I wasn't allowed to that as the teacher might get into trouble.

Any ideas?
Thanks, Rowan.

---

### Post by Randomskk on 2006-07-07
DHCP should be easy enough to set up :/

Anyway, I can't help much without seeing the actual IP and data you've got, but how are you checking there's an IP to use? Are the school IPs world routable? Is it a private network? What's the address of the DHCP server? Can you connect at all? Does the ethernet card work? Can you ping by numbers?

---

### Post by rowanparker on 2006-07-08
I am not allowed to use DHCP, unless Graham (system admin) is out (then he can't find me).

I am pinging random IP's to find one that's not in use (what PapaWiskas said). The ethernet card works because you can connect to the network in Windows. I have not a clue about whether it's a privat network or not, is there anyway I can find out without asking my teacher.

Thanks, Rowan.

---

### Post by Randomskk on 2006-07-08
Ok, first few things.
1) The ethernet card works in windows, but does it work in linux? Most do, some don't. This probably isn't an issue if you can ping an IP (and get a reply).

2) Why would he be able to find you if you do use DHCP, and if he does, what'l he do? Even if he does check the logs all the time, the DHCP entry will appear to be exactly the same as a windows computer doing it, so it'l look like someone rebooted one of the workstations, which I'm sure happens all the time (windows :P)

3) Do the IPs you're given start 10. or 192.168? If so, it's a private network, which is a whole different ball game from a public network.

Once you're on the network, before setting up DNS try this:
ping 64.233.167.99
If that works, it means you can access the internet and you just need to setup DNS, if it doesn't it means you still are not online.

I'm guessing the subnet is something like 255.255.0.0? I don't know why you'd hide it, it's not exactly unique most of the time =P
That subnet defines what IPs the school have, although it's worth noting that the router you're connected to may only allocate a certain range.
If you can boot windows, can you find out what IP it's using?

Alternatively, what IP have you got? Is that a usable IP or what?
And by Default, do you mean Default Gateway?

If the IP is one you can use (don't trust pinging to find you an IP though...), or if not get one from the windows computer then turn it off (ipconfig in windows command line):
```
sudo -i
ifconfig eth0 down
route add default gw <DEFAULT>
ifconfig eth0 <IP>
ifconfig eth0 up
ping 64.233.167.99
```

If that works, and you have internet, to get DNS do this:
```
((STILL IN sudo -i WINDOW, if not do sudo -i))
echo "nameserver <DNS>" >> /etc/resolv.conf
ping google.com
```

Try that out, anyway.

By the way, going on PapaWiskas's post, is the IP range something like 192.168.86.x? If so, it's a private network.

---

### Post by mips on 2006-07-08
> **rowanparker said:**
> 
I am pinging random IP's to find one that's not in use (what PapaWiskas said). 


That is way worse than requesting IP information via DHCP. When you just grab any unallocated IP address the DHCP server would not know that the address is in use already and might assign it to another PC. This will cause IP address conflicts and that is when the SysAdmin is gonna get pissed, I sure did. Easy to trace and catch the culprit.

If you just use DHCP the above will not happen and the loggs will look the same for a windows vs Linux PC. In basic DHCP setups the only thing that gets recorded is the MAC address corrosponding to the IP address. The MAC address is a hardware address on the ethernet card and does not change irrespective of the OS.

---

### Post by rowanparker on 2006-07-08
I'll use DHCP then next time (could be next year now (September that is)).

Thank you people, I will get back to you when I have had another go. (could be a new thread if I can't find this one).

Rowan.

---

