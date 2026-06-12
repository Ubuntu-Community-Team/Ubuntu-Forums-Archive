---
title: "Can get to my server using my DYNDNS name"
date: 2010-04-12
forum: Server Platforms
---

### Post by barnesey on 2010-04-12
[COLOR=black][FONT=Verdana]Hi there,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have setup a web server, ftp, ssh with ubuntu server which is working with phpmyadmin and webmin installed with it as well. (I am considering upgrading to 10.04LTS when it comes out)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]However I can’t get to my website with the domain name that I am using from dyndns.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]From on my LAN I can get to my server but using it ip address (10.10.0.200) and it work fine with ssh and ftp as well. But when I try my public address or my name it does not work. I am using IE8 as I am using a windows machine.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Out side the network the domain name won’t work at all, but I tried my public address and everything worked perfectly.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have recently installed ddclient to see if had made any difference but no luck. But I am keeping it there as it is working and updating my ip address.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have been looking on Google and tried a few things but have had no luck at all at fixing the problem.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I am completely confused so any input is welcome so I can learn from this.[/FONT][/COLOR]

---

### Post by Ryan Dwyer on 2010-04-12
You won't be able to use your domain name from inside your network.

You said you can access it from outside using your public IP address but not your domain name. You need to make sure your domain name resolves to your public IP address.

---

### Post by barnesey on 2010-04-12
[COLOR=black][FONT=Verdana]Oh, that will resolve why i can’t use my domain on my lan,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I have installed the ddclient which updates my public addresses for me but it still can’t get to my website etc with the domain name out side my network.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I thought i had the wrong ip address on dyndns settings and installed ddclient to update the address for me.[/FONT][/COLOR]

---

### Post by cK` on 2010-04-12
> **Ryan Dwyer said:**
> You won't be able to use your domain name from inside your network.



I can use my domain from inside my network.




If you access your server on the same network you dont need ddclient if you have dyndns. The updater should take care of that.

IF you are accessing your server on the same network that the server is on then just go to dyndns.com and click update my ip address. 

If thats the same ip you have on your server then 

Check to make shur your ports are open (I.E port 80 for http.)

If what i am saying is completely useless to you try 

[http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html")

I was having the same problem as you but that helped me trouble shoot it.


Hope that helps.

---

### Post by FuturePilot on 2010-04-13
Do you have the necessary ports forwarded in your router?

---

### Post by barnesey on 2010-04-14
HI, the port forwarding was ok as i could connect with my public ip address, but i followed the link that  cK` had put on his post and this helped me getting everything working ok. 

Thanks for the help guys,

---

