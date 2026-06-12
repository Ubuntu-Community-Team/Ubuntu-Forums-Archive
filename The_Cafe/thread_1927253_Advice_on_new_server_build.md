---
title: "Advice on new server build"
date: 2012-02-17
forum: The Cafe
---

### Post by CharlesA on 2012-02-17
Hello,

I am thinking about replacing my current home server, which is running a Dual core with 6GB of RAM with a newer build. It is currently running Lucid x64 in an Antec 900 case with 4 HDDs.

I've think the case I will be going with is [this Lian-Li]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811112304"), since it looks pretty nice, and isn't as "flashy" with all the lighted fans and junk that the 900 has. Downside is that it does not have a top fan or side fan, but I don't really think that will be a problem as long as it can pull enough air to keep everything cool.

I'm debating between going quad or hex-core CPU because this will be my VM host as well as file server. Although, I will probably stick with a quad core, but I'd like some thoughts first. AMD or Intel makes no difference to me, but I want to throw 16GB of RAM at this thing, so I have plenty of resources to play with.

Not sure on mobo yet, but that would also depend on which CPU I get. Leaning toward a Gigabyte, because I have had good results with them.

Any advice would be appreciated.

Thanks!

---

### Post by robsoles on 2012-02-17
I am currently 'romanced' well enough by i# chips from Intel and I am throwing i7s at desktops people are getting me to 'spawn' for them and I am throwing i5s at servers.

If you are going to use raid# on this server I am currently hating s/w and contemplating h/w: [http://www.highpoint-tech.com/USA_new/cs-series_rr600.htm](http://www.highpoint-tech.com/USA_new/cs-series_rr600.htm) - I've been offered the 620 for $109.- in Australia.

I go text only on the absolute majority of servers pending who is specified as the maintainer/admin of the machine - it is uglier flying VMs under text only but well worth it if you bother, at least, in my humble opinion.

16GiB!!! Wow, my Desktop has 12 and my server has 4 and I thought I was a power pig :roll:
:lolflag:

---

### Post by CharlesA on 2012-02-17
Already got the RAID controller, and I saw a pretty nice AMD processor on newegg - 3Ghz quad core at 95Watts. Thinking that might be a good one to get instead of a 3.6Ghz at 125Watts. Not 100% sure tho. :o

My current machine is running headless, so text mode wouldn't be a problem.

So far the parts list is as follows:

[LIAN LI PC-9F Black Aluminum ATX Mid Tower]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811112304")
[AMD Phenom II X4 960T Zosma 3.0GHz Socket AM3 95W Quad-Core HD96ZTWFGRBOX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103995")
[GIGABYTE GA-970A-UD3 AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128519")
[CORSAIR Vengeance 16GB (4 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820233143")
[OCZ ModXStream Pro 700W Modular High Performance Power Supply]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817341018")

I've got the hard drives already, and the RAID card so that won't be a problem. Also, got a video card I can pull out of my current server instead of buying a new one.

EDIT: The RAID card I am using now is the [RocketRAID 2640X1]("http://www.highpoint-tech.com/USA_new/cs-series_rr2600.htm"). Wonder if it'll let me compile the drivers on a 3.x kernel... hmm...

---

### Post by Dangertux on 2012-02-17
Two things to consider. If youre going to be provisioning a decent amount of virtual processors you will want more procs and or cores. If you are only going to be running a few vms or not running them all at once then it is not as important.

In terms of performance for a server you will want to maximize IO and your procs wont be your downfall  

Hope this helps

---

### Post by CharlesA on 2012-02-17
Thanks for that. I usually have 2 VMs running all the time, and if I start another one (or two), it starts getting sluggish. I was thinking I might have 3 to 6 VMs running at the same time, mostly for school stuff or testing. Maybe a hex-core would be a better way to go.

Maybe running the VM's drives off the RAID array instead of a single disk would be a good idea too.

EDIT: I found [my old thread]("http://ubuntuforums.org/showthread.php?t=1520837") from a couple of years ago too. O_o

---

### Post by haqking on 2012-02-17
i recently built a new desktop, i7 2700k and 16gb ram.

i am running 4 VM's at the momment, all with 2 gb ram each.

a little earlier i was playing black ops on the one monitor whilst the VM's were running on the other monitor

( i was running 4 VM's just to test things out by the way i would usually only run 1 or 2 concurrently)

didnt notice anything even trying to work hard.

running kde 4.8 on slackware current

CPU never went above 35 degrees and mobo not above 30 though my gtx 580 went upto 45

I love this new kit.

oh and im semi inebriated from terrible irish single malt ;-)

i love the weekends

---

### Post by CharlesA on 2012-02-17
Nice rig!

I might just stick with the quad, but I'll know more after I poke around on Newegg some more. :p

---

### Post by haqking on 2012-02-17
> **CharlesA said:**
> Nice rig!

oh yeah...

Intel i7 2700K
Asus P8z68-v/gen 3 mobo
16gb ram
corsair h80 closed loop waterooler
asus nvidia gtx 580 graphics
dual dell 23" 1920x1080p IPS panels
2 x 128GB crucial M4 SSD 
3 x 2TB HDD (was origainlly the one but they were cheap so bought 2 more) giving me 6 TB data (great for VM's)
coolermaster cm690 II advanced windowed case


and some other stuff i cant remember right now...LOL

it runs like its on rocket fuel

KDE 4.8 on slack current does things before i tell it to its so fast...LOL

I have windows 7 on first SSD also for a few games (like black ops and such though im not really a game player per se)

---

### Post by CharlesA on 2012-02-17
Nice cooler there. Does the watercooling make a big difference over air? I've been eyeballing those Corsair coolers, but I've stuck to air due to cost.

EDIT: I've done some more poking around and it looks like the 6 core bulldozer is only 25 bucks more than the quad core I was looking at. The 8 core version is 50 bucks more and the mobo supports both of them. Hmm...

---

### Post by haqking on 2012-02-17
> **CharlesA said:**
> Nice cooler there. Does the watercooling make a big difference over air? I've been eyeballing those Corsair coolers, but I've stuck to air due to cost.

as far as temps go i dont think there is much difference.

It is more about noise levels or at least was for me.

I have a front fan. top exhaust fan, side panel intake fan, the twin fans on the grfx so wanted some quiet in there also, that being said the rad has 2 fans also...LOL

either way its not that noisy, the corsair has a push button with 3 profiles, i keep it on quiet profile and even running everything i do and playing games the temps stay at 30 or below and on quiet settings hottest it has been is 35

i may upgrade to SLI at some point and if i do i may upgrade to the h100 from corsair for the twin rad, but to be honest i doubt i need it.

but this kit rocks right now, i havent built a machine for a few years so was good and fun to get back into it again and learn all the new hardware and stuff.

was a fun project and now i sit back and chill and reap the dual display rewards ;-)

---

### Post by robsoles on 2012-02-17
> **haqking said:**
> i recently built a new desktop, i7 2700k and 16gb ram.

i am running 4 VM's at the momment, all with 2 gb ram each.

a little earlier i was playing black ops on the one monitor whilst the VM's were running on the other monitor

( i was running 4 VM's just to test things out by the way i would usually only run 1 or 2 concurrently)

didnt notice anything even trying to work hard.

running kde 4.8 on slackware current

CPU never went above 35 degrees and mobo not above 30 though my gtx 580 went upto 45

I love this new kit.

oh and im semi inebriated from terrible irish single malt ;-)

i love the weekendsI love the weekends too but are you sure your Irish single malt is really that terrible? I'm sure I'd not complain to share a sifter or two of it with you :)


Charles, please get a live demonstration of booting your preferred LiveCD on an i7 mounted on a well matched Asus motherboard before dropping your dollars on more AMD without this check - I was an AMD fanboy till the i#s came out and I probably need to do this very same thing I am advising you only with the demo of the AMD instead.

I am mates with a couple of computer shop owners so I can gaurantee myself to get to see the latest AMD offering(s) demoing my current preferred LiveCD and I hope you are in a similar or better circumstances re the Intel demo :)

---

### Post by haqking on 2012-02-17
> **robsoles said:**
> I love the weekends too but are you sure your Irish single malt is really that terrible? I'm sure I'd not complain to share a sifter or two of it with you :)


Charles, please get a live demonstration of booting your preferred LiveCD on an i7 mounted on a well matched Asus motherboard before dropping your dollars on more AMD without this check - I was an AMD fanboy till the i#s came out and I probably need to do this very same thing I am advising you only with the demo of the AMD instead.

I am mates with a couple of computer shop owners so I can gaurantee myself to get to see the latest AMD offering(s) demoing my current preferred LiveCD and I hope you are in a similar or better circumstances re the Intel demo :)

well its not that terrible, its just that i am usually a single scottish malt guy, its ok i guess but the barley was dried over peat so a very earthy taste, but whose complaining its friday/saturday and i have whisky ! ;-)

and a big +1 to the i7 and a asus mobo, great combo.

havent overclocked it yet, but if want to i can do it from my android phone with one button push, how cool is that...LOL

---

### Post by CharlesA on 2012-02-17
Thanks for the info.

My main desktop is a Phenom II x4, old one was Intel. I switched mostly due to AMD being cheaper then Intel.

I don't think that Fry's has any live demos set up unless you count the OEM boxes they sell.

EDIT: Found a decent Intel CPU that I have heard a bunch of good stuff about:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115072](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115072)

And mobo:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128495](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128495)

I could probably find a different mobo since I don't need 3 x 16x PCIe slots.

Probably go with this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128512](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128512)

---

### Post by CharlesA on 2012-02-17
Well I did some poking around and ended up going with the i7 2600K, the gigabyte mobo above and the rest of the stuff in the OP.

Wonder how well it'll run on Lucid. :p

---

