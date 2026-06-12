---
title: "Not Able To Access IIS Web Server Externally"
date: 2019-06-22
forum: Security
---

### Post by techgeek2019 on 2019-06-22
[FONT=Roboto][FONT=Arial]For 4 days, I have been trying to get my IIS web server to work! I am able to access the website internally through the internal static ip address 192.###.#.201 from different devices on the network. I have setup port forwarding on my Verizon router to forward all incoming requests from the external public to the internal port 80 on the Windows 10 desktop where my IIS server is sitting. I have completely turned off all firewall settings and anti-virus applications/processes on my Windows 10. Even after having all these doors being opened, still every time I access the website through the url [http://public-ip-address.port#]("http://public-ip-address:port#") I got the "This site can't be reached" message. I tried opening the url with both IE and Chrome browsers. But none of them work. From the public, I have no problem accessing other web servers connected to the same Verizon router that send and receive communication through port 80. So, clearly there is either something wrong with my Windows 10 or the setup of my IIS server. Or it could be that the router has trouble forwarding the port. I am just guessing. I don't know. It has been 4 days and countless hours, but I am still not able to find any clue to why this is happening. Could someone who has been through similar situation help me out?! Thank you for all of your help!








[/FONT]





[/FONT]
[FONT=Roboto][TABLE="class: cf wS"]
[TR]
[TD="class: amq"][IMG]https://ssl.gstatic.com/ui/v1/icons/mail/no_photo.png[/IMG][/TD]
[TD="class: amr"][COLOR=inherit][COLOR=#5F6368][FONT=&amp]Reply[/FONT][/COLOR][COLOR=#5F6368][FONT=&amp]Forward[/FONT][/COLOR][/COLOR][/TD]
[/TR]
[/TABLE]



[/FONT]

---

### Post by TheFu on 2019-06-22
Do you realize this is the Ubuntu Forums, not Windows or IIS forums,  right?  
How is this question tied to Linux or Ubuntu?

Regardless, URLs need to be [[noparse]http://DNS-Name:port/[/noparse]]([noparse]http://DNS-Name:port/[/noparse])  or [[noparse]http://IP-address:port/[/noparse]]([noparse]http://IP-address:port/[/noparse])

The period, ., shown above before the port is wrong.

---

### Post by coffeecat on 2019-06-23
Thread closed because:

[list=1][*]This is nothing to do with Ubuntu.
[*]It's in the wrong sub-forum even if it was.
[*]The post has been cross-posted on several other forums.
[/list]

@TheFu - the forum software parsed smiley code from part of the URLs you posted. I've edited your post to disable the smileys. You can avoid that by either using BBCode [noparse][noparse] and [/noparse][/noparse] tags, or by ticking the "disable smileys in text" button under the advanced reply message editor box. Thanks for your reply.

---

