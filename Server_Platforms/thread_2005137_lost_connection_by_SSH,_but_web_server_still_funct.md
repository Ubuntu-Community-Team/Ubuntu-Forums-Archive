---
title: "lost connection by SSH, but web server still functional, ideas?"
date: 2012-06-17
forum: Server Platforms
---

### Post by anon0 on 2012-06-17
[edit: title is wrong, web server was down, I was just viewing the cache]

I suddenly lost SSH connection to the Ubuntu server. It's giving me a Connection Timed Out message in PuTTy. I can not access the phpMyAdmin interface or any of the web pages. I do have access to the server's shared files from the local network. I rebooted the server but it's acting the same way. I can't do anything by SSH due to the lack of connection. Some tips?

This happened some time after I ran a PHP script to insert a large number of rows, which seems to have exceeded the default limit and halted the script. Does this sound like a related issue, or can anyone think of other reasons why this may have happened?

Edit: well, apparently the router for some reason decided to suddenly change the server's IP address on the LAN, causing the disconnections. Guess this is a network problem...

---

### Post by Robinio on 2012-06-17
Does your Router has DHCP enabled?
And is your new Server Adress in the DHCP Range?

I also had the Problem, and the I found out, that my ubuntu server was in the DHCP range of my router. 

When I edited the /etc/network/interfaces, so it gives me an static ip out of the DCPH range it worked.
(I had to change it two times, because the first time i messed it up and gave the server a static ip which my wireless repeater already had. So watch out that you don't pick a IP which is already used).

---

### Post by anon0 on 2012-06-17
> **Robinio said:**
> Does your Router has DHCP enabled?
And is your new Server Adress in the DHCP Range?

I also had the Problem, and the I found out, that my ubuntu server was in the DHCP range of my router. 

When I edited the /etc/network/interfaces, so it gives me an static ip out of the DCPH range it worked.
(I had to change it two times, because the first time i messed it up and gave the server a static ip which my wireless repeater already had. So watch out that you don't pick a IP which is already used).

Can we assign an IP outside of the DHCP range without issues, ie. as long as it's in the same LAN?

---

### Post by darkod on 2012-06-17
> **anon0 said:**
> Can we assign an IP outside of the DHCP range without issues, ie. as long as it's in the same LAN?

Of course, that's the point of it. In fact, the static IPs used on a LAN always have to be outside the dhcp range, but within the range used on the LAN.

Otherwise the dhcp server might try to allocate to some workstation the same IP you have set on your server.

And while talking about the dhcp, I assume you didn't leave the server network configured as dhcp because that's what it tries first during install. You do have static IP right?

---

### Post by anon0 on 2012-06-17
I need to modify /etc/network/interfaces, trying to follow some instructions. Please correct me if my comments below are wrong:

auto eth0
iface eth0 inet static
address 192.168.X.Y
 //^ this is the static IP I want to assign 

netmask 255.255.255.0
 //leave this unchanged

network 192.168.X.0
 // X is based on the LAN, but leave the 0? (what's this for?)
 
broadcast 192.168.X.255
 // X is based on the LAN, but leave the 255? (what's this for?)

gateway 192.168.X.Z
 // this is the IP of the router

Edit: I think these assumptions are wrong because I'm reading examples with different values...

---

### Post by darkod on 2012-06-18
The example you posted is correct. The network and broadcast values are used for communication on the LAN but they are not necessary because it can calculate them according to the IP address and the netmask.

One more value you can put there is the dns-nameservers which is the value of the DNS servers you want the server to use. In fact, if I'm not mistaken, with the latest 12.04 version you have to put the DNS servers in there, while in earlier versions it also works if the DNS servers are in /etc/resolv.conf.

So, the entry in /etc/network/interfaces would look like:
auto eth0
iface eth0 inet static
   address 192.168......
   netmask 255.255.255.0
   gateway 192.168......
   dns-nameservers x.x.x.x y.y.y.y

That would be it.

---

### Post by anon0 on 2012-06-19
Alright, for dns-nameservers I've entered my ISP's DNS servers' addresses. But I noticed that my /etc/resolv.conf includes the following:

domain domain.invalid
search domain.invalid
nameserver 192.168.X.Y
nameserver 192.168.X.Y


The last two lines are the same: the address of my router. Should either of these still be there?

---

### Post by spynappels on 2012-06-19
I would normally place all dnsservers in /etc/resolv.conf, and I'd put your router as one, and the other DNS servers you use as the other entries. I also tend to use Google's DNS servers rather than my ISP ones as they give me better performance.

FYI, the google servers can be found at 8.8.8.8 and 8.8.4.4. as well as a few others around this IP range.

---

### Post by darkod on 2012-06-19
> **spynappels said:**
> I would normally place all dnsservers in /etc/resolv.conf, and I'd put your router as one, and the other DNS servers you use as the other entries. I also tend to use Google's DNS servers rather than my ISP ones as they give me better performance.

FYI, the google servers can be found at 8.8.8.8 and 8.8.4.4. as well as a few others around this IP range.

As I already mentioned, according to reports this would work for previous versions except the latest 12.04. In 12.04 the way DNS is configured was changed and the recommended way is to use dns-nameservers because the /etc/resolv.conf seems to be created automatically and not to be edited.

So it might be a good practice for the future to start avoiding to edit /etc/resolv.conf.

Besides, we still don't know what version of the Server are we talking about here.

---

### Post by anon0 on 2012-06-19
> **darkod said:**
> As I already mentioned, according to reports this would work for previous versions except the latest 12.04. In 12.04 the way DNS is configured was changed and the recommended way is to use dns-nameservers because the /etc/resolv.conf seems to be created automatically and not to be edited.

So it might be a good practice for the future to start avoiding to edit /etc/resolv.conf.

Besides, we still don't know what version of the Server are we talking about here.

Yes I read some users saying that their /etc/resolv.conf would reset after a restart. 

However, my Ubuntu box just reverted back to dynamic IP again, being assigned one in the DHCP range. Even though /etc/network/interfaces has been edited (and seemed to work initially). Some ideas?

I'm on 11.10.

Maybe this is a bug? I see several others reporting this issue on 11.10.
[http://ubuntuforums.org/showthread.php?t=1898637&page=2](http://ubuntuforums.org/showthread.php?t=1898637&page=2)

Update: I rebooted and it got assigned the static IP again. I'll report back if I get another IP change.

---

### Post by darkod on 2012-06-19
Is there some sort of setup in the router to tie a particular IP to the server MAC address or similar? If there is, that might force it to have that IP (change it).

Other than that, if the /etc/network/interfaces was edited correctly, I see no way that the server can change the IP.
You assigned a static IP outside of the dhcp range, right?

---

### Post by anon0 on 2012-06-19
> **darkod said:**
> Is there some sort of setup in the router to tie a particular IP to the server MAC address or similar? If there is, that might force it to have that IP (change it).

Other than that, if the /etc/network/interfaces was edited correctly, I see no way that the server can change the IP.
You assigned a static IP outside of the dhcp range, right?

If the router has such a setup, I can't see it. Yes I set it outside the DHCP range. I haven't encountered the problem again, but I'll keep an eye on it.

---

