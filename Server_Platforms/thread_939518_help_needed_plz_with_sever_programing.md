---
title: "help needed plz with sever programing"
date: 2008-10-06
forum: Server Platforms
---

### Post by snowstorm167 on 2008-10-06
I have added a secound lan card to my comp so i can share my connection with my laptop or ps2 but i am unsure of how to do this    I have the hardy server os      net  is listed as    eth 0   and eth 1          my laptop has xp pro installed               thanks ahead of tie for help on this

---

### Post by cdenley on 2008-10-06
Just configure a bridge. I think this is all you need to do. It has been a while since I did this, and I have not tested these steps.

```

sudo apt-get install bridge-utils

```
Edit /etc/network/interfaces to look like this.
```

auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1

```
Sections for eth0 and eth1 should be commented out.

---

### Post by snowstorm167 on 2008-10-07
i am getting command not found

---

### Post by cdenley on 2008-10-07
> **snowstorm167 said:**
> i am getting command not found

For what? sudo? apt-get? Are you running ubuntu? Did you read my post carefully. The second code box contains the contents of a file, not commands.

---

### Post by snowstorm167 on 2008-10-07
ok i thought they where the configureing codes and yes the apt-get worked and still no laptop online

---

### Post by cdenley on 2008-10-07
> **snowstorm167 said:**
> ok i thought they where the configureing codes and yes the apt-get worked and still no laptop online

Once you change the network configuration file, you have to restart the networking for the changes to take effect
```

sudo /etc/init.d/networking restart

```
or reboot the computer. Have you done that? If so, and it doesn't work, post the output of these commands.
```

ifconfig
brctl show

```
Also, I assumed you are connecting to a LAN. What type of connection does your linux computer have?

---

### Post by snowstorm167 on 2008-10-08
Yes my linux machine has lan set up times 2one for net other for shareing net tryed the commands you gave me and for first one this is what it says:                                                                         eth0      Link encap:Ethernet  HWaddr 00:50:ba:4d:cf:ff
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:17:31:27:fb:f0
          inet addr:199.247.241.210  Bcast:199.247.241.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe27:fbf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000
          RX bytes:1185098 (1.1 MB)  TX bytes:219266 (214.1 KB)
          Interrupt:23 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53960 (52.6 KB)  TX bytes:53960 (52.6 KB)



command 2 is as follows :  bridge name     bridge id               STP enabled     interfaces        tnx for your help so far

---

### Post by cdenley on 2008-10-08
> **snowstorm167 said:**
> Yes my linux machine has lan set up times 2one for net other for shareing net tryed the commands you gave me and for first one this is what it says:                                                                         eth0      Link encap:Ethernet  HWaddr 00:50:ba:4d:cf:ff
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:17:31:27:fb:f0
          inet addr:199.247.241.210  Bcast:199.247.241.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe27:fbf0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2983 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000
          RX bytes:1185098 (1.1 MB)  TX bytes:219266 (214.1 KB)
          Interrupt:23 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53960 (52.6 KB)  TX bytes:53960 (52.6 KB)



command 2 is as follows :  bridge name     bridge id               STP enabled     interfaces        tnx for your help so far

