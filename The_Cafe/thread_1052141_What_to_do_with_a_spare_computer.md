---
title: "What to do with a spare computer"
date: 2009-01-27
forum: The Cafe
---

### Post by PurposeOfReason on 2009-01-27
So as it stands, I have three computers. One is hooked up to a tv running xbmc and housing all my files which I mount over the network to my work computer in my room. Then I have this old computer that used to run torrentflux (900Mhz PIII, 256mb RAM, 20GB HDD) and am trying to find a use for it. I'm up for ideas, though I would like it if possible to use it as some sort of firewall before or after the router. I'm not too sure if that is even possible because everything I read also makes that computer a makeshift router, which I don't want or need. I guess I want it to act like a spiderweb, stopping all traffic I don't want before it even gets into the network.

However, I'm open for suggestions. Oh, and in before "make it a linux server for x repo". I don't have the network for that.

---

### Post by Frak on 2009-01-27
F@H, Home Server, Print Server (maybe you have more than 1 computer), File server, Intranet Server...

Finally, torrent server.

---

### Post by PurposeOfReason on 2009-01-27
I shoved the printing into the media center, as well as torrenting (I mean, a simple script and it finds my TV shows, gets them, and puts them where I want them trumps tivo). It might just fold, just meets the requirements.

---

### Post by timcredible on 2009-01-27
donate it to a charity that you like, or a nearby school that could use an extra computer, you'll be doing something good, and get a little tax break.

---

### Post by mamamia88 on 2009-01-27
+ 1 for the charity idea i never saw the point in having more than 2 main computers 1 laptop and 1 desktop

---

### Post by lukjad on 2009-01-27
Besides the charity idea, which is a good one, I would use it as a test box. Do all the things you never would dream of doing on your main one. Try out commands, install rare forms of Linux, try LFS... in short, break it, and fix it.

---

### Post by njwoods on 2009-01-27
hello all,
I would say to donate it to a community organization, they never have money for new or decent equipment. Or even a school as someone suggested already. 

Or I guess you can spend hours of research online and see what other uses it may be good for.

---

### Post by Dragonbite on 2009-01-27
> **PurposeOfReason said:**
> I'm up for ideas, though I would like it if possible to use it as some sort of firewall before or after the router. 

I have an old P3 700MHz system running IPCop as a router/firewall and (optional) content filter system.

It is really quick and easy to set up (need 2+ NICs).

Since my kids are 4,6 & 8 I also added DansGuardian for content filter and it works great!  Since it is right off of the modem then even if somebody connects via wireless the internet traffic is filtered.

The filtering, mind you, can be modified (black list, white list, etc.) as well as weighted for more or less filtering.

If I read right, it also handles dial-up as well as broadband connections.

---

### Post by urukrama on 2009-01-27
K.Mandla has a few ideas: [http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/](http://kmandla.wordpress.com/2007/09/14/things-to-do-with-an-old-computer/)

---

### Post by PurposeOfReason on 2009-01-27
> **Dragonbite said:**
> I have an old P3 700MHz system running IPCop as a router/firewall and (optional) content filter system.

It is really quick and easy to set up (need 2+ NICs).

Since my kids are 4,6 & 8 I also added DansGuardian for content filter and it works great!  Since it is right off of the modem then even if somebody connects via wireless the internet traffic is filtered.

The filtering, mind you, can be modified (black list, white list, etc.) as well as weighted for more or less filtering.

If I read right, it also handles dial-up as well as broadband connections.
Do you think it'd be possible to make a diagram of that? If I read right you have it so you have the modem, modem goes to one NIC, the other NIC then goes to the router then the router does its thing.

---

### Post by mips on 2009-01-27
> **PurposeOfReason said:**
> Do you think it'd be possible to make a diagram of that? If I read right you have it so you have the modem, modem goes to one NIC, the other NIC then goes to the router then the router does its thing.

I think you got that 100% correct.

---

### Post by Mason Whitaker on 2009-01-27
Home server would be good

---

### Post by ntowakbh on 2009-01-27
On a related note, does anyone of any suggestions what I can do with my old computer?  It has 64MB of RAM, a 2GB hard drive, working floppy drive, and a cd drive that can read, but won't write. (I don't even know the processor's speed, but you can probably infer from the other stuff that it isn't too high.

---

### Post by zmjjmz on 2009-01-27
> **ntowakbh said:**
> On a related note, does anyone of any suggestions what I can do with my old computer?  It has 64MB of RAM, a 2GB hard drive, working floppy drive, and a cd drive that can read, but won't write. (I don't even know the processor's speed, but you can probably infer from the other stuff that it isn't too high.

A router seems like a good use for that :P

---

### Post by ntowakbh on 2009-01-27
> **zmjjmz said:**
> A router seems like a good use for that :P
Seems a bit redundant though, I have a router right next to it...

---

### Post by Frak on 2009-01-27
> **PurposeOfReason said:**
> Do you think it'd be possible to make a diagram of that? If I read right you have it so you have the modem, modem goes to one NIC, the other NIC then goes to the router then the router does its thing.
If you have wireless, you could configure it to use (as long as you have an adaptor) that as a server and route all information through it to the modem.

That's how my filtering server works anyways.

---

### Post by wolfen69 on 2009-01-27
torrent slave? you could help seed .iso's for some of the smaller distros that need help.

---

### Post by Dragonbite on 2009-01-27
> **PurposeOfReason said:**
> Do you think it'd be possible to make a diagram of that? If I read right you have it so you have the modem, modem goes to one NIC, the other NIC then goes to the router then the router does its thing.
```

       {internet}
           |
           |
        [modem]
           |
           |
[IPCop (eth0)-- (eth1) ]
                  |
                  |
         [switch/wireless router]
              ____|____
             |         |
       [computer]    [computer]

```

How's that?

In my case the IPCop provides an IP address to the router (10.0.7.x), and the router provides an IP address to the computers (192.168.1.x)

You access most of it through a web interface and one of the options is to turn on SSH.  I leave mine off and only turn it on when I need to do maintenance (like installing the DansGuardian aspect, etc.)

---

### Post by PurposeOfReason on 2009-01-27
Looks just like what I wanted. From what I read about ipcop, the interface from the modem (eht0) would be "green" and out would be "red", right? Then I would just mess around will all the settings (I assume there are many in the web interface) to block and filter all I want?

---

### Post by Dragonbite on 2009-01-27
> **PurposeOfReason said:**
> Looks just like what I wanted. From what I read about ipcop, the interface from the modem (eht0) would be "green" and out would be "red", right? Then I would just mess around will all the settings (I assume there are many in the web interface) to block and filter all I want?

The interface connected to the Internet is RED I believe (so the connection to the modem would be red)

The interface to the internal network (wired) would be GREEN which means very open.

If you have 3 NICs then you can set up one connected to the Wireless router to the BLUE (or is it ORANGE?) zone, or the DMZ since you may want to be careful what somebody may be able to see if they get on your network.

---

### Post by MikeTheC on 2009-01-28
You could always have it calculate twenty-two divided by seven...

*wink wink, nudge nudge*

---

### Post by lukjad on 2009-01-28
Or the value of pi...

---

### Post by S0VERE1GN on 2009-01-28
Command Line Firewall Compy ^_^

---

