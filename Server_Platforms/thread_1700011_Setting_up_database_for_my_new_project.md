---
title: "Setting up database for my new project"
date: 2011-03-04
forum: Server Platforms
---

### Post by rajnikhil on 2011-03-04
Hi,

I require a database to record details of customers/orders. I'll be accessing and updating this database remotely. I've been doing some research lately and found two possible solutions.
1. Install open office base>create data base>create form>ssh to the box in which I install ooBase.
2. Install LAMP>Use MySQL>use MyPhpAdmin to update the data base for info said above.

I tried the first one. It works well but is slow and the customer might not be willing to bare with me while I update the details in which case I might have to use pen & paper and this defeats the idea of having database, partially if not completely.

So I'm thinking to try out the second one but it seems a little scary when I see so much info about it and also issues being discussed around configuring it. However I'll still go ahead with it hoping you guys are there for helping me out. 

To keep the damages to a minimal I'll install it in a virtual machine having Ubuntu 10.10.

One doubt I'd like to get clarified at this point is, whether I can update the database with details I mentioned above using MyPhpAdmin. If no then what else should I use or do.

This is my first question and I'll post more on this thread as and when I get them, while I try and set this database up and make it operational.

---

### Post by Neo@Matrix on 2011-03-04
Let me ask you something before I try to answer some of your questions here:

1.Is the web page using database already up'n'running or jet under dev?
2.What are the expectations regarding the quantity of data in this database?
3.Volume of users visiting-using this database?
  
MyPHPAdmin is a handy tool for the job like this.By using it , you can access , 
change , update , create , update  or whatever your need is remotely.

---

### Post by wongo888 on 2011-03-04
There must be a million commercial apps that do exactly this. If this is a business, why not buy one? You would get commercial level support and the expense is often tax deductible.

Salesforce.com comes to mind.

---

### Post by rajnikhil on 2011-03-05
> **Neo@Matrix said:**
> Let me ask you something before I try to answer some of your questions here:

1.Is the web page using database already up'n'running or jet under dev?
2.What are the expectations regarding the quantity of data in this database?
3.Volume of users visiting-using this database?
  
MyPHPAdmin is a handy tool for the job like this.By using it , you can access , 
change , update , create , update  or whatever your need is remotely.
Hi Neo@metrix

1. The database isn't setup yet, I'll have to do it.
2. I'm not sure what you mean by the quantity of data but I'm assuming you mean how much in terms of numbers. If yes, I'm speculating around 40 to 50 order details per day with about 13 fields per order and all text.
3. For the moment it is only going to be one and may be two more a few months down the line.

> **wongo888 said:**
> There must be a million commercial apps that do exactly this. If this is a business, why not buy one? You would get commercial level support and the expense is often tax deductible.

Salesforce.com comes to mind.

Hi Wongo888,

I haven't checked out any commercially available apps for one simple reason that is I cannot afford it just yet.

---

### Post by SeijiSensei on 2011-03-05
Unless you're ideological opposed to Windows or proprietary software, go get yourself a copy of [Quickbooks]("http://quickbooks.intuit.com/") and be done with it.  They also offer a "cloud"-based solution as well that presumably needs nothing more than a browser.

---

### Post by BkkBonanza on 2011-03-05
Installing LAMP (includes mysql!) and PhpMyAdmin will give you what you need and is fairly easy to install for someone with a bit of technical experience. It gives you full control over what you're doing and you can start out with adding/editing records in PhpMyAdmin and build a more suitable web interface as you go.

The main problem with using PhpMyAdmin is that for orders you generally need to use relations between tables and that is pretty much manual in that tool as it's meant as a very general purpose DB manager. ie. You usually want an **orders** table with data per order, and an **order_items** table with each item row in the order. This is better handled with a customized script to handle the web forms because you will want an order_id value to link them.

I'm pretty sure if you googled around you'd find ready to use web apps that are pre-made for order handling and just sit on top of LAMP. There are proper ecommerce apps like osCommerce and ZenCart that do much more but  have the basic order management tools as a subset.

---

### Post by rajnikhil on 2011-03-05
> **SeijiSensei said:**
> Unless you're ideological opposed to Windows or proprietary software, go get yourself a copy of [Quickbooks]("http://quickbooks.intuit.com/") and be done with it.  They also offer a "cloud"-based solution as well that presumably needs nothing more than a browser.

You guessed it right seiji, I'm slightly if not completely opposed to windows and/or proprietary s/w for atleast the level of my requirements which is fairly simple.

> **BkkBonanza said:**
> Installing LAMP (includes mysql!) and PhpMyAdmin will give you what you need and is fairly easy to install for someone with a bit of technical experience. It gives you full control over what you're doing and you can start out with adding/editing records in PhpMyAdmin and build a more suitable web interface as you go.

The main problem with using PhpMyAdmin is that for orders you generally need to use relations between tables and that is pretty much manual in that tool as it's meant as a very general purpose DB manager. ie. You usually want an **orders** table with data per order, and an **order_items** table with each item row in the order. This is better handled with a customized script to handle the web forms because you will want an order_id value to link them.

I'm pretty sure if you googled around you'd find ready to use web apps that are pre-made for order handling and just sit on top of LAMP. There are proper ecommerce apps like osCommerce and ZenCart that do much more but  have the basic order management tools as a subset.

Thanks a lot for such a comprehensive answer bonanza. I can see the point you are trying to make and I've already taken that into consideration when I decided to go this way. One reason for my decision is that at least in the near future I am assuming that I'll be able to manage with not so sophisticated app too another reason reason I'm just in love with ubuntu or for that matter linux (I use a maemo os phone ;)) and want to stick to it and scale it as my project grows (fingers crossed). However if you know of any such commercial app for linux which might be useful for me to know, keeping in view the scalability, please let me know.

---

