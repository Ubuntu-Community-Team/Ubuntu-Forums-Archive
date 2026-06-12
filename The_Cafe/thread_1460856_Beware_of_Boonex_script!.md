---
title: "Beware of Boonex script!"
date: 2010-04-23
forum: The Cafe
---

### Post by msnonline on 2010-04-23
I would like to warn all webmasters who want to create a social  networking site not to use Boonex. Boonex is a scam.

 Boonex  problem nr1. No coding standard  
 Boonex is writen by several  people using different technologies. Its main base (Dolphin) is writen  in pure php with its own template engine and forum  (Orca) uses xlst.  That has large negative impact to integration of forum in site and site  in forum. When coding, please use single technology and template  system.  
 Whats even worser, different parts of dolphins code  itself is writen by completely different people, and very in the hurry.  So everyone has its own imagination how to interact with different parts  of the code. It is very tricky to modify code that way to suit site  needs.  
 Boonex problem nr2. Template engine and separation of  code/design/database 
 This problem in dolphin/boonex needs a  point on its own. Boonex uses custom template system ( that should be  called layout system). The blocks of generated html code are pased to  specific places in the template. That creates a big headache for  programers as they need to search through code for the place where some  box is generated. It might be generated in template, or in specific  function in one of numerous includes. And so on. Even pligg has better  templating than this.  
 It is very tricky to rip boonex  templating apart, as whole coding is based on such poor programming  practice. They would be better off using existing template system like  smarty or similar one.  
 This leads to problem nr3 
 Boonex  problem nr3. Crapy use of Database 
 We saw serveral other  competing sites launched on boonex, but we did not care much. Why?  Becouse when they reach 500-1000 daily visitors they will break apart.  The reason for it is very bad programming and use of database.  
  For example, boonex uses profile builder which assigns fields to  profiles. So the output of profile uses more than one table and is quite  inefficient.  
 Also, there is a nice 20-30 query overhead on  each page display to fetch all the configuration values from table.  Silly, isn’t it ? They would be FAR better of using a file for  configuring sofware or caching it in php file like it is done in most of  the systems.  
 Another simple problem. When boonex wants to  display a profile being online it additionally check database for its  status. But that data was pulled from database already. So 20 useless  queries again.  
 Resume 
I would not suggest using boonex  if you want to keep your programmers sane. We have have changed the code  almost completely for now, and you will need to do that too. Boonex is a  scam. Try googling "boonex scam" first.  [http://www.google.com/search?q=boonex+scam](http://www.google.com/search?q=boonex+scam) or boonex dolphin scam.

---

### Post by dragos240 on 2010-04-23
Please don't spam our forums. You've posted this EXACT SAME topic in the past minute.

---

### Post by Khakilang on 2010-04-23
Ban the msnonline.

---

### Post by Tristam Green on 2010-04-23
[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]

use it, and stop making demands in the middle of a thread lol.

---

