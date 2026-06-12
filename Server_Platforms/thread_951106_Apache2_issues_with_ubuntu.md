---
title: "Apache2 issues with ubuntu"
date: 2008-10-17
forum: Server Platforms
---

### Post by emada on 2008-10-17
Hello

Ok i removed apache2 via apt-get --purge remove apache2 and noticed it didnt rm /etc/apache2 dir so i deleted it my self and now when i run sudo apt-get install apache2 it says it installed but there is no /etc/apache2 dir anymore. i dont know what to do next. its broken for ever isnt it?? :( 

-ae

---

### Post by emada on 2008-10-17
ok i dled apache2 source and installed it that way which still didnt give me back /etc/apache2 dir so i deleted /usr/sbin/apache2 "because sudo make uninstall didnt work and thats where it said it installed to" and then did apt-get install apache2 again which didnt give me /etc/apache2 despite it saying its installed but now when i do sudo /etc/init.d/apache2 restart it says "No apache MPM package installed" which before i started messing around it didnt say this...someone please help me before i blow this thing up with my mindless messing around

---

### Post by cariboo on 2008-10-17
Did you make sure before you started deleting things that apache2 was not still running. When you uninstall apache2 you also have to uninstall the following files:

> 
apache2-mpm-event
    Event driven model for Apache HTTPD
apache2-mpm-itk
    multiuser MPM for Apache 2.2
apache2-mpm-prefork
    Traditional model for Apache HTTPD
apache2-mpm-worker
    High speed threaded model for Apache HTTPD 

If you remove the above files, you may be able to reinstall it.

Jim

---

### Post by emada on 2008-10-18
tyvm for the fast reply cariboo907 after about five more hours of searching i found this little diamond [http://ubuntuforums.org/showpost.php?p=3227009&postcount=26](http://ubuntuforums.org/showpost.php?p=3227009&postcount=26) which says what you just told me to do :D again thank you for the help and the fast reply. you rock and w/o ppl like you ppl like me would be lost and forever be a victim of M$. you :guitar:

---

