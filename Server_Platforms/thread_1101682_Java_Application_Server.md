---
title: "Java Application Server"
date: 2009-03-20
forum: Server Platforms
---

### Post by Vegan on 2009-03-20
I was wondering what is available in the Ubuntu camp to provide a Java Application Server so I could add Java applications to my LAMP stack.

There seems to be several alternatives and I wanted to hear about them and any headaches there might be.

---

### Post by Vegan on 2009-03-21
Found this stuff when attempting to run Java

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * cacao-oj6-jre-headless
 * gij-4.2
 * kaffe
 * jamvm
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * sablevm
Try: sudo apt-get install <selected package>
-bash: java: command not found

I am looking for something I can use to serve Java pages from Apache or as a standalone server. So that my Linux can serve Java applications and leverage MySQL which is found resource.

---

### Post by windependence on 2009-03-22
You want to set up a Tomcat server.

-Tim

---

### Post by Vegan on 2009-03-22
I chose tomcat6 for the service, so what do i need for mime types to serve JSP and JSPX named pages as well as HTML with inline Java etc.

tomcat6 came with a boatload of other programs that it evidently needs. not that i care, as long as at the end of the say I get where i want to be.

i wanted to add java to the portfolio as its a popular language in larger corporate shops.

---

### Post by windependence on 2009-03-22
I'm afraid I may not be of too much help with setting up Tomcat as the only Tomcat servers I use are Zimbra servers and they preconfigure Tomcat on installation. 

I will say this, I have several Java college courses under my belt, and I have worked for companies like IBM before going off on my own, and I'm not sure the java application server thing is that big in the corporate world. We ran WebSphere at one place I worked, but it ran on the AS/400 which is what I did there anyway, but we didn't write the applications for it.

Right now, if you want to make yourself marketable to the corporate types, you need VMware, maybe some web development like Ajax, Java Script (completely not related to Java), and some Linux/Unix skills don't hurt either. I'm just not sure the Java stuff will be worth what you put in to it.

-Tim

---

### Post by Vegan on 2009-03-22
Well I am increasingly comfortable with my Linux server and have been accumulating more.

As for marketability, that is tough. Speaking Linux does have an upside so that is why my web server is Linux. But why stop there, can it do more? So hence, why not java?

As for an application server, I think maybe I was a little off the mark. I have MySQL so can it do the job, seems OK to me. So I see java as a language and my as the application developer.

Its a change of page from PHP and HTML/CSS on the site.

One idea in mind for an application, games on the web site in Java. Why not?

I saw some examples of java pages and it like what I wanted to achieve, AJAX like functionality. I liked the code example to dynamically make a table for displaying rows from a database.

I like the code to live edit a grid of numbers and add rows. Makes a web based spreadsheet possible. 

This is what I am looking at. Looks better than what I have now.

---

### Post by windependence on 2009-03-23
Well, good luck at that. My final exam in one of my Java classes was to write a card game in Java. It was NOT easy, I have to tell you.

-Tim

---

### Post by xymor on 2009-03-23
I don't like installing java and tomcat though apt-get and I find the difficulty of installing it otherwise to make up for having a more up-to-date environment. 

All you need to do is 4 steps:

1. get java (download linux jre and expand it somewhere)
2. Add JAVA_HOME=/<somewhere> and PATH=$JAVA_HOME/bin:$PATH to /etc/bash.bashrc

Now you have java running. Type java -version to test. 

3. get tomcat (download and expand it somewhere)
4. run <somewhere>/bin/startup.sh

That's it. It should be listening on port 8080. Simply drop war files in the <somewhere>/webapps and tomcat will start serving them. 

Here's the tomcat official docs for more in depth configs: [http://tomcat.apache.org/tomcat-6.0-doc/index.html](http://tomcat.apache.org/tomcat-6.0-doc/index.html)

---

### Post by Vegan on 2009-03-23
My goal is to server JSP and JSPX type web pages. I now have java available on the command line so as far as I see the mime types are really all I need to use java with my web server.

I wanted to have an integrated environment. A pure HTML "hello world" document is a legal Java page.

Adding a for loop allows me to draw as many rows as needed for a data source.

---

