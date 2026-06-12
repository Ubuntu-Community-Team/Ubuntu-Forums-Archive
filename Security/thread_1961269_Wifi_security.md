---
title: "Wifi security"
date: 2012-04-18
forum: Security
---

### Post by donwolfani on 2012-04-18
ok so im thinking of getting internet set up at home when i can finally afford it so i can stop using public wifi for everything but there are a few things i need to know.

first of all i know your wireless router/server/ and whatever else that makes up your network can keep logs of traffic and which machines have made that traffic

i also have already learned about how to view/ temporarily change my mac address   but not how to permanately change it.

im also still a noob at anything security or really more than surfing the web really so is it ok if i ask around a few things i will want/need to know?

basicly i need to know what besides mac address can be logged by a network and how to configure those on my machine so each one can be as unique to my machine as i need to assist in identification both of what is on my wifi once i set it up but what it is doing on it as well.

basicly i am going to be more than likely sharing a wifi between me and room mates and we will all be pitching in, and since i am smart enough to know that sometimes illegal things get done over wifi by ppl who sometimes are just "borrowing" the wifi connection of a neighbor i want to be able to strictly display and identify my machine by such things as it's mac and hostname that way i can honestly say it wasn't my machine involved if someone does something.   and thus be able to know i am safe atleast that much as well as being able to share that with my roomates so they can take the same steps to ensure all info about their machine can clearly be distinct from that of others on the network.

sorry for being lengthy

---

### Post by Hungry Man on 2012-04-19
Your router will log your IP and MAC. It does this so that it can differentiate each device and route data to multiple devices. This isn't a security issue.

It depends... it could log a lot of different things. I wouldn't worry about it. I don't think it logs your information correlated with the MAC but I don't know.

Your router than has its own IP address and that's what every server sees.

Make sure you're using WPA2 and at least an 8 character (recommended 12) password.

Also, when you go to your routers IP address (just type in 192.168.1.1 [or whatever it is]) you should change the Admin information for logging into it.

---

### Post by anejo on 2012-04-19
Just to add to Hungry Man's post... I would also:
- make the SSID hidden
- change the Admin password
- and optional... consider using an OpenDNS IP for DNS

---

### Post by kurt18947 on 2012-04-19
> **anejo said:**
> Just to add to Hungry Man's post... I would also:
- make the SSID hidden
- change the Admin password
- and optional... consider using an OpenDNS IP for DNS

definitely on points 2 & 3.  Use a strong network key.  Hiding the SSID seems to be of limited utility because there are utilities that can easily 'discover' hidden SSIDs.  There was a white paper that claimed hiding your SSID was actually less secure than broadcasting it.

---

### Post by Hungry Man on 2012-04-19
Hiding the SSID does nothing as the packets are still in the air. Any tool that is used to bruteforce a password to hack into Wifi in any way won't even notice that the SSID is hidden.

By hiding your SSID you're probably forcing an "Automatically connect" situation that could potentially be dangerous if the attacker spoofs a wifi hotspot.

---

### Post by Ms. Daisy on 2012-04-19
If you want to limit access then you should use WPA2.  But if you and  your roommates would end up giving the password to all your friends/  girlfriends/ acquaintances, then there's not really any point in using  WPA2.  

If you haven't bought the router yet, you may want to consider creating  two subnets; one with  WPA2 security for you & your roommates, and  one without password protection for everyone else.  Having two subnets  would keep all the traffic totally separate.  If I were in your place I  would be concerned about friends bringing in malware-infested devices  onto my network.  Keeping the subnets separate will isolate you from the  guest machines.  This option will take some research but it may be  worth it.