"199.247.241.210" is not a LAN IP. As I said, I assumed your Linux server was connecting to a LAN. A bridge will not work. You need NAT.
[http://ubuntuforums.org/showthread.php?p=5923531](http://ubuntuforums.org/showthread.php?p=5923531)

---

### Post by snowstorm167 on 2008-10-09
i have tryed these steps you have given me but still no luck



am i useing the right line to do this hookup (ethernet)

---

### Post by cdenley on 2008-10-09
> **snowstorm167 said:**
> i have tryed these steps you have given me but still no luck



am i useing the right line to do this hookup (ethernet)

Which thread are you referring to? I already told you a bridge will probably not work since your server is connected directly to the internet. Sorry for my incorrect assumption. Your question is almost identical to the thread I linked to.

The reason a bridge will not work is it binds the two networks you are connected to as if they were on the same switch. Both your computers would be clients on the same network. They would each expect to be assigned an IP address. However, your ISP is not going to give you two WAN IP's. NAT would allow your two computers to share a single WAN IP. Once again, you need NAT routing, forget about a bridge. Either configure NAT on your Linux computer, or buy a router.

---

### Post by snowstorm167 on 2008-10-09
i am trying to setup the nat way and it does not work either i tred another way as well this is the link  [http://revsys.com/writings/quicktips/nat.html](http://revsys.com/writings/quicktips/nat.html) and these steps tell me to install dhcp and that is already in.


my laptop tells me a wire is not attached to the net the os on the macine i am doing this on is hardy x64 server (desktop)     laptop is windows xp pro

---

### Post by cdenley on 2008-10-09
> **snowstorm167 said:**
> i am trying to setup the nat way and it does not work either i tred another way as well this is the link  [http://revsys.com/writings/quicktips/nat.html](http://revsys.com/writings/quicktips/nat.html) and these steps tell me to install dhcp and that is already in.


my laptop tells me a wire is not attached to the net the os on the macine i am doing this on is hardy x64 server (desktop)     laptop is windows xp pro

You already have a dhcp server which assigns static LAN addresses? If not, it would be simpler to assign static IP's.

You need a crossover cable, not a patch cable, to connect one computer to another.

---

### Post by snowstorm167 on 2008-10-09
how do I assign static ip and is the cable you meantioned a data transfer one or is it dif  


      thanks for your help so far

---

### Post by cdenley on 2008-10-10
> **snowstorm167 said:**
> how do I assign static ip and is the cable you meantioned a data transfer one or is it dif

If you're using the ubuntu desktop, you should be able to do it from:
System>Administration>Network
Otherwise:
[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

It's not called a "data transfer" cable, but I think we're talking about the same thing. A crossover cable is used to go from one computer to another. A patch cable goes from a computer to a network device (switch, router). Technically, all cables transfer data, but a crossover cable is often used to network two computers directly to transfer files from one to another.

---

### Post by snowstorm167 on 2008-10-10
i think your right about the type i have a cat 5e
I looked it up at the store I bought it from and it says it is a crossover patch cable

but yet still no luck  


   is there something i need to do to windows   

  I also get a message from my linux that says card eth1 is not ready

---

### Post by cdenley on 2008-10-10
> **snowstorm167 said:**
> i think your right about the type i have a cat 5e
I looked it up at the store I bought it from and it says it is a crossover patch cable

but yet still no luck  


   is there something i need to do to windows   

  I also get a message from my linux that says card eth1 is not ready

crossover patch cable? There are two different types of ethernet cables: crossover and patch. When you connect to your cable modem, router, or switch, you use a patch cable. When you connect to another computer, you use a crossover cable.

[http://en.wikipedia.org/wiki/Crossover_cable](http://en.wikipedia.org/wiki/Crossover_cable)

It sounds like you're either using the wrong cable, or you have a bad cable.

---

### Post by snowstorm167 on 2008-10-10
it looks like the store sold me the wrong one

  it has stamped on it the following 

 belkin corporation 5e patch cable #r7j304 utp 24awg type cm (ul) c(ul) e164469-f3 etl verified to tia/eia-568-b.2



   the laptop says limited or no connectivity

---

### Post by snowstorm167 on 2008-10-10
this is the info for where i bought my wire and it is the same one

  	The RJ45 CAT 5e UTP crossover cable with molded strain relief is designed to connect Hub-to-Hub, PC-to-PC or Mac to Mac. Features RJ45 male-to-male connectors and a molded strain relief. Manufacturer's lifetime guarantee.

    * Features: Perfect in conjunction with 10 and 100 Base-T networks.
    * 50 micron gold plated connectors to ensure a clean and clear transmission.
    * Molded strain relief provides extra security around connector.
    * Exceeds the performance requirement of Category 5e.

---

### Post by cariboo on 2008-10-10
I don't know if I can explain it any better. The cable you have is the right cable to connect between your two computers. You should make sure you can communicate back and forth between the two.

Before continuing please read the instructions first and remember to make backups of every file you modify first before doing anything.

Step 1. Set a static ip address for eth1 (assuming you are using eth1 to connect to the other computer) at the command prompt (this also assume you are running your server without a gui) edit /etc/network/interfaces:

```
sudo nano /etc/network/interfaces
```

Enter your password when asked. Add this to the bottom of the file.

```
auto eth1
iface eth1 inet static
address 192.168.1.100
netwmask 255.255.255.0
broadcast 192.168.1.255
gateway XXX.XXX.XXX.XXX

```

Where XXX.XXX.XXX.XXX is the ip address of eth0. Press Ctrl-o to save and Ctrl-x to exit.Now restart networking:

```
sudo /etc/init.d/networking restart
```

Step 2. Now it is time to go to your other  computer and set the static ip address there. Press Alt-F2 and enter the following:

```
gksu gedit /etc/network/interfaces
```

Enter your password when asked:

Delete any lines referencing eth0 then type:

```
auto eth0
iface eth0 inet static
address 192.168.1.101
netblock 255.255.255.0
broadcast 192.168.1.255
gateway XXX.XXX.XXX.XXX
```

Where XXX.XXX.XXX.XXX is the same as you entered for the gateway above. Save and exit. Open a Applications-->Accessories-->Terminal and type the following:

```
sudo /etc/init.d/networking restart
```

If you typed everything correctly the restart command should echo OK.

Step 3. It is time to check if the two computers can communicate. Go to System-->Administration-->Network Tools-->Ping enter the ip address from the other computer in Nettwork Address:

```
192.168.1.100
```

Then click the ping button.THe result should look something like the attached screenshot. At least I hope it looks like the attached screenshot I'm running Intrepid, so thing might look a little different.

Step 4. Now go back to your server, we need to set up IP forwarding. At the prompt type:

```
sudo nano /etc/sysctl.conf
```

ENter your password when asked. Look for the following line:

```
#net.ipv4.conf.default.forwarding=1
```

remove the # sign from the start of the line. Pres Ctrl-o to save the file then Ctrl-x to exit. you have to edit one more file before your done:

```
sudo nano /etc/rc.local
```

Enter your password when asked. Add the following line before the **exit 0**

```
sysctl -w net.ipv4.ip_forward=1
```

Press Ctrl-o to save, Ctrl-x to exit. Now just repboot and you should be ready to surf.

You should also set up a firewall, but that is beyond me at this point. I use a router to do the above. 

Jim

---

### Post by cdenley on 2008-10-10
> **cariboo907 said:**
> The cable you have is the right cable to connect between your two computers.

The description from the store describes the correct cable. However, if it says "belkin corporation 5e patch cable", it is the wrong cable, and not the one described. To verify, if you look at the colored wires inside the connector at each end, they should be arranged in a different order. See the link I posted if you want a diagram.

---

### Post by snowstorm167 on 2008-10-11
yes i thought of checking the wires inside and dif order


the command alt+f2 does not work on windows xp pro

---

### Post by lisati on 2008-10-11
> **snowstorm167 said:**
> 

the command alt+f2 does not work on windows xp pro

but the key combiination will work with Ubuntu and will allow you to put in the suggested gksu .... command

---

### Post by cariboo on 2008-10-11
Oops, I assumed you working with two Ubuntu computers, Go to Start-->Control Panel-->Network Connections-->Local Area Connection, rick click on Local area Connectios and then click Properties in the Window that pops up highlight Internet Protocol and click the Properties button. Click the radio button beside Use the following ip address then enter the information in my previous post.

Jim

---

### Post by snowstorm167 on 2008-10-12
well i have done all the steps to install the other comp but my linux machine not finding windows

windows connected but not going online 


you guys are a big help and i thank you again

---

### Post by snowstorm167 on 2008-10-15
how can I reset my network to defaults

---

### Post by snowstorm167 on 2008-10-19
I have a major problem now I can not use my pc for net at all 
I have tryed 4 dif windows to fix the prob all have same thing going on I even put the proper net driver in so it could go on line now it can not find the net at all

---

### Post by snowstorm167 on 2008-10-19
well i found the prob with my net and maybe with my internal network
my bios has a net maneger built in

---

