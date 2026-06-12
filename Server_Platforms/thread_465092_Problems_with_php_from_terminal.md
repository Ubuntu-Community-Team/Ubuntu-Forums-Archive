---
title: "Problems with php from terminal"
date: 2007-06-05
forum: Server Platforms
---

### Post by umattu on 2007-06-05
Here is my dimemna,

I have a Dapper LAMP server up and running a ticketing system at my company. The system is oneorzero, I have the system running perfectly on the http side of things. The site works, the tickets can be created from the web interface, it emails notifications via postfix to the ticket managers and what not. 

The problem comes in when tickets are emailed to the system. I have set up a job in crontab to check for emails for the system. When it sees a message it will grab the message but it will not interact with mysql. I get the following error.

Fatal error: Call to undefined function mysqli_connect() in /var/www/common/mysql5.class.php on line 51

I had this problem initially with the web end but I uncommented this extension in the php.ini file in the apache2 directory which smoothed everything over. 

I tried adding these extensions, mysql.so and mysqli.so to the php.ini file found in the cli directory but it is not working, I made sure the path to the extensions were corret in the /cli/php.ini file, but when i runthe job I get this error:

PHP Warning:  PHP Startup: Unable to load dynamic library './usr/lib/php5/ext/mysqli.so' - ./usr/lib/php5/ext/mysqli.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP Warning:  PHP Startup: Unable to load dynamic library './usr/lib/php5/ext/mysql.so' - ./usr/lib/php5/ext/mysql.so: cannot open shared object file: No such file or directory in Unknown on line 0
Could not open input file: phpinfo

What am I missing here? I have been trying to work through this problem for 4 days now and I am hardly gaining ground. I am happy that I discovered that the terminal (cli) is working off of a different php.ini file then apache is but it seems not to be working.

I installed the Lamp server from a dapper server install disc and I am positive that both extension, mysql.so and mysqli.so exist and that the paths to them in the /etc/php5/cli/php.ini file is correct.


Please HELP!!!!!!

---

### Post by umattu on 2007-06-05
Anyone?

---

### Post by umattu on 2007-06-05
after a stint in a PHP forum I realized that the problem existed with the path to the extensions in the php.ini file. The problem is actually right in the error message. When I went back into the cli php.ini file to double check the path, for the hundreth time I noticed that I had typed a period prefixing the path and if you look in the error message you can clearly see the period.

PHP Warning: PHP Startup: Unable to load dynamic library './usr/lib/php5/ext/mysqli.so' - ./usr/lib/php5/ext/mysqli.so:

I feel like a heel, but I'm just glad that I got it figured out. Not that anyone cares but thats all it took.  

My network administrator at work was running this ticketing system on a windows server 2003 Virtual machine on his desktop. He knows that I am into ubuntu and is always telling me how silly it is to not focus on the MS os's because according to him "thats where the money is". He refers to ubuntu as a toy, even though he has never used ubuntu. So when he decided that the overhead of running this system , which is used by our entire IT dept;, was too much for his machine he decided that he would have me throw together an ubuntu LAMP server to run it on. The thing is he said I had to use everything from the MS box and move it to the linux box, instead of just freshly installing the system and importing the mysql tables, OMG what a mess, I think he wanted to prove something I dont know, but after dealing with replacing tons of windows paths in the files with the correct ubuntu paths I got this system blazing away, the only thing that wouldn't work was this inbound email ticket creation aspect of it. Now its running and I couldn't be happier. Now to top it off I am going to modify the site template to include a "powered by UBUNTU" l ogo at the just to remind everyone that our all important ticketing system is now running on, in his words "a toy OS" 

Sorry to ramble but I AM SO PROUD to have gotten an ubuntu box into my company amongst all of the MS loyalists that have to use it on a daily basis to perform their day to day duties!!!!!

GO UBUNTU!!!!!!!!!!!!!!!!!!!!!!!!!!;)

---

