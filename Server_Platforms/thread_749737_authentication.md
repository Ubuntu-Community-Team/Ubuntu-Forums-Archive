---
title: "authentication"
date: 2008-04-08
forum: Server Platforms
---

### Post by dsonc on 2008-04-08
Hello you all! My question is: to access the internet i have to authenticate my machine on the firewall, actually i do this trough web browser on the desktop: put the ip address of my firewall in the URL box and then it bring to me the boxes to enter my user and password and i can access the internet. But using my ubuntu server through the command line i don't how to pass to firewall these informations.

Sorry my poor English Best regards.

Edson

---

### Post by pseudo-random on 2008-04-08
What application are you using on the command line?
Your company is blocking all non-HTTP for security.

---

### Post by dsonc on 2008-04-08
Hi 'pseudo-random'! That's the point, i just enter into shell on my server box and i don't know  how to pass  to the firewall or what command use to make the authetication using *_command line_*. Trough the desktop box it's easy, as i described in the post. I did several researches on the web but they wasn't succesfully.Thank you.

---

### Post by Maxtorm on 2008-04-08
dsonc: have you tried accessing it using the [EMAIL="user@pass@site.doma"]user:pass@site.doma[/EMAIL]in format? For instance, if you were trying to access "http://www.dsonc.com/" using userid "dscon" and password "blahblah", you would use ```
http://dscon:blahblah@www.dsonc.com/
```

---

### Post by Slushdoot on 2008-04-08
Worst case scenario, if you can't get any more elegant means of authentication working, you could install elinks on your Linux machine and manually authenticate with that. :)

---

### Post by cdenley on 2008-04-09
If it uses http authentication
```

wget -O /dev/null --http-user=user --http-password=password http://[firewall ip]

```
If it uses another form of authentication, then we would need to see the html source of the login page.

---

### Post by dsonc on 2008-04-10
> **Slushdoot said:**
> Worst case scenario, if you can't get any more elegant means of authentication working, you could install elinks on your Linux machine and manually authenticate with that. :)

Aaah, yeah!! I will study it, thank you very much.

---

### Post by dsonc on 2008-04-10
> **cdenley said:**
> If it uses http authentication
```

wget -O /dev/null --http-user=user --http-password=password http://[firewall ip]

```
If it uses another form of authentication, then we would need to see the html source of the login page.

i tried that way but,  i didn't used some parameters. That one is "beautiful"! Thanks.

---

