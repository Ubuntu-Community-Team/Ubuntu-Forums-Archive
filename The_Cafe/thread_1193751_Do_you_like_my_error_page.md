---
title: "Do you like my error page?"
date: 2009-06-21
forum: The Cafe
---

### Post by K.Y.A on 2009-06-21
Title page says it all. It's for my server. When someone goes to one of my 8 websites and clicks a link that is bad or types a wrong url it goes to this:


[http://www.directoryadmin.info/SOME%20ODD%20ERROR.html](http://www.directoryadmin.info/SOME%20ODD%20ERROR.html)

---

### Post by monsterstack on 2009-06-21
Not bad, but if you're trying to persuade people to stop using IE of all browsers, the best way to do it would be to have this in every page on every site that you run,

```
if(window.XMLHttpRequest){ //proceed as normal
        }
else
        {
        if(window.ActiveXObject){
                document.write "Error 404 Page Not Found"
                }
        }
```

If everybody did that, people would soon change their ways.

---

### Post by K.Y.A on 2009-06-21
> **monsterstack said:**
> Not bad, but if you're trying to persuade people to stop using IE of all browsers, the best way to do it would be to have this in every page on every site that you run,

```
if(window.XMLHttpRequest){ //proceed as normal
        }
else
        {
        if(window.ActiveXObject){
                document.write "Error 404 Page Not Found"
                }
        }
```If everybody did that, people would soon change their ways.

How do I make it change to the link instead of say error 404?

---

### Post by monsterstack on 2009-06-21
> **K.Y.A said:**
> How do I make it change to the link instead of say error 404?

Just my luck for making a joke like that! Just use the usual <a href="blah"> html you would normally. Are you serious, though? You want to send all IE users to the sin bin? It's your decision after all :)

---

### Post by K.Y.A on 2009-06-21
> **monsterstack said:**
> Just my luck for making a joke like that! Just use the usual <a href="blah"> html you would normally. Are you serious, though? You want to send all IE users to the sin bin? It's your decision after all :)

All my sites are Linux based anyway, except one, which will not have this feature. My sites:

[www.zephyruslinux.info](www.zephyruslinux.info)
[www.thelinuxhowto.co.nr](www.thelinuxhowto.co.nr)
[www.directoryadmin.info](www.directoryadmin.info)
[www.wbaker.co.nr](www.wbaker.co.nr)
mail.directoryadmin.info

---

### Post by SerenityKill3r on 2009-06-21
You would be a god among mere mortals if you do this :D

---

### Post by CharmyBee on 2009-06-21
Hey help I can't get into the limbo menu!!!

---

### Post by K.Y.A on 2009-06-21
> **CharmyBee said:**
> Hey help I can't get into the limbo menu!!!

Hit escape, go to game options and find the page that has the game controls. Find the thing that says limbo menu and make the bind letter L again.

---

### Post by K.Y.A on 2009-06-21
> **monsterstack said:**
> Just my luck for making a joke like that! Just use the usual <a href="blah"> html you would normally. Are you serious, though? You want to send all IE users to the sin bin? It's your decision after all :)
Like this:
```
if(window.XMLHttpRequest){ //proceed as normal
        }
else
        {
        if(window.ActiveXObject){
                <a href="http://www.directoryadmin.info/SOME%20ODD%20ERROR.html">
                }
        }
```

---

### Post by monsterstack on 2009-06-21
> **K.Y.A said:**
> Like this:

Almost:
```
if(window.XMLHttpRequest){ //proceed as normal
        }
else
        {
        if(window.ActiveXObject){
                document.write('<a href="http://www.directoryadmin.info/SOME%20ODD%20ERROR.html">text</a>')
                }
        }
```

I think. I feel like I'm helping you commit a crime. I shall have no further part of this. :P

---

### Post by K.Y.A on 2009-06-21
> **monsterstack said:**
> Almost:
```
if(window.XMLHttpRequest){ //proceed as normal
        }
else
        {
        if(window.ActiveXObject){
                document.write('<a href="http://www.directoryadmin.info/SOME%20ODD%20ERROR.html">')
                }
        }
```I think. I feel like I'm helping you commit a crime. I shall have no further part of this. :P

Bill Gates is a crime :)

EDIT: This is html, right? I guess I put it into the header?
EDIT2:oooo this looks like css or javahell.

---

