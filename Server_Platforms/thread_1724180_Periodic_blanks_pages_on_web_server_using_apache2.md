---
title: "Periodic blanks pages on web server using apache2"
date: 2011-04-08
forum: Server Platforms
---

### Post by lebbok on 2011-04-08
I am a newbie and my training is as an Elementary School Teacher.  I am a "System Administrator" at our school and have a web server that has been setup to host a grading program. 

The problem I am facing is that I am experiencing periodic blank pages when accessing the grading program. The program is written in php and works most of the time, but as we have come to the end of our quarter and there is a high load on the pages as staff are inputting comments and the pages seem to get lost and when I hit refresh a couple of time it returns, sometimes without saving the information.

This problem seems to have started since our last update on the web server. 

I would appreciate any help or ideas. Thanking all in advance.

---

### Post by t3r0 on 2011-04-08
Timeout maybe? Enable php error logging and see if there are any errors there.. You could try increasing php max_execution_time or better solution is to optimize our software...  

- Tero

> **lebbok said:**
> I am a newbie and my training is as an Elementary School Teacher.  I am a "System Administrator" at our school and have a web server that has been setup to host a grading program. 

The problem I am facing is that I am experiencing periodic blank pages when accessing the grading program. The program is written in php and works most of the time, but as we have come to the end of our quarter and there is a high load on the pages as staff are inputting comments and the pages seem to get lost and when I hit refresh a couple of time it returns, sometimes without saving the information.

This problem seems to have started since our last update on the web server. 

I would appreciate any help or ideas. Thanking all in advance.

---

### Post by SeijiSensei on 2011-04-08
This sounds more like a problem with the performance of the back-end database. Can you give us a few specifics like the capabilities of the server (memory in particular), the operating system involved, the database it uses, and any details or a link to information about the program itself?  Is this a home-grown, open source, or commercial application?

---

### Post by cabaro on 2011-04-08
Also is every visit on the webpage generating database queries or backend generating static output for the webpage?

---

