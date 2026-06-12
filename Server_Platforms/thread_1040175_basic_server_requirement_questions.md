---
title: "basic server requirement questions"
date: 2009-01-15
forum: Server Platforms
---

### Post by redroad55 on 2009-01-15
HI ..I am trying to understand the requirement of a static IP address in many server environments and the reality of DHCP being the only choice I may have..I have read many posts manuals etc. and come back to this basic stumbling spot ... I have been weaning myself off of microsoft for the last year and currently have this setup.. 2ea. surfing machines.. 1ea. server (yet to be configured)..2ea. media machines .. and an older workstation that could be used for a mail server if needed .. All sit behind a verizon dsl connection and there modem/router..  then a D-link 1g switch .. I would like to be able to have all mail available to all machines incld. history ... then have a media archive file server .. the two media machines are 8.04 hardy and the two surfers are dual boot xp pro / 8.04 hardy both of these formatted ntfs/ "/home" / "/" / swap ..Any input,opinions,or links would be greatly appreciated ..Thanks in advance

---

### Post by HermanAB on 2009-01-15
DHCP can assign a fixed IP address based on the MAC of the server.  Read the man page.

Cheers,

Herman

---

### Post by hrod beraht on 2009-01-15
> **redroad55 said:**
> HI ..I am trying to understand the requirement of a static IP address in many server environments and the reality of DHCP being the only choice I may have.

Please elaborate. What is it about your situation that makes you think you can't use a static IP for your server?

Bob

---

### Post by redroad55 on 2009-01-15
Thanks for your reply...I assumed that a static IP address was something that my ISP provided at a cost ... I must admit that my basic understanding of this is limited .. Verizon seems to force you to use their equipment ... I am aware that as the server within my local network as file server all is good but what happens as LAMP is where I am in unfamiliar as well as unknowledgeable ... So I am paying currently $28.00 for all the bandwidth I can get .. There is a substantial increase in price for the sTatic IP requiement .. I am not sure what my options are?? Thanks again for your reply

---

### Post by redroad55 on 2009-01-15
> **HermanAB said:**
> DHCP can assign a fixed IP address based on the MAC of the server.  Read the man page.

Cheers,

Herman
Hi Herman not sure of "man page".. Please specify ..Thanks for your reply..

---

### Post by Traumadog on 2009-01-15
Hi!

A "man page" is a manual page.  These "pages" provide information on various commands and functions in your operating system.  For example, if you wanted to know more information concerning the "cp" command you would type the following in a terminal window:

```
man cp
```

The resulting output would be a "page" that tells you all about the "cp" command.

As to your need for a static IP address....

You only need to worry about a static IP address from your ISP if you need to access your server from outside your Local Area Network.  (An example would be if you needed to access your files from work or if you wanted to create a web page.)  Even then, you really don't need a static address.  You could sign up with a service like DynDNS and they will help monitor your dynamic IP address and keep it associated with a domain name so that your server is accessible over the internet.  Within your LAN, however, you might want to consider assigning a local static IP address to your server.  That will allow you to better direct the flow of data to your server. (This allows your router to direct all traffic coming in on a given port to your server. This is referred to as "Port Forwarding" ) 

Of course, all of the above is just gerneral information.  I might be able to give more assistance if I knew the following:

Do you wish to access your server from outside your local area network?  e.g. from other computers than the ones in your home.  If so, what what type of access are you interested in?  e.g. Web, simple upload/download of files, etc.

If possible, please post more on what you are trying to specifically accomplish and I or someone on the forum may be able to provide more direct assistance.

Best wishes to you! :-)

Traumadog.







> **redroad55 said:**
> Thanks for your reply...I assumed that a static IP address was something that my ISP provided at a cost ... I must admit that my basic understanding of this is limited .. Verizon seems to force you to use their equipment ... I am aware that as the server within my local network as file server all is good but what happens as LAMP is where I am in unfamiliar as well as unknowledgeable ... So I am paying currently $28.00 for all the bandwidth I can get .. There is a substantial increase in price for the sTatic IP requiement .. I am not sure what my options are?? Thanks again for your reply

---

### Post by redroad55 on 2009-01-15
Hi TRUMADOG , Thanks  for your reply that clarifies man page quite well thanks .. As to further description of my intent for now I would like to serve mail on all local machines .. Plan to insatall 8.04 server on 36gb scsi hard drive on server it has a u320 control hub have a promise sata card with two 250gb sata drives attached .. would like to backup all files on server .. I am starting with 2 250gb drives and will expand as needed .. So a local file server with mail with the ability to expand to more (possible web page down the road) .. all machines in local network will be linux 8.04 hardy so I don't see any need for samba as of yet .. open to any suggestions .. welcome any help .. Thanks in advance for all help and Thank You for the help thus far

---

### Post by hrod beraht on 2009-01-15
[QUOTE=redroad55]I am aware that as the server within my local network as file server all is good...[/quote]
Yes, a static IP within our local network (e.g. 192.168.1.xxx) is the way to go so you can just forward ports via your router to your server address.
[QUOTE=redroad55]I assumed that a static IP address was something that my ISP provided at a cost...[/QUOTE]
Your external internet IP address (i.e. the address of your router) will indeed be periodically changed by your ISP (most ISP's like to discourage the running of servers). Depending on your ISP it may not be changed too often (mine does it about every 8 months). If you don't have a domain name, consider using [[COLOR="Blue"]DynDNS[/COLOR]]("http://www.dyndns.com/services/dns/dyndns/"), who will not only give you a domain name, but allow that domain name to be automatically re-directed each time your ISP may change your internet IP address.

Bob

---

