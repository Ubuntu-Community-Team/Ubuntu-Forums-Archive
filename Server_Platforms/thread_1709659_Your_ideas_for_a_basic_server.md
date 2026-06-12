---
title: "Your ideas for a basic server?"
date: 2011-03-18
forum: Server Platforms
---

### Post by ubuntu1sttimer on 2011-03-18
For several years we have had a personal genealogy web/email server hosted by a national company. The cost raises every renewal so we are considering hosting ourselves. 

Requirements are web and email with light usage. There will be a couple thousand smaller files so the heavy users are the search engines. Normal users will will only access a few files at at time. The electric bill is a factor so a larger power supply and case are not what we need. 

While I have used Ubuntu since Dapper, I have not worked with the server edition. I would even consider a used packaged server if one could be found at the right price.

Your ideas please.

---

### Post by drdos2006 on 2011-03-18
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by wongo888 on 2011-03-18
Get a VPS. Name your "right price" on a hosting forum like webhostingtalk and see if someone can match it. You ISP will load whatever you want on it.

---

### Post by rbishop on 2011-03-18
Here are a couple things to consider when looking to host at home:

Who is your broadband provider?
Is your connection a residential account?


If you have a residential broadband connection your email will probably not work since most providers block email that doesn't go to their mail server.

Your best bet would be to look for a VPS or colo if you already have a box for hosting your site on.

Just my $0.02 worth.

---

### Post by SeijiSensei on 2011-03-18
I'm with wongo; get yourself a virtual server.  For [as little as $20]("http://www.linode.com/") a month, you can have a virtual machine with a big pipe to the Internet and a public IP address in a large hosting facility with backup power.  For a few more bucks you can have daily snapshot backups as well. The only issue might be file storage charges.

---

### Post by BkkBonanza on 2011-03-19
To get some idea of scale - how much are you paying now? And for what resources?
And how much of those resources are you currently using?

I'd also recommend a VPS. It really is a far better solution than plugging a box in at home and mostly the cost will be about the same as the electricity for a box at home (or office). Providing a good connection and stable power is quite important in web serving and it's just better to use a data center. There is a lot of room for variation though and not all hosting companies are the same. You may just be paying too much where you are now.

I pay $11/mo. for a 1024 MB VPS and have had very little trouble with this over the last two years wth this company. But companies do vary and often finding a known good one can cost more. I'm not looking for any management though - just solid server and solid connection. I do the rest via SSH myself.

Another solution I've had good success with is using Amazon EC2 - their costs keep going down not up. And it's very flexible, much like having a super scaleable VPS, though not as good as a lowest price solution. They run a tight professional ship but it's only well suited if you can manage your own technical details. It can be very cheap if you don't need much cpu power or bandwidth and more of both is always ready on hand.

---

