---
title: "Another Virtual Hosting Question"
date: 2006-06-28
forum: Server Platforms
---

### Post by jordans on 2006-06-28
I have a new problem with setting up virtual hosting. This is the code for how the file stands now.```

<VirtualHost *:80>
ServerName doddjohnson.com
ServerAlias www.doddjohnson.com
DocumentRoot /var/www/DJC/
CustomLog /var/log/apache2/sitename.com-access.log combined
ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>
<VirtualHost *:80>
ServerName vashontechsupport.com
ServerAlias www.vashontechsupport.com
DocumentRoot /var/www/NPP/
CustomLog /var/log/apache2/sitename.com-access.log combined
ErrorLog /var/log/apache2/sitename.com-error.log
</VirtualHost>

```
For some reason or another when you type vashontechsupport.com it works and when you type **www**.vashontechsupport.com it doesn't work. Is there something that I am missing. I added the address as an alias too.

---

### Post by MJN on 2006-06-29
You need to sort your DNS out.
 
**vashontechsupport.com** has an A record pointing to **67.170.99.31** whereas **[www.vashontechsupport.com]("http://www.vashontechsupport.com")** has a CNAME of **premium6.geo.yahoo.akadns.net** which has multiple A records - none of which point to **67.170.99.31**.
 
In this instance I would suggest removing the CNAME and putting an A record to 67.170.99.31 (or a CNAME of vashontechsupport.com).
 
Needless to say, given the nature of your business you really ought to know stuff like this.. ;)
 
Mathew

---

### Post by jordans on 2006-06-30
Oh, it isn't setup that way now but usually it is. I will fiddle with it a bit more.

---

### Post by MJN on 2006-06-30
The DNS is now aligned - and it works with both names. Do you still think you've got a problem? Remember the old DNS records may be cached hence without some flushing you might not see the effects straight away.

Mathew

---

### Post by jordans on 2006-06-30
Ya, it wasn't me. When I went back into the Yahoo control panel I found that the settings hadn't been changed at all. What I had done wasn't saved from before. Thanks for you help anyway!

Jordan ;) (and hey, should I know all this. I am only 14)

---

### Post by MJN on 2006-07-01
[SIZE=2]To quote from your website:

[I][FONT=Trebuchet MS]Do you have a computer or technical problem? We may be thirteen and fourteen but that doesn't mean we can't answer it!
 
 [/FONT][/I][/SIZE]  [FONT=Trebuchet MS][SIZE=2]Seriously, when I was 14 I didn't even know what a website was so you've got one up on me there!
  
  Good to see you're now up-and-running.
  
  Mathew

P.S. I would ditch your comments page, at least whilst you fill it with staged comments from the same person! ;)
  [/SIZE][/FONT]

---

### Post by Randomskk on 2006-07-01
[QUOTE=jordans](and hey, should I know all this. I am only 14)[/QUOTE]
Pft, I had a nameserver and apache setup when I was 14 :P
..which just about makes us equal XD

I'm also part of a tech company with two 15 year olds o_o;

---

### Post by jordans on 2006-07-02
Thanks, 
Believe it or not the comments page is real, didn't have to make em up. I love how supportive our school is of nerds! We just got our buisness license and are about to begin the advertising routine. Oh boy I love buisness!

---

### Post by MJN on 2006-07-02
Yeah right...

---

