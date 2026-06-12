---
title: "Apache Tomcat virtual host configuration"
date: 2010-06-11
forum: Server Platforms
---

### Post by Thyagaraj on 2010-06-11
I've apachectl installed(downloading & extracting "httpd-2.0.62.tar.gz" to /usr/local/apache) having the default apache(/etc/apache2) and Tomcat is installed(/usr/share/tomcat) & is configured for port forwarding(to port 80). i.e without typing [http://ip:8080/](http://ip:8080/) i can directly access by typing [http://ip/](http://ip/) or along with any virtual host under tomcat/webapps.

I've lot of applications under tomcat/webapps which are created using java css xml php scripting languages.

What i want is virtual host configuration,
I want to configure a virtual host under "/usr/local/apache/conf/httpd.conf" with the DocumentRoot of "/usr/share/tomcat/webapps"

for e.g: if i type [http://ip/](http://ip/) i should directly get an application which is located under tomcat/webapps (or) else if it could be done editing the "/usr/share/tomcat/conf/server.xml " file then it's fine.

plz... anyone help to sort out this problem
 		                   		  		  		  		  		 		 			 				 				* 					 						[Last edited by Thyagaraj]("http://ubuntuforums.org/posthistory.php?p=9434209"); 20 Hours Ago at 04:42 PM.. 					 					 				* 			
 		 		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=9434209") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=9434209")

---

