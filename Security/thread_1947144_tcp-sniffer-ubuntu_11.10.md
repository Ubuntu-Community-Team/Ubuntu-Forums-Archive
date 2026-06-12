---
title: "tcp-sniffer-ubuntu 11.10?"
date: 2012-03-26
forum: Security
---

### Post by isosikabigpig on 2012-03-26
Ubuntu 11.10, kernel 3.0.
Got trojan?

System slow, cpu load 80-90%.
No network applications running by user.
```
**[COLOR=Red]Command "ss -t -a" outputs:[/COLOR]**
----------------------------                                   State      Recv-Q Send-Q      Local Addressort          Peer Addressort    
 LISTEN     0      128                     *:9030                     *:*        
 LISTEN     0      128                     *:9001                     *:*        
 LISTEN     0      128                   ::1:8118                    :::*        
 LISTEN     0      128             127.0.0.1:ipp                      *:*        
 LISTEN     0      128                   ::1:ipp                     :::*        
 LISTEN     0      128             127.0.0.1:9050                     *:*        
 LISTEN     0      32              127.0.0.1:8123                     *:*        
 TIME-WAIT  0      0                10.0.0.3:54273              209.85.173.99:www      
 ESTAB      0      0                10.0.0.3:34299                   195.242.152.250:https    
 TIME-WAIT  0      0                10.0.0.3:39763               91.189.94.12:www      
 ESTAB      0      0                10.0.0.3:44857                      94.127.76.120:www      
 ESTAB      0      0                10.0.0.3:53130                     176.28.18.221:https    
 ESTAB      0      0                10.0.0.3:34897                    77.247.181.165:https    
 ESTAB      0      0                10.0.0.3:47624                     173.194.32.35:www      
 TIME-WAIT  0      0                10.0.0.3:43912            193.184.164.192:www      
 TIME-WAIT  0      0                10.0.0.3:43913           193.184.164.192:www      
 ESTAB      0      0                10.0.0.3:36602                      91.143.93.242:https 



-----------------------------------------------------

 Other time:

 

 

 ESTAB       0      0               10.0.0.3:59468           94.127.76.90:www      
 ESTAB       0      0               10.0.0.3:47694               46.4.58.8op3s    
 ESTAB       0      0               10.0.0.3:49798            78.46.66.112:9001     
 ESTAB       0      0               10.0.0.3:34299        195.242.152.250:https    
 ESTAB       0      0               10.0.0.3:44857           94.127.76.120:www      
 ESTAB       0      0               10.0.0.3:50934           83.169.20.105:9001     
 ESTAB       0      0               10.0.0.3:53130          176.28.18.221:https    
 ESTAB       0      0               10.0.0.3:46062          74.120.13.132:https    
 ESTAB       0      0               10.0.0.3:43263          91.121.85.130:47168    
 ESTAB       0      0               10.0.0.3:46297          199.48.147.45:ssh 



-------------------------------
```


Any ideas to look at?:confused:

---

### Post by Ms. Daisy on 2012-03-26
Hmm. If you didn't initiate the ssh connection then I would say that's a bad indicator.

Look at the "[did i just get owned]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned")" wiki.

Back up your data and reinstall if you see evidence of compromise.

---

### Post by CharlesA on 2012-03-26
> **Ms. Daisy said:**
> Hmm. If you didn't initiate the ssh connection then I would say that's a bad indicator.

Look at the "[did i just get owned]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned")" wiki.

Back up your data and reinstall if you see evidence of compromise.
What she said.

Can you post the output of this command:

```
sudo netstat -nlpu
```

---

### Post by isosikabigpig on 2012-03-27
*Netstat *don't show ***tor*** connections- see below.
 
 [SIZE=4]Case report:[/SIZE]
 

 Network connections is the problem?
 I did try a random experiment:
 

 *sudo find / -print | xargs grep network >file*
 

 Finding  something funny in my home directory:
 

   *./xxxxxx/phone/mybankname/yyyyy/zzzzzz/a.html*
 *  ./xxxxxx/phone/mybankname/yyyyy/zzzzzz/a*
 

 This funny*  a.html* (I newer created directory phone) containing:  
 ….............
 *</script><script language="javascript" src="IfrJSAdLoader_data/a"></script><script type="text/javascript" src="IfrJSAdLoader_data/a_002"></script><script type="text/javascript" src="IfrJSAdLoader_data/a.html"></script><a href="ht..........................*
 

 File”a”:
 …..................
 *3d&ad2dest=",CREFURL:"http%3A%2F%2Fadmeta%2Evo%2Ellnwd%2Enet%2Fe1%2Fstatic%2Fad2%2FIfrJSAdLoader%2Ehtm%3Fclickthrough%3Dhttp%253a%252f%252fadserver%2Eadtech%2Ede%252fadlink%252f969%252f2177901%252f0%252f82%252fAdId%253d515",BN:"393668"}; *
 *if(!Adform.ADFBannerParams)Adform.ADFBannerParams=[];Adform.ADFBannerParams.push(Adform.ADFBannerData); *
 *typeof Adform.ADFUtilInstance=="undefined"?document.write('<scr'+'ipt type="text/javascript" src="http:/............................*........
 

 No execute rights, still!
 

 This script was not (most probably) connected to the current problem (time stamps can be changed, but...).
 

 Must try something better:
 
[LIST]
[*]I run *rkhunter*- nothing
[*]check modules, LKM?-nothing
[*]*.bashrc* -nothing
[*]suspicious new files......
[*]…....
[/LIST]
 

 Must take more carefully.
 New connections wake up after boot. One explanation: Most probably something connected to kernel init scripts.
 

 Files */lib/init, /etc/rc0.d,..........,/etc/init.d/xxx.....*
 

 Here is really something! ***tor*** client start configuration in */etc/init.d*.
 (*Tor* network hides IP. Can access any place even banned by network operators. I have installed it but not started at boot, manually by *vidalia*. )
 

 Now I know: I have messed up with Firefox add-ons long time ago.
 I was finding information about XSS (Cross Site Scripting) and accepted XXS 0.4.5  add-on :oops:.
 **But the key issue is that Firefox created *tor* system connection (my own fault ), but when I disabled add-on, Firefox did not take away *tor* start from init procedure!**
 

 What I did learn:
 
[LIST]
[*]Most configuration files of 3.0     are very different from old style Linux (not  inittab- file)
[*]Linux start is slow because it is     built at a very complicated way
[*]rkhunter* i*s good
[*]hidden “a” ????
[*]browser is the king of the system-     be careful
[/LIST]

---

### Post by CharlesA on 2012-03-27
Box is owned. Backup your stuff and reinstall.

---

### Post by isosikabigpig on 2012-03-28
Owned by: usage of XSS 0.4.5-> XSS script attach
Techique: put tor in /etc/inet.d and ......

---