As for monitoring who and what's on your network, you can use wireshark  or some other network monitoring tool.  You'll need to understand basic  TCP/IP traffic to get any use out of the tools.  You can tell everyone  that you're monitoring the traffic on the open wifi network. That may be  a deterrent enough, just knowing that they would be logged.  If I were  your roommate I wouldn't want you monitoring my traffic (even if we're  great friends), so I think you'd want to come to an agreement with the  roommates that are paying for the service.

---

### Post by Ms. Daisy on 2012-04-19
Oh, and I'm not sure what you want to accomplish by changing your mac address.

---

### Post by CharlesA on 2012-04-19
> **Ms. Daisy said:**
> 
If you haven't bought the router yet, you may want to consider creating  two subnets; one with  WPA2 security for you & your roommates, and  one without password protection for everyone else.  Having two subnets  would keep all the traffic totally separate.  If I were in your place I  would be concerned about friends bringing in malware-infested devices  onto my network.  Keeping the subnets separate will isolate you from the  guest machines.  This option will take some research but it may be  worth it.

If I remember right there are home routers that can do a "guest" wireless network. Looks like the Cisco E series has that feature:

[http://fixhomenetwork.com/blog/guest-network-access-for-linksys-e1000-e2000-e3000-routers/](http://fixhomenetwork.com/blog/guest-network-access-for-linksys-e1000-e2000-e3000-routers/)

---

### Post by josephmills on 2012-04-19
set up so only certain mac address can access the wifi 

two remember that it is easier to beat the crap out of someone to get there password then it is to breaking (sometimes_) 

also keep in mind that there are not that many scum bag script kiddies out there

see to a real pentester they see that as more money in there pocket more times script kiddies want to learn how to crack wireless the more jobs they get as the more fear drives into people. 

this is what I do. On I look to see if there are vans or the fbi out side my house after that if no I run around with a chicken custom on screaming I am a elephant please dont drop the bar of soap in the shower. Then after that is all done I go over to all people that are close to my house and I kick the crap out of them with my my sandles on. this is funny sometimes because it has nothing to do with inter stellar space travel. But if I did want to go to space I would take mark with me or vise versa. 

so as you can see when utility research centers for white kids with out shin pads comes out then you are in deep dodo as there is nothing you can do but drink hot iced tea and listen to music about love. now  I find myself some times fearing the inevitable and want to get scared but then I remember I dont have a bank or car or a elephant suit so are my neighbor nice THEY BETTER BE. LOL 


but on a real not mac cloning can still happen but on a even realer note the sky can be red on days that it is going to get a ring around the moon to make sure to let us know that it is  going to be cold. 

so all in all. 

wpa2 mac address filtering  and a baseball bat for that idiot in the elephant suit 

hope this helps

---

### Post by wacky_sung on 2012-04-19
The best is still use wired instead of wifi connection. If using wifi, use WPA2 with AES with a password length of 21 characters or more. It gonna take months just to dictionary attack your password. Apart from that use a smart password.

Pentester or script kiddies will just give us cracking your password.:lolflag::lolflag::lolflag::lolflag:

---

### Post by haqking on 2012-04-19
> **wacky_sung said:**
> The best is still use wired instead of wifi connection. If using wifi, use WPA2 with AES with a password length of 21 characters or more. **It gonna take months just to dictionary attack your password**. Apart from that use a smart password.

Pentester or script kiddies will just give us cracking your password.

A dictionary attack would only work if its a dictionary word, if it is then it is easy to crack.

There are also known hash/rainbow tables for default SSID.

To OP preferably use WPA2 or Enterprise, and use full 63 chr space.

Hiding your SSID does not matter as any decent security auditing tool will show it anyways.

Peace

---

### Post by wacky_sung on 2012-04-19
> **haqking said:**
> A dictionary attack would only work if its a dictionary word, if it is then it is easy to crack.

There are also known hash/rainbow tables for default SSID.

To OP preferably use WPA2 or Enterprise, and use full 63 chr space.

Hiding your SSID does not matter as any decent security auditing tool will show it anyways.

Peace

63 Character space is way too paranoid and overkill.:lolflag::lolflag::lolflag::lolflag:

---

### Post by haqking on 2012-04-19
> **wacky_sung said:**
> 63 Character space is way too paranoid and overkill

Information entropy and bit space is more important overall than complexity so if given the option then use it, if nothing else then use simple padding to the complexity.

By all means use 12 or 20 or 30 or 63, if option is there always use the maximum if security is your concern.

Peace

---

### Post by Ms. Daisy on 2012-04-19
I think you're missing the point, though.  If you have a 63 character password and you give that password to all your friends & associates, then you may as well not have a password at all.

---

### Post by haqking on 2012-04-19
> **Ms. Daisy said:**
> I think you're missing the point, though.  If you have a 63 character password and you give that password to all your friends & associates, then you may as well not have a password at all.

im not missing anything ;-)

hence my > By all means use 12 or 20 or 30 or 63, if option is there always use the maximum if security is your concern.

A Wireless key usually has to be entered once only.

But use what works for you or what you can make work.

If you dont want it secure and want to make it easy for others using it then use WEP or Open

Peace

---

### Post by CharlesA on 2012-04-19
Don't forget that mac filtering is pretty pointless if someone actually wanted to get on your network. Spoofing MAC addresses is trivial.

I use a 63-character WPA2 key that I have on a thumb drive - if someone I know whats to access it, I can either give it to them or set it up myself.

---

### Post by haqking on 2012-04-19
> **CharlesA said:**
> Don't forget that mac filtering is pretty pointless if someone actually wanted to get on your network. Spoofing MAC addresses is trivial.

I use a 63-character WPA2 key that I have on a thumb drive - if someone I know whats to access it, I can either give it to them or set it up myself.

+1

exactly.

SSID hiding and mac filtering are of little or no consequence.

Someone who has knowledge to use the tools to crack your wireless will know all of that, if they dont then i wouldnt worry about them cracking your wireless anyways.

---

### Post by Ms. Daisy on 2012-04-19
> **CharlesA said:**
> Don't forget that mac filtering is pretty pointless if someone actually wanted to get on your network. Spoofing MAC addresses is trivial. 
+1, that's where I was going with my comment earlier.

---

### Post by Ms. Daisy on 2012-04-19
> **haqking said:**
> im not missing anything ;-)
 
