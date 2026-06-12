---
title: "[SOLVED] anyone can help me with apache server....??"
date: 2008-08-06
forum: Server Platforms
---

### Post by trevelyan on 2008-08-06
Hi. I'm trying to start a web server in my wife's computer (Canada) so i can download her TV shows collection to my computer (Honduras). we are using Apache 2.0 in her windows vista laptop computer. we managed to get it working locally. that is.. from her computer we get the "if you can see this then it works" or something like that, page. if we try her IP address it works.. and if we try the domain name we got from dyndns.com then it also works. but as soon as i try it in my computer the thing doesn't work.

I'm lost at this point as to why it doesn't work.. i was hoping someone here might know or have an idea why it doesn't...

---

### Post by tamoneya on 2008-08-06
when you try to access from your computer what IP address or domain name are you using.  Is it the local IP or external?

---

### Post by trevelyan on 2008-08-06
when i try to access from my computer i do it with the dynamic DNS i got from dyndns.org but it doesnt work. hoever, it works from my wifes computer.

---

### Post by tamoneya on 2008-08-06
It is most likely a problem in your router.  You need to setup "port forwarding" so that it forwards all port 80 requests to your wife's computer.  You specify the computer by giving the internal IP address.  Also the simplest way to test it is to type your wife's internal IP into firefox on your computer.  If that works then it is definitely the router that needs work.

---

### Post by trevelyan on 2008-08-06
i have port forwading in my wifes computer set up.. its forwarding port 80 to her computer's ip (192.168.1.100). when i try it from my computer.. nothing works.. her external IP her DDNS. nothing.. when i do it from her computer everything works.. DDNS external and internal IPs also [http://localhost/](http://localhost/)

if all this works in her computer.. i dont know why i cant connect to it. i even asked a few freinds to test it.. it didnt work for them either. why could this be happening???

---

### Post by tamoneya on 2008-08-06
okay now it seems like some sort of firewall issue or a blocked port.

Try opening up port 80 in iptables (linux firewall).  [http://forums.devshed.com/security-and-cryptography-17/how-do-i-open-port-80-in-iptables-securely-412650.html](http://forums.devshed.com/security-and-cryptography-17/how-do-i-open-port-80-in-iptables-securely-412650.html)

---

### Post by Lostincyberspace on 2008-08-06
Try pinging you wifes computer and if that fails then run tracert.

---

### Post by trevelyan on 2008-08-06
i disabled windows firewall.. also disabled NOD32 internet monitoring protection thing. and i forwarded port 80 to her internal IP (if i don't forwarded it, it doesn't work on her computer anymore, so i know i did it right) what could i possibly be forgetting.. I'm out of ideas.

---

### Post by tamoneya on 2008-08-06
oops i forgot it was windows on that PC.  You are going to have trouble finding iptables there.  Unfortunately I am not familiar with configuring apache on windows.  you could also try nmap instead of just pinging the computer.  It will be more descriptive.

---

### Post by trevelyan on 2008-08-06
i forwarded port 80 on windows firewall but i disabled it altogether after that.

also when i ping my wife's computer.. the requests times out
when i tracert it does a lot of pinging then it reaches a point at step 18 (or connection 18?) and it times out on 18 to 30.

is it safe if i post this information here or not?
thanks

---

### Post by tamoneya on 2008-08-06
considering that we dont have your external IP and you have a firewall in your router still it is pretty safe.

---

### Post by trevelyan on 2008-08-06
Removed :P

---

### Post by thisllub on 2008-08-07
Are you sure that is the right IP address?

It is most likely to be something like 192.168.1.x
Your router is 192.168.1.1 so look on that network.

---

### Post by trevelyan on 2008-08-07
no its not. we are talking about two computers in two different countries. not in the same LAN.
thanks anyways.

---

### Post by trevelyan on 2008-08-07
i went to [this website]("https://www.grc.com/x/ne.dll?bh0bkyd2") and i tested my ports there. all of them have stealth. does that affect the apache HTTP server?

---

### Post by thisllub on 2008-08-07
When you say "forwarded port 80" do you mean on her router or is she directly connected to the internet?

If she has a router make sure it doesn't have external management enabled on port 80 otherwise it won't forward.

---

### Post by trevelyan on 2008-08-07
i forwarded port 80 on her router and later in mine becuase i wanna have a web server too. and the external management thing isnt enabled.
i think its jus her ISP blocking the ports, in this case port 80 (my ISP does this too) i tried looking for an open port with the dyndns.com [open port tool]("https://www.dyndns.com/support/tools/openport.html") but no port no matter which one i try works. how do i get around this without changing ISPs? can it be done?
thanks.

---

### Post by JillSwift on 2008-08-07
May I suggest using BitTorrent? If you wife's machine is running Windows, you can use [uTorrent]("http://www.utorrent.com/"), which has a [built in tracker]("http://www.utorrent.com/faq.php#Does_.C2.B5Torrent_have_an_embedded_tracker.3F"). She could easily [make torrents of batches of files]("http://www.utorrent.com/torrent.php"), e-mail you the torrents, and you could then start downloading. This way you can pick your ports and recover more easily from net down-time and crashes.

---

### Post by trevelyan on 2008-08-07
omg JillSwift!!! without knowing you solved my problem. not by using utorrent. but by using the port utorrent suggested!! i checked that port on dyndns.com's open port tool and it was open! :D 
after that i just told Apache to listen on that port, then i forwarded it on the router and then i redirected my DDNS from port 80 to port 39973 and it worked!!
thank you!

btw.. we did try torrents (with vuze/azureus) but for some reason she wasn't able to upload to me... only very slowly.
thanks again. \\:D/

---

### Post by JillSwift on 2008-08-07
> **trevelyan said:**
> omg JillSwift!!! without knowing you solved my problem. not by using utorrent. but by using the port utorrent suggested!! i checked that port on dyndns.com's open port tool and it was open! :D 
after that i just told Apache to listen on that port, then i forwarded it on the router and then i redirected my DDNS from port 80 to port 39973 and it worked!!
thank you!

btw.. we did try torrents (with vuze/azureus) but for some reason she wasn't able to upload to me... only very slowly.
thanks again. \\:D/
Yay! Glad it's solved =^_^=

---

### Post by thisllub on 2009-01-12
Ignore that.

---

