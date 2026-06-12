---
title: "iplist"
date: 2012-07-28
forum: Security
---

### Post by antobbo on 2012-07-28
Chaps, can anybody help me to install iplist please? I found this [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183) but the version of ubuntu I am running (12.04) isn't there. What should I do? Sorry I am pretty new to ubuntu

---

### Post by ubudog on 2012-07-28
Hi, [this]("http://ubuntuforums.org/showpost.php?p=12121429&postcount=6") post may help you.

Best of luck,
ubudog

---

### Post by antobbo on 2012-07-28
hi thanks for that, really useful. It is all done, and I have removed the current list and updated it, but in the list tab now I have only this lists.php. Is that correct?
Also, about iplist in general, is there anything else I need to do? Like do I have to open it every time I access my laptop etc
thanks

---

### Post by dodo3773 on 2012-07-29
> **antobbo said:**
> hi thanks for that, really useful. It is all done, and I have removed the current list and updated it, but in the list tab now I have only this lists.php. Is that correct?
Also, about iplist in general, is there anything else I need to do? Like do I have to open it every time I access my laptop etc
thanks

There should be an included daemon called ipblock. Not sure what lists.php is off the top of my head but you probably need to add ip block lists so that it is actually blocking something. If I go to the tab called "Lists" in my gui it looks like this:
```

/home/dodo3773/Documents/NewBlocklists/activision.gz
/home/dodo3773/Documents/NewBlocklists/blizzard.gz 
/home/dodo3773/Documents/NewBlocklists/bt_ads.gz 
/home/dodo3773/Documents/NewBlocklists/bt_bogon.gz 
/home/dodo3773/Documents/NewBlocklists/bt_edu.gz 
/home/dodo3773/Documents/NewBlocklists/bt_level1.gz 
/home/dodo3773/Documents/NewBlocklists/bt_level2.gz 
/home/dodo3773/Documents/NewBlocklists/bt_level3.gz 
/home/dodo3773/Documents/NewBlocklists/bt_microsoft.gz 
/home/dodo3773/Documents/NewBlocklists/bt_proxy.gz 
/home/dodo3773/Documents/NewBlocklists/bt_spyware.gz 
/home/dodo3773/Documents/NewBlocklists/bt_templist.gz 
/home/dodo3773/Documents/NewBlocklists/electronicarts.gz 
/home/dodo3773/Documents/NewBlocklists/ijfqtofzixtwayqovmxn.gz 
/home/dodo3773/Documents/NewBlocklists/nintendo.gz 
/home/dodo3773/Documents/NewBlocklists/squareenix.gz 
/home/dodo3773/Documents/NewBlocklists/ubisoft.gz 
/home/dodo3773/Documents/NewBlocklists/xfire.gz

```

