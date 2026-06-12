---
title: "Great Open Source apps, easy install &amp; run in less than 10min"
date: 2009-04-23
forum: Server Platforms
---

### Post by bmullan on 2009-04-23
For those of you wanting to get some of the more popular Open Source applications running on Ubuntu and/or on Ubuntu/EC2
be sure to check out [http://bitnami.org/]("http://bitnami.org/")

**Nearly turn-key** installation as they've done all the hard work for you.   Their model builds a .bin file which you chmod 755 once you've copied it to your server/workstation,
then you execute the file.   It will ask you a few various respective installation questions then install the software for you.  In the app directory entry for each application there is
also an uninstall program to remove that same application.

Start by installing the LAMP, Ruby etc stacks then go on to install the other various applications that interest you.

NOTE 1:  if you install LAMP, then later want to install an application read the BitNami menu for that app carefully as there are often 2 choices.  One is for a .bin file that is a bundled package of apache etc and the app, the other assumes that the apache etc are already installed and the .bin only includes the app --- much smaller and much faster to install.

NOTE 2: during installations of some of the applications they will prompt you for the IP address and the default provided is the INTERNAL AMAZON IP address (if you are on EC2)... you need to be SURE to change that to the external IP address of your EC2 instance.  

Example:   in AWS Management Console if your instance indicates your PUBLIC DNS is
                                                               Public DNS: ec2-174-129-87-194.compute-1.amazonaws.com

   then your public IP address is 174.129.87.194

Lastly, If you have the skills try to help BitNami expand this list as what they are doing is really great work to add to capabilities of the Linux community.

The following are BitNami's current list of pre-built applications ready to install and use... each will take you about 10 minutes to get up and running.

**Infrastructure**

    * DjangoStack
    * JRubyStack
    * LAMPStack
    * LAPPStack
    * MAMPStack
    * MAPPStack
    * RubyStack
    * SAMPStack
    * WAMPStack
    * WAPPStack

**Blog**

    * Roller
    * WordPress

**Bug-Tracking**

    * Mantis
    * Redmine
    * Trac

**Business Intelligence**

    * JasperServer

**CMS**

    * Alfresco
    * Drupal
    * Enano CMS
    * eZ Publish
    * Joomla
    * KnowledgeTree

**CRM**

    * SugarCRM

**ECM**

    * Alfresco
    * KnowledgeTree

**Forum**

    * phpBB

**Photo Sharing**

    * Coppermine Photo Gallery
    * Gallery

**Planning**

    * Tracks

**Poll Management**

    * Opina

**Portal Server**

    * JasperServer
    * Liferay

**Version Control**

    * Subversion

**Wiki**

    * DokuWiki
    * MediaWiki

**eLearning**

    * Moodle

**BitNami Stacks**

BitNami stacks make it incredibly easy to install your favorite open source software. Application stacks include an open source application and all the dependencies necessary to run it, such as Apache, MySQL and PHP or Ruby. 

All you need to do is download the Stack, provide a few pieces of information when prompted by the installation wizard, and that's it. By the time you click 'finish', your new application will be ready to run. All stacks have been packaged using BitRock's multiplatform installer.


**BitNami Application Stacks**

Which application should we package next?
  	  	 
  	
WordPress Joomla Roller Liferay

DokuWiki MediaWiki Drupal phpBB

Mantis Opina KnowledgeTree Redmine

Trac Alfresco Moodle Subversion

Tracks JasperServer eZPublish SugarCRM

Coppermine Photo Gallery EnanoCMS Gallery 	

**BitNami Infrastructure Stacks**
Infrastructure stacks are designed for developers and system administrators and provide you a way of installing a LAMP or Ruby environment, but do not include any extra applications. It is not necessary to download an infrastructure stack to use an application stack.

Which application should we package next?
  	  	 
  	
WAMPStack 	LAMPStack 	MAMPStack 	SAMPStack

WAPPStack 	LAPPStack 	MAPPStack 	
	   	  	 
RubyStack 	JRubyStack 	DjangoStack

---

