---
title: "Hosting website"
date: 2019-09-18
forum: Server Platforms
---

### Post by yxridevvv on 2019-09-18
Hey I’m wanting to host a website on my Ubuntu server but when I put all the files there it don’t work I followed this [https://tutorials.ubuntu.com/tutorial/install-and-configure-apache#4](https://tutorials.ubuntu.com/tutorial/install-and-configure-apache#4) which allowed my server to display a page but not my url? Then I looked at [https://www.linode.com/docs/websites/hosting-a-website-ubuntu-18-04/](https://www.linode.com/docs/websites/hosting-a-website-ubuntu-18-04/) and it still doesn’t work can anybody help?

---

### Post by yancek on 2019-09-18
Is this on your local machine or do you have a site hosting service?  What does happen when you enter your URL?

---

### Post by TheFu on 2019-09-18
> **yancek said:**
> Is this on your local machine or do you have a site hosting service?  What does happen when you enter your URL?
And are you trying to access it from a different machine or from the same machine?

---

### Post by yxridevvv on 2019-09-18
Different the Ubuntu is hosted in a data centre

---

### Post by yxridevvv on 2019-09-18
the Ubuntu is hosted in a data centre and I just get a cloudflare 521 error

---

### Post by slickymaster on 2019-09-18
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2019-09-18
> **yxridevvv said:**
> the Ubuntu is hosted in a data centre and I just get a cloudflare 521 error

Is DNS setup?
Does the trivial test page in apache show up when you access it by IP?
Did you specifically setup cloudflare?  Cloudflare is a little beyond what a total noob should attempt, IMHO.
Is the firewall open for the port and allows connections from your workstation?
Is apache running?

I can't help with the LAMP stuff. Never use that. I don't have the skills to secure php properly.

---

### Post by yxridevvv on 2019-09-18
Everything is setup but I’ve never tried lamp I’ll see if I can get that to work

---

### Post by mörgæs on 2019-09-18
LAMP installs with one command:
```
sudo apt install lamp-server^
```

---

### Post by TheFu on 2019-09-18
> **yxridevvv said:**
> Everything is setup but I’ve never tried lamp I’ll see if I can get that to work

Please assume we are old, hard of hearing, idiots.  Can you please explain what "everything is setup" means?  Details.   We've asked a few questions.  If you don't intend to answer, that's fine.  Please let us know. 


You've basically said, "My car won't start", but didn't drop it off for anyone to check out.  What mechanic could possibly help?

---

### Post by yxridevvv on 2019-09-18
Everything works now but I’m not sure how to connect my domain to it [http://38.127.92.109](http://38.127.92.109)

---

### Post by #&amp;thj^% on 2019-09-18
Again with no answer's to the questions asked of you, Everything dose not work.
have a look here: [https://hooshmand.net/how-to-use-cloudflare/](https://hooshmand.net/how-to-use-cloudflare/)
And: [https://community.cloudflare.com/t/community-tip-fixing-error-521-web-server-is-down/42461](https://community.cloudflare.com/t/community-tip-fixing-error-521-web-server-is-down/42461)
Also like TheFu "I can't help with the LAMP stuff._ Never use that. I don't have the skills to secure php properly." _

---

### Post by SeijiSensei on 2019-09-18
Where are your domain's DNS records stored? You need to add an "A" record that points a hostname like "www" to your server's address.

```

www     IN     A     38.127.92.109

```

You'll also need to make sure that the configuration for your site in Apache has a matching ServerName or ServerAlias directive.

```

<VirtualHost *:80>
[stuff]
ServerName     www.example.com
ServerAlias    web.example.com
[stuff]
</VirtualHost>

```

---

### Post by yxridevvv on 2019-09-19
I got it to work! Thanks

---

### Post by SeijiSensei on 2019-09-19
Please tell us what you did, and select "Mark as Solved" from Thread Tools at the top of this thread.

---

### Post by annamurray on 2020-08-18
[COLOR=#000000][FONT=Arial]I faced the same problem. Could you tell me how to solve it?[/FONT][/COLOR]

---

### Post by coffeecat on 2020-08-18
@annamurray, please start your own thread, detailing your setup and exactly what problems you are facing. Necromancing an old thread where the OP is long gone is not the best way to get help. 

Thread closed.

---

