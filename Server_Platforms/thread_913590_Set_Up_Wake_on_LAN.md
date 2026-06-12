---
title: "Set Up Wake on LAN"
date: 2008-09-07
forum: Server Platforms
---

### Post by Kain000 on 2008-09-07
Hey everyone, 
I've been trying to set up a wake on lan operation for my server at home so i can turn it on when I need it rather than have it suck power all day long.

So I've installed wakeonlan and have been sucessfull with using it over my home network using the comand 

wakeonlan 00:00:00:00:00:00 (mac address) and it works fine
from the usage model below I was hopeing that someone could tell me the format it wants me to put my comands into 
for example to send the magic packet from outside my network I would need to specify an Ip and port and then the mac address.    
Its worked from one of those remote wake sites that just need my ip and mac address.

I dont understand however how it wants me to imput it.


sean@Inspiron:~$ wakeonlan
Usage
    wakeonlan [-h] [-v] [-i IP_address] [-p port] [-f file] [[hardware_address] ...]

Options
    -h
        this information
    -v
        displays the script version
    -i ip_address
        set the destination IP address
        default: 255.255.255.255 (the limited broadcast address)
    -p port
        set the destination port
        default: 9 (the discard port)
    -f file 
        uses file as a source of hardware addresses

See also
    wakeonlan(1)

---

### Post by volkswagner on 2008-09-08
It is a little different outside lan.  Since the pc is not on the ip address is not readable.  You need to activate this through the router.  The following site helped me. This was for my particular router.  If yours is different, you may want to google your router model and WOL.

The main things are changing the subnet and forwarding port 9 to the proper machine ip.  Be aware, when changing the subnet, your existing machines, should have their network interfaces reconfigured.  You may want to record 

For linux machines
```
ifconfig
```


For windows
```
ipconfig
```



[http://n01getsout.com/blog/2006/11/16/wake-on-lan-on-linux-with-a-linksys-wrt54g/]("http://n01getsout.com/blog/2006/11/16/wake-on-lan-on-linux-with-a-linksys-wrt54g/")

---

### Post by Kain000 on 2008-09-08
thanks for the reply, I already have my router set up to foward port 9 from any outcoming ips to my server's interinal ip, witch is assigned by it's mac address.  so thats not a problem, I've already tested it from an online utitality.  my question is how would i enter the command, acording to the output wakeonlan gave me to specify 
1)my boradcast address (routers ip)
2)mac address of the card in my server 
3)port number to talk threw.
this together is enough to get to my server and power it on, but I just cant figure out how the program wants me to enter the above information.

---

### Post by Meson on 2008-09-08
```

wakeonlan -i 101.202.1.2 -p 9 00:99:EE:33:AA:1B

```

