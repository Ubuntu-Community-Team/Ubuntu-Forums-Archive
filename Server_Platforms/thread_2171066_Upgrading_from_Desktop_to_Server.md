---
title: "Upgrading from Desktop to Server"
date: 2013-08-29
forum: Server Platforms
---

### Post by Peter_Sotos on 2013-08-29
Hello there!

I'm new to the forums and I had a question. First let me make a statement: The company that I purchased my Linux box from would do 0 and i mean 0 config on it. i asked for them to install Ubuntu Server. Nope. This was a desktop class machine and by golly it must have Desktop. So now I am stuck upgrading the darn thing myself. What apt-get stuff do I need to do? :)

Any help is greatly appreciated.

Peter

---

### Post by carl4926 on 2013-08-29
We need to know what version of Ubuntu you have
Ubuntu Server is actually distributed as separate install media
Are you actually wanting to run a server?

---

### Post by Peter_Sotos on 2013-08-29
Hello!

I tried posting this earlier but something went wrong and it got posted as a private message? wth?

Anyway, I bought a Desktop but I *really* wanted a server. I told the guy this, but he basically said no, they dont do any custom configurations and this box you ordered only comes with Ubuntu Desktop. *lame*

So in any case, I am now stuck with the situation where I need to convert my desktop to a server. What apt-get packages do I need to install? Is there a guide or a faq availabel about this? I did find some old information but it was for a MUCH older version of Ubuntu and I am afraid of following out-dated instructions.

FYI, I own a small company and will have no more than 10-20 employees on my employee site at any one time (I might have a few hundred on my Wordpress site tho). In any case, I could not afford more than this machine so it is what it is. ;)

Thanks in advance for your help!! :)

Peter

---

### Post by Peter_Sotos on 2013-08-29
Hello Carl!

I have a brand spanking new machine with Ubuntu 13.04 Desktop on it. Yes I really really want a server. I will be running Apache, Git, JBoss, Spring Libraries, Hibernate Libraries, PostgreSQL, a firewall (doh!), and sendmail.

:)

Peter

---

### Post by carl4926 on 2013-08-29
You already posted about this and I replied

But I suggest you download 12.04 server
[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

Install it yourself, at least you know exactly what's installed

---

### Post by lisati on 2013-08-29
*Threads merged and moved to **Server Platforms**.*

---

### Post by Peter_Sotos on 2013-08-29
Ah I was hoping for an easier way. :P

I read someone that the only real different is a few packages. Also, why the downgrade in versions? Anyway forgive my newbie questions. I havent used Unix/Linux since the SCO days. :P

---

### Post by carl4926 on 2013-08-29
server = something needed long term

12.04 is LTS

---

### Post by Peter_Sotos on 2013-08-29
Hmm ok fair enough. So much for all the configuring I have already done. *cry*

Downloading 12.04 right now.

Thanks for the help mate! :)

---

### Post by carl4926 on 2013-08-29
> **Peter_Sotos said:**
> 

Downloading 12.04 right now.

Thanks for the help mate! :)
The server edition...right?

---

### Post by Peter_Sotos on 2013-08-29
Yes Sir! ;)

---

### Post by Peter_Sotos on 2013-08-29
Carl,

Just a status report: I got server up and running on the machine. Woot! I had to install a CD ROM drive on the computer because it didnt have one. Anyway, thanks for your help! :)

Peter

---

### Post by CharlesA on 2013-08-29
Just for the record, you could have installed whatever services you wanted on Ubuntu Desktop and it would have been fine. The only difference between the Desktop and Server editions is the desktop version has a GUI and some added packages. :)

---

### Post by carl4926 on 2013-08-30
> **CharlesA said:**
> Just for the record, you could have installed whatever services you wanted on Ubuntu Desktop and it would have been fine. The only difference between the Desktop and Server editions is the desktop version has a GUI and some added packages. :)
My recommend came from the fact that the OP reported that the company that installed Ubuntu were less than helpful. My gut feeling anyway is to do the install yourself, so you know exactly what's what. But given the circumstances, I'd definitely do a clean install.
You can't be too careful.

---

### Post by CharlesA on 2013-08-30
> **carl4926 said:**
> My recommend came from the fact that the OP reported that the company that installed Ubuntu were less than helpful. My gut feeling anyway is to do the install yourself, so you know exactly what's what. But given the circumstances, I'd definitely do a clean install.
You can't be too careful.

Agreed. I wonder what company it was cuz that sure isn't very good customer service.

You can read all you want, but you won't actually learn anything until you get your hands dirty. ;)

---

### Post by carl4926 on 2013-08-30
> **CharlesA said:**
> 
You can read all you want, but you won't actually learn anything until you get your hands dirty. ;)

Darn... that's the best bit, isn't it just!

---

### Post by Peter_Sotos on 2013-08-30
Actually they are a highly respected company just would not budge on the types of custom configuration I needed. Not even adding additional hardware. I wanted Server installed on the machine as opposed to Desk and I wanted to possibly add a second NIC...Not an option. LOL

Anyway, its System 76. They definitely did a good job with what they would do, just would not upgrade the software from Desktop to Server, or add a second NIC. Oh well. LOL

---

### Post by carl4926 on 2013-08-30
> **Peter_Sotos said:**
> Actually they are a highly respected company just would not budge on the types of custom configuration I needed. Not even adding additional hardware. I wanted Server installed on the machine as opposed to Desk and I wanted to possibly add a second NIC...Not an option. LOL

Anyway, its System 76. They definitely did a good job with what they would do, just would not upgrade the software from Desktop to Server, or add a second NIC. Oh well. LOL

Really!
It's kind of sad to read that. I guess they have to draw lines somewhere....And they are in business to make money.
I'm sure their install would have been fine though

---

### Post by CharlesA on 2013-08-30
Well they do sell [servers]("https://www.system76.com/servers/"), so there is probably some line they cannot cross.

---

### Post by Peter_Sotos on 2013-08-30
Right I knew that. The problem was, the tiny machine was all I could afford. Besides, Linux is famous for running on low powered hardware. Anyway, I thought both my requests were fairly trivial. I guess I am used to the Windows world where when you call up a computer store they build you the exact machine you want with the parts you desire.

Anyway, I do love my little box.

---

### Post by CharlesA on 2013-08-30
> **Peter_Sotos said:**
> 
Anyway, I do love my little box.

And that is what counts.

I remember looking at their servers a long time ago, but they were way out of my price range (at least for the base hardware, my RAID array is another matter).

---

