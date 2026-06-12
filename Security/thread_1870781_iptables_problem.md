---
title: "iptables problem"
date: 2011-10-27
forum: Security
---

### Post by BigCityCat on 2011-10-27
I started ufw with sudo ufw enable and immediately I started having problems. I can not use citrix anymore and Firefox takes forever to close. I disabled ufw and restarted. Problem persists.

[http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshotat2011-10-27211652.png](http://i276.photobucket.com/albums/kk14/bigcitycat/Screenshotat2011-10-27211652.png)

---

### Post by BigCityCat on 2011-10-27
I ran firefox in the terminal.

This is all I got except for some gtk errors.

sh: /usr/lib/nspluginwrapper/i386/linux/npviewer: not found

---

### Post by Dangertux on 2011-10-27
I'm not sure that this is an iptables or ufw issue to be honest. As far as citrix goes, citrix makes a lot of products, which are you referring to.

List of default ports for common citrix products can be found[ here]("http://www.google.com/url?sa=t&rct=j&q=default%2Bcitrix%2Bports&source=web&cd=4&ved=0CDwQFjAD&url=http%3A%2F%2Fsupport.citrix.com%2Fservlet%2FKbServlet%2Fdownload%2F2389-102-659842%2FCitrixPorts_by_Port_1199.pdf&ei=xgSqTry0AtK2tgfG68jiDg&usg=AFQjCNFdz890K2D0zN_Di_gKc9eNPaTHuA&sig2=tKRhEvnLnBj8QEBXbHN3kA&cad=rja")


If the product is not working you may have to allow traffic to it in ufw

```

sudo ufw allow from any to $yourip port $portnumber proto tcp

```

Hope that helps.

---

### Post by BigCityCat on 2011-10-28
All I know is that as soon as I turned on the firewall my browser started acting up and citrix which had worked with no problems stopped working. I disabled the firewall and the problem remains. It had to change a setting and is having some residual effect but I have no idea what it could be.

---

### Post by BigCityCat on 2011-10-28
> **Dangertux said:**
> I'm not sure that this is an iptables or ufw issue to be honest. As far as citrix goes, citrix makes a lot of products, which are you referring to.

List of default ports for common citrix products can be found[ here]("http://www.google.com/url?sa=t&rct=j&q=default%2Bcitrix%2Bports&source=web&cd=4&ved=0CDwQFjAD&url=http%3A%2F%2Fsupport.citrix.com%2Fservlet%2FKbServlet%2Fdownload%2F2389-102-659842%2FCitrixPorts_by_Port_1199.pdf&ei=xgSqTry0AtK2tgfG68jiDg&usg=AFQjCNFdz890K2D0zN_Di_gKc9eNPaTHuA&sig2=tKRhEvnLnBj8QEBXbHN3kA&cad=rja")


If the product is not working you may have to allow traffic to it in ufw

```

sudo ufw allow from any to $yourip port $portnumber proto tcp

```

Hope that helps.

sent private message

---

### Post by Dangertux on 2011-10-28
For future reference try to ask the questions in public so that they may help others who have the same issues.  However the syntax for the command you wanted would be.  

```
 
sudo ufw allow from any to 127.31.214.61 port 80,443 proto tcp

```Where 127.31.214.61 is your ip ports 80 and 443 are the ports you want opened and the protocol is tcp.

hope this helps.

---

### Post by BigCityCat on 2011-10-29
Thanks wasn't sure if I should openly post my ip. Even though I know that it is readily available if someone wants to see it.

---

### Post by BigCityCat on 2011-10-29
Okay that had to be the issue because it is working now. I did allow a few more ports off that pdf list you gave me but it is working and no more problems with the browser closing.

Thanks a lot.

---

### Post by BigCityCat on 2011-10-29
Should have mentioned that this was with citrix reciever/xenapp.

---

### Post by Dangertux on 2011-10-29
Glad it all worked out.

EDIT: Just so everyone knows. The ip I used 127.31.214.61 is a loopback address, I used it to demonstrate where the IP address would be, the OP originally had sent me a PM with his actual IP.

For amusement purposes : 127.anything is loop back.

---

