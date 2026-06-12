---
title: "Avoiding the pitfalls/downsides to a potentially horrendous dystopian future"
date: 2012-08-08
forum: The Cafe
---

### Post by Eiji Takanaka on 2012-08-08
Changing your computers identity. Script it all if possible, thus with a  clickety click all is changed and is not as whence came before. This is  basic and should go as a prerequisite to any further actions.

Consideration 1) Spoofing your macaddress is basic shiz, you can do this  with the macchanger tool for ubuntu. This may be alright for some but  you might find you have problems authenticating with any potential  networks. 

 But if you want to use generic tools, the best place to spoof the mac would be editing /etc/network/interfaces to something as follows....

> auto lo
iface lo inet loopback
pre-up ifconfig wlan0 hw ether 10:00:00:00:00:00This way it keeps all your networking shiz in order. 

Consideration 2) Changing your computers hostname. 

Edit /etc/hosts & /etc/hostname change this accordingly with each  change of the mac, so as to avoid cross-referencing efforts. Something  generic like Windows7-PC is probably best ;).

Clear your logs. Use an exit script of some sort utilizing "shred -u -n  7" (*warning file system dependent, see shred Documentation) to  accomplish this. Or if you wanted to go pro, you could use some generic  pattern matching program like awk, and write a script that merely  censors/spoofs the specific values in the logs. (By this i mean changes  of computer name, maccaddress yadda yadda.  Lol i am not yet pro. ;) 

Consideration 3) change your browsers signature.

With firefox this is as easy as entering "about:config" into your address-bar. 
Then...
Find or add "general.useragent.override" and set the value as  "Mozilla/5.0 (Windows NT 6.1; rv:10.0)" Or something equally juicy. Be  careful though not to create a unique signature by accident! The point  in question is to blend in, thus the more common the string the better  ;).Use your brain and Look for common-strings on google. 

*Another vital point to consider is that any other packet headers from  varying protocols that your system might send or receive, could  potentially contradict this browser signature and thus create a  completely unique user signature, you really do not want to do this.  Keep wireshark open and be aware of any tell-tale signs you might give  away. Which leads us onto the next point.

Consideration 4) Ubuntu repository and system updates, disable these if  you are looking to be stealthy. Also disable the time server, or replace  it with a generic one, it dials out to ubuntu servers. Doesn't help if  what looks like a windows machine is dialing ubuntu headquarters =P.

[https://help.ubuntu.com/10.04/serverguide/NTP.html](https://help.ubuntu.com/10.04/serverguide/NTP.html)

Consideration 5) All of the above is pointless unless you are using a trusted machine in the first place, be aware of this. 

Consideration 6) If you use internet cafes be aware of video cameras and  surveillance nearby. If you use your own machine be aware of geotags,  and other embedded code that can give away your position, should the  proxy daisy chain/liberated vpn fail/be compromised, the wi-fi  sniper-rifle, with 10-mile range, associated with an easily breached wps  enabled wpa2 network..

[http://code.google.com/p/reaver-wps/](http://code.google.com/p/reaver-wps/)

is only gonna buy you so much time! ;) 

Consideration 7) Where did you purchase that wi-fi sniper rifle from? Second hand with cash and via a proxy or two i hope? ;) 

Consideration 8) Be careful with your disclosures of information, as it  draws attention to yourself. Unless of course you deem it worthwhile and  important to disclose said intel. Or unless you have a suitable  guise/cover to disclose the intel, i'm a sci-fi writer, i guess thats  mine ;) 

Consideration 9) Trust your instincts and be aware that people can be  manipulated, even if they mean well. Be mindful and make good sound  judgments, according to your conscience. 

Consideration 10) Make knowledge available that needs to be available. 

Consideration 11) Always keep an eye on the angles, when you can't see  the angles no more, you in trouble baby, you in trouble. Situational  awareness is a good trait to have. Enhance/reinforce it. 

Consideration 12) A little knowledge is a dangerous thing. If you don't  know your path in life, save your energy, research, focus, if in doubt  go with your heart. 

Consideration 13) Try not to preach or come across as cheesy, even if you mean well ;) 

This tutorial on avoiding the potential dangers/pitfalls of a horrendous  dystopian future is copyleft. Feel free to add/change as you feel free.

---

### Post by KiwiNZ on 2012-08-09
"Almost any non-tech-support topic may be  discussed here. Discussions on religion and politics are not allowed.  These two topics have caused serious problems in the past and are now  forbidden topics in the forums."

Given the political overtones of this thread it is closed

---