### Post by K.Y.A on 2009-06-21
I can still view the site in windows explorer :(

---

### Post by monsterstack on 2009-06-21
> **K.Y.A said:**
> I can still view the site in windows explorer :(

Yes, it's javascript.
```
<script language="javascript"> 
if(window.XMLHttpRequest){ //proceed as normal
        }
else
        {
        if(window.ActiveXObject){
                document.write('<a href="lololol">zomg</a>')
                }
        }
</script>
```

Better?

---

### Post by K.Y.A on 2009-06-21
> **monsterstack said:**
> Yes, it's javascript.
```
<script language="javascript"> 
if(window.XMLHttpRequest){ //proceed as normal
        }
else
        {
        if(window.ActiveXObject){
                document.write('<a href="lololol">zomg</a>')
                }
        }
</script>
```Better?

I put it in the body, saved it to server, and ran it in my XP virtual machine using idiot explorer 7. IT still works :( see screenshot.

---

### Post by monsterstack on 2009-06-21
> **K.Y.A said:**
> I put it in the body, saved it to server, and ran it in my XP virtual machine using idiot explorer 7. IT still works :( see screenshot.

Hrmm, how odd. But then I don't use javascript or Windows much so how would I know? :P Perhaps you should try this instead:

```
<!--[if IE]>
<script type="text/javascript">
  document.write("etc stuff etc")
</script>
<![endif]-->
```

or maybe this:
```

<SCRIPT LANGUAGE="JavaScript" TYPE="text/javascript">
<!--
  if( -1 != navigator.userAgent.
      indexOf ("MSIE") )
  {
    location.href="error_page.html";
  }
  else
  {
    // load the other version
    location.href="other_page.html";
  }
-->
</SCRIPT>
```

Be careful!! And if it still doesn't work, read up on browser-specific code. Start [here]("http://perishablepress.com/press/2006/09/04/fun-with-downlevel-conditional-comments/").

---

### Post by K.Y.A on 2009-06-21
Yay, the first one kinda works, but it just says "etc stuff etc" on top of screen, lol.

If I do the 
('<a href="lololol">zomg</a>')




It just creates a link that says "zomg"

---

### Post by K.Y.A on 2009-06-21
I tried 
```
<!--[if IE]>
<script type="text/javascript">
  document.write("<meta http-equiv="REFRESH" content="0;url=http://www.directoryadmin.info/SOME%20ODD%20ERROR.html">")
</script>
<![endif]-->
```And nothing happens...


EDIT: just a typo in code. IT WORKS NOW THANK YOU! I LOVE YOU (well not really).

---

### Post by K.Y.A on 2009-06-21
Haha, the funniest part is when you visit [www.thelinuxhowto.co.nr](www.thelinuxhowto.co.nr) a piece of java code above the new code makes it take like 3 seconds to load, and you think its gonna work, then just crashes to the error page. Just like a Windows error. :D:D:D

---

### Post by monsterstack on 2009-06-21
Well I'm glad you fixed it. :P I'm sorry I thought you just wanted a link to the error page. To do a redirect you could also use "window.location" javascript: 

```
<!--[if IE]>
<script type="text/javascript">
  window.location = "path/to/error/page.html"
</script>
<![endif]-->
```

That'll take the poor IE user directly to the error page. Heh heh. So evil.

---

### Post by frup on 2009-06-22
On a website that I did the web design on and used to help administer, we used to disallow IE for quite a few things.

IE users could become members,
IE users were given an error message stating that there browser was not standards compliant,
IE users could not download the content, which was the entire point of the site.

From this we got about 55% firefox usage, 5% opera usage and 2% safari usage.

IE 7 came out shortly afterwards. We then sold the website and the new owner allowed IE and pretty much ruined everything that was good about the site.

It saved us a lot of bandwidth and allowed us to use valid XHTML. I couldn't be bothered installing IE's for linux so wasn't going to try make everything work in IE and disallowing it was far easier. 

We were getting about 90,000 hits per month.

---

### Post by -grubby on 2009-06-22
Whoa, wait a second! Isn't one of the main "selling" points of Linux choice? Isn't it a user's *choice* to use Internet Explorer? Go ahead, ignore Internet Explorer support, but don't purposely break the website for users of operating systems and/or browsers you don't approve of.

P.S: I don't consider it very 'new age' to edit text files to get my graphical hardware working ;)

---

### Post by frup on 2009-06-22
Choice is excellent, when you know of the different options.

---

### Post by cc8balla on 2009-06-22
I find it funny that people hate IE so much (trust me, I am one of them) but then code their website, and go to this thread's lengths, to make their website inaccessable to IE users. So basically, you wish to NOT have 50% of the market share visiting your site? Seems awful stupid to me. 

IE7 isn't hard to code for, I do it all the time. IE6 is the nightmare, and MOST have upgraded to that. That is a browser I will not code for anymore, and I will not just cut IE users off my site, because well....


...I'm not an elitist, lazy, idiot.

---

### Post by Skripka on 2009-06-22
> **cc8balla said:**
> I find it funny that people hate IE so much (trust me, I am one of them) but then code their website, and go to this thread's lengths, to make their website inaccessable to IE users. So basically, you wish to NOT have 50% of the market share visiting your site? Seems awful stupid to me. 


My thoughts exactly.

---

### Post by Wiebelhaus on 2009-06-22
That's cool.

---

### Post by Simian Man on 2009-06-22
No, it's retarded and makes you look extremely unprofessional - even to a fellow Linux user like me.

---

### Post by RATM_Owns on 2009-06-22
What about mah error page?
[http://ratm.net63.net/NONEXISTANTLINK](http://ratm.net63.net/NONEXISTANTLINK)

---

