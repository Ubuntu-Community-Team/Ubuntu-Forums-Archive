---
title: "Filing"
date: 2007-04-25
forum: The Cafe
---

### Post by richardjennings on 2007-04-25
I have a client who would like me to reform their methods of filing. Currently they use a directory structure to ensure certain criteria.  I have suggested a database application might better server their needs. For example being able to search for files beginning with A from year 1999. 

The company are chartered accountants.

They operate in a purely windows environment.

Are there any programs available that will make filing easier.

I am currently preparing to write a custom application.

cheers,

rich

---

### Post by ssodhi on 2007-04-26
Hi,
If you are proficient in using PHP and MySQL, I'd go with a simple PHP frontend to a standard MySQL database. MySQL using MyISAM has searching features, and a well crafted regular expression is more than enough to give an outstanding level of flexibility on your end, I'd imagine that the focus would largely be on keeping the client's financial records very secure. If you are willing to put more work into a 'nice' User Interface, you may wisht o offload the revision and access control work to a backend based on SVN or some such thing, with the end user entirely shielded from the less friendly features.

I hope this helps some, I can be more specific if you'd like.

-Sanjay Sodhi

---

### Post by richardjennings on 2007-04-26
Thank you that was extremely helpful. Php and Sql was also my first suggestion. I am having trouble picturing what a use full interface would be. 

1) new exel document
2) saved to storage server
3) details entered into sql via php front end.


If you would not mind being more specific I would be very thankful. 

I am finding it hard to even imagine how to present the interface to the user to ensure that files are entered into the database.

---

### Post by richardjennings on 2007-04-26
say I set up a dedicated server to handle the filing. Something along the lines of a small VIA ITX integrated cpu box to minimize power consuption. An Ubuntu server install with php mysql and apache. Would it be possible using samba for the filing server to run a cron job on the php/sql filing script to update itself every morning and catalogue all the files that have been modified/created since the last cron update? 

If this is possible could details of the author of the file also be gathered? If that is possible the script could email the author of the files with a list of required information every morning such as client name, year end etc.

I would like to separate the filing from the content. I.e there are already systems in place to ensure that data is not lost. It seems to me that having a filing server to index the "company shared folder" file locations would be the way to go.

---

### Post by ssodhi on 2007-04-26
I think you could save yourself the trouble of having a specific file server by using a PHP/MySQL based file system. The document would be uploaded and all of the data stored in a MySQL BLOB field, and when you want to retrieve it you send the appropriate file headers out (e.g application/msword) and output the data from the MySQL table. By giving the right headers, it is interpreted together as the original MS Word document.

I would strongly suggest that you invest in some hard books on PHP/MySQL and you read up on how to do PHP file upload and download with MySQL storage. [here]("http://http://www.php-mysql-tutorial.com/php-mysql-upload.php") is a nice basic introduction to it. Essentially this removes a lot of the difficulties of having a File Server and maintaining the files. Think about how you would structure the database! The frontend would be relatively simple to do, it's setting up your schema that will likely give you trouble.

I suggest further research before you continue

-Sanjay Sodhi

---

### Post by richardjennings on 2007-04-26
I don't think storing files in a database is a good idea. Certainly it is a very good choice for attachments to a forum, or such like web based applications.

However - if you assume that one file takes 30mins to produce - then I will assume an arbitrary value of $10; this value is probably slightly understated. If I were to store 2000 of these files in a database, the databases liability would be in excess of $20k. If there were a problem with the database, say for example I let a small bug slip through that led to the corruption of the database - even if I fixed it quickly there will be a massive amount of chaos. I will have my head chopped off.

However if the filing sever database were to go down - there would not be so much of a problem. 

These are my concerns over using a database to store files.  What are your thoughts?

---

### Post by ssodhi on 2007-04-26
Hello,
Yeah I can see where you're coming from. You could, at the least, maintain an index of all uploads in a database with the necessary paths stored, so for all intents and purposes you *are* controlling and maintaining the files as database entries, but they have their own physical representation on a server. Having a separate file server brings in a number of issue of its own, which are largely unnecessary, thus I would be reluctant to go along those lines. AJAX frontend, PHP interface to MySQL storing file and user information. You may wish to think about how you are going to migrate to the new system, as well. If you go with their current directory structure but formalize it with PHP/MySQL, for all they care you've created a whole new system, and your backend should keep it very robust and secure

Just my thoughts
-Sanjay Sodhi

---

