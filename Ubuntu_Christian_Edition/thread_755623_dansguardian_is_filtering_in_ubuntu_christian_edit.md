---
title: "dansguardian is filtering in ubuntu christian edition"
date: 2008-04-15
forum: Ubuntu Christian Edition
---

### Post by sudheer123 on 2008-04-15
Hello all, i am new to the Ubuntu, once i have seen on the intenet, that dansguardian is inbuilted within the ubuntu christian edition , so i installed it on my system ,  but  it is not filtering with the default settings.

Do i need to change any settings in dansgurdan.conf  or tinyproxy.conf  or any others

when i enable the "dansguardian"  , the message is displayed on firfox as 

firefox is unable to connect  "www.   ........"  server

and when disable it we can access internet normally

so what would be problem ?????????????


thanks
sudheer

---

### Post by wineman on 2009-04-16
ok you have firewall issues. try swapping your cables into the other plugs (i.e. - the LAN cable into the ADSL side's lan eth card, and the ADSL cable into the LAN side's eth plug). This might help.

Otherwise, add this line to the beginning of the tinyproxy.conf file:
```
iptables -t nat -A PREROUTING -p tcp --dport 3128 -j REDIRECT --to-port 8080
```

also, have you setup your browser to connect to the UbuntuCE pc first? set your proxy's address to the pc's IP and the port to 8080 (dansguardian standard port).

Hope this helps.

---

