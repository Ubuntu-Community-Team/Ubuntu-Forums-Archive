---
title: "I've broke my server when moving hard drives around."
date: 2008-05-29
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-29
Hello everyone I thought I'd post a new thread because the last ones getting pretty long.

Basically I was discussing my partitions with Nateman and I had my setup decided..

This required a moving around of the hard drives so I did.

I was just swapping them around so the most critical drives were on individual cables. Something went seriously wrong, I booted the install CD and my drives were showing up as the wrong capacities ( and some not at all )

After a lot of troubleshooting I narrowed it down to all drives are fine except one ( 40GB ) which has seemed to have died.

I determined this by placing all drives in another tower. I have just tried swapping the IDE cables in the other tower for the ones out of the server but it now wont boot the CD. I'm now gonna try the other way ( put server IDE cables into the other tower )
to determine if it's the cables ( one of the plugs is cracked, but I don't think it would affect it, but u gotta b sure )

The computer seems to be working fine everywhere else, it's just when I install Ubuntu I get drive errors, it logs me in to a root recovery console and I can't access use any commands.

Has anyone got any ideas? I'm really gutted about this cos I had everything planned out perfect for it and had tested a lot of different setups. I should've left the drives where they were!

Thanks

---

### Post by tigerplug on 2008-05-29
Google! 

HDD Regenerator! ;)

---

### Post by garethsimpsonuk on 2008-05-29
I don't think the hard disks are damaged (apart from 1 40GB) because they work fine in another tower. I've tried the cables from another box and it's still not workin so it looks like Ive got a mobo problem?

---

### Post by mamyte18 on 2008-05-29
Premium Membership

Upgrade your account and earn more with Bux.to. The Premium Membership comes with the following features: 
» Surf Ads guaranteed loaded with minimum 20 ads every Day!
» Earn $0.0125 each click and $0.0125 each click from your referrals.
» Priority Payments.
Exclusively for premium members: Get your Prepaid Bux.to MasterCard®
Earnings Example
» You click 20 ads per day = $0.25
» 25 premium referrals click 20 ads per day = $6.25
» Your monthly earnings = $195.00
» Your total annual earnings = $2,340.00
Processing time: 2 working days.
I'm so proud of everybody, who clicks for bux.to and everybody who works at bux.to, they made a fantastic system. You are clicking for a wanderful system. I joined bux.to in the middle of January, but I have to admit that I wasn't brave enough to invest 500$-s with no previous knowledge about the system. So I only bought 115 refs and a premium to test bux.to and I saw that the money is comming back really fast, so in March I bought another 335 refs. So totally I invested 500$-s.

Now I reached 1000$, I duplicated my investments in 1 month. Thank you bux.to! Thanks for the clickers and the advertisers, who made bux.to a smooth running machine! Thanks for everybody, who writes success stories to make people trust the system! And finally, thanks for my referrals, especially for the guy, who bought premium membership 1 week after joining!

We have to continue our journey through the ads. Good luck for everybody!
  
Steps how to register to bux!

1 step:  [http://bux.to/?r=mamyte18](http://bux.to/?r=mamyte18)   go to this site. And register here.
2 step:  [http://www.alertpay.com](http://www.alertpay.com)
Then "SIGN UP", choose your country, then "Personal Starter" and "Get Started"; and write your name and other information. Where need.
Then you will receive a message to your email address.

When the alertpay are created go to link [http://bux.to/?r=mamyte18](http://bux.to/?r=mamyte18), then"I Accept the Terms of Service” and  click butoon register.   And that’s all. You are the member.

To look videos click "Surf Ads". And you will earn your money.
Good luck. Odeta.
If there are ome problems write to me I could help you I promise. [email]odetux18@yahoo.com[/email]

---

### Post by garethsimpsonuk on 2008-05-29
<snip>  comment referred to deleted spam.

---

### Post by garethsimpsonuk on 2008-05-29
thanx mod

---

### Post by garethsimpsonuk on 2008-05-29
right if i cant sort this im gonna have 2 use the next best tower which i dont really wanna do. n e ideas n e 1? also can i use 2 80 wire cables or do i have to use 1 40 and 80 ( all my comps come with this )

---

### Post by garethsimpsonuk on 2008-05-29
Good News! It turns out that it might be ok. Or at worst another drive is bust. I need a tool HDD Generatiion for ubuntu that i can apt-get any ideas anyone? I've googled but can't find one amongst all the junk that comes up

---

### Post by garethsimpsonuk on 2008-05-29
for some reason my 80GB drive produces errors on one ide slot but not on the other?? I guess I shouldn't complain! I wanna try and repair all secotrs befor eI do anyhting is there any good tools in the repos?

---

### Post by artesvida on 2008-05-29
Not sure what your errors are, but the drives could be bad.  Or at least hinky enough to cause problems with ext3 filesystem.  I've had systems that ran Windows fine but complained severely when wiped and formatted ext3.  I'm no filesystem expert, but it seems like ext3 is a bit less tolerant of borderline drives.

---

### Post by garethsimpsonuk on 2008-05-29
thankx for your reply! can anyone explain to format from cli plz? 

i have used fdisk -l to identify then mkfs.ext3 /dev/sdb I recieved a message saying 'sdb is a whoile drive not a partition, continue anyway?' i sed yes and now when i do fdisk sdb comes back as 'not ext3 or something'

i want to create one big partiton on the drive and format and check for errors and repair / ignore any bad sectors.
can someone plz explain to me the right commands?

thanx a lot 

(ive managed to get evrything working i just have 3 drives with bad blocks!, maybe there was a power surge or something because my media centre has had its psu blown!, not a good day!)

---

### Post by Barrucadu on 2008-05-29
cfdisk is a CLI partitioner, but I'm not sure if it is in the repos.

---

### Post by garethsimpsonuk on 2008-05-29
so u cant format drives from the cli? thats surprising. is gparted gui only?

edit: or is it qparted? i wanna fix bad blocks on disks, does anyone know how to do this?

---