hence my 
 
A Wireless key usually has to be entered once only.
 
But use what works for you or what you can make work.
 
If you dont want it secure and want to make it easy for others using it then use WEP or Open
 
Peace
Don't know if you read the OP or not ;)
He wants the network available for friends but also wants it secure. I suggested subnets, what other options are there to achieve both simultaneously?

---

### Post by CharlesA on 2012-04-19
> **Ms. Daisy said:**
> Don't know if you read the OP or not ;)
He wants the network available for friends but also wants it secure. I suggested subnets, what other options are there to achieve both simultaneously?
I guess he could try the wireless guest thing that Cisco has, but I have no personal experience with it.

I've tried different subnets but could only get one subnet to access the internet, but that might be cuz I didn't set it up right.

---

### Post by haqking on 2012-04-19
> **Ms. Daisy said:**
> Don't know if you read the OP or not ;)
He wants the network available for friends but also wants it secure. I suggested subnets, what other options are there to achieve both simultaneously?

give the friends the 63 chr key ;-)

Anyways its all been addressed now, use a long secure WPA2 key, use mac filtering if you wish and hide your SSID if you wish, layers are good, but they are trivial to bypass.

And yes alot of home routers have guest functions now which dont allow access to the LAN only to the outside world.

As for subnets, im guessing the OP is newbie to this hence the question so subnetting may be overreaching.

Peace

---

### Post by Ms. Daisy on 2012-04-19
> **haqking said:**
> give the friends the 63 chr key ;-)
Sorry, I do not understand this option.  If the OP is concerned about guests doing questionable things on his network, then how does this help him control/contain that?

---

### Post by haqking on 2012-04-19
> **Ms. Daisy said:**
> Sorry, I do not understand this option.  If the OP is concerned about guests doing questionable things on his network, then how does this help him control/contain that?

it doesnt.

anything questionable (if warranted as tracable) would come to the public IP and then forensics done on the machines using it and the owner of the network primarily responsible (but that is an extreme case scenario)

