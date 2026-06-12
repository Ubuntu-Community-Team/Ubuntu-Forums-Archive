---
title: "Dansgaurdian Parental Controls Problem"
date: 2006-11-15
forum: Ubuntu Christian Edition
---

### Post by ReaderRat on 2006-11-15
Last night,while researching on the net, I was denied access with a great big 
[COLOR="Red"][SIZE="7"][FONT="Arial Black"]STOP[/FONT][/SIZE][/COLOR]
I wondered what the problem was, but was too tired to figure it out. I ran into this again tonight. But,tonight , I could see the faint lettering on the stop sign said Dansguardian. I found "Configure ParentalControls", and I attempted to do so. I clicked on it and nothing happened....
How can I turn off this annoying and bothersome Dansguardian?

---

### Post by mhancoc7 on 2006-11-15
> **ReaderRat said:**
> Last night,while researching on the net, I was denied access with a great big 
[COLOR=Red][SIZE=7][FONT=Arial Black]STOP[/FONT][/SIZE][/COLOR]
I wondered what the problem was, but was too tired to figure it out. I ran into this again tonight. But,tonight , I could see the faint lettering on the stop sign said Dansguardian. I found "Configure ParentalControls", and I attempted to do so. I clicked on it and nothing happened....
How can I turn off this annoying and bothersome Dansguardian?

I am not sure why you would get the STOP sign. It is not default in Ubuntu CE or in the other dansguardian scripts that are part of the Ubuntu CE project. :-k  You can completely remove the dansguadian by doing the following.

```
    apt-get --purge remove --assume-yes "dansguardian"
    apt-get --purge remove --assume-yes "tinyproxy"
    apt-get --purge remove --assume-yes "clamav"
    apt-get --purge remove --assume-yes "firehol"
    apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"
```I hope that will help.

You will also need to unlock the firefox proxy settings using the script attached. Simply extract the file and then double click on the "unlock_proxy" file and choose run in terminal.

God Bless, Jereme

---

### Post by ReaderRat on 2006-11-16
Thanks, Jereme,

My web browsing and research will be much more enjoyable without the STOP!

Ben (ReaderRat)

---

### Post by sam_uk on 2006-12-03
I woulds also like to remove Dans guardian. I have followed the above instructions. I have also run iptables -L and iptables -F.

I can ping google, download software using apt etc, i can use vnc.

I have tried changing the proxy settings in firefox to 'direct connection to the internet' I just get a 'unable to connect - firefox can't establish a connection to the server' message.

anyone out there help??

thanks

Sam]   (*,)

<edit> Ok i kind of fixed it by setting my browser to use an anonymous proxy from this list [http://www.proxy4free.com/page1.html](http://www.proxy4free.com/page1.html) if anyone can help with a 'proper' fix it would still be appriciated..

---

### Post by mhancoc7 on 2006-12-03
I have just released a script to disable/enable dansguardian in Ubuntu CE.

[http://www.ubuntuforums.org/showthread.php?p=1841627#post1841627](http://www.ubuntuforums.org/showthread.php?p=1841627#post1841627)

Jereme

---

