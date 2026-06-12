---
title: "Error in the install CP ispconfig"
date: 2009-08-25
forum: Server Platforms
---

### Post by Abdul Majeed on 2009-08-25
[COLOR=red]Hello[/COLOR] ...
 
I have [COLOR=red]problem[/COLOR] During the install of the Control Panel (** [FONT=Arial][SIZE=2][COLOR=red]ispconfig[/COLOR][/SIZE][/FONT]** ) 
 
the Link Explanation : [**Click here**]("http://www.howtoforge.com/perfect-server-ubuntu-8.10-ispconfig-3-p5")
 
**+----------[COLOR=red]------[COLOR=darkgreen]--[COLOR=blue]-[COLOR=darkorange]--[/COLOR]-[/COLOR]--[/COLOR]--------[/COLOR]-------------+**
 
**[COLOR=red]The problem install CP[/COLOR] [COLOR=red]...[/COLOR]**
 
[PHP]sh: /etc/init.d/saslauthd: Permission denied
 * Restarting web server apache2
   ...fail!
Installation completed.
[/PHP]
 
Greetings

---

### Post by cariboo on 2009-08-25
You have to use sudo to run the command eg:

```
sudo /etc/init.d/apache2 restart
```

---

