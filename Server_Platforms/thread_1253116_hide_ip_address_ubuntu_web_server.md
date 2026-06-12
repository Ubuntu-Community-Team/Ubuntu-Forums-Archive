---
title: "hide ip address ubuntu web server"
date: 2009-08-29
forum: Server Platforms
---

### Post by Kaparzo on 2009-08-29
Hi all, 

Newbie question time.

I just installed LAMP on an ubuntu server and its working great.  Only problem is, when you hover over a link on the webpage that I've uploaded, the IP address shows in the status bar and I would like to hide this.

For example, if the html says something like...

> <a href="file.pdf">link</a>

when you hover over the link, the status bar will say something like...

> [http://72.104.103.102/file.pdf](http://72.104.103.102/file.pdf)

how can i configure apache to make it say "domain/file.pdf" instead of the IP without redoing the HTML code?

thanks in advance

---

### Post by hessiess on 2009-08-29
> **Kaparzo said:**
> Hi all, 

Newbie question time.

I just installed LAMP on an ubuntu server and its working great.  Only problem is, when you hover over a link on the webpage that I've uploaded, the IP address shows in the status bar and I would like to hide this.

For example, if the html says something like...



when you hover over the link, the status bar will say something like...



how can i configure apache to make it say "domain/file.pdf" instead of the IP without redoing the HTML code?

thanks in advance

Set up a dynamic domain name, i.e. with dyndns.

---

### Post by Kaparzo on 2009-08-30
thanks

i should be able to do this with godaddy right (already have an account with them)? dyndns.com costs extra cash

---

### Post by koenn on 2009-08-30
you understand that this merely cosmetics; the people that browse your web pages already know the IP address of that server, right ?

---

### Post by Kaparzo on 2009-08-31
yup i understand that

---

### Post by koenn on 2009-08-31
if the server reports its address to the server, is that because you use urls with an ip address ?

if so, that's probably the reason the browser shows an address rather than a name.

if not, maybe the (web-)server doesn't know its name - check your apache configs for 'ServerName' and/or and make sure there's an address and matching name in the DNS server this Web server uses, or in the /etc/hosts of the machine where the web server runs.

---

### Post by credobyte on 2009-08-31
```
<a href="http://78.128.82.94/mybook.pdf">Link to my book</a>

```

When you hover the link, status bar shows it's target ( href ). You can't mask it.

---

### Post by koenn on 2009-08-31
> **credobyte said:**
> ```
<a href="http://78.128.82.94/mybook.pdf">Link to my book</a>

```

When you hover the link, status bar shows it's target ( href ). You can't mask it.

check the OP; he's doing relative links.

---

### Post by credobyte on 2009-08-31
> **koenn said:**
> check the OP; he's doing relative links.

So what ? Target will always stay the same, no matter in what style you do it ..
All I can think off is to use JavaScript @ onClick event ( create a fake link & use JavaScript/AJAX to fetch data from somewhere else ).

---

### Post by koenn on 2009-08-31
I don't think you understand the question. 

If I write a an absolute reference, say
```
<a href="http://78.128.82.94/mybook.pdf">Link to my book</a>
```, it's obvious the status bar will show [http://78.128.82.94/mybook.pdf](http://78.128.82.94/mybook.pdf) when hovering. 
That's not the quaetion


If you use a relative path , say
```
<a href="mybook.pdf">Link to my book</a>
```
this will be pre-pended in the status bar: the status bar might show 
[http://78.128.82.94/mybook.pdf](http://78.128.82.94/mybook.pdf) *or* [http://hostname.domain.ltd/mybook.pdf](http://hostname.domain.ltd/mybook.pdf)

the question is how you control which of the 2 possibilities will appear.

---

### Post by credobyte on 2009-08-31
> **koenn said:**
> I don't think you understand the question. 

If I write a an absolute reference, say
```
<a href="http://78.128.82.94/mybook.pdf">Link to my book</a>
```, it's obvious the status bar will show [http://78.128.82.94/mybook.pdf](http://78.128.82.94/mybook.pdf) when hovering. 
That's not the quaetion


If you use a relative path , say
```
<a href="mybook.pdf">Link to my book</a>
```this will be pre-pended in the status bar: the status bar might show 
[http://78.128.82.94/mybook.pdf](http://78.128.82.94/mybook.pdf) *or* [http://hostname.domain.ltd/mybook.pdf](http://hostname.domain.ltd/mybook.pdf)

the question is how you control which of the 2 possibilities will appear.

If you open a website through it's IP, you can't pretend or let HTML think that you're on domain.com, not it's IP.
Th, someone will probably find a reason to argue, but there's no way you could do it with in-built functions/expressions.

---

### Post by koenn on 2009-08-31
> **credobyte said:**
> If you open a website through it's IP, you can't pretend or let HTML think that you're on domain.com, not it's IP.

Well, that's exactly what I said in post 6.

---

