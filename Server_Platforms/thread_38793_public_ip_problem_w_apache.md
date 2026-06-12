---
title: "public ip problem w/ apache"
date: 2005-06-02
forum: Server Platforms
---

### Post by dfghost on 2005-06-02
i have a 2-wire SBC DSL home portal gateway.  It's ip is obviously private because they are all the same and can only be accessed by the lan connection to the computer.  Thus, i have apache on my ubuntu computer set up, the ip works on the private network, but not anywhere outside the network.  I think port 80 is on listen.  When i go anywhere else and type in my computer's ip, it says cannot be found.  I also know that making a private network public is possible because i have a friend that has a linux machine and a private network, but you can still access his server either through ip or his web domain that he bought.  So, how do i allow my server to comunicate to the world and the world to communicate to my server?  Any help would  be appreciated, thanks in advace.

---

### Post by dataw0lf on 2005-06-02
What IP are you assigned by your ISP?  If it's static, just figure it out, enable port forwarding on your gateway to your internal Ubuntu machine, and outside the network point computers toward the static ip.  If it's a dynamic IP, you're going to have to use something like dyndns.org.

---

### Post by NewbieNik on 2005-06-02
[QUOTE=dfghost]i have a 2-wire SBC DSL home portal gateway.  It's ip is obviously private because they are all the same and can only be accessed by the lan connection to the computer.  Thus, i have apache on my ubuntu computer set up, the ip works on the private network, but not anywhere outside the network.  I think port 80 is on listen.  When i go anywhere else and type in my computer's ip, it says cannot be found.  I also know that making a private network public is possible because i have a friend that has a linux machine and a private network, but you can still access his server either through ip or his web domain that he bought.  So, how do i allow my server to comunicate to the world and the world to communicate to my server?  Any help would  be appreciated, thanks in advace.[/QUOTE]

DatawOLf is spot on. 
Lets say your IP address from your supplier is 1.2.3.4 then your gateway has that address on the internet and 192.168.0.1 on your network and your Ubuntu box will probably be 192.168.0.100.
You need to configure your gateway to foward traffic on port 80 to 192.168.0.100 so it hits your Ubuntu box. Otherwise your gateway is the only thing that traffic from the intenet is seeing.

Beware of port-fowarding though. Ensure that you know what each port does and how to secure your Ubuntu box. If you are not 100% sure ask around. An unsecured PC open to the internet is as bad as you can get.

---

### Post by dfghost on 2005-06-03
[QUOTE=NewbieNik]DatawOLf is spot on. 
Lets say your IP address from your supplier is 1.2.3.4 then your gateway has that address on the internet and 192.168.0.1 on your network and your Ubuntu box will probably be 192.168.0.100.
You need to configure your gateway to foward traffic on port 80 to 192.168.0.100 so it hits your Ubuntu box. Otherwise your gateway is the only thing that traffic from the intenet is seeing.

Beware of port-fowarding though. Ensure that you know what each port does and how to secure your Ubuntu box. If you are not 100% sure ask around. An unsecured PC open to the internet is as bad as you can get.[/QUOTE]

OK, i looked up on dyndns.org, set up a domain name, put in all of the ip's that the gateway would give me, and oppened the firewall wide open on that machine.  So why doesn't it work still.  It shows up on my computers actually connected to the gateway, but not on anyother one.  Please help.  Thanks

---

### Post by dfghost on 2005-06-03
yes.  I opened the firewall, rebooted, set a domain, and bang she's up.
Thank's guys.  It's ongoing but you can visit @ [http://rainbowopera.homedns.org](http://rainbowopera.homedns.org)

---

