---
title: "SSH Into Home Server: Connection Timed Out"
date: 2009-05-01
forum: Server Platforms
---

### Post by BrandonBan6 on 2009-05-01
Hey All!

I think I am close here, but I seem to be stuck on this issue. I have read the [community pages on SSH]("https://help.ubuntu.com/community/SSHHowto") and several other tutorials, but no luck yet. 

So I have ubuntu server running on an old PIII box at home. The distro is great, thank you dev & support teams!

From my home network, I can ssh into it with no problems. However, I'd like to be able to SSH into from work. I have both an ubuntu box and windows+Putty box at work, so either one would be fine. Whenever I try, I get a connection timed out error. So here's the setup. 

-SSH is installed and working on the home server. 
-My home router (DD-WRT) I've forwarded port 22 to my server IP address. 
-From Putty on WinXP, I insert the following: (note: i've removed the actual addresses for security reasons)
[IMG]http://lh5.ggpht.com/_VLDXTaX4rOE/SfsYCQ2Ax4I/AAAAAAAAE8E/EV_JG0lNTM4/ScreenHunter_001.jpg[/IMG]

[IMG]http://lh5.ggpht.com/_VLDXTaX4rOE/SfsYCfIEzVI/AAAAAAAAE8M/z5rgPy-gByc/ScreenHunter_002.jpg[/IMG]

[IMG]http://lh6.ggpht.com/_VLDXTaX4rOE/SfsYCUJlnYI/AAAAAAAAE8U/apYi6OV1EWg/ScreenHunter_003.jpg[/IMG]

So, I'm wondering, perhaps my port numbers are way off? I'm not sure :( 
No firewalls beyond the router, any thoughts here??

Thanks!!

---

### Post by spiderbatdad on 2009-05-01
Is it possible your isp blocks port 22? Or perhaps your work network blocks outbound 22, as this can be used in reverse.

---

### Post by heebus on 2009-05-01
Try setting the port to something like 9000 and reconfiguring your router.  You can change the listening port of your sshd.

sudo pico /etc/ssh/sshd_config

After that restart the service

sudo /etc/init.d/ssh restart

---

### Post by BrandonBan6 on 2009-05-04
Thanks guys, finally got an opportunity to try this out. Spider, a port scan is showing port 22 is open from both locations. However, I realized I hadn't considered my DSL modem as a router, So essentially I have the The Internet -> My Modem/Router -> My Router -> My Server to go through. I'm thinking that is where the problem is...I would have to create an SSH connection to my public IP address, then a tunnel to my router, which would forward the tunnel to the correct listening port right? Or am I missing some network fundemental here :D 

Heebus, I'll give your solution a try tonight. Thanks for the help guys!

---

### Post by heebus on 2009-05-04
Sounds like you know what the problem is.  You can either bridge the modem or open the port from there to your router.  Your router will then send it to your PC.

Easiest solution is bridging your modem.

---

### Post by BrandonBan6 on 2009-05-05
that was the trick!!! Bridged the Modem and the Router and we were home free!! thanks so much !!!

---

