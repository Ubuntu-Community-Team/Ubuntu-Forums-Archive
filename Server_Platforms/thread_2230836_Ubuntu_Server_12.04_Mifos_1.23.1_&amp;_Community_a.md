---
title: "Ubuntu Server 12.04 Mifos 1.23.1 &amp; Community app Install Guide/HOWTO"
date: 2014-06-21
forum: Server Platforms
---

### Post by misha4 on 2014-06-21
**Installation guide: Linux Server for Mifos Platform using Ubuntu Server 12, JDK7, Tomcat web server and mysql server.**

 
                         Versions at a time of this guide
                             Icon                                              All required software in this guide (with an exception of mifosplatform) comes from Ubuntu Package System.
Ubuntu 12.04.4 LTS  Release:    12.04   Codename:    precise
mysql  Ver 14.14 Distrib 5.5.37, for debian-linux-gnu (i686) using readline 6.2
Apache Tomcat/7.0.42 
mifosplatform-1.23.1.RELEASE
OpenJDK Runtime Environment (IcedTea6 1.13.3) (6b31-1.13.3-1ubuntu1~0.12.04.2)
OpenJDK Server VM (build 23.25-b01, mixed mode)
                     
     
  
**Step 1 - Installing System Updates and Prerequisites:**

 [INDENT]# sudo -s
# apt-get update
# apt-get upgrade
# apt-get install openjdk-7-jdk mysql-server tomcat7
[/INDENT]
                         

 Set mysql root password to: mysql
(Bad for security, but just to get all installed and instructions on how to change it will be provided later in this guide)

[LIST]
[*]You **could** skip to Appendix A below and setup a custom mifos db user/password right away. 
[/LIST]
                     
     
  
OPTIONAL (nano text editor & date/time settigns)[INDENT]# apt-get install  nano[/INDENT]
Check date:[INDENT]# date
[/INDENT]
and if needed update with[INDENT]# dpkg-reconfigure tzdata
[/INDENT]
 
**Step 2 - Enabling SSL**

To enable tomcat SSL (https), generate and store a key:[INDENT]
All in one line:
 # keytool -genkey -keyalg RSA -alias tomcat -keystore /etc/tomcat7/keystore.jks
 -storepass keystore -validity 360 -keysize 2048
[/INDENT]

Update /etc/tomcat7/server.xml configuration file[INDENT]
Find:
    <Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               URIEncoding="UTF-8"
               redirectPort="8443" />

and after add:

<Connector protocol="org.apache.coyote.http11.Http11NioProtocol"
           port="8443" SSLEnabled="true" maxThreads="200"
           scheme="https" secure="true"
           keystoreFile="/etc/tomcat7/keystore.jks"
           keystorePass="keystore" clientAuth="false"
           sslProtocol="TLS" />

[/INDENT]
Restart and test tomcat:[INDENT]
# /etc/init.d/tomcat7 restart

[/INDENT]
                         Tomcat Testing
                             
Tomcat should be listening on localhost and your external ip if you have one.

