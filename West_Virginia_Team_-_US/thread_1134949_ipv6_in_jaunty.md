---
title: "ipv6 in jaunty"
date: 2009-04-24
forum: West Virginia Team - US
---

### Post by pacco on 2009-04-24
ok i have googled and read all the posts on how to disable ipv6 in jaunty.

nothing seems to work,i tried adding the disable.ipv6=1 on the kernel line and nothing just ignoring unknown option.
can anyone help me out?

Thanks in advance

---

### Post by hakweldag on 2009-04-29
Jes nothing is working but a patch:

[http://patchwork.ozlabs.org/patch/24127/](http://patchwork.ozlabs.org/patch/24127/)

and after that disable Ipv6 with :

sudo su -

echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

add : 
ipv6.disable=1

To check if Ipv6 is disabled :

sudo ip a | grep inet6

If there is a output then Ipv6 is not disabled.


[LEFT]If you know how to patch the jaunty kernel please help me, from the next kernel is not necessary to patch, because the code is in the 2.6.29.2 tree. So the disable option in the /proc/sys/net/ipv6/conf/all/disable_ipv6 is normally working.

In the kernel tree from jaunty 2.6.28.2 (witch I have) this option is not working without the kernel patch I gave as first link. 

There is also a guy who made a nasty, but I guess working, work around. 
[http://ubuntuforums.org/showpost.php?p=7033690&postcount=9](http://ubuntuforums.org/showpost.php?p=7033690&postcount=9)
But this is not the best and most beautiful way. 

Sow hope you or somebody else will help me out with the kernel patch thingy, I give you the patch link, please help me to patch!!!! 


:guitar:



[/LEFT]

---

### Post by SnappyU on 2009-04-29
This is once again, one of those, "Why on earth did they 'fix' something that was not broken?" moments.

New "features" that is for our own good should by default come disabled with the option to enable it, and not being force fed to us.  Think PulseAudio.

---

### Post by hakweldag on 2009-04-29
@[SnappyU]("http://ubuntuforums.org/member.php?u=275092")

My two cents man!!

Ridiculous why its not easy to enable or disable ipv6 or pulseaudio for example. Finally the nvidia support is alright. Programs load much easier etc. Its a good distro except for the Ipv6 and apache. 

I had the .PHTML horror also again, and its not fixable with the normal ways. 

So except for a few things its great, but the few things need to be sorted out.

---

### Post by hakweldag on 2009-04-30
Bump.....

---

### Post by pacco on 2009-05-01
ok,now how do you apply this patch?
:confused:

---

### Post by hakweldag on 2009-05-02
Yes pacco,

Thats the main question right now. 

Or its this patch to kill the ipv6, or its a upgrade to the 2.6.29.2 kernel. There is no other way.

Can some goeroe please help us out here?

---

### Post by pacco on 2009-05-03
i hope someone can,man this is getting ridiculous,i don't want to have to re-do my kernel just to disable ipv6
****

---

### Post by hakweldag on 2009-05-04
Seems like the guru´s have a holiday pacco. 

I have post a question about the ipv6 matter at the Dutch board. I will wait for another day, if there come nothing I will mail the patchmaker for a solution. 

You can disable ipv6 in the Firefox browers. Type about:config  in your browser, and search for Ipv6, click once  ¨disable = true¨ for disable ipv6 within Firefox. Its a little faster to browse. But globally needs a fix.

---

### Post by hakweldag on 2009-05-04
Check also this pacco, will make it a little faster. 

[[SIZE=+1][COLOR=black]**How To Speed Up Firefox (Helpful Vanity)**[/COLOR][/SIZE]]("http://www.freerepublic.com/focus/news/1299854/posts")
  
 Posted on **zo 12 dec 2004 21:45:50 CET** by [[COLOR=black]**KoRn**[/COLOR]]("http://www.freerepublic.com/%7Ekorn/")
   Here's something for broadband people that will really speed Firefox up: 
1.Type "about:config" into the address bar and hit return. Scroll down and look for the following entries: 
network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests 
Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading. 
2. Alter the entries as follows: 
Set "network.http.pipelining" to "true" 
Set "network.http.proxy.pipelining" to "true" 
Set "network.http.pipelining.maxrequests" to some number like 30. This means it will make 30 requests at once. 
3. Lastly right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it recieves. 
If you're using a broadband connection you'll load pages MUCH faster now!

---

### Post by pacco on 2009-05-04
yeah at least this wasnt dismissed as well as the aliases file was,lol
i already got firefox tweaked to these settings,still no reply on  how to apply the patch to disable the ipv6

---

### Post by hakweldag on 2009-05-06
Going totally out of my mind now. 

Ported everything to Debian pacco. They just did a release, and Ubuntu is build on it.

No ipv6 trouble and so on, just mod it with /etc/modprobe.d/aliases and your good. 

Maybe you want that too, I have one machine wich i keep for Ubuntu to look in the 
future, but at this moment I am setting up a debian server, desktop and laptop. 

Everything is working flawless. 

Will help you out if you want debian too.

---

### Post by pacco on 2009-05-07
i have the debian dvd's, i just wanted to know how to aplly the patch to disable ipv6 in ubuntu,but if debian works great for it,then debian it is

---

### Post by pacco on 2009-05-22
well even if i do have the debian dvd's,i would still like to disable ipv6 in ubuntu globally,i just wish i knew how to apply the patch.
:cry:

---

### Post by pacco on 2009-06-07
Hey evryone,finally found something that works go to this address
[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html)

i followed the instructions and it works,finally:o

P.S- I have a Ubuntu running on a toshiba L305-S5865

---

### Post by pacco on 2009-08-08
I finally found something that really works here is the address: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4), i tested it and confirmed that it works using 
lsmod | grep inet6, this really does stop ipv6

---

