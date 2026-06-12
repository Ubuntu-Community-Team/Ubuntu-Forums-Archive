---
title: "Thinking about building a cloud"
date: 2016-10-14
forum: The Cafe
---

### Post by ELMIT on 2016-10-14
I am now a long time with Linux and since 5.04 with Ubuntu. I had many hardware and software upgrades. I want to go to the next challenge to a cloud. I am not at a specific step, therefore I talk here in the cafe.

Every year new hardware is available, you want to upgrade, you cannot upgrade all, ... some even don't need to. Some always need the most power!
Latest push thinking at that was a computer class. The peripheral computers should be simple (not the need to upgrade), but the power behind should be great. I am not sure what exactly I am looking for here.

I think we could start with a few servers (I think I read somewhere I can start with 3) to make it happen, with the help of the cloud forum. I want to build it up by myself. Not for the sake of saving money, but as a learning experience.
A few virtual domains on an apache2 server, mysql server, multiple versions of PHP, ... would be my first start.

As soon it is working I would start to add more servers. I believe that this way is cheaper to get a server with more that 4 CPUs and a lots of RAM, then with high class servers.

Any thoughts, hints, ... and "encouragements, please.

---

### Post by colmax on 2016-10-15
Hi Elmit
Maybe a Xeon chip would serve you well
Bulk ram is definately a must :)
Depends if you're gonna run a personal cloud or open to the masses
I applaude your endeavour
Even tho linux doesn't tend to need anti-malware ur server/s may need it so malware is not passed onto the users
The learning curve & upkeep should keep u busy :)
Good on you for pushing the limits!

---

### Post by ELMIT on 2016-10-15
Money is of course an issue, .... 
I need to show something before they open their wallet.:D

I googled for minimal required hardware, and found different answers. It might be that depends on the Ubuntu version you are using.

I got 2~4 Dell HP Compaq de7900 Small Form Factor around:
Intel(R) Core2 Duo CPI @ 3.00GHZ
4GB  DDR2 RAM

and I got a better motherboard, what I can use for it.

The hardware requirement speaks from 2 hard disks. I scratch my head what this means, because it does not say EACH one needs 2 hard disk. Which one needs a say 300 GB hard disk?

I understand that one serve is used for the front end and the others are nodes. Which one(s) do you suggest to use Xeon?

Finally I don't understand the license fee. It says 10 servers are free, are that the "nodes"? or all used computers for that Cloud? It further says the license fee is 750 US$ per year - Is that from 11. onwards or if I got the 11th than minimum 11x 750 us$?

Could I use for my convincing demo a flashdrive (1GB USB3) - on which machines? I want better a cheap demo set :D

Just to confirm, if I have set it up, I can add/remove a node(s) on the fly, correct?

---

### Post by colmax on 2016-10-15
Hi Elmit
Think multiple disk ask is to setup a raid array for redundancy
If a drive fails the other/s can still deliver
There are different arrays
Raid0 stripes i think which overlaps data across multiple drives
Raid1 maybe mirroring so 2 disks have the same data incase 1 fails
There are other flavours of raid
I must let you know im a novice at this stuff ;)
Xeon is an intel server chip which of course gonna need an appropriate motherboard which would be expensive
4GB of ddr2 is not gonna cut it
Ram seems to be the defining thing with servers as well as a capable cpu (normally 128GB and above)
Figure an i5 with 16GB ram could be a place to start
Depends how many requests are made at any 1 time
Sorry if im just telling you what you already know

---

### Post by mastablasta on 2016-10-17
what exactly are you trying to do? what kind of "cloud"? what will it do? store files? process complex computer simulation? run AI? be a media galery?

> **ELMIT said:**
> 
A few virtual domains on an apache2 server, mysql server, multiple versions of PHP, ... would be my first start.
.

you can run that on Raspbery Pi. 


you can also use virtualisation (e.g. virtualbox) for demo.

---

### Post by SeijiSensei on 2016-10-17
I lease complete virtual servers from [Linode]("http://www.linode.com/") at $10/month.  You should take a look at them before going too far down this road.  I suggest creating a VM and examining the extensive array of tools available.  If you tear it down within the one-month period, you'll get a refund to your credit card for the unused time.

---

