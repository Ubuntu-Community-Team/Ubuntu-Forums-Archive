---
title: "Got Starling today!!"
date: 2009-09-22
forum: System76 Support
---

### Post by Tart on 2009-09-22
Woohooo! Waiting is over. Got a new toy today! The one I got is actually for my wife, but I played with it all day today. Great machine, love it. I asked my wife to write a short review of her experience with Starling and ubuntu, and I'll post it here once she is done with it.

PS. On the side note, how do I change machine name? Standard way of going to System -> Administration -> Networking doesn't seems to work since there is no Networking. There is Network Tools and I couldn't find tab with computer name in there.

Thanks

---

### Post by thomasaaron on 2009-09-23
Hey! I don't think we've ever had that question here before! 

Open a terminal and run this command...
```
sudo gedit /etc/hostname
```

Change the name. Save. Reboot.

---

### Post by Tart on 2009-09-23
Thank you Thomas!

---

### Post by aysiu on 2009-09-24
It's good to get into the habit of using *gksudo* for graphical applications: ```
gksudo gedit /etc/hostname
```

---

### Post by macabrem on 2009-09-24
> **aysiu said:**
> It's good to get into the habit of using *gksudo* for graphical applications: ```
gksudo gedit /etc/hostname
```

I've seen this mentioned before, but I can't recall ever reading a concise reason for this.  Can somebody give a fairly simple explanation for using gksudo for graphical apps?  Thanks.

---

### Post by aysiu on 2009-09-24
> **macabrem said:**
> I've seen this mentioned before, but I can't recall ever reading a concise reason for this.  Can somebody give a fairly simple explanation for using gksudo for graphical apps?  Thanks.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

It's the same reason you should use ```
sudo -i
``` instead of *sudo -s* if you want a persistent root prompt.

---

### Post by macabrem on 2009-10-09
> **thomasaaron said:**
> Hey! I don't think we've ever had that question here before! 

Open a terminal and run this command...
```
sudo gedit /etc/hostname
```Change the name. Save. Reboot.


I know that this name "whatever@system76-netbook" or whatever, shows up for switching users on the computer, but where else does this name show up?

When connecting to someone's wireless connection, does it show something in their logs that "whatever@system76netbook" connected to their network?

Does this name show up elsewhere where others can see it?

---

### Post by marshmallow1304 on 2009-10-10
> **macabrem said:**
> I know that this name "whatever@system76-netbook" or whatever, shows up for switching users on the computer, but where else does this name show up?

When connecting to someone's wireless connection, does it show something in their logs that "whatever@system76netbook" connected to their network?

Does this name show up elsewhere where others can see it?

My wireless router shows hostnames on its config page.

The name also shows up in the shell, like so:
```
user@system76-pc:~$
```

It also shows up when using bluetooth.

---

### Post by Rayve on 2009-10-10
I just ordered my Starling today... woohoo!  Can't wait to [s]play with it[/s] do homework on it.

---

### Post by vttay03 on 2009-10-10
Been a week and a half since I ordered mine and it still hasn't shipped...trying not to get anxious.  It did say it would ship 7-9 business days after the order was placed so I'm not upset or anything....just can't wait to get my hands on it :)

---

### Post by macabrem on 2009-10-11
> **vttay03 said:**
> Been a week and a half since I ordered mine and it still hasn't shipped...trying not to get anxious.  It did say it would ship 7-9 business days after the order was placed so I'm not upset or anything....just can't wait to get my hands on it :)

Yeah, no sense getting upset.  Apparently the demand for System 76 computers has been pretty great.  It took awhile for my Starling to ship, but it was well worth the wait.  I would rather them take the full time needed for assembly and setup than have any corners cut - not that they would cut corners anyway...

Everyday I use my Starling, and Ubuntu in general, I am more and more impressed.

---

### Post by vttay03 on 2009-10-11
yeah I figured the demand has been growing rapidly by the fact the Starling actually went out of stock a few months back...but that's a good sign right?  they must be making quality machines and you couldn't ask for better support.

---

### Post by theZoid on 2009-10-13
> **thomasaaron said:**
> Hey! I don't think we've ever had that question here before! 

Open a terminal and run this command...
```
sudo gedit /etc/hostname
```

Change the name. Save. Reboot.

Hi Tom....I would like know who the base manufacturer is of the Darta?  Who Sys76 gets them from, i.e. Clevo, Compal, Asus, Ocz, MSI, etc etc.

thanks as I'm thinking of ordering one.

EDIT:  Sorry..Sager (Clevo) 7220....(Clevo..that is a GOOD thing)

---