Should be a button on the bottom called "Add File" that you can click and point it to lists that you have downloaded to block. I get my lists from here:
[http://www.iblocklist.com/lists.php](http://www.iblocklist.com/lists.php)
I do not think you set it up right. At least it does not sound like it. On that web page you need to go to the "Update URL" section and download each list you want. Before I was only pointing you to that site so that you can look and see what lists you might want. So, remove lists.php from that list because it is probably not doing anything at all.

---

### Post by antobbo on 2012-08-24
fantastic thanks for your help. Now my list looks like this [http://antobbo.webspace.virginmedia.com/various_tests/iplist_list.png](http://antobbo.webspace.virginmedia.com/various_tests/iplist_list.png)
1 questions if I may:when I enable the lists some websites, I mean ordinary websites, are not available anymore, it's like I can't connect to them anymore, say for example google calendar and others that are otherwise innocuous, iplist blocks the connection so I have to disable it
thanks

---

### Post by dodo3773 on 2012-08-24
> **antobbo said:**
> fantastic thanks for your help. Now my list looks like this [http://antobbo.webspace.virginmedia.com/various_tests/iplist_list.png](http://antobbo.webspace.virginmedia.com/various_tests/iplist_list.png)
1 questions if I may:when I enable the lists some websites, I mean ordinary websites, are not available anymore, it's like I can't connect to them anymore, say for example google calendar and others that are otherwise innocuous, iplist blocks the connection so I have to disable it
thanks


Your welcome. Happy to help. The simplest way to unblock whatever website you want is to add it to your whitelist. For example, if you wanted Facebook to the whitelist, you would do this:

Find the ip range
```

$ host facebook.com
facebook.com has address 66.220.152.16
facebook.com has address 66.220.158.70
facebook.com has address 69.171.234.21
facebook.com has address 69.171.237.16
facebook.com has address 69.171.247.21
facebook.com has address 66.220.149.88
facebook.com has IPv6 address 2a03:2880:10:cf01:face:b00c::
facebook.com has IPv6 address 2a03:2880:2110:3f01:face:b00c::
facebook.com has IPv6 address 2a03:2880:2110:9f01:face:b00c::
facebook.com has IPv6 address 2a03:2880:10:8f01:face:b00c:0:25
facebook.com mail is handled by 10 smtpin.mx.facebook.com.
$ whois 66.220.158.70 | grep -e "inetnum" -e "NetRange"
NetRange:       66.220.144.0 - 66.220.159.255
$               

```

Now we know the net range for facebook.com is
```

66.220.144.0 - 66.220.159.255

```

So let's put that in an ip blocklist p2p format like so:
```

Facebook:66.220.144.0-66.220.159.255

```

Now let's stop ipblock, add the above to it's whitelist, and restart it. Here is mine (not too much in there just google): 
```

$ cat /var/cache/iplist/allow-perm.p2p
Google:173.194.0.0-173.194.255.255
$ 

```

That's about it. If you have any more questions feel free to ask.

---

### Post by antobbo on 2012-08-24
hi thanks for that. I see. You know your code to find the ip range, did you use the terminal to do that or is it a script?
SO I would have to do this operation for every website I wish to visit if they are blocked
thanks

---

### Post by dodo3773 on 2012-08-24
> **antobbo said:**
> hi thanks for that. I see. You know your code to find the ip range, did you use the terminal to do that or is it a script?
SO I would have to do this operation for every website I wish to visit if they are blocked
thanks

No, that's not a script. It's terminal output. I put the "$ command" to let you know that it is to be run as a regular user. Usually when you see something like that on wikis, forums, etc.. "$" is your user and "#" is for root. To answer your question yes. If you are running into a site that is blocked and you want to add it to your whitelist the process would be the same.

---

### Post by antobbo on 2012-08-25
fantastic, thanks a lot for your help, I will give this a go right away!

---

### Post by antobbo on 2012-08-25
AH sorry, one thing I haven't asked you. Some of the lists picked up form here [http://www.iblocklist.com/lists.php](http://www.iblocklist.com/lists.php) are files, which is ok, I managed to put them on upblock, but some others are in a differen formats like this one [http://iblocklist.rlcassidy.net/f/osdrsopcohkhlzytgzng/bt_bogon.gz](http://iblocklist.rlcassidy.net/f/osdrsopcohkhlzytgzng/bt_bogon.gz)
This is not a file, it is just a webpage with a list, so how do I proceed in this case? Do I save this in a file and import it the same way? if so what extension should the file have?
thanks

---

### Post by dodo3773 on 2012-08-25
> **antobbo said:**
> AH sorry, one thing I haven't asked you. Some of the lists picked up form here [http://www.iblocklist.com/lists.php](http://www.iblocklist.com/lists.php) are files, which is ok, I managed to put them on upblock, but some others are in a differen formats like this one [http://iblocklist.rlcassidy.net/f/osdrsopcohkhlzytgzng/bt_bogon.gz](http://iblocklist.rlcassidy.net/f/osdrsopcohkhlzytgzng/bt_bogon.gz)
This is not a file, it is just a webpage with a list, so how do I proceed in this case? Do I save this in a file and import it the same way? if so what extension should the file have?
thanks


Right click the page and save page as "bt_bogon.gz". Simple enough.

---

