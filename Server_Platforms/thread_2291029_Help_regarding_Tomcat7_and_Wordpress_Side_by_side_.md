---
title: "Help regarding Tomcat7 and Wordpress Side by side installtions"
date: 2015-08-17
forum: Server Platforms
---

### Post by Mohan1289 on 2015-08-17
Hey guys, i have a little problem with installation of wordpress and tomcat 7

I am able to install both of them by using "sudo apt-get install tomcat7-* and several steps for wordpress.

But i am unable to redirect through servers as i want.


My Goal is:

if i enter "www.example.com" It should re direct it to the site in tomcat7 server (port 8080)
If i enter "www.example.com/wordpress" It should redirect it to the site in apache2 (port 80)


I tried several things but i am not able to get the result.

I tried using proxy but it ended up like whatever i entered it's going for port 8080 
:( :( :(

Can any one help me with this?? any suggestions or solutions??


Thank you

---

### Post by SeijiSensei on 2015-08-17
You can't redirect a URI like /wordpress to another port.  What you might be able to use is a different hostname for the tomcat site like this:
```

<VirtualHost *:80>
ServerName wordpress.example.com
Redirect / http://www.example.com:8080/
</VirtualHost>

```
Now requests for [http://wordpress.example.com/](http://wordpress.example.com/) will be sent to [http://www.example.com:8080/](http://www.example.com:8080/).

---

### Post by Mohan1289 on 2015-08-17
Thanks for the info seiji.. so i can't redirect like /wordpress huh?

so i will have to change the port number of wordpress to 8082 and redirect it to wordpress.example.com???

---

### Post by Bucky Ball on 2015-08-17
*Thread moved to **Server Platforms**.*

---

