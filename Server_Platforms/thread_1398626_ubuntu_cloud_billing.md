---
title: "ubuntu cloud billing"
date: 2010-02-04
forum: Server Platforms
---

### Post by mepatuhoo on 2010-02-04
ok i think at this point i have a good idea what cloud computing is and i think it can help me with some of my clients i want to switch my clients from a normal ubuntu server to a ubuntu cloud. as of right now i have to send out a bill to them and if they dont pay i have to shut down there service till they pay. what i would like to do is to have a cloud where i can sell them based on what they use not a set price like it is now. and have them be able to pay there bill on the cloud and if they miss the bill then the cloud can shut off there service till its payed. i dont know if this is possible and i have looked everywhere and all i can find is info on other businesses billing and now how to set up a cloud to do this. i wish there was some kind of tutorial for this. if anyone can direct me to some good notes/tutorials that would be very helpful. this could be a big changing point in my business if i can do this. it would save a lot of time and cash. thank you for any help.

---

### Post by BkkBonanza on 2010-02-04
Isn't the ubuntu cloud run on Amazon EC2? I had a brief look a while back so I'm not that familiar with ubuntu cloud but I do use Amazon EC2. 

Amazon has some payment services and cloud controls that allow setting up per use billing for your customers. They charge them through their credit card billing gateway and pay thru to you, and it can be tied to services rendered through some control interface. I haven't made use of it but I did read some of their docs and was thinking about trying out that aspect of their services.

I dug up this link so you could see if it's relevant. They call it DevPay and charge 3% of your "value-add" on the service, which is about the same as most cc billing methods.

[http://aws.amazon.com/devpay/](http://aws.amazon.com/devpay/)

---

### Post by mepatuhoo on 2010-02-04
that looks exactly like what i am looking for but i think that is just for amazon. is there something like that built into the ubuntu cloud? or can this be installed on a ubuntu cloud?

---

### Post by BkkBonanza on 2010-02-04
Not that I've seen yet. I haven't really searched for it though. It wouldn't be hard to make a simple management interface for this and I'm sure someone will do it eventually.

What about running your service offerings on EC2? Maybe you could make more money not having to worry about running the hardware? Just questions, as I don't know what you're really doing anyway. I think this was the idea, that people could make money bundling EC2 and reselling it, which is why they needed to create DevPay to make it easier to re-sell.

---

### Post by mepatuhoo on 2010-02-07
yeah but some how giving up that much power over my business to another business gets me a little uneasy. being that i already have the hardware it would be more of a burden to me to have the hardware and not use it. being that i have to account for the hardware depreciation based on income and if its not working for me then its wasted expenses on my balance sheet. having the software available in the Ubuntu software center to let me install a payment system on my own cloud would be better in my situation.

---