He said roommates in the OP to use the WIFI (give the key to), and Neighbours borrowing the wifi ETC (secure the key against).

Hence the security of the wireless key, the actions of others than yourself is uncontrollable though you may be found liable ;)

---

### Post by donwolfani on 2012-04-19
> **Ms. Daisy said:**
> Oh, and I'm not sure what you want to accomplish by changing your mac address.

actually i want my machine disguised as another one for "anonymity" while im in public.  the simple truth is that if there exists a record of me being on a wifi at the same time as someone else might have been using it to torrent a movie or some other such activity then that means that i might end up on a suspect list.  that makes me very uncomfortable so i have gotten good at making sure i have deniability when doing anything online just incase one of my friends does something illegal with my machine or whatever else happens.
not that i wouldn't have done the same small wrongs we all have and do at times but i try and avoid leaving evidence even when im innocent as leaving it behind is just sloppy

---

### Post by donwolfani on 2012-04-19
> **haqking said:**
> it doesnt.

anything questionable (if warranted as tracable) would come to the public IP and then forensics done on the machines using it and the owner of the network primarily responsible (but that is an extreme case scenario)

He said roommates in the OP to use the WIFI (give the key to), and Neighbours borrowing the wifi ETC (secure the key against).

Hence the security of the wireless key, the actions of others than yourself is uncontrollable though you may be found liable ;)


exactly my point i want to change all my info so after a reboot i can honestly say that my hostname is the default as it might be for anyone and that my mac address does not match what they find in records.  not that i plan on doing any thing extremely wrong mind you but i still don't like big brother knowing what i do online outside of what i chose to state on facebook.  it just makes me feel safer legally to know that my machines info does not match what is on record

---

### Post by CharlesA on 2012-04-19
> **donwolfani said:**
> exactly my point i want to change all my info so after a reboot i can honestly say that my hostname is the default as it might be for anyone and that my mac address does not match what they find in records.  not that i plan on doing any thing extremely wrong mind you but i still don't like big brother knowing what i do online outside of what i chose to state on facebook.  it just makes me feel safer legally to know that my machines info does not match what is on record
You will never be untraceable if you are on the internet.

---

### Post by haqking on 2012-04-19
> **charlesa said:**
> you will never be untraceable if you are on the internet.

+1

Besides what you do on your machine, if you are the owner/provider of the wireless service the onus is on you and you could be held liable.

If you are paranoid then use a virtual appliance that wipes everything and dont use personal information online, use a service such as TOR and/or other proxies.

However as i said if you own the Wireless then its your responsibility and liable.

---

### Post by dontquoteme on 2012-04-19
My question would be how much do you trust your friends?  
They can easily give away the preshared key - or share it with girlfriends etc.  If the girlfriends carry out illegal stuff?   But you're getting into a risky situation - so be prepared to defend yourself - and use highly encrypted applications such as hushmail that use https - to encrypt your comms from your neighbours.  Messaging apps are bitwise.com - which encrypts skype and file transfers.  Both are free.

Torrents are probably the least of your worries.

In this situation, you're wide open -  so you can't expect any form of security to work.  In fact, they could change the router settings, remove the firewalls and logging can be turned off.  Most hackers would amend any logs to remove signs of their activity.    They could sit with wireshark on the network and read all the packets - or set up a man in the middle attack. Physical access to a laptop/router means that all security can be compromised.

Please do not tell any defence barrister that you spoofed your MAC or IP as this makes you look guilty and it's not going to protect you - locking up your laptop and using encrypted usb pens might give you a breathing space.  The concept is called "Defense in Depth".  You layer your security - starting with physical security.  As you're walking into trouble here.  Of course, your friends are honest, and trustworthy and you trust them - but make sure they can't download onto your laptop or external hard drives...  Have all of that encrypted so that they can't use it.  Free open source apps that work on ubuntu include Truecrypt.  Layer your defence, otherwise they might "borrow" your kit...and you'll get a nasty surprise.  It would actually be pretty dumb of them to download onto their own laptops/drives - putting it on an innocent persons kit gives them plausible denialabilty - it muddies the water if the issue ever comes to court.  Of course, you as the innocent person would be landed right in it... with "no idea" how those files got on your laptop.  Do you see how dumb that sounds in court?  No one will believe you.