Visit [https://](https://)[server ip address]::8080   to confirm tomcat is running
Visit [https://](https://)[server ip address]::8443   to confirm tomcat ssl is working  
(you'll need to accept cerfificate manually)

If pages fail to load, something it probably wrong wiht tomcat. 
Tomcat on ubuntu logs to  /var/lib/tomcat7/logs/  and /var/log/ 

# netstat -ltpu
You should be able to find sometihng like:  0      0 [::]:8443               [::]:*                  LISTEN      27217/java
 You'll need this working to get mifos running.
                     
     
  
**Step 3 - Mifos Platform and Database Setup/Population**

Download and extract mifos platform:[INDENT]# cd /usr/src
# wget [http://downloads.sourceforge.net/project/mifos/Mifos%20X/mifosplatform-1.23.1.RELEASE.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fmifos%2Ffiles%2FMifos%2520X%2F&ts=1403225973&use_mirror=softlayer-dal](http://downloads.sourceforge.net/project/mifos/Mifos%20X/mifosplatform-1.23.1.RELEASE.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fmifos%2Ffiles%2FMifos%2520X%2F&ts=1403225973&use_mirror=softlayer-dal)
# mv mifosplatform-1.23.1.RELEASE.zip\?r\=http\:%2F%2Fsourceforge.net%2Fprojects%2Fmifos%2Ffiles%2FMifos%20X%2F  mifos.zip
# unzip mifos.zip
# cd mifosplatform-1.23.1.RELEASE
[/INDENT]
                                 
Icon                                              If wget/download fails,  get a working link here [http://sourceforge.net/projects/mifos/files/Mifos%20X/](http://sourceforge.net/projects/mifos/files/Mifos%20X/) )
                     
     
 
Create and populate databases (more at  [https://github.com/openMF/mifosx/blob/master/INSTALL.md](https://github.com/openMF/mifosx/blob/master/INSTALL.md) )[INDENT]
# mysql -uroot -pmysql
-- In mysql console type:

create database `mifosplatform-tenants`;
create database `mifostenant-default`;
exit

# mysql -uroot -pmysql mifosplatform-tenants < database/mifospltaform-tenants-first-time-install.sql
# mysql -uroot -pmysql mifostenant-default < database/migrations/sample_data/load_sample_data.sql
[/INDENT]

Add database Resource to tomcat config[INDENT]
# nano /etc/tomcat7/server.xml


 <GlobalNamingResources>
    <!-- Editable user database that can also be used by
         UserDatabaseRealm to authenticate users
    -->
    <Resource name="UserDatabase" auth="Container"
              type="org.apache.catalina.UserDatabase"
              description="User database that can be updated and saved"
              factory="org.apache.catalina.users.MemoryUserDatabaseFactory"
              pathname="conf/tomcat-users.xml" />


<Resource type="javax.sql.DataSource"
            name="jdbc/mifosplatform-tenants"
            factory="org.apache.tomcat.jdbc.pool.DataSourceFactory"
            driverClassName="com.mysql.jdbc.Driver"
            url="jdbc:mysql://localhost:3306/mifosplatform-tenants"
            username="root"
            password="mysql"
            initialSize="3"
            maxActive="10"
            maxIdle="6"
            minIdle="3"
            validationQuery="SELECT 1"
            testOnBorrow="true"
            testOnReturn="true"
            testWhileIdle="true"
            timeBetweenEvictionRunsMillis="30000"
            minEvictableIdleTimeMillis="60000"
            logAbandoned="true"
            suspectTimeout="60"
       />
  </GlobalNamingResources>
[/INDENT]
**Step 4 - Activate Mifos**

Copy mifos and community app to Tomcat's webapps folder:[INDENT]
# cd /usr/src/mifosplatform-1.23.1.RELEASE
# cp mifosng-provider.war /var/lib/tomcat7/webapps/
# cp -r api-docs/ /var/lib/tomcat7/webapps/ROOT/
# cp -r apps/community-app/ /var/lib/tomcat7/webapps/ROOT/
# cp -r api-docs/ /var/lib/tomcat7/webapps/ROOT/


[/INDENT]
Create a directory for mifos uploads and change ownership:[INDENT]
mkdir -p /var/lib/tomcat7.mifosx/default/documents/
chown tomcat7 /var/lib/tomcat7/webapps/.mifosx/
[/INDENT]
                         .mifos/    Upload Directory
                             Icon                                              
[LIST]
[*]If .mifos directory is not  created, Clients > Upload Documents  will fail with:  "Error  error.msg.document.save"  (firebug, network tab) 
[/LIST]


[LIST]
[*]Access to this directory should **be restricted** to authorized personnel only.
While  all accounting related information is stored in a database, submitted  documents are simply stored in a same format. Mifos will store user  uploaded files/documents relating to clients,loans,etc   in .mifos/ 
[/LIST]
                     
     
  
and  finally[INDENT]# /etc/init.d/tomcat7 restart

[/INDENT]
Setup is complete and mifos should be running.
 
OPTIONAL:
*in sepperate terminal you may watch your Mifos come to life like this:
 [INDENT]
# tail -f /var/lib/tomcat7/logs/mifos-platform.log
 
[/INDENT]
(if  all is good, after a while of loading, you should see sometihng like:  Root WebApplicationContext: initialization completed in 45876 ms)


                         It's Done!
                             Icon                                               
**Congratulations!**

 
Mifos:
Platform  application should be available @ [https://](https://)[server ip  address]:8443/mifosng-provider/api/v1/offices?tenantIdentifier=default&pretty=true
Community  application should be available @ [https://](https://)[server ip  address]:8443/community-app?baseApiUrl=https://[server ip  address]:8443/mifosng-provider/api/v1/
 
username: mifos
password: password
 
                     
     
 **Appendix A - Change mysql username/password**

Change Mifos default mysql password:[INDENT]# apt-get install phpmyadmin
[/INDENT]
1.  Go to   [http://](http://)[yourserverip]/phpmyadmin  and login

2.  Click on Privileges, then Add a new User

3.  Pick a username/password and create it. Assign full privileges  globally, or on  mifosplatform-tenants &  mifostenant-default  databases.

4. On the left, select/open mifosplatform-tenants database,
you should see a table with a single column , click "edit" infront of it.

Locate:
schema_username
schema_password

And set user/pass created in step #3.

Finally, edit

/etc/tomcat7/server.xml
username="root"
password="mysql"

And set user/pass created in step #3 here as well.

You can now set new mysql root password, without braking mifos.

Restart tomcat. Finish.

[INDENT]# /etc/init.d/tomcat7 restart

[/INDENT]

---

