---
title: "OpenMRS with Apache Tomcat / MySQL"
date: 2009-08-15
forum: Server Platforms
---

### Post by ugm6hr on 2009-08-15
I am experimenting with Electronic Medical Records (EMR) software, but am struggling to get a setup I can work with.  I plan to implement a database for a public hospital department to help track patients' progress and enable efficient communication between care providers.

OpenMRS 1.4.4 is available as a VM appliance on Ubuntu 8.04, and works well.  However, the module I want requires v1.5+

Hence, I have now decided to try and install the 1.50RC2 from [http://openmrs.org/wiki/Downloads](http://openmrs.org/wiki/Downloads) to an 8.04LTS server (although would be prepared to use 9.04 server if required).  I am creating this thread as a diary of my experience to help myself repeat this (currently trying on a VM), and potentially to benefit others...  And hopefully get some assistance here too!

The readme file makes it sound very simple, but it obviously is not that straightforward.

Other links I have read through and tried to navigate:
[http://open.intrahealth.org/mediawiki/Installation_Documentation](http://open.intrahealth.org/mediawiki/Installation_Documentation) (not 100% related)
[https://help.ubuntu.com/community/ApacheTomcat5](https://help.ubuntu.com/community/ApacheTomcat5)
[http://openmrs.org/wiki/Step-by-Step_Installation_for_Implementers](http://openmrs.org/wiki/Step-by-Step_Installation_for_Implementers)

---

### Post by ugm6hr on 2009-08-15
Sorry... forgot to ask my first question.

I have got as far as the Apache Tomcat "If you're seeing this page via a web browser, it means you've setup Tomcat successfully. Congratulations!" page after:

```
sudo apt-get install libapache2-mod-jk tomcat5.5 lcab smarty-gettext php5-mysql libapache2-mod-php5 mysql-server mysql-client ant-optional sun-java6-jdk tomcat5.5-admin cabextract

```

Then:
```
export JAVA_HOME=/usr/lib/jvm/java-6 (-> press Tab here)
export PATH=$PATH:$JAVA_HOME/bin
JAVA_HOME=/usr/lib/jvm/java-6-sun
sudo ufw allow 8080
sudo ufw enable
sudo /etc/init.d/tomcat5.5 start
```

The Tomcat webpage ([http://server_ip:8080/](http://server_ip:8080/)) states  the location of webapps as $CATALINA_HOME/webapps/ROOT/index.html

Where is CATALINA_HOME as default?  I presumed it was /usr/share/tomcat5.5 but /usr/share/tomcat5.5/webapps does not contain any index.html file.

EDIT: Similarly, /var/lib/tomcat5.5/webapps has no index.html either

---

