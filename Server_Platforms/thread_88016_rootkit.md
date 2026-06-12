---
title: "rootkit?"
date: 2005-11-09
forum: Server Platforms
---

### Post by aragorn2909 on 2005-11-09
Perhaps someone can shed some light on this for me.   I have run both chkrootkit and rkhunter on my hoary box, and both are offering up some things that I'm not sure I should (or shouldn't) be concerned with:
chkroot
```
Checking `bindshell'... INFECTED (PORTS:  600)
Checking `lkm'... You have     1 process hidden for readdir command
You have     2 process hidden for ps command
Warning: Possible LKM Trojan installed

```
rkhunter
```
* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.udev.tdb
/dev/.udevdb /etc/.pwd.lock
---------------
Please inspect:  /dev/.udevdb (directory)
```

Any help here is appreciated.

A

---

### Post by HJThis on 2005-11-09
Hello,aragorn2909

Hmm i don't get that with chkrootkit

but i get the same thing with rkhunter

i think the one from rkhunter is a F&P

but i'm sure one of the pros here may have an idea for you

also did you run netstat or nmap to see if anything 
looks out of place?????

Best of luck

---

### Post by aragorn2909 on 2005-11-09
[QUOTE=HJThis]

also did you run netstat or nmap to see if anything 
looks out of place?????

Best of luck[/QUOTE]

Netstat doesn't show anything out of the ordinary, just things related to nfs/cups and the like...

---

### Post by HJThis on 2005-11-09
Hi,

Now not sure how much help this is but have a look for your self

[http://www.google.com/search?lr=&ie=UTF-8&oe=UTF-8&q=Warning%3A%20Possible%20LKM%20Trojan%20installed](http://www.google.com/search?lr=&ie=UTF-8&oe=UTF-8&q=Warning%3A%20Possible%20LKM%20Trojan%20installed)

i think your looking at a false positive.

but again i could be wrong

Best of luck

one other thing are you running both progs up todate

---

### Post by LordHunter317 on 2005-11-09
The second output is not to be worried about.  Not sure about the first.

---

### Post by lotusleaf on 2005-11-09
On the rkhunter website there's a feedback form for contacting the author of Rootkit Hunter. FWIW YMMV

You may also update your version of rkhunter online via CLI, read the included docs, sometimes that helps to avoid FP.

---

### Post by aragorn2909 on 2005-11-10
Thanks all for replying.  It looks as if chkrootkit *was* offering me a false positive.  Ran it again tonight (several times) and everything came up clean.  The RKHunter output is still the same however.  Will contact the author, see what they have to say about it.  Either way, my mind is much more at ease and as the saying goes, all's well that ends well.

---

### Post by HJThis on 2005-11-10
Hey,aragorn2909

Glad to hear it's working out for you as for
rkhunter i was gething them same thing tell 
i run an update.

sudo rkhunter --update

was gone for a day or 2 came back oh well

it's a FP i'm sure of it

Best of luck ;)

---

### Post by aragorn2909 on 2005-11-10
[QUOTE=HJThis]Hey,aragorn2909

Glad to hear it's working out for you as for
rkhunter i was gething them same thing tell 
i run an update.

sudo rkhunter --update

was gone for a day or 2 came back oh well

it's a FP i'm sure of it

Best of luck ;)[/QUOTE]

Well, I updated rkhunter last night, and still receiving the same warning, but not nearly as concerned about it as I was.  I am also fairly convinced that its a false positive.  Thanks again for helping out, it sure does put my mind at ease to see that others are receiving the same warning.

A

---

### Post by HJThis on 2005-11-10
Hi,aragorn2909

Ya it's one of them odd things

BOL ;)

---

