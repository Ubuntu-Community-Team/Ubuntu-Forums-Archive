---
title: "Looking for some guidance on a SQL project"
date: 2010-12-08
forum: Server Platforms
---

### Post by Headfirst on 2010-12-08
Hey all I'm fairly new to using SQL I am trying to teach myself because I have an idea that I think a database would prove very beneficial also I need a project to take up my free time, with the semester coming to a close and it being too cold to go mountain biking. I think the best way to describe what I need is to tell about what I hope to achieve. 

I am kind of a statistics nerd, sports nut, and gambling aficionado needless to say I do a lot of betting through an online book and what better way to learn from one's mistakes than to analyze them. I want to create a database containing pertinent information from each of the bets I make and then the ability to run queries on them. For example finding my win percentage based on bets on home team favorites or if I win more football or basketball bets.. Get the idea?

What I have done so far is use open office database to create a table and the columns along with entering in quite a few different bets. I then created a basic query for a sum of the bet amounts and sum of winnings. I can also create a "report" but what I can't do is figure out how to make a field that will tell me if I'm up or down over the long run. I also can't get it to put out an actual win percentage only total wins and total losses which I then have to manually calculate to get my percentage. I've used a script that turned this database into a SQL file. What I'd like to do is set up a locally hosted web page with a form on it to enter data in to or run queries. 

So if you are still with me on this and actually took the time to read my long winded request I thank you. If anyone could provide me some direction on what to do in order to get this sql script into the sql-server for starters. I'm not looking for someone to do this for me by any means it's something I'm very excited to learn about and I've always found these forums extremely helpful in the past since I became a Linux for lifer :P

If I left anything out or you have additional questions let me know and thanks again!

---

### Post by lykeion on 2010-12-08
> **Headfirst said:**
> What I'd like to do is set up a locally hosted web page with a form on it to enter data in to or run queriesI think you'd do best to install LAMP =  **L**inux-**A**pache-**M**ySQL-**P**HP. 
Linux is the operative system, Apache is the web server, MySQL is the database, PHP is the scripting language.
Install instructions for Ubuntu [HERE]("http://www.howtoforge.com/ubuntu_lamp_for_newbies").

> **Headfirst said:**
> If anyone could provide me some direction on what to do in order to get this sql script into the sql-server for starters.First of all, check [THIS]("http://www.tizag.com/mysqlTutorial/index.php") MySQL tutorial.

You can import the SQL file into MySQL from a terminal (Applications > Accessories > Terminal) like this:
```
mysql -u USERNAME -p DATABASENAME < FILE.SQL 
```

Read [THIS]("http://www.freewebmasterhelp.com/tutorials/phpmysql/1") tutorial to help you create a form using HTML/PHP to query your MySQL database.

Hope that this helps, I know it was a lot of info to read, so please post if you need more help.

---

### Post by draperdt on 2010-12-08
Just so OP knows, that *is* a lot to read. No way around it. Do or perish.

---

### Post by Headfirst on 2010-12-09
Thank you lykeion that is a lot to read but I will definitely get to reading on all of it. I just updated to 10.10 which took most the evening. I am now going to start installing LAMP. 

I'll let you know if I have any questions.

---

### Post by Headfirst on 2010-12-09
One quick question. I'm pretty sure I got this right but just want to check.

> Step 2 (optional). In order for other computers on your network to view the server you have created, you must first edit the "Bind Address". Begin by opening up Terminal to edit the my.cnf file.

gksudo gedit /etc/mysql/my.cnf

Change the line

bind-address = 127.0.0.1

And change the 127.0.0.1 to your IP address. 

For this step I would change it to the IP address assigned by my ISP not the router assigned IP address right? Forgive me if my descriptions of the two IP addresses is not accurate, networking isn't my cup of tea :p

---

### Post by Girya on 2010-12-09
You might want to check out awk. It will do everything you want it to do: calculate wins and losses, averages, return on investment, whatever you can think of. I think you could figure out which day of the week is the most profitable. 

