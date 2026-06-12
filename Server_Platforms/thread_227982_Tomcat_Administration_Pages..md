---
title: "Tomcat Administration Pages."
date: 2006-08-02
forum: Server Platforms
---

### Post by Phasmagon on 2006-08-02
Hello everybody.

I recently installed tomcat 5.0.30 from the repos. My problem is that the administration pages do not work as expected. The menu to the left does not expand as expected. I have spent almost all day trying to resolve this issue, unseccessfully. I know there was an issue with tomcat 5.0.30 beta administration pages, but my guess that the version on the repos is the stable.

Anybody can help?

---

### Post by garylai on 2006-08-16
I think the admin tool is running ok. In here I guess your Tomcat5 is running smoothly, all you have to do first is to change the conf file in:

/var/lib/tomcat5/conf/tomcat-users.xml

It should look smilar to this:
<user username="tomcat" password="your_password" roles="tomcat,admin"/>

Now restart tomcat:
sudo /etc/init.d/tomcat5 restart

Tomcat is listening on port 8180. So open up firefox and enter [http://localhost:8180](http://localhost:8180) in the address bar. Once the page loads you should see a tomcat welcome page. You can see the "Administration/Tomcat Administration Link" on the left, click and login to the admin page.

Hope this can help you :D .

---

### Post by Gustavo Orair on 2006-09-26
I think you just forget to install These webservices!!!
tomcat5 package won`t provide admin and manager webapps!!!
To get this you have to install respectively tomcat5-admin and tomcat5-webapps packages!!!

---

### Post by nsleiman on 2006-12-14
I got another kind of problems;

the [http://localhost:8180](http://localhost:8180) dont work, as if it times out! 

any help maybe?

Regards,

---

### Post by el670005 on 2007-06-15
I believe Phasmagon has correctly installed Tomcat 5 and that he has properly configured his tomcat-users.xml file according to:

[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")
[https://help.ubuntu.com/community/ApacheTomcat5]("https://help.ubuntu.com/community/ApacheTomcat5")
 
There is clearly a problem with the [COLOR="Blue"]tomcat5-admin[/COLOR] package. One only has to do a base install according to the instructions (above),  make a simple change in the Tomcat Web Server Administration Tool application, and attempt to persist it using the [COLOR="blue"]Commit Changes[/COLOR] button. Then, take a look at the following log to see that there is a multitude of file-permission issues associated with the admin tool.  
 
[COLOR="blue"]/var/log/tomcat5/localhost_admin_YEAR-MONTH-DAY.log[/COLOR]

The contributors who respond half-hazzardly without reading or attempting to diagnose the actual issue should seriously consider that they are only wasting time and decreasing the value of this forum.

---

### Post by el670005 on 2007-06-15
> **Phasmagon said:**
> Hello everybody.

I recently installed tomcat 5.0.30 from the repos. My problem is that the administration pages do not work as expected. The menu to the left does not expand as expected. I have spent almost all day trying to resolve this issue, unseccessfully. I know there was an issue with tomcat 5.0.30 beta administration pages, but my guess that the version on the repos is the stable.

Anybody can help?

I have confirmed it on my host also.  I am having the exact same problem.  The left-navigation will neither expand or contract.  Leaf-nodes will display their corresponding page in the content-well.  All attempts to persist any change made through the administration tool fail.

---

### Post by el670005 on 2007-06-15
I have tested the Tomcat Web Server Administration Tool in version 5.0.30.x on a separate Windows XP host.  The exact same issue appears to be occuring.  This is evidently a Tomcat bug.

---

### Post by el670005 on 2007-06-15
> **el670005 said:**
> I have tested the Tomcat Web Server Administration Tool in version 5.0.30.x on a separate Windows XP host.  The exact same issue appears to be occuring.  This is evidently a Tomcat bug.

To be more specific.  The Tomcat 5 and the Administration Tools packages that are downloaded from the multiverse repository have minor file-system permission issues.  These can easily be fixed by making the tomcat5 user the owner of the $CATALINA_HOME folder. However, because the version of the Administration Tool that ships with Tomcat 5.0.30.x is effectively unusable anyway, there is no sense in attempting to fix it.  This is one for the folks at Apache.

---

