---
title: "Mapping Shares..."
date: 2009-05-27
forum: Server Platforms
---

### Post by roystreet on 2009-05-27
Hello,
   I have a very successful linux ubuntu server setup.  I have windows users connecting to it.  I want my users to be able to map a share without having to enter their username/password everytime they boot up their machine.  

Thanks,
  ~roystreet

---

### Post by LEO_Servers on 2009-05-28
If you set them up with a Directory such as E-Directory which is perferd or Active Directory you can than put the users in OU's and giving the OU's a script that auto adds the directors as needed.:D

---

### Post by roystreet on 2009-05-28
I was hoping not to use Active Directory because of the work involved.  I've never heard of E-Directory.  I mainly want the drives mapped for the behind the scenes backup program.  Their main documents folders, etc will still remain on local machines & not the server. It's just a basic file server. Although I love things like AD, but it takes so much time that isn't needful for just maybe 3 users.

Any other ideas? (I will also look at e-directory)
~roystreet

---

### Post by LEO_Servers on 2009-05-30
when you map the drive their is a option to check a setting to keep the mapped drive in windows so when you log back in there  it automaticaly maps, this may be the best way for three users.
 
as far as backup there are mutiple things that can be done using a 3rd party program such as "amanda" Open source back up utility or setting up corn job in the linux box for backup what kind of system do you want to do the back up from? 
 
[http://amanda.zmanda.com/](http://amanda.zmanda.com/)
 
and also what type of back up are we talking about there are three types of backup's differential backup, incremental backup, full backup
 
Explains the dirfent types of backups if you dont know them right off the top of your head. 
[http://www.geekgirls.com/windows_backup_strategies_table.htm](http://www.geekgirls.com/windows_backup_strategies_table.htm)

---

### Post by roystreet on 2009-05-30
I actually have a windows program that backs up the local files on to the server.  It builds machines images & the other 3 backup types.  I have it set to perform incremental back up jobs weekly on a specific share for each user.  Although I have nothing that backs up the linux server.

Even though I would check the box for the users machine to connect next time, it wouldn't keep it the next time.  I then changed the samba password to match that on the users machine. Then the windows machine kept that drive mapped every time.

Thanks for the help
~roystreet

---

### Post by HermanAB on 2009-05-30
Actually, setting up Active Directory is very easy.  If you have more than 10 users, then get MS Server 2003 and use that.  You'll have it running within a day.

The secret to Active Directory happiness is to ***Never Change Anything***.  If you need to make a change, create a new record and then delete the old one. Fail to heed that simple rule and you are guaranteed to have the most weird and wonderful problems.  The second trick is to run it on a VMware virtual machine on Linux. That way you can backup the whole machine regularly.

If you have the time to read a guide and experiment a bit, then go to the Samba web site and read the Official Howto and set up a Samba directory server.

---

### Post by roystreet on 2009-05-31
Hi HermanAB, I used to have server 2003 & it was pretty solid.  I really liked AD.  It was much more powerful than my needs...Which means that I wouldn've spent a ton of time learning all sorts of great things.  I decided it was eating into some precious time & thus said goodbye to it.  I like to figure things out, so it's easy for me to spend a ton of time on it. My ubuntu server is a happy little box that took hardly anytime to build/setup.  I can't say I've ever setup server 2003 on a linux box, that sounds really interesting...One day I might do that.

Oh! I wanted to add that I've setup a win server before, but not a linux one...So this was my opportunity to do it! - Surprisingly easy!

Thanks for everyone's help!
~roystreet

---

### Post by LEO_Servers on 2009-05-31
Every pc can be treated in windows as a stand alone server right click the my computer go to managment in here you can configure each pc just like you would AD in here you can set up a script in ther servirces area => setup in here you would place you batch script for mapping drives so you know how to make a bath file script? if not i can make it for you, :D

---