You need to send the magic packet to your public IP address.  You might as well specifiy the port manually (so you can do anything you'd like 9 is just the deafult).  Whichever port you choose to use, you need to forward it from your home router/nat device.

You can forward it to 255.255.255.255, 192.168.1.255, or 192.168.1.100 (where .100 is your computers address)

---

### Post by Kain000 on 2008-09-10
> **Meson said:**
> ```

wakeonlan -i 101.202.1.2 -p 9 00:99:EE:33:AA:1B

```

You need to send the magic packet to your public IP address.  You might as well specifiy the port manually (so you can do anything you'd like 9 is just the deafult).  Whichever port you choose to use, you need to forward it from your home router/nat device.

You can forward it to 255.255.255.255, 192.168.1.255, or 192.168.1.100 (where .100 is your computers address)

Alright thankyou for your help, the program wakeonlan accepted this and came back saying it's sending the magic packet, however nothing happens.  I dont think there is anything as far as configuration goes because i Have used the web baised wake on wan 's that just use an ip address and macaddress.

---

### Post by volkswagner on 2008-09-10
> **Kain000 said:**
> Alright thankyou for your help, the program wakeonlan accepted this and came back saying it's sending the magic packet, however nothing happens.  I dont think there is anything as far as configuration goes because i Have used the web baised wake on wan 's that just use an ip address and macaddress.

Do you mind telling us what app you are using.  I hit the same wall when trying to use my phone and JWakeME.  There were so many settings, I did not know what to enter in each field.

---

### Post by Kain000 on 2008-09-10
hey voltswagner, 
This is one of the sites that came up when I googled wake on WAN
[http://www.lchu.net/wowASP/wow.asp](http://www.lchu.net/wowASP/wow.asp)
It apears to only need a broadcast address (public IP) and the mac address of the hardware that will be listning on that network for it's magic packet.   also you need the port that you forwarded threw your NAT router if aplicable.  
However I cannot figure out how do do this threw the program wakeonlan in ubuntu.  It seems like it should be capiable because it allows you to specify an ip for the network and a mac address on that network.

---

### Post by Uzi on 2008-09-10
Hey, thanks, helped me a lot

---

### Post by volkswagner on 2008-09-10
> **Kain000 said:**
> hey voltswagner, 
This is one of the sites that came up when I googled wake on WAN
[http://www.lchu.net/wowASP/wow.asp](http://www.lchu.net/wowASP/wow.asp)
It apears to only need a broadcast address (public IP) and the mac address of the hardware that will be listning on that network for it's magic packet.   also you need the port that you forwarded threw your NAT router if aplicable.  
However I cannot figure out how do do this threw the program wakeonlan in ubuntu.  It seems like it should be capiable because it allows you to specify an ip for the network and a mac address on that network.


Hey you just gave me a new nickname.  It just might stick since I am an electrician.  LOL

In the above statement you should be using the mac address of the router correct.  Since the pc is off, the router will direct the forward to the correct box.......just to clarify.....

I am going to give this another go, since I got my MacDaddy (Nokia N95-4).

---

### Post by Kain000 on 2008-09-11
haha sorry about that, wolkswagner.  Perhaps it will!  Sorry been thinking too much of my electronics course. anyhow what do you mean my routers mac?  This may be why I cannot get magic packets to work outside the LAN.   I've done nothing with the mac address of the router.  I've used the IP the router is broadcasting on.   As I understood the process (and obviously that understanding is not complete or I would of had this working like 3 posts ago lol.) that all that was needed was the Ip of the router to get the packet that far, and the port that it comes to the router on will have to be fowarded to the pc I want to wake.  witch I have done.  and the mac address is just to generate the magic packet that the card is listning for.     I didnt know that the router's Ip played into it at all.    

my command is :
```
wakeonlan -i 76.120.108.222 -p 9 01:2b:3t:6g:3g:56
```
and it will output "sending magic packet to 76.120.108.222:p (my routers public ip on port 9) with 01:2b:3t:6g:3g:56 (mac address of the network card)
so the program accepts this and is sending somthing, but for some reason it wont wake it up.  Within my home network I can use this same command and it works fine, also does just the command 
```
wakeonlan 01:2b:3t:6g:3g:56
```

So I'm not sure what I'm not giving the program that it needs to work, espacially because the website from my last post works from the net and doesnt require any more info than the public IP, port number, and mac address.    
What is it doing that wake on lan is not??? 
this is really driving me nuts because it seems like it should work.

---

### Post by volkswagner on 2008-09-11
> **Kain000 said:**
> 

So I'm not sure what I'm not giving the program that it needs to work, espacially because the website from my last post works from the net and doesnt require any more info than the public IP, port number, and mac address.    
What is it doing that wake on lan is not??? 
this is really driving me nuts because it seems like it should work.

Sorry about the mis-information.  I don't think the router mac is used.  I had wrote that from memory.  I guess my memory fails me. 

The linked site you are using also requires the subnet.  I think this is giving my trouble. 

One thing to keep in mind, is how your machine is shutdown.  When my backend shutsdown via ACPI wake command, the WOL does not work.  :(

This is a big bummer for me, since this is the machine I want to wake, in case I want to schedule, or watch a recording and the machine is off. 

I am not sure if wakeonlan is designed to work outside the network.

I see the utility at ichu.net modify the information to a broadcast address.

I could not get my system to wake at ichu.net.  I did however get it to wake at [http://www.dslreports.com/wakeup](http://www.dslreports.com/wakeup).

Still working on a solution from my phone, and issue with ACPI wake.

EDIT: Found this in the README for wakeonlan

3. How is it implemented here ?

The scripts takes 2 arguments, the MAC-address of the NIC, and an IP
address. The IP-address is tricky :

For a NIC on your local subnet, use the broadcast-address of this subnet.
(e.g. subnet 192.168.10.0 with netmask 255.255.255.0, use 192.168.10.255)

For waking up a PC on a network behind one or more routers, some tricks must
be used. When the routers forward directed subnet broadcasts, it is possible
to use the broadcast address of the destination network. The problem is that
many routers dont forward broadcast packets, so the packet will never arrive
at the network.

It is possible to send the packet to the remote net however, by sending it
to the IP address of another host on that network that's alive at that
moment. The remote hosts will probably ignore the packet, but it has been
seen by the listening NIC that's also on the same subnet, and it will turn
on the computer... Feel free to experiment on this.

---

### Post by Meson on 2008-09-11
From where are you sending the signal using wakeonlan?  Is it at a school that possibly restricts outgoing information and religates it to things like http, pop, smpt, etc.  You might try it from a friend's house nearby.

If you are entering the same IP address and MAC address at dslreports.com/wakeup that are you using wakeonlan - then I can't think of any obsticle other than the firewall of the network you're currently behind.

---

### Post by volkswagner on 2008-09-13
I thought I had an issue due to changing the subnet mask in the router settings, after setting up wakeonlan script.  I made this change due to info found at dsl site mentioned earlier.

After editing the script wakeonlan to reflect subnet=255.255.255.128 to match my current router setting.  Local wake on lan failed and I get an "invalid argument at line 126".

here is line 126 from /usr/bin/wakeonlan.
```

send(S, $pkt, 0, $them) or die "send : $!";
```




Still can only get it to wake outside lan via web utitlity, not any external programs.  

Wonder if it is a router limitation.  I would love to know what the web utility does differently.

I guess I'll need to clutch the online utility.  I hope I can get acpi wake and wakeonlan to play.

---

### Post by Meson on 2008-09-14
You could also try the program etherwake, which is in the repositories.

---

### Post by Kain000 on 2008-09-14
> **volkswagner said:**
> I thought I had an issue due to changing the subnet mask in the router settings, after setting up wakeonlan script.  I made this change due to info found at dsl site mentioned earlier.

After editing the script wakeonlan to reflect subnet=255.255.255.128 to match my current router setting.  Local wake on lan failed and I get an "invalid argument at line 126".

here is line 126 from /usr/bin/wakeonlan.
```

send(S, $pkt, 0, $them) or die "send : $!";
```




Still can only get it to wake outside lan via web utitlity, not any external programs.  

Wonder if it is a router limitation.  I would love to know what the web utility does differently.

I guess I'll need to clutch the online utility.  I hope I can get acpi wake and wakeonlan to play.

Hummm, 
what is the exact command you issue to wake on lan?
it should be (when logged onto your home network) just the mac address of your computers hardware.  wake on lan will push this magic packet to everything on the network  and everyone but the target computer will discard the packet.  Just make sure you have a (usually port #9) port open and forwarded to your target under port mapping or NAT routing or w/e the tab is in your router's set up app.   
By the way what router are you using?  
also how are you shutting down your computer?  I dont suppose this could be the problem as you've gotten the packet form the internet to work, thus passing both the NAT firewall and shutdown tests.   The only thing I can think of doing From inside the network is to try these. (insert correct mac address and or ip/port)

```
wakeonlan 00:00:00:00:00:00
```
or
```
wakeonlan -i 23.45.67.891 00:00:00:00:00:00
``` your routers public ip and the mac of your target's network card
or 
```
wakeonlan -i 23.45.67.891 -p 9 00:00:00:00:00:00
```your ip, and port forwarded (guessing it's port #9) and mac address.

Technically from inside your network you should get away with just using the first example, as wakeonlan should, if no network address is specified, push the magic packet to the entire subnet of the network (every computer on your lan) and if connected the computer that it's for will hear it and wake up.

Try em and let me know
-sean

---

### Post by volkswagner on 2008-09-15
> **Kain000 said:**
> Hummm, 
what is the exact command you issue to wake on lan?
it should be (when logged onto your home network) just the mac address of your computers hardware.  wake on lan will push this magic packet to everything on the network  and everyone but the target computer will discard the packet.  Just make sure you have a (usually port #9) port open and forwarded to your target under port mapping or NAT routing or w/e the tab is in your router's set up app.   
By the way what router are you using?  
also how are you shutting down your computer?  I dont suppose this could be the problem as you've gotten the packet form the internet to work, thus passing both the NAT firewall and shutdown tests.   The only thing I can think of doing From inside the network is to try these. (insert correct mac address and or ip/port)

```
wakeonlan 00:00:00:00:00:00
```

-sean

Yes, when inside my lan, I use the mac address of the target pc.  

I noticed wakeonlan displayed

```
Sending magic packet to 255.255.255.255:9 with 00:xx:xx:xx:xx:xx
```
This works.  Odd thing is my subnet is 255.255.255.128.  If I change my subnet in wakeonlan script, that is when I get the error and wakonlan fails.

Router-Linksys WRT54G ver. 8, firmware ver. 1.02.0
I shut down using sudo halt and all is ok.  When ACPI wake command sets the shutdown, wakeonlan Fails.

---

### Post by volkswagner on 2008-09-15
OK, got it working.

I am using microWow from google-code.

Via my Nokia N95 my settings are as follows

Name-AnyName
Network:
    Host-volkswagner.com
    Port-9
    Mac-my:ma:ca:dd:re:ss
Packets to send-1

It works both via my wifi (lan) and GPRS connection (outside lan).

:guitar:

---

### Post by Kain000 on 2008-09-16
Excelent my friend! so this microWOW is for any os?  I looked on the download page and cannot find a specific os.  How'd you get it on your phone?

---

### Post by volkswagner on 2008-09-16
> **Kain000 said:**
> Excelent my friend! so this microWOW is for any os?  I looked on the download page and cannot find a specific os.  How'd you get it on your phone?

It is a MIDlet.  It is a java app for embeded devices such as any mobile phone that can run java apps.

I just downloaded it and installed all via my phone.

This was my ultimate goal, since I can easily wake my machine from home and anywhere there is cell service.

I should also mention dyndns is resolving my host name and dynamic ip.

---

### Post by jamesrfla on 2008-09-17
Don't you have to edit IP tables to allow port 9 through your firewall on Ubuntu?

---

### Post by Kain000 on 2008-09-18
> **jamesrfla said:**
> Don't you have to edit IP tables to allow port 9 through your firewall on Ubuntu?

no, because when trying to wake a powered off computer ip tables is not running so there is no firewall to speak of until the computer is booted.   However you do have to foward the port from your router.




Hey volkswagoner, 
did you run into any other problems configureing microWOW?  I've used those settings (replacing my numbers ofcourse)  and it will tell me
1: proceding to remote system wake up
2:sending magic packet.....can't send magic packet.
nothing else, not sure why.
i've got my host ip, port and mac address.
any ideas?

---

### Post by volkswagner on 2008-09-18
> **Kain000 said:**
> 

Hey volkswagoner, 
did you run into any other problems configureing microWOW?  I've used those settings (replacing my numbers ofcourse)  and it will tell me
1: proceding to remote system wake up
2:sending magic packet.....can't send magic packet.
nothing else, not sure why.
i've got my host ip, port and mac address.
any ideas?

Not sure here.  I am not sure why it is not working.  It seems to me the key was to use my hostname.  Now it even works with the ip provided by my ISP.  Make sure you have used colons for the mac address.  I am not using a password so security check box is unchecked.

It works with external ip and mac of target machine.  Works within my lan and via gprs data connections.  Not sure where the logs go, but it should create a log file. 

Did the app get proper permissions to connect to the net?  What device are you running?

---

### Post by Kain000 on 2008-09-18
I've got it running on an AT&T tilt.  I'll check the logs and see if it ever got out.
thanks though.

---

### Post by volkswagner on 2008-09-19
Try to reboot your tilt.

---

