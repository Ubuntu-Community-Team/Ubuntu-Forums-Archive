---
title: "Home Amazon ec2 server..."
date: 2010-09-09
forum: Server Platforms
---

### Post by waloshin on 2010-09-09
What is the Amazon ec2 server, what use would it have on a home server? Does it just give me access to my server like ftp would?

---

### Post by BkkBonanza on 2010-09-09
Amazon runs a data center where you can rent computer resources. That's called EC2.
You can start, run, stop computers remotely and in automated ways to scale up/down how much processing you need. You pay only for hours used, data in/out, disk space etc.

It's nothing to do with a home server, other than giving you the option to move system needs out to a real data center with great connectivity.

Some people use it as a remote proxy for secure net activities as well. 

While it's inexpensive for large companies to use due to many factors, for your average home user with a small site it's quite expensive. The best option for small startup sites is to use a VPS hosting account. 

The new "micro" instances look promising though - 2 cents/hour, or spot pricing at 0.7 cents/hour (within some restrictions), about $5/mo...

That's kind of a quick, rundown. For details visit [aws.amazon.com]("http://aws.amazon.com")

---

### Post by waloshin on 2010-09-09
So whats the point of installing amazon ec2 on your own server just to deploy your tasks then just upload it to amazons servers?

---

### Post by BkkBonanza on 2010-09-09
How can you install "amazon ec2" on your server? That makes no sense.

Do you mean install the package "ec2-api-tools"?

Then yes, those are tools used for managing machines/data/features out there on Amazon's EC2 servers. You can build an AMI (Amazon Machine Image) and upload it.

Or you can just use pre-built machines already on EC2 and manipulate them with the tools.

---

