---
title: "Server hard ware"
date: 2009-08-26
forum: Server Platforms
---

### Post by sir_jct on 2009-08-26
I want to put together a server at home but don't know how to go about it.

I want it to be cheap and easy on the power consumption.

Could you please give me some help.

sir_jct

---

### Post by volkswagner on 2009-08-26
I would start with an Intel Atom 330 based system.  I am not sure of you hard disk needs so you may want to build your own case.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119013](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119013)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167032)

Or build your own

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010200446%201370044872&name=Intel%20Atom](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010200446%201370044872&name=Intel%20Atom)

---

### Post by fela on 2009-08-26
This is what's in my £120 server:

Athlon 64 LE-1600
2GB DDR2 memory
Gigabyte AM2 motherboard
500GB SATAII HDD
super cheap mATX case with a 450W PSU

I should probably get a better case and PSU, but it's not a TOP priority. It runs great right now, really low temps with cool'n'quiet. BTW, you WANT to keep track of temps on a server.

---

### Post by sir_jct on 2009-08-26
Thanks for your advice.
Just one more thing _:- what server operating system should I go for?

I am torn between ubuntu and mac os x?

---

### Post by fela on 2009-08-26
> **sir_jct said:**
> Thanks for your advice.
Just one more thing _:- what server operating system should I go for?

I am torn between ubuntu and mac os x?

Ubuntu of COURSE!!! What were you thinking, mac os x....essentially linux with a nice GUI - ie might aswell use linux on a server.

Plus you'd need a mac to reliably run osx.

EDIT: you do know that Linux is the dominant server OS worldwide, and that google run Linux on their servers? OSX is NOT made for servers, no matter how many times steve jobs says it's the world's most advanced OS. Answer: it's not.

---

### Post by cariboo on 2009-08-27
@fela

Do some research first, check [this]("http://www.apple.com/server/macosx/") out.

---

### Post by fela on 2009-08-27
> **cariboo907 said:**
> @fela

Do some research first, check [this]("http://www.apple.com/server/macosx/") out.

Oh, I used to be a complete apple-head so I know that site. If someone tells me that there's any good thing a OSX server can do that a Linux server can't, I'll eat my words.

Why should a server have a composited desktop? Sure maybe so you can offload the GUI onto the GPU. That begs the question: why should you need a GUI on every server?

EDIT: or does OSX server not have a GUI? <- somehow doubt it.

---

### Post by wojox on 2009-08-27
No it's all GUIed up. Plus it's $499.00

---

### Post by fela on 2009-08-27
> **wojox said:**
> No it's all GUIed up. Plus it's $499.00

^ Wise words. Now you know why OSX is NOT a server OS. No matter how much steve jobs doesn't want you to know that.

---

### Post by sir_jct on 2009-08-27
what is a cheap server unit to acquire and easy on the electric?

---

### Post by fela on 2009-08-27
> **sir_jct said:**
> what is a cheap server unit to acquire and easy on the electric?

Build it yourself of course.

That's the only way to customize components properly.

You could get an Athlon 64 for low energy usage + low cost, with say 512MB RAM to start with. It would be DDR2 as that's very very cheap right now. You could use integrated graphics so make sure that's built into the motherboard. A word of warning though: don't go for the cheapest PSU as you'll likely end up with a broken PSU, and if you're unlucky a broken computer (fried components). Get a good PSU from a reputable manufacturer such as antec or corsair.

---

### Post by nerr on 2009-08-27
I own this little box and it's awesome:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16859321013&Tpk=Acer%20easystore]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859321013&Tpk=Acer%20easystore")

Running Ubuntu Server 9.04 no sweat.  It doesn't have video out, so you'll have to install the OS in another system, install SSH, then move it over to that box and continue working over SSH.  Once you get it going though, it's a great little machine.  With an Atom processor, it's only supposed to draw maybe 30W or so at full load, just add an extra 7-10W for each hard drive.  Not bad at all.

---

### Post by fela on 2009-08-27
> **nerr said:**
> I own this little box and it's awesome:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16859321013&Tpk=Acer%20easystore]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859321013&Tpk=Acer%20easystore")

Running Ubuntu Server 9.04 no sweat.  It doesn't have video out, so you'll have to install the OS in another system, install SSH, then move it over to that box and continue working over SSH.  Once you get it going though, it's a great little machine.  With an Atom processor, it's only supposed to draw maybe 30W or so at full load, just add an extra 7-10W for each hard drive.  Not bad at all.

No offence man but that looks BAD :P

It doesn't look like it can hold more than 1 harddrive. Where's my 8xHDD RAID? Also how do I add more fans? In fact that thing looks like it would have terrible airflow. How do I put multiple DVD drives in it so I can use it as a DVD copier? How do I add USB and eSATA and FireWire ports for external devices? What if I want a screen on it so I can actually administrate it in case I can't SSH it for some reason?

To the OP or whoever asked: build it yourself. Seriously. Micro ATX case and a few super cheap computer parts does the job nicely. That's how my server was put together. My server is built out of plastic, metal, gaffa tape and maybe a bit of blood ;)

---

### Post by cariboo on 2009-08-28
Look at post #2, if you can't afford to buy new, almost anything would work as a file server. I have a file/http/media server that I aquired from a former employer, 1Ghz Athlon cpu 512MB ram and 4 hard rives ranging from 120Gb to 400Gb.

I have an email server running on an Apple G3 with a 350Mhz cpu and 256Mb ram.

---

### Post by fela on 2009-08-28
> **cariboo907 said:**
> I have an email server running on an Apple G3 with a 350Mhz cpu and 256Mb ram.

And I do hope you're running Linux on it, not MacOS!

---

### Post by MrWES on 2009-08-28
> **cariboo907 said:**
> Look at post #2, if you can't afford to buy new, almost anything would work as a file server. I have a file/http/media server that I aquired from a former employer, 1Ghz Athlon cpu 512MB ram and 4 hard rives ranging from 120Gb to 400Gb.

I have an email server running on an Apple G3 with a 350Mhz cpu and 256Mb ram.

Same here, my employer was tossing an old HP Pavillion, so I snatched it up, threw 2gb RAM in it, and added a 1TB eSATA drive. Runs headless in my closet. Mediatomb runs great to my PS3.

Bill

---

