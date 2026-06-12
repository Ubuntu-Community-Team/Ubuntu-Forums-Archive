---
title: "Firestarter showing different connections"
date: 2009-11-09
forum: Security
---

### Post by jmore9 on 2009-11-09
I am having problems with firefox.  When i set the default page to load it goes to Yahoo.com which is where it is supposed to go.

But when you look at firestarter bottom where it says source / destination it shows the following :

71.205.117.xx (changed then xx) and destination of 209.85.225.138 port 80

Just before this happened my cable modem went off completely except for power light for about 8 minutes.

I also did a netstat -a and this is at the top:

Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 c-71-205-117-87.h:58177 iw-in-f101.1e100.ne:www ESTABLISHED
tcp        0      0 c-71-205-117-87.h:47047 iy-in-f101.1e100.ne:www ESTABLISHED
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
udp        0      0 *:47802                 *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:mdns                  *:*                                

I did a google search for iw-in-f101.1e100.ne and it came back as windows update.

The yahoo web page is displayed and 209.85.225.138 is the destination address which is google.

This all happened after the comcast tech was in my apartment building.

Comcast support said they did have a tech in my building today , but i saw him come and go.  They also said that Ubuntu has a very bad virus and i should get macafee or nortons and do a scan !!

Anyone have any ideas why firestarter shows connection to google when yahoo is being disp[ayed ?

---

### Post by NJ0E on 2009-11-09
IP Address Location 
IP Address 71.205.117.10 
City Grand Rapids 
State or Region Michigan 
Country United States 
ISP Comcast Cable Communications IP Services.  

I found this at [http://www.melissadata.com/Lookups/iplocation.asp?ipaddress=71.205.117.10](http://www.melissadata.com/Lookups/iplocation.asp?ipaddress=71.205.117.10)

Looks like a redirect page that Comcast has set up in conjunction with Yahoo.com

As a side note -- I would ask the comcast tech assist where they got the info about a virus in ubuntu.  Would be intresting to know.

---

### Post by jmore9 on 2009-11-09
Well i ask the gentleman when he gets a chance to call over to their tech support and ask for info on macfee and nortons on linux, just for his own info.

here are some snaps of what i am talking about .  Had a little bit of trouble uploading now that they have screwed up my internet.

[http://farm3.static.flickr.com/2800/4090436805_b1d9d7c58f_m.jpg](http://farm3.static.flickr.com/2800/4090436805_b1d9d7c58f_m.jpg)

[http://farm3.static.flickr.com/2603/4090436711_77a1f1c46f_m.jpg](http://farm3.static.flickr.com/2603/4090436711_77a1f1c46f_m.jpg)

[http://farm3.static.flickr.com/2447/4090436647_ec61dbe9a4_m.jpg](http://farm3.static.flickr.com/2447/4090436647_ec61dbe9a4_m.jpg)

Plus they could not explain why the modem was off ( every light except power , ethernet ( oops forgot that ) for 8 minutes. )

---

### Post by cdenley on 2009-11-10
Ubuntu does not have a virus. The tech you talked to just makes that assumption based on all the windows users he deals with whenever he doesn't understand the problem. He probably doesn't even know what ubuntu is. You can't be surprised by connections your browser makes to google, especially with the auto-complete google search bar.

By the way, you're probably safer without firestarter. It is old and no longer maintained. If you need a firewall, use GUFW instead. With netstat, always use the "-n" option, because reverse DNS lookups aren't as useful, especially when they get truncated.

---