awk parses a simple text file, fields are separated by whatever character you choose: tab, ",", ":" etc. Records are separated by newlines. It takes a little planning when you set up the text file but its a lot less planning than setting up a database. The advantage of awk over a LAMP stack is its simplicity, you only have to learn one program. I know you could make the same argument with Mysql and just use a sql shell but I don't think thats very common.  

If your goal is learning LAMP then go with it but check out awk its great old school.  

To answer your question you dont need to edit that line. you would change it only if you wanted your database accessible by other computers on your network. definitely don't use the ip address that is supplied by your isp. that would be bad.

---

### Post by Headfirst on 2010-12-09
Thanks for the insight Girya. I looked into Gawk somewhat the only thing I don't like is it doesn't allow for data entry it just scans a generated file. While you are right it would do exactly what I want and it would be easier buuuuuut I think it would be way cooler if I was able to accomplish this with LAMP.. Plus it gives me an excuse to put to use the PHP programming class I took a few semesters back. ;)

I've decided to leave the bind = 127.0.0.1 for now. Is it my understanding that if I assigned it to an IP address on my network then I would be able to access the server by typing in that IP address in FF instead of typing in the local host IP? If so that is pretty cool because my roommate does some betting and that would give him access to the database too. Again thanks for everything.

---

### Post by tgalati4 on 2010-12-09
Besides a database, you need an artificial intelligence (AI) algorithm to model the data.  Handicapping horse races is a common application.  You input a horse's race results then run a simulation for how that horse would perform given a set a track conditions and a field of competitive horses.

There are lots of variables to input, and lots of correlations to make.  

apt-cache search game theory

This brings up gambit.  Try installing it and see if it gets you any closer.

sudo apt-get install gambit

---

### Post by lykeion on 2010-12-10
> **Headfirst said:**
> One quick question. I'm pretty sure I got this right but just want to check.
For this step I would change it to the IP address assigned by my ISP not the router assigned IP address right? Forgive me if my descriptions of the two IP addresses is not accurate, networking isn't my cup of tea :p
For a local database you will leave it to localhost (127.0.0.1). It's only if you need a remote connection to it you would change the bind-address.
EDIT
Just read Girya's post and saw that he already answered.
Good luck with the LAMP setup and the gambling project.

---

### Post by Headfirst on 2010-12-13
Ok I wrote my php code and now I'm just trying to get the database all set up. The first issue I'm having ( I'm sure there will be more ) is that I can't get into phpmyadmin. I tried using
```
sudo dpkg-reconfigure -plow phpmyadmin
```
and setup the host as 127.0.0.1 but when I go to 
```
http://localhost/phpmyadmin
```
I get a 404 Not Found. What am I doing wrong?

---

### Post by lykeion on 2010-12-14
You might have forgotten to configure Apache to work with phpMyAdmin. To do this you need to edit the Apache configuration file:```
gksu gedit /etc/apache2/apache2.conf
```
And add this line:```
Include /etc/phpmyadmin/apache.conf
```
Save and exit gedit.
Restart Apache like this:```
sudo service apache2 restart
```

Personally I never use phpMyAdmin because I think it's much easier to handle MySQL from command-line.

Apache/MySQL/PHP is very well documented on the web and the problem is rather to filter out wrong/irrelevant info. For every web guide out there you need to ask yourself is this info relevant to your Ubuntu version and the version of Apache/MySQL/PHP you are using.

The Ubuntu Community Documentation is often very good, like this page: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Girya on 2010-12-15
you might want to try a virtual appliance for your lamp server very simple and will let you get going in less than two beers. I downloaded and started one up in about as long as it took me to write this post. 

it takes a little bit of time for the virtual machine to update but thats about it.

if your interested install virtualboxose with synaptic then download the LAMP virtual appliance from turnkey linux-- [http://www.turnkeylinux.org/lamp](http://www.turnkeylinux.org/lamp) download the VM 162mb file
and unzip it then import it into virtual box file> import virtual appliance... browse to the folder and open it click okay and go. 

keep awk in the back of your mind. its really useful to mock up databases

---

