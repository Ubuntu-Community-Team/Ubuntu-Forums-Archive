---
title: "Zend Studio and localhost - Forbidden error"
date: 2010-10-30
forum: Server Platforms
---

### Post by slandau88 on 2010-10-30
Okay so basically, I switched my DocumentRoot in Apache2 default to look like this:
  DocumentRoot /home/scott/MySite/
  That works. I have a file called index.php in that root.


  I created a Zend Studio project, pointing to /home/scott/MySite/, and  was able to create my project use this line as it's source, modify the  .php file and see the change when I navigate to localhost in my browser.


  Now, in Zend I created a folder called 'Index', and placed my  index.php file in there, because I want to separate my files in the  project to things like Database/, Index/, Login/, etc. all different  folders. Now, when I navigate to localhost, I get:


  You don't have permission to access / on this server.


  When I place the index.php file back in the main root it works fine again.


  I tried changing the apache2 default DocumentRoot to look like this:


  DocumentRoot /home/scott/MySite/Index/


  But that doesn't work either. Is there a way to get all this to work  and have like my folder structure be able to separate all the logic for  the project as well as apache2 still find my index.php and be able to  call all the files it calls correctly?


  Thanks guys.

---