Imagine you're in an internet cafe - and wide open to abuse, as that in effect is what this situation truly means - only your name is on the billing address. 
If you've got a bad vibe about one or two of them, then don't go ahead with this on security grounds.  Everything will probably be fine, but if one or two of them are dodgy - that's your answer... walk away.

---

### Post by Dangertux on 2012-04-19
Here is an idea that hasnt been tossed around in this thread yet.

Get an additional router, preferably a real router/firewall with real (v)ACLS. In the event that this is too expensive you could build one out of a linux box. Use this as a border forewall between your wireless access point and the internet. You can make this a seperate access point for your use. Have the existing access point use the new one as a  gateway. Give your friends exisiting ap information. Then just lock down that gateway, which will be very much out of your friends control.

That will keep them from doing anything bad on the internet and if you use subnetting you can keep your machines separated from theirs as well.

Hope this helps.

---

### Post by CharlesA on 2012-04-19
> **Dangertux said:**
> Here is an idea that hasnt been tossed around in this thread yet.

Get an additional router, preferably a real router/firewall with real (v)ACLS. In the event that this is too expensive you could build one out of a linux box. Use this as a border forewall between your wireless access point and the internet. You can make this a seperate access point for your use. Have the existing access point use the new one as a  gateway. Give your friends exisiting ap information. Then just lock down that gateway, which will be very much out of your friends control.

That will keep them from doing anything bad on the internet and if you use subnetting you can keep your machines separated from theirs as well.

Hope this helps.
That is probably the best way to do it.

Huge +1.

---

### Post by haqking on 2012-04-19
edit: actually never mind ;)

---

### Post by rookcifer on 2012-04-20
Haven't read this whole thread, so what I am going to say has probably been covered.  But here's what you need to do:

1) Flash your router with Tomato or DD-WRT.  In the long run you will be glad you did.  However, if you don't want to, then the rest of the steps will still apply.

2) Use WPA2-AES.  Usually this will be "WPA2-personal."  The AES part is very important as well.  Be sure to use it over TKIP.

3) Use a long key, preferably with 128 bits of entropy.  Even though 128 bits is certainly overkill (unless you have NSA scanning your network), I see no reason not to use it since most clients will remember the password anyway (saving you from having to type it each time).  You can generate a high quality password with /dev/urandom like so:

```
cat /dev/urandom| tr -dc 'a-zA-Z0-9' | fold -w 22| head -n 1
```

The above command will generate a 22 digit password which should give 128 bits of entropy (at least theoretically).  **Do not** use the router's built-in password generator, as it is almost certainly of lower entropy than /dev/urandom (because embedded devices have a HARD time generating entropy).  After you're done doing that, copy and paste the password into your router and then find a way to transfer it to your client machines securely.

4) Leave SSID broadcasting and change your router's name to something unique.

5) If you want to use MAC filtering, fine, but it is very minimal security.

6) Be sure that telnet is turned OFF in the router if your router has the option for it. (Some routers will give you the option to connect via telnet and it's ALWAYS a bad idea).  If you need remote access, use SSH (but turn SSH off as well if you don't use it).

7) Unless you absolutely need remote HTTP access to the router, turn that option OFF as well.  Make it so you can only connect via localhost.  If you *do* need remote router administration via HTTP, then be sure you use HTTP**S** and a strong admin password (10-12 characters is fine).  However, I would be careful about trusting the router's built-in SSL certificate as it has a good chance of being broken as we have seen in the news recently (a study showed that embedded devices have a HARD time generating good entropy for certificates and keys).  The better option is just to administer the router from the local machine.

#8 Be sure the firewall in the router is set to DROP all incoming probes.

That's pretty much it.  Use these steps and you will have as secure a router as you can have in the consumer world.

---

