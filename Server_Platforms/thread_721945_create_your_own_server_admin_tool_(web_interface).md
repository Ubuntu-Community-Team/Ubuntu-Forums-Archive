---
title: "create your own server admin tool (web interface)"
date: 2008-03-11
forum: Server Platforms
---

### Post by ianeazca8 on 2008-03-11
I am experimenting with Ubuntu Server 7.10 and thinking about doing a little web hosting. I have looked at admin tools like VHCS, ISPConfig, Webmin, GPLHost, and SysCP. I was wondering if anyone knows of anywhere I can look to start building something like that on my own. 

Any ideas? Anyone have input on the whole idea? If possible, I want to write it in PHP...

Thanks!

---

### Post by insineratehymn on 2008-03-11
Write it in perl!

Thats my advice. :)

---

### Post by ianeazca8 on 2008-03-11
any advice on where to even start?

---

### Post by insineratehymn on 2008-03-12
Sure... Ummm....

You're gonna need to be able to see your whole file structure, right?
Write a script that browses your whole file structure, breaks it down, and if you wanna get fancy CSS the hell out of it so its pretty and has a top-down architecture.

Wanna get really fancy?

Make an upload/download feature.

---

### Post by neverett on 2008-03-15
Any certain reason why Perl would be better than PHP in this task?

---

### Post by chris.zeman on 2008-03-15
I don't know if Perl would be better than PHP, but...

Writing your own control panel is most certainly possible. I guess the best place to start might be to get an idea of what you want the control panel to look like. make a rough list all the software your interface will need to manipulate, and figure out how you'd like it sorted in your program.

The part that might take you the longest is learning everything you'll need to know about all the programs you'll be manipulating (Apache, MySQL, etc.). 

Good luck!
Chris

---

### Post by HermanAB on 2008-03-15
Why re-invent Webmin?  Just install it from Synaptic.

Cheers,

Herman

---

### Post by chris.zeman on 2008-03-16
Why not just settle for what's out there ALL the time? We wouldn't have tools like Webmin if that's what people did. I think it's commendable that he wants to make the committment to write his own panel. 

I like Webmin, but it's lacking. I have never been a fan of ISPConfig or many of the others out there. The hosting company I'm with wrote their own panel, and it's pretty nice. Innovation should be encouraged, not discouraged.

Chris

---

### Post by HermanAB on 2008-03-16
Most people that re-invent the wheel, end up with a square one and if they are very good they optimize away one corner to eliminate one bump and end up with a triangular wheel...

I'd recommend taking Webmin and if required, improve on it.  The base  design of Webmin is pretty good and very extensive, so take what works and rewrite what isn't.

---

