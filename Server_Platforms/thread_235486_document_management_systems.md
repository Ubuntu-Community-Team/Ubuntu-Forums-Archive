---
title: "document management systems"
date: 2006-08-13
forum: Server Platforms
---

### Post by jurzi on 2006-08-13
I'm running Ubuntu 6.06 LAMP server and am now searhing for a proper document management server software for it. My expectations for the functionality include:
 - version management
 - workflow for document review and approval
 - access control for each file and/or folder
 - check-out (=document locked when being edited)
 - potentially integration with MS Office when editing Word or Excel files

From commercial products something similar would be Documentum's eRoom. But this time I need an open source package. I've done a lot of Googling but haven't found anything proper. Any suggestions from the Forum users?

---

### Post by Blind Sight on 2006-08-13
I've played with Knowledge Tree and it may do the job. They have both commercial and open source versions:

[http://www.ktdms.com]("http://www.ktdms.com")

Hope that helps.

---

### Post by cantormath on 2006-08-13
> **jurzi said:**
> I'm running Ubuntu 6.06 LAMP server and am now searhing for a proper document management server software for it. My expectations for the functionality include:
 - version management
 - workflow for document review and approval
 - access control for each file and/or folder
 - check-out (=document locked when being edited)
 - potentially integration with MS Office when editing Word or Excel files

From commercial products something similar would be Documentum's eRoom. But this time I need an open source package. I've done a lot of Googling but haven't found anything proper. Any suggestions from the Forum users?

A really good play by play, with pictures, howto for setting up LAMP system, install to launch.
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
Some of your answers may be here.

---

### Post by jurzi on 2006-08-14
> I've played with Knowledge Tree and it may do the job. They have both commercial and open source versions:

[http://www.ktdms.com](http://www.ktdms.com)

Hope that helps.

Thanks Blind Sight, the feature list on their website seems very promising. If any other forum users are aware of something similar, please let me know. I'll give Knowledge Tree a try tonight and post an update here.

---

### Post by jurzi on 2006-08-14
It turned out that Knowledge Tree is only for PHP versions 4.3 and above but not for 5.X. I wouldn't like to downgrade because other applications require 5.X so I'm back to the starting point.

Edit: ktdms forums indicate that it works on PHP5 as well even though not supported by the supplier... I'll give it a try.

---

### Post by jurzi on 2006-08-16
After 2 nights of playing with KnowledgeTree, I decided to go for it. It's far from perfect but still clearly the best open source DMS that I've seen. Might even go for the commercial version at a later stage. I'm now half-way through translating it to my local language. Despite of the warnings, it runs without problems on PHP5. The authorization concept of the system is rather complex (compared to what you get out of it) and I've also struggled a little with customizing the contents of the email notifications, but otherwise I'm very happy with the system!

---

### Post by stfu on 2006-11-30
> **jurzi said:**
> After 2 nights of playing with KnowledgeTree, I decided to go for it. It's far from perfect but still clearly the best open source DMS that I've seen. Might even go for the commercial version at a later stage. I'm now half-way through translating it to my local language. Despite of the warnings, it runs without problems on PHP5. The authorization concept of the system is rather complex (compared to what you get out of it) and I've also struggled a little with customizing the contents of the email notifications, but otherwise I'm very happy with the system!

Did you continue using the Knowledge Tree? Did you try the commercial version or the Open Source? I'm thinking of trying it too. I need the client for scanning the documents though.

---

